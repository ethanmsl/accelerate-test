# Testing Accelerate BLAS linking in Rust

## Succeeds if:
- build.rs gives explicit [library linkage command]([url](https://doc.rust-lang.org/cargo/reference/build-scripts.html#rustc-link-lib)): **"cargo:rustc-link-lib=framework=Accelerate"**
- Plain crate

## Fails if:
- build.rs is not present.  (despite explicit use of accelerate feature, `blas-src = { version = "0.9", features = ["accelerate"] }`)
- build.rs *is* present, but used for crate in a workspace.  (with the build.rs in workspace or crate root -- possible I'm missing something here though)
  - This is not demonstrated here, but tested elsewhere.
 
## Dependencies used:
```rust
[dependencies]
ndarray = { version = "0.15.6", features = ["blas"] }
ndarray-linalg = "0.16.0"
blas-src = { version = "0.9", features = ["accelerate"] }
```
