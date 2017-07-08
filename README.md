# gltf-legacy

This crate is intended to load [glTF 1.0](https://www.khronos.org/gltf), a file format designed for the efficient transmission of 3D assets. As of 15th June 2017 it is no longer actively maintained.

`rustc` version 1.15 or above is required.

[![Build Status](https://travis-ci.org/alteous/gltf-legacy.svg?branch=master)](https://travis-ci.org/alteous/gltf-legacy)
[![crates.io](https://img.shields.io/crates/v/gltf-legacy.svg)](https://crates.io/crates/gltf-legacy)
[![docs.rs](https://docs.rs/gltf-legacy/badge.svg)](https://docs.rs/gltf-legacy)

### [Documentation](https://docs.rs/gltf-legacy)

### Usage

Add `gltf-legacy` to the dependencies section of `Cargo.toml`.

```toml
[dependencies]
gltf-legacy = "0.1"
```
Import some glTF 1.0.

```rust
extern crate gltf_legacy as gltf;

fn main() {
    match gltf::v1::import("Example-1.0.gltf") {
        Ok(root) => println!("glTF 1.0: {:#?}", root),
        Err(err) => println!("{:?}", err),
    }
}
```

### Extensions

All glTF extensions are opt-in and are enabled by specifying [features](http://doc.crates.io/specifying-dependencies.html#choosing-features) in your crate's Cargo.toml manifest file.

#### Examples

Enabling the `KHR_binary_glTF` extension.

```toml
[dependencies]
gltf-legacy = { version = "0.1", features = ["KHR_binary_glTF"] }
```

### Extras

By default all `extras` included with glTF assets are ignored. You can negate this by enabling the `extras` feature.

```toml
[dependencies]
gltf-legacy = { version = "0.1", features = ["extras"] }
```

### Examples

#### gltf-display

If you want to see how the structure of the glTF file is deserialized, you can
use the example here to poke at it.

```sh
cargo run --example gltf-display Example.gltf
```

