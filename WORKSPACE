load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "rules_rust",
    sha256 = "aaaa4b9591a5dad8d8907ae2dbe6e0eb49e6314946ce4c7149241648e56a1277",
    urls = ["https://github.com/bazelbuild/rules_rust/releases/download/0.16.1/rules_rust-v0.16.1.tar.gz"],
)

load("@rules_rust//rust:repositories.bzl", "rules_rust_dependencies", "rust_register_toolchains")

rules_rust_dependencies()

rust_register_toolchains(
    edition = "2018",
    versions = [
        "1.66.1",
    ],
)

load("@rules_rust//crate_universe:repositories.bzl", "crate_universe_dependencies")

crate_universe_dependencies()

load("@rules_rust//crate_universe:defs.bzl", "crates_repository")

crates_repository(
    name = "crate_index",
    cargo_lockfile = "//:Cargo.lock",
    lockfile = "//:cargo-bazel-lock.json",
    manifests = [
        "//:Cargo.toml",
        "//:serialize/Cargo.toml",
        "//:serialize-derive/Cargo.toml",
        "//:ff-macros/Cargo.toml",
        "//:ff-asm/Cargo.toml",
        "//:ff/Cargo.toml",
        "//:ec/Cargo.toml",
        "//:poly/Cargo.toml",
        "//:poly-benches/Cargo.toml",
        "//:test-curves/Cargo.toml",
        "//:test-templates/Cargo.toml",
    ],
)

load(
    "@crate_index//:defs.bzl",
    cargo_local_crate_repositories = "crate_repositories",
)

cargo_local_crate_repositories()
