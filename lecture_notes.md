# 1. Introduction and Matrix Multiplication

- **Performance**: the currency of computing; it can be traded for other properties like readability or extensibility of code
- Until 2004, Moore's law and "Dennard Scaling" were primarily responsible for performance improvements -- hardware scaling
- More recently, parallelism and multi-core processors were introduced, but require software to utilize this hardware effectively (GPUs, FPGAs, vector units, cache hierarchies) 

## 53,292x MatMul speedup
![square matmul example](assets/1_square_matmul.png)
- Python vs. Java vs. C
    - Python is interpreted
    - Java is compiled to byte-code, which is JIT (just-in-time) compiled to machine code
    - C is compiled directly to machine code

- Interpreters trade off performance for high-level features, like dynamic code alteration
- JIT compilers can bridge this gap, compile frequently used code chunks into machine code _(is this like hotspot JIT optimizations?)_
- Row-major / column-major matrices in memory
- Loop ordering is important because of cache locality
- The compiler can apply different levels of optimization (clang flag -O[0-3])
- Multicore parallelism, speedup can outweigh scheduling overhead
- Tiled matmuls, allows for fewer memory accesses by better taking advantage of the cache (using NxN blocks)
    - This can be extended for a cache hierarchy
- Parallel D&C matmul, using nxn threshold to prevent function-call overhead from outweighing improvement 
![recursive matmul example](assets/1_recursive_matmul.png)
- Vectorize operations using single-instruction stream, multiple-data stream (SIMD)
    - This can be done through the compiler or manually using intrinsic instructions (AVX)
