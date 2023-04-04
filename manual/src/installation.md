# Installation

## Installing a binary

Difftastic [provides GitHub
releases](https://github.com/Wilfred/difftastic/releases) with
prebuilt binaries. The
[changelog](https://github.com/Wilfred/difftastic/blob/master/CHANGELOG.md)
describes the changes in each release.

Packages are also available on the following platforms.

[![Packaging status](https://repology.org/badge/vertical-allrepos/difftastic.svg)](https://repology.org/project/difftastic/versions)


## Installing via homebrew (on macOS or Linux)

Difftastic can be installed with [Homebrew](https://formulae.brew.sh/formula/difftastic) on macOS or Linux.


```
$ brew install difftastic
```

## Installing from source

### Build Requirements

Difftastic is written in Rust, so you will need Rust installed. I
recommend [rustup](https://rustup.rs/) to install Rust. Difftastic
requires Rust version 1.57 or later.

You will also need a C++ compiler that supports C++14. If you're using
GCC, you need at least version 8.


### Experimental: nix develop (on macOS or Linux)

Make sure Nix is installed for your system, as well as flake support is enabled, or you can temporary alias the nix command as:

```shell
alias nix="nix --experimental-features 'nix-command flakes'"
```
by specifyinmg `trusted-users` in the config, you are making sure Nix binary caches will be used, when appropriate,
which significantly speeds up the compilation

config example:
```shell
# cat /etc/nix/nix.conf

build-users-group = nixbld
trusted-users = youruser

auto-optimise-store = true
experimental-features = nix-command flakes
```

Run:

```shell
nix develop
```

This will spawn development shell with all the requirements installed.

Build using `cargo`, as per instructions below (no need to specify compiler flags as they should be properly set).

### Build

You can download and build [difftastic on
crates.io](https://crates.io/crates/difftastic) with Cargo (which is
part of Rust).

```
$ cargo install difftastic
```

Difftastic uses the `cc` crate for building C/C++ dependencies. This
allows you to use environment variables `CC` and `CXX` to control the
compiler used (see [the cc
docs](https://github.com/alexcrichton/cc-rs#external-configuration-via-environment-variables)).

See [contributing](./contributing.md) for instructions on debug
builds.

### Experimental: nix build (on macOS or Linux)

The project also can be built using `nix build`, without using `cargo` at all.

TODO: this is currently broken



## (Optional) Install MIME Database

If a MIME database is available, difftastic will use it to detect
binary files more accurately. This is the same database used by the
`file` command, so you probably already have it.

The MIME database path is [specified in the XDG
specification](https://specifications.freedesktop.org/shared-mime-info-spec/0.11/ar01s03.html). The
database should be at one of the following paths:

* `/usr/share/mime/magic`
* `/usr/local/share/mime/magic`
* `$HOME/.local/share/mime/magic`
