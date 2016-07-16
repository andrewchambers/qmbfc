# qmbfc

qmbfc is a [brainfuck](https://en.wikipedia.org/wiki/Brainfuck) compiler written in the [Myrddin](https://myrlang.org) programming language.
qmbfc emits [QBE](http://c9x.me/compile/) intermediate assembly, which is then translated to x86_64 assembly via the qbe
backend executable.

# lmbfc

This is a port of qmbfc which emits llvm IR contributed by Quentin Carbonneaux (The author of qbe).
It serves as a good comparison of the minimum essentials of emitting llvm or qbe IR directly as text.

## Building

(Only tested on linux)

Install myrddin from source and then run in the project directory:

```
$ mbld
```

You should then have two binaries ./qmbfc and ./lmbfc corresponding to the qbe and
llvm versions of the binary.

## Running the compilers

You must have llvm and qbe to run either version of the compiler.

For example, to execute the qbe version and run the compiled binary.

```
./qmbfc < examples/mandlebrot.bf > mandlebrot.ssa && qbe < mandlebrot.ssa > mandlebrot.s && gcc mandlebrot.s && ./a.out
```

To execute the llvm version and run the compiled binary.

```
./lmbfc < examples/mandlebrot.bf > mandlebrot.llvm && llc < mandlebrot.llvm > mandlebrot.s && clang mandlebrot.s && ./a.out
```

## Links

- [QBE home page](http://c9x.me/compile/)
- [Myrddin compiler and stdlib](https://github.com/oridb/mc)
- [My C compiler written in myrddin emitting qbe IR](https://github.com/andrewchambers/qc)
- [The suckless C compiler targetting qbe IR](http://git.suckless.org/scc/)
