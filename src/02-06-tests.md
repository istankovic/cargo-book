## Tests

Cargo can run your tests with the `cargo test` command. Cargo looks for tests
to run in two places: in each of your `src` files and any tests in `tests/`.
Tests in your `src` files should be unit tests, and tests in `tests/` should be
integration-style tests. As such, you’ll need to import your crates into
the files in `tests`.

Here's an example of running `cargo test` in our project, which currently has
no tests:

<pre><code class="language-shell"><span class="gp">$</span> cargo test
<span style="font-weight: bold"
class="s1">   Compiling</span> rand v0.1.0 (https://github.com/rust-lang-nursery/rand.git#9f35b8e)
<span style="font-weight: bold"
class="s1">   Compiling</span> hello_world v0.1.0 (file:///path/to/project/hello_world)
<span style="font-weight: bold"
class="s1">     Running</span> target/test/hello_world-9c2b65bbb79eabce

running 0 tests

test result: ok. 0 passed; 0 failed; 0 ignored; 0 measured
</code></pre>

If our project had tests, we would see more output with the correct number of
tests.

You can also run a specific test by passing a filter:

<pre><code class="language-shell"><span class="gp">$</span> cargo test foo
</code></pre>

This will run any test with `foo` in its name.

`cargo test` runs additional checks as well. For example, it will compile any
examples you’ve included and will also test the examples in your
documentation. Please see the [testing guide][testing] in the Rust
documentation for more details.

[testing]: https://doc.rust-lang.org/book/testing.html