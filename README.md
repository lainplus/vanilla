# vanilla
### a small c compiler

vanilla is a small C compiler that implements most C11 features.
even though it still probably falls into the "babby's first compiler"
category just like other small compilers do, vanilla can compile
things such as [git](https://git-scm.com/), [sqlite](https://sqlite.org),
[libpng](http://www.libpng.org/pub/png/libpng.html) and
[itself](https://github.com/lainplus/vanilla) without making modifications
to the programs themselves. generated executables of these programs pass
their corresponding test suites. so, vanilla actually supports a wide
range of C11 features and is able to compile hundreds of thousands of lines
of "real-world" C code correctly.

### status

vanilla supports almost all mandatory features and most optimal features
of C11 and some GCC language extensions.

features that are often missing in a small compiler but supported by
vanilla include but not limited to:

- preprocessor
- float, double and long double / x87 80-bit floating point numbers
- bit-fields
- alloca()
- variable-length arrays
- compound literals
- thread-local variables
- atomic variables
- common symbols
- designated initializers
- L, u, U, and u8 string literals
- functions that take or return structs as values, as specified by the
  x86-64 SystemV ABI

vanilla does not support complex numbers, K&R-style function prototypes
and GCC-style inline assembly. digraphs and trigraphs are intentionally
left out.

vanilla outputs a simple error message when it finds an error in the
source code.

there's no optimization pass. vanilla can and will spit out terrible code
which is probably 2x slower than GCC's output. i'll add one eventually.

### internals

vanilla consists of the following stages:

- tokenize: takes a string as an input, breaks it into a list of tokens
  and returns them.

- preprocess: takes a list of tokens as input and outputs a new list of
  macro-expanded tokens. it interprets preprocessor directives while
  expanding macros.

- parse: recursive descendent parser which constructs abstruct syntax
  trees from the output of the preprocessor. it also adds a type of
  each AST nodes.

- codegen: emits an assembly text for given AST nodes. i hated writing
  this the most.

anyway enjoy
