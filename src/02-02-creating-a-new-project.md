## Creating a new project

To start a new project with Cargo, use `cargo new`:

```shell
$ cargo new hello_world --bin
```

We’re passing `--bin` because we’re making a binary program: if we
were making a library, we’d leave it off. This also initializes a new `git`
repository by default. If you don't want it to do that, pass `--vcs none`.

Let’s check out what Cargo has generated for us:

```shell
$ cd hello_world
$ tree .
.
├── Cargo.toml
└── src
    └── main.rs

1 directory, 2 files
```

If we had just used `cargo new hello_world` without the `--bin` flag, then
we would have a `lib.rs` instead of a `main.rs`. For now, however, this is all
we need to get started. First, let’s check out `Cargo.toml`:

```toml
[package]
name = "hello_world"
version = "0.1.0"
authors = ["Your Name <you@example.com>"]
```

This is called a **manifest**, and it contains all of the metadata that Cargo
needs to compile your project.

Here’s what’s in `src/main.rs`:

```
fn main() {
    println!("Hello, world!");
}
```

Cargo generated a “hello world” for us. Let’s compile it:

```shell
$ cargo build
   Compiling hello_world v0.1.0 (file:///path/to/project/hello_world)
```

And then run it:

```shell
$ ./target/debug/hello_world
Hello, world!
```

We can also use `cargo run` to compile and then run it, all in one step (you
won't see the `Compiling` line if you have not made any changes since you last
compiled):

```shell
$ cargo run
   Compiling hello_world v0.1.0 (file:///path/to/project/hello_world)
     Running `target/debug/hello_world`
Hello, world!
```

You'll notice several new files and directories have been created:
```shell
$ tree .
.
├── Cargo.lock
├── Cargo.toml
├── src
│   └── main.rs
└── target
    └── debug
        ├── build
        ├── deps
        │   └── hello_world-2386c2fd0156916f
        ├── examples
        ├── hello_world
        ├── hello_world.d
        ├── incremental
        └── native

8 directories, 6 files
```

The `Cargo.lock` file contains information about our dependencies. Since we
don’t have any yet, it’s not very interesting. The `target` directory contains
all the build products, and, as can be seen, Cargo produces debug builds by
default. You can use `cargo build --release` to compile your files with
optimizations turned on:

```shell
$ cargo build --release
   Compiling hello_world v0.1.0 (file:///path/to/project/hello_world)
```

`cargo build --release` puts the resulting binary in `target/release`
instead of `target/debug`.

Compiling in debug mode is the default for development -- compilation time is
shorter since the compiler doesn't do optimizations, but the code will run
slower. Release mode takes longer to compile, but the code will run faster.
