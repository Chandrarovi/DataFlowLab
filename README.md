# DataFlowLab — CFG-Based Optimizer with Data-Flow Analysis

Builds on MiniCC's three-address code; partitions into basic blocks, constructs CFGs, applies local DAG-based CSE/constant folding/copy propagation, runs iterative worklist data-flow analyses (liveness, constant propagation, available expressions), and performs liveness-driven dead-code elimination. Includes Graphviz CFG visualization.

## Architecture Pipeline

1. **Frontend**: Lexing -> Parsing -> CodeGen (extends MiniCC)
2. **CFG Construction**: Linear TAC -> Basic Blocks -> CFG
3. **Local Optimizations**: DAG-based CSE, constant folding, and copy propagation
4. **Global Data-Flow**:
   - Constant Propagation
   - Liveness Analysis
   - Available Expressions
5. **Dead-Code Elimination**: Liveness-driven removal of unused assignments
6. **Backend**: CFG -> Linear TAC -> MiniCC VM execution

## Build & Usage

```bash
make
./dataflowlab [options] <file.mc>
```

**Options:**
- `--tac`: Print TAC before optimization
- `--opt-tac`: Print TAC after optimization
- `--stats`: Print optimization statistics
- `--graphviz`: Generate `.dot` files in current directory
- `--no-opt`: Disable all optimizations
- `--no-local`: Disable local optimizations
- `--no-constprop`: Disable constant propagation
- `--no-dce`: Disable dead code elimination
- `--no-avail`: Disable available expressions

## Benchmarks

| Test | Original | Optimized | Reduction | Status |
|------|----------|-----------|-----------|--------|
| Constants | ... | ... | ... | ... |

*(Run `run_benchmarks.ps1` to see populated results)*

## Project Structure
Extends `MiniCC` located in `../MiniCC`. Contains custom data-flow and optimization passes within `src/`.
# DataFlowLab
