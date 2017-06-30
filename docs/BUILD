# To regenerate html docs, run:
#   ./update_docs.sh

load("@io_bazel_skydoc//skylark:skylark.bzl", "skylark_doc", "skylark_library")

skylark_library(
    name = "libs",
    srcs = [
        "//docker:filetype.bzl",
        "//docker:hash.bzl",
        "//docker:label.bzl",
        "//docker:layers.bzl",
        "//docker:path.bzl",
        "//docker:serialize.bzl",
        "//docker:zip.bzl",
    ],
)

skylark_library(
    name = "build",
    srcs = [
        "//docker:build.bzl",
    ],
    deps = [
        ":libs",
    ],
)

skylark_library(
    name = "import",
    srcs = [
        "//docker:import.bzl",
    ],
    deps = [
        ":libs",
    ],
)

skylark_library(
    name = "pull",
    srcs = [
        "//docker:pull.bzl",
    ],
    deps = [
        ":libs",
    ],
)

skylark_library(
    name = "push",
    srcs = [
        "//docker:push.bzl",
    ],
    deps = [
        ":libs",
    ],
)

skylark_library(
    name = "docker-rules",
    srcs = [
        "//docker:docker.bzl",
    ],
    deps = [
        ":build",
        ":import",
        ":pull",
        ":push",
    ],
)

# TODO(mattmoor): Incorporate contrib
skylark_doc(
    name = "docs-md",
    format = "markdown",
    overview = True,
    site_root = ".",
    deps = [":docker-rules"],
)

skylark_doc(
    name = "docs-html",
    format = "html",
    overview = True,
    site_root = ".",
    deps = [":docker-rules"],
)
