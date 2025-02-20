# Examples Repository

This repository serves as a template for setting up tools and toolchains used in Score, providing small examples that demonstrate how these tools work in practice.

## Available Toolchains

Currently, the repository includes:

- LLVM from the Bazel community

## Setting Up Toolchains in Your Module

To integrate a toolchain into your Bazel module, follow these steps:

- Copy the relevant content from MODULE.bazel in this repository.
- Add the necessary bazel_dep() entries to your module’s MODULE.bazel file.
- Ensure your build configurations align with the toolchain requirements.

This approach allows developers to quickly set up and reuse toolchains in their own projects with minimal effort.
