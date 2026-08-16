# Debugging Prompt: Real-Time WebSocket & Connection Pool Leak Detector

## Purpose
Isolate memory leaks, hanging file descriptors, socket exhaustion, and connection leaks in long-lived real-time applications (WebSockets, gRPC, HTTP Keep-Alive).

## Inputs
- `NETSTAT_LSOF_LOGS`: System logs, `netstat`, `ss`, `lsof`, or server memory profiles showing active socket connections.
- `SERVER_CODE`: Connection handling, heartbeat ping/pong, and cleanup routines.

## Instructions
1. Inspect `NETSTAT_LSOF_LOGS` to analyze TCP socket states (`CLOSE_WAIT`, `FIN_WAIT2`, `ESTABLISHED`) and thread/FD growth rates.
2. Review `SERVER_CODE` to locate missing socket close calls, broken event listener unbindings, or unhandled ping/pong timeouts.
3. Diagnose connection pool leak causes (e.g., unclosed client sessions, missing ping frames, TCP keepalive misconfigurations).
4. Provide immediate remediation code introducing heartbeat timers, backoff logic, and mandatory connection cleanup blocks.
5. Detail monitoring alerts and socket metric tracking guidelines.

## Constraints
- Explicitly check for dangling asynchronous promises or callbacks retaining closed socket handles.
- Address both server-side memory leaks and client-side reconnection storms.

## Expected output
- **Socket & FD Connection Diagnostics**: Breakdown of leaked connection states and memory usage.
- **Code Bug Isolation**: Specific line-by-line identification of missing socket cleanup logic.
- **Refactored Connection Lifecycle Code**: Production-ready code fix implementing robust cleanup and heartbeats.
