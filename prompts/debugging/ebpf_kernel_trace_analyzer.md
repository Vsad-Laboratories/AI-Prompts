# Debugging Prompt: eBPF Kernel Tracing & Syscall Performance Profiler

## Purpose
Analyze `bpftrace`, `eBPF` program outputs, and Linux kernel syscall profiles to isolate deep I/O latency, kernel thread contention, and network stack bottlenecks.

## Inputs
- `EBPF_TRACING_OUTPUT`: Raw output logs from `bpftrace`, `bcc` tools (`syscount`, `biolatency`, `offcputime`), or `perf`.
- `KERNEL_ENVIRONMENT`: Linux kernel version, container runtime context, and storage/network driver specs.

## Instructions
1. Parse `EBPF_TRACING_OUTPUT` to identify high-latency kernel tracepoints, blocked syscalls, or slow kprobes.
2. Correlate kernel-level latency distribution histograms with user-space process threads and file descriptors.
3. Isolate root causes: disk I/O queuing, lock contention (futex), TCP socket backlogs, or memory page fault stalls.
4. Formulate OS kernel tuning (`sysctl`), I/O scheduler modifications, or code refactoring steps.
5. Provide actionable validation scripts to verify latency resolution.

## Constraints
- Base analysis strictly on kernel telemetry; do not confuse user-space CPU time with off-CPU wait time.
- Verify system safety of recommended `sysctl` modifications before applying in production.

## Expected output
- **Kernel Latency Breakdown**: Histogram analysis and top offending syscalls/kprobes.
- **Root Cause Isolation**: Exact kernel mechanism causing execution stalls.
- **Kernel Tuning & Optimization Strategy**: Recommended `sysctl`, mount options, or code fixes.
