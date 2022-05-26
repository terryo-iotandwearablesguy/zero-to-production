# Zero To Production In Rust

<div align="center"><a href="https://zero2prod.com" target="_blank"><img src="https://www.zero2prod.com/assets/img/zero2prod_banner.webp" /></a></div>

[Zero To Production In Rust](https://zero2prod.com) is an opinionated introduction to backend development using Rust.

This repository serves as supplementary material for [the book](https://zero2prod.com/): it hosts several snapshots of the codebase for our email newsletter project as it evolves throughout the book.

## Chapter snapshots

The [`main`](https://github.com/LukeMathWalker/zero-to-production) branch shows the project at the end of the book.

You can browse the project at the end of previous chapters by switching to their dedicated branches:

- [Chapter 3, Part 0](https://github.com/LukeMathWalker/zero-to-production/tree/root-chapter-03-part0)
- [Chapter 3, Part 1](https://github.com/LukeMathWalker/zero-to-production/tree/root-chapter-03-part1)
- [Chapter 4](https://github.com/LukeMathWalker/zero-to-production/tree/root-chapter-04)
- [Chapter 5](https://github.com/LukeMathWalker/zero-to-production/tree/root-chapter-05)
- [Chapter 6, Part 0](https://github.com/LukeMathWalker/zero-to-production/tree/root-chapter-06-part0)
- [Chapter 6, Part 1](https://github.com/LukeMathWalker/zero-to-production/tree/root-chapter-06-part1)
- [Chapter 7, Part 0](https://github.com/LukeMathWalker/zero-to-production/tree/root-chapter-07-part0)
- [Chapter 7, Part 1](https://github.com/LukeMathWalker/zero-to-production/tree/root-chapter-07-part1)
- [Chapter 7, Part 2](https://github.com/LukeMathWalker/zero-to-production/tree/root-chapter-07-part2)
- [Chapter 8](https://github.com/LukeMathWalker/zero-to-production/tree/root-chapter-08)
- [Chapter 9](https://github.com/LukeMathWalker/zero-to-production/tree/root-chapter-09)
- [Chapter 10, Part 0](https://github.com/LukeMathWalker/zero-to-production/tree/root-chapter-10-part0)
- [Chapter 10, Part 1](https://github.com/LukeMathWalker/zero-to-production/tree/root-chapter-10-part1)
- [Chapter 10, Part 2](https://github.com/LukeMathWalker/zero-to-production/tree/root-chapter-10-part2)
- [Chapter 10, Part 3](https://github.com/LukeMathWalker/zero-to-production/tree/root-chapter-10-part3)
- [Chapter 11](https://github.com/LukeMathWalker/zero-to-production/tree/root-chapter-11)

## Pre-requisites

You'll need to install:

- [Rust](https://www.rust-lang.org/tools/install)
- [Docker](https://docs.docker.com/get-docker/)

There are also some OS-specific requirements.

### Windows
  
```bash
cargo install -f cargo-binutils
rustup component add llvm-tools-preview
```

```
cargo install --version=0.5.7 sqlx-cli --no-default-features --features postgres
```

### Linux

```bash
# Ubuntu 
sudo apt-get install lld clang libssl-dev postgresql-client
# Arch 
sudo pacman -S lld clang postgresql
```

```
cargo install --version=0.5.7 sqlx-cli --no-default-features --features postgres
```

### MacOS

```bash
brew install michaeleisel/zld/zld
```

```
cargo install --version=0.5.7 sqlx-cli --no-default-features --features postgres
```
**Note if you don't have Xcode installed, or it's not up to date you may see this error**

```text
xcode-select: error: tool 'xcodebuild' requires Xcode, but active developer directory '/Library/Developer/CommandLineTools' is a command line tools instance
make: *** [build_homebrew] Error 1

If reporting this issue please do so at (not Homebrew/brew or Homebrew/core):
https://github.com/michaeleisel/homebrew-zld/issues
```

The issue happens when xcode-select developer directory was pointing to /Library/Developer/CommandLineTools when a full regular Xcode was required (happens when CommandLineTools are installed after Xcode)

If you don't have Xcode already installed or an older copy please do the following:

1.	Install Xcode (get it from https://appstore.com/mac/apple/xcode) if you don't have it yet.
2. 	Accept the Terms and Conditions. Command: 

```bash
sudo xcodebuild -license accept  
```

4.	Ensure Xcode app is in the /Applications directory (NOT /Users/{user}/Applications).
5.	Point xcode-select to the Xcode app Developer directory using the following command:

```bash
sudo xcode-select -s /Applications/Xcode.app/Contents/Developer
```
7. 	Then finally the command: 

```bash
brew install michaeleisel/zld/zld
```

It's improtant to make sure your Xcode app path is correct. 

  - Correct Xcode: /Applications/Xcode.app/Contents/Developer
  - Incorrrect Xcode: /Users/{username}/Applications/Xcode.app/Contents/Developer

## How to build

Launch a (migrated) Postgres database via Docker:

```bash
./scripts/init_db.sh
```

Launch a Redis instance via Docker:

```bash
./scripts/init_redis.sh
```

Launch `cargo`:

```bash
cargo build
```

## How to test

Launch a (migrated) Postgres database via Docker:

```bash
./scripts/init_db.sh
```

Launch a Redis instance via Docker:

```bash
./scripts/init_redis.sh
```

Launch `cargo`:

```bash
cargo test 
```
