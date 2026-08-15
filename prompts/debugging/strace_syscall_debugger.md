# Debugging Prompt: Syscall Tracing & OS I/O Bottleneck Profiler

## Purpose
Interpret `strace`, `dtrace`, or `ebpf` system call trace outputs to diagnose unexpected process freezes, disk I/O bottlenecks, file lock contention, and permission failures at the Linux OS interface.

## Inputs
- `STRACE_LOG`: Raw or summarized output from `strace -T -tt -e trace=file,process,network,ipc` or similar OS trace utilities.
- `TARGET_PROCESS`: Process binary, service description, and environment configuration.
- `SYMPTOM`: Unresponsive behavior, high system load, or silent crash observed by monitoring.

## Instructions
1. Filter `STRACE_LOG` for system calls returning high execution durations (`<0.05...>` elapsed time tags) or error codes (e.g., `ENOENT`, `EAGAIN`, `EACCES`, `ETIMEDOUT`).
2. Identify blocking I/O calls (`read`, `write`, `futex`, `select`, `epoll_wait`, `flock`) consuming thread execution time.
3. Detect file lock contention or slow storage filesystem interactions.
4. Locate missing dynamic libraries, misconfigured file permission paths, or zombie child processes (`wait4` failures).
5. Recommend OS kernel tuning, file descriptor limit increases (`ulimit`), or application I/O buffering fixes.

## Constraints
- Distinguish between benign wait calls (e.g., idle event loop `epoll_wait`) and blocking thread stalls.
- Ensure syscall analysis aligns with user permissions and container cgroup boundaries.

## Expected output
- **Top Blocking Syscalls**: Ranked list of time-consuming or failing system calls.
- **OS Resource Vulnerability Report**: File descriptor, locking, or permissions failure summary.
- **System & Application Fixes**: OS tuning parameters and application I/O optimization instructions.
