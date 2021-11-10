# cargo

Rust's project manager.

- create a library:
`cargo new --lib {{name}}`

- check that the code compiles, without compiling:
`cargo check`

- (build and) execute:
`cargo run`

- update dependencies (if new versions appear that still satisfy the requirements of cargo.toml):
`cargo update`

- run tests:
`cargo test`
first arguments are for cargo test, then (after --) they are for the test binary:
`cargo test -- --test-threads=1`

- see the stdout of passing tests as well:
`cargo test -- --show-output`

- only run a subset of the tests, by matching substring (including the module name):
`cargo test {{substring}}`

- run ignored (i.e. long) tests:
`cargo test -- --ignored`

- run only a specified integration test:
`cargo test --test {{integration_test}}`

- build profiles: https://doc.rust-lang.org/book/ch14-01-release-profiles.html


