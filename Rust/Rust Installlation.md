# Rust Installlation
[Rust Playground](https://play.rust-lang.org/)

[Learn Rust](https://www.rust-lang.org/learn)
- [Rust Documentation](https://doc.rust-lang.org/book/)
- [Rust by Example](https://doc.rust-lang.org/stable/rust-by-example/)
## Install for WSL

````shell
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
````

## Install for Windows
Download [64 bit](https://static.rust-lang.org/rustup/dist/x86_64-pc-windows-msvc/rustup-init.exe) or [32 bit](https://static.rust-lang.org/rustup/dist/i686-pc-windows-msvc/rustup-init.exe) and run `rustup init.exe`
## After Installation
#### Rust Version & Update
````rust
// rust version
rustup --version
// rust update
rustup update
````

#### Rust Compiler & Package Manager
````rust
// rust compiler version
rustc --version
// rust package manager version
cargo --version
````

#### Create Project or Init
````rust
// create project
cargo new folder_name
// init project
cargo init
````

#### Project Run or Build
````rust
// project run
cargo run
//project build
cargo build
````

## VSCode Extension
[Rust Extension Pack](https://marketplace.visualstudio.com/items?itemName=swellaby.rust-pack)
