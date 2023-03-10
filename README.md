# Programming Language Ideas

### Philosophy and values (Tentative)
- Orthogonal features
- Simplicity where reasonable
- Try to make illegal states irrepresentable.

### Features:
- Types (stricter than C, looser than Rust)
- algebraic effects
  - [Koka can use algebraic effect to implement async](https://www.forrestthewoods.com/blog/learning-jai-via-advent-of-code/#runtime_reflection), which seems really useful.
- Linear types
- Traits that specify the existence of member variables or member functions:
  - These could also come with default implementations
  - TODO: Should the struct that bolts on the trait need the member declared?
      - Probably yes?
- Package manager
- Build script + build instructions and flags inside the file if necessary
  - I'd like to be able to point the compiler at a file and have that single file build one it's own.
  - However, overall build scripts make sense to automate other build tasks.
- Metaprogramming:
  - Being able to convert code into data and vice versa
  - Being able to iterate through struct members
  - Being to unroll loops at compile time
  - Generics
  - [JAI's reflection](https://www.forrestthewoods.com/blog/learning-jai-via-advent-of-code/#runtime_reflection)
- Errors/excetions
  - Try the Midori [try syntax](http://joeduffyblog.com/2016/02/07/the-error-model/)
- Contracts (invariants for function start and end)
  - [Midori syntax again](http://joeduffyblog.com/2016/02/07/the-error-model/)
- Defer
- A Rust-like match
- Nurseries for stdlib concurrency
- Doc generation
  - This needs to be a priority from the start (unlike what Zig)
  - Sphinx but better
    - Sphinx seems to force you into a certain document layout
    - Maybe be more like LaTeX, which allows you to do what you want more (manual links and labels and sections)
  - Docs will be near the code
  - Image support (assuming images are already sitting on the filesystem)
  - Maybe dependency graphs and links to other docs
  - Have links to source too
  - Have a search mechanism
  - **Organize layout as "What can I do with this type?"**
    - Maybe by listing all the functions that take or return that type
    - Or allow searching by return or argument type
  - Allow docs to be html, single page html file, or PDF (through latex maybe)
- Tagged union support (Like Zig)
- Find a way to iterate over objects that have a certain trait.

### Implementation
- Start with an interpreter in C, then make a transpiler to C.
  - If the interpreter needs a VM, then consider borrowing from lua
  - OR making a VM that's a stack-like machine
    - The big difference will be that you can access things that are offset from the top of the stack
    - It will probably still need a couple registers though.
