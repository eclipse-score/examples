# Examples Repository

This repository serves as a template for setting up tools and toolchains used in Score, providing small examples that demonstrate how these tools work in practice.

> NOTE: The example directory only exist to show how configurations work and it's not mandatory to keep it in derivative repositories.

## Available Tools & Toolchains

The repository includes:

- LLVM from the Bazel community - Host C++ toolchain which is by default registered for host platform.
- CopyRight checker tool `cr_checker` - Small utility tool which will check presence of copyright header in selected source files.

## Setting Up Your Module

To integrate default tools & toolchain into your Bazel module, the best practise is to follow these steps:

- Setup module name in `MODULE.bazel` file, that needs to be in the root of new module. Assuming that the new module name is `score_guidelines`, the first lines of `MODULE.bazel` file are:

  ```python
  module(
      name = "score_guidelines",  # the module name
      version = "0.1",            # the version of module
      compatibility_level = 0,    # the compatibility level of the module.
  )
  ```

  > NOTE: To see all available attributes of `module` function, visit [MODULE.bazel](https://bazel.build/rules/lib/globals/module#module) on Bazel documentation webpage.

- The next step is to copy the relevant content from [MODULE.bazel](https://github.com/eclipse-score/examples/blob/main/MODULE.bazel#L20-L49) (everything except the `examples` module name) in new module `MODULE.bazel` file. If `cr_checker` is the only tool that needs to be integrated in new module (repo) from all tools available in `examples` repo, we only need to copy following line:

  ```python
  bazel_dep(name = "score_cr_checker", version = "0.2.0")
  ```

  The same approuch needs to be done with any other tool that is in `examples/MODULE.bazel` file or, as already said,

- Copy the `.bazelrc` file as is since it holds essential configuration for setting up [SBR](https://github.com/eclipse-score/bazel_registry) (S-CORE Bazel registry).

  ```ini
  common --registry=https://raw.githubusercontent.com/eclipse-score/bazel_registry/main/
  common --registry=https://bcr.bazel.build
  ```

- Copy the .gitignore file.

This approach allows developers to quickly set up and reuse toolchains in their own projects with minimal effort.
