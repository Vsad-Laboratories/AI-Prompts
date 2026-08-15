# Debugging Prompt: Network Packet & PCAP Protocol Analysis

## Purpose
Examine packet capture (PCAP) summaries, Wireshark text dumps, and network telemetry logs to diagnose connection drops, latency anomalies, TCP window stalls, and TLS handshake failures.

## Inputs
- `PCAP_TEXT_LOG`: Formatted packet capture log (e.g., tshark or tcpdump output) showing IP headers, TCP flags, sequence numbers, and packet timestamps.
- `NETWORK_TOPOLOGY`: Network paths, load balancers, proxies, dynamic NAT gateways, or firewalls between client and server.
- `EXPECTED_BEHAVIOR`: Target protocol exchange (e.g., gRPC over HTTP/2, WebSocket handshake, TLS 1.3 negotiation).

## Instructions
1. Analyze packet sequence numbers, TCP flags (SYN, ACK, FIN, RST), and timestamps in `PCAP_TEXT_LOG`.
2. Detect common transport failure modes:
   - TCP Retransmissions and Duplicate ACKs (network loss or buffer bloat).
   - Zero Window Alerts (receiver process frozen or socket buffer exhausted).
   - TLS Handshake Alerts (cipher mismatch, SNI failure, certificate untrusted).
   - Connection Reset (RST) injections by intermediate middleboxes or firewalls.
3. Isolate whether latency originates in transport network propagation vs. application socket processing delays.
4. Provide actionable OS kernel parameter tweaks (`sysctl`) or network infrastructure recommendations.

## Constraints
- Do not assume network packet loss without checking duplicate ACK patterns.
- Distinguish between application-layer HTTP errors and transport-layer TCP/TLS failures.

## Expected output
- **Packet Sequence Timeline Analysis**: Chronological breakdown of anomalous packets.
- **Protocol Failure Point**: Pinpointed TCP/TLS/Application layer failure step.
- **Infrastructure & Kernel Remediation**: Fix recommendations for OS socket configuration, MTU, or middlebox routing.
