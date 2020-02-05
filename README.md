# bazel-microgen-test

This repository is strictly for debugging the `go_gapic_library` Bazel target,
implemented by `gapic-generator-go`.

In `repositories.bzl` change the `path` attribute of the `local_repository`
rule named `com_googleapis_gapic_generator_go` to the path of a local copy of
`gapic-generator-go`. This project will build with the local copy's definition
of `go_gapic_library`.

Once the path is changed, from the project root directory simply run
`bazel build :echo_go_gapic`.

# Disclaimer

This is **not** a canonical example and should not be used as a basis for
generating a production library.

This is not a product of my employer and will not be supported as one. This is
purely for personal development.
