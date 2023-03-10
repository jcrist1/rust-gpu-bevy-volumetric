## `rust-gpu` Workspace

Nightly rust workspace housing `rust-gpu` shader crates.

`rust-toolchain` contains the necessary toolchain specification for `rust-gpu`,
and `.cargo/config.toml` contains environment variables overriding the permutation file used to compile `bevy-pbr-rust` entry points.

To avoid depending on a local clone of `rust-gpu` for SPIR-V compilation, `rust-gpu-builder` has been added to the `crates` directory as a submodule,
and is set as the workspace's default build target.

You will need [rust-gpu-builder](https://github.com/Bevy-Rust-GPU/rust-gpu-builder/tree/2f8f6c7410fd27cbe071d2e3925a4a9e458b2c1b)
to run. From that crate

Run `cargo run --release -- "{path-to-this-repo}/rust-gpu/crates/shader"` to produce `target/spirv-builder/spirv-unknown-spv1.5/release/deps/shader.spv`.

Run `cargo run --release -- "{path-to-this-repo}/rust-gpu/crates/shader" -w {path-to-this-repo}/rust-gpu/crates/shader/src -w {path-to-this-repo}/bevy-app/crates/viewer/entry_points.json` to watch both workspaces and recompile on change.

### `shader`

Project-level `rust-gpu` shader crate. Pulls in `bevy-pbr-rust` to expose its entrypoints.

