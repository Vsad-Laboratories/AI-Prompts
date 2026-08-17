# eBPF Kernel Network Latency & Packet Drop Profiler

## Purpose
Analyze `bpftrace`, `bcc`, eBPF kernel tracepoint logs, and Linux network stack performance counters to isolate, diagnose, and eliminate deep kernel network packet drops, TCP retransmissions, socket backlog queue overflows, and SoftIRQ CPU processing bottlenecks.

## Inputs
- `EBPF_TRACE_OUTPUTS`: Stack trace dumps from `kfree_skb`, `tcp_retransmit_skb`, `netif_receive_skb`, or `skb_consume_udp` tracepoints.
- `NETWORK_STACK_METRICS`: Outputs from `nstat`, `ethtool -S <eth0>`, `/proc/net/snmp` (`TcpExtListenDrops`, `TcpExtListenOverflows`, `TcpExtTCPTimeouts`), `ip -s link`.
- `KERNEL_SYSCTL_CONFIG`: Active kernel network parameters (`net.core.somaxconn`, `net.ipv4.tcp_max_syn_backlog`, `net.core.netdev_max_backlog`, `net.netfilter.nf_conntrack_max`).

## Instructions
1. **Dissect Kernel `skb` Drop Stack Traces**: Parse `kfree_skb` tracepoint stack outputs. Map drop symbol locations to kernel subsystem functions:
   - `nf_hook_slow` / `ipt_do_table`: Netfilter / iptables firewall rule rejection.
   - `tcp_v4_rcv` / `tcp_v4_do_rcv`: Socket backlog queue or accept queue full (`ListenOverflows`).
   - `__netif_receive_skb_core`: Ring buffer / NAPI backlog exhaustion (`netdev_max_backlog`).
   - `ip_rcv` / `ip_forward`: Route lookup failure or TTL expired.
2. **Differentiate Network Loss vs Host Kernel Bottleneck**: Determine whether packet loss is driven by physical link degradation vs host OS kernel processing bottlenecks.
3. **Analyze Socket Queue Dynamics**:
   - **SYN Queue Drops**: Compare `tcp_max_syn_backlog` against incoming SYN packet rates.
   - **Accept Queue Overflow**: Compare `somaxconn` and socket backlog settings against application thread accept speed.
4. **Evaluate SoftIRQ & NAPI Core Balance**: Inspect `ksoftirqd/X` CPU utilization and RSS (Receive Side Scaling) multi-queue IRQ affinity across physical CPU cores using `/proc/interrupts`.
5. **Formulate Sysctl & Interface Optimization Strategy**:
   - Deliver precise kernel parameter tuning commands (`sysctl -w`).
   - Deliver ring buffer (`ethtool -G <eth0> rx <max>`) and Receive Packet Steering (RPS) configuration recommendations.
6. **Architect eBPF/XDP Early Packet Filtering (Optional High-Throughput Track)**: If drops are caused by malicious/DDoS traffic or iptables overhead, design an eBPF XDP (`XDP_DROP`) program snippet to drop packets at the NIC driver layer before `sk_buff` allocation.

## Constraints
- **Zero-Loss Target**: Recommended parameters MUST eliminate socket backlog and ring buffer packet drops under high PPS (Packets Per Second) load.
- **Provide Precise Sysctl Commands**: Deliver copy-paste `sysctl -w` and `/etc/sysctl.conf` parameters with explicit justification.
- **CPU Affinity Preservation**: Ensure multi-queue IRQ affinity recommendations balance interrupts evenly across non-NUMA bounded CPU cores.

## Expected Output Format
```markdown
### 1. eBPF Network Drop & Stack Trace Analysis
- **Primary Drop Location**: `[kernel_function_symbol]` (e.g., `tcp_v4_rcv+0x1a4`)
- **Drop Mechanism**: [Accept Queue Overflow / Netfilter Drop / NAPI Ring Backlog]
- **Diagnostic Stack Trace**:
```text
kfree_skb
  tcp_v4_rcv
  ip_protocol_deliver_rcu
  ip_local_deliver_finish
  __netif_receive_skb_one_core
```

### 2. Network Telemetry & Metric Mapping
| Metric Key | Value | Threshold / Limit | Status |
| :--- | :--- | :--- | :--- |
| `TcpExtListenOverflows` | 42,104 | 0 | CRITICAL OVERFLOW |
| `TcpExtListenDrops` | 42,104 | 0 | CRITICAL DROPS |
| `net.core.somaxconn` | 128 (Default) | Required: 4096 | SEVERE BOTTLENECK |

### 3. Kernel & Interface Tuning Remediation Plan
```bash
# 1. Expand socket accept queue and SYN backlog limits
sysctl -w net.core.somaxconn=4096
sysctl -w net.ipv4.tcp_max_syn_backlog=8192
sysctl -w net.core.netdev_max_backlog=10000

# 2. Expand NIC Ring Buffer
ethtool -G eth0 rx 4096 tx 4096
```

### 4. eBPF / XDP High-Performance Bypass (If Applicable)
```c
// XDP eBPF kernel program snippet for driver-level early packet filter
SEC("xdp")
int xdp_drop_malicious_filter(struct xdp_md *ctx) {
    // Early packet inspection and XDP_DROP before sk_buff allocation
    return XDP_PASS;
}
```
```

## Evaluation Criteria
- **Diagnostic Precision**: Accurately maps `kfree_skb` stack symbols to root cause kernel subsystem bottlenecks.
- **Tuning Effectiveness**: Proposed kernel sysctl tuning eliminates socket overflow metrics (`TcpExtListenOverflows`).
- **Low-Overhead Solutions**: Prefers kernel sysctl/XDP optimizations over heavy user-space logging or un-indexed firewalls.

## Failure Considerations
- **Generic Sysctl Dumping**: Outputting standard sysctl cheat-sheets without tying parameters to the specific eBPF trace drop point.
- **Ignoring Application Layer**: Tuning `somaxconn` without advising application developers to increase worker accept loop concurrency.
