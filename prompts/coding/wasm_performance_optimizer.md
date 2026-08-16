# Coding Prompt: WebAssembly (WASM) Module & Runtime Performance Optimizer

## Purpose
Optimize Rust, C/C++, or AssemblyScript code compiled to WebAssembly (WASM) for high-throughput browser and edge runtime execution.

## Inputs
- `WASM_SOURCE_CODE`: Source code intended for WASM compilation or WAT (WebAssembly Text Format).
- `TARGET_RUNTIME`: Execution environment (e.g., Browser V8, Cloudflare Workers, Wasmtime, Node.js).

## Instructions
1. Inspect `WASM_SOURCE_CODE` for memory allocation bottlenecks, excessive JS-WASM boundary crossings, and unoptimized loops.
2. Optimize linear memory layout, buffer passing mechanisms, and pointer arithmetic to minimize copy overhead.
3. Apply WASM-specific compiler flags, feature proposals (SIMD, Multi-threading, Bulk Memory Operations), and code structures.
4. Refactor DOM or host-environment interactions to minimize synchronous FFI calls.
5. Benchmark binary size reductions (wasm-opt) and execution throughput gains.

## Constraints
- Ensure target WebAssembly features are compatible with `TARGET_RUNTIME`.
- Preserve memory safety and guard against out-of-bounds linear memory access.

## Expected output
- **Optimized WASM Source Code**: Clean, refactored code optimized for WASM compilation.
- **Memory & Host Interface Optimization Plan**: Detailed explanations of buffer and FFI improvements.
- **Compilation Flag Pipeline**: Recommended `wasm-pack` / `emcc` / `wasm-opt` build flags.
