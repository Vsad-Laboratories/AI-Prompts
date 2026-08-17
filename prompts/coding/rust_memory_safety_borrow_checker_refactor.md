# Rust Memory Safety & Borrow Checker Refactoring Guide

## Purpose
Guide engineers in refactoring legacy Rust code or unsafe memory blocks to resolve strict borrow checker errors (`E0382` use of moved value, `E0502` cannot borrow as mutable, `E0506` cannot assign to borrowed value, `E0515` returns value referencing local variable), eliminate unnecessary heap allocations (`.clone()`), and safely encapsulate `unsafe` memory operations.

## Inputs
- `RUST_SOURCE_CODE`: Rust file, function, or module exhibiting borrow checker compiler errors or performance bottlenecks.
- `COMPILER_ERROR_LOG`: Output from `cargo check` or `rustc` including error codes, span annotations, and help hints.
- `PERFORMANCE_CONSTRAINTS`: Guidelines regarding acceptable `.clone()` allocations, thread safety (`Send`/`Sync`), or zero-copy memory requirements.

## Instructions
1. **Analyze Compiler Diagnostic**: Inspect `COMPILER_ERROR_LOG` alongside `RUST_SOURCE_CODE`. Map out variable ownership scopes, active references, lifetimes (`'a`), and mutation boundaries.
2. **Identify Borrowing Antipattern**:
   - *Self-Referential Structs*: Attempting to store a reference to a field within the same struct.
   - *Iterative Mutation*: Mutating a collection while holding an active reference or iterator over the same collection.
   - *Escaping Local Lifetimes*: Returning references to stack-allocated variables created within the function body.
   - *Closure Environment Capture*: Attempting to move variables into closures while retaining outer access.
3. **Formulate Idiomatic Rust Refactoring Strategy**:
   - **Lifetime Parameterization**: Annotate explicit lifetime relationships (`'a`, `'b`) when references cross function boundaries.
   - **Interior Mutability**: Utilize `RefCell<T>`, `Mutex<T>`, or `RwLock<T>` when shared mutable access is strictly required at runtime.
   - **Smart Pointers & Reference Counting**: Introduce `Arc<T>` or `Rc<T>` for multi-owner pointer graphs.
   - **Data Structure Redesign**: Re-architect indices/handles (`SlotMap`, `Arena` allocation, array index identifiers) to eliminate complex reference graphs.
   - **Zero-Copy Slices**: Utilize `&str`, `&[T]`, `Cow<'a, B>` to eliminate unnecessary `.to_string()` or `.clone()` calls.
4. **Encapsulate Unsafe Blocks**: If `unsafe` blocks are present, audit raw pointer operations (`*const T`, `*mut T`) and enforce strict safety invariants with detailed safety documentation comments (`// SAFETY:`).
5. **Generate Refactored Source Code**: Output memory-safe, idiomatic, fully compiled Rust code with zero borrow checker warnings.

## Constraints
- **Zero Heap Overhead Default**: Prefer lifetime annotations, borrowing, or arena designs over naive `.clone()` calls.
- **Mandatory Safety Documentation**: Every remaining `unsafe` block MUST contain a formal `// SAFETY:` invariant comment.
- **Idiomatic Rust Style**: Adhere strictly to standard Rust conventions (`clippy` compliant, `rustfmt` formatted).

## Expected Output Format
```markdown
### 1. Borrow Checker Error Diagnostics
- **Primary Error Code**: `[E0382 / E0502 / E0506 / E0515]`
- **Root Cause**: [Explanation of ownership/lifetime scope collision]
- **Ownership Diagram / Lifetime Mapping**:
```text
var x: active immutable borrow 'a ---------------------------->
var y: attempted mutable borrow 'b (COLLISION) --------------^
```

### 2. Architectural Refactoring Approach
- **Selected Idiom**: [Explicit Lifetimes / Arena Handles / Cow / Interior Mutability / Split Borrows]
- **Performance Impact**: [Zero-copy preservation / Allocation count reduction]

### 3. Memory-Safe Refactored Code
```rust
// SAFETY: [Safety invariant documentation if unsafe used]
pub fn refactored_function<'a>(input: &'a ProcessingContext) -> Result<ProcessedOutput<'a>, EngineError> {
    // Idiomatic Rust implementation
}
```

### 4. Verification & Cargo Check Validation
- **Borrows Resolved**: [Confirmation of clean borrow graph]
- **Lifetime Safety**: [Explanation of how references remain valid for lifetime 'a]
```

## Evaluation Criteria
- **Compilation Correctness**: Refactored Rust code compiles cleanly without borrow checker errors or clippy warnings.
- **Zero-Copy Efficiency**: Resolves borrow errors without introducing performance-degrading deep clones.
- **Unsafe Safety Verification**: Sound encapsulation and valid invariant reasoning for all raw pointer interactions.

## Failure Considerations
- **Clone Spraying**: Resolving borrow errors by naively dropping `.clone()` on every variable without addressing design issues.
- **Unsound Unsafe**: Hiding borrow checker errors inside `unsafe` blocks without ensuring underlying memory layout safety.
