load("@io_bazel_rules_go//go:def.bzl", "go_library")
load("@io_bazel_rules_go//proto:def.bzl", "go_proto_library")
load("@bazel_gazelle//:def.bzl", "gazelle")
load("@com_googleapis_gapic_generator_go//:rules_go_gapic/go_gapic.bzl", "go_gapic_library")

# gazelle:prefix github.com/googleapis/bazel-microgen-test
gazelle(name = "gazelle")

proto_library(
    name = "echo_proto",
    srcs = ["echo.proto"],
    visibility = ["//visibility:public"],
    deps = [
        "@go_googleapis//google/api:annotations_proto",
        "@go_googleapis//google/rpc:status_proto",
    ],
)

go_proto_library(
    name = "echo_go_proto",
    compilers = ["@io_bazel_rules_go//proto:go_grpc"],
    importpath = "github.com/googleapis/bazel-microgen-test/genproto",
    proto = ":echo_proto",
    visibility = ["//visibility:public"],
    deps = [
        "@go_googleapis//google/api:annotations_go_proto",
        "@go_googleapis//google/rpc:status_go_proto",
    ],
)

go_library(
    name = "go_default_library",
    embed = [":echo_go_proto"],
    importpath = "github.com/googleapis/bazel-microgen-test/genproto",
    visibility = ["//visibility:public"],
)

go_gapic_library(
  name = "echo_go_gapic",
  srcs = [
    # BUILD target for proto_library
    ":echo_proto",
  ],
  deps = [
    # BUILD target for go_library_proto
    ":echo_go_proto",
  ],
  # go-gapic-package parameter value
  importpath = "github.com/googleapis/bazel-microgen-test/client;client",
  grpc_service_config = ":echo_grpc_service_config.json",
  service_yaml = ":echo_v1beta1.yaml",
  release_level = "alpha",
)
