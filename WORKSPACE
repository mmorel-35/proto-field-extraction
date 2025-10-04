workspace(name = "proto_field_extraction")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "bazel_skylib",
    sha256 = "6e78f0e57de26801f6f564fa7c4a48dc8b36873e416257a92bbb0937eeac8446",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/bazel-skylib/releases/download/1.8.2/bazel-skylib-1.8.2.tar.gz",
        "https://github.com/bazelbuild/bazel-skylib/releases/download/1.8.2/bazel-skylib-1.8.2.tar.gz",
    ],
)

http_archive(
    name = "com_google_googletest",
    sha256 = "7ff5db23de232a39cbb5c9f5143c355885e30ac596161a6b9fc50c4538bfbf01",
    strip_prefix = "googletest-f8d7d77c06936315286eb55f8de22cd23c188571",
    urls = [
        "https://github.com/google/googletest/archive/f8d7d77c06936315286eb55f8de22cd23c188571.tar.gz",  # v1.14.0
    ],
)

load("@com_google_googletest//:googletest_deps.bzl", "googletest_deps")

googletest_deps()

# Archive building rules.
http_archive(
    name = "rules_pkg",
    sha256 = "d20c951960ed77cb7b341c2a59488534e494d5ad1d30c4818c736d57772a9fef",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_pkg/releases/download/1.0.1/rules_pkg-1.0.1.tar.gz",
        "https://github.com/bazelbuild/rules_pkg/releases/download/1.0.1/rules_pkg-1.0.1.tar.gz",
    ],
)

http_archive(
    name = "grpc_httpjson_transcoding",
    strip_prefix = "grpc-httpjson-transcoding-707b30339ef40f654fb93a175528b8c165688fc8",
    url = "https://github.com/mmorel-35/grpc-httpjson-transcoding/archive/707b30339ef40f654fb93a175528b8c165688fc8.tar.gz",
    #    commit = "707b30339ef40f654fb93a175528b8c165688fc8",
    #    remote = "https://github.com/mmorel-35/grpc-httpjson-transcoding.git",
)

# For status_macros
http_archive(
    name = "ocp",
    patch_args = ["-p0"],
    patches = ["//:ocp_protobuf29_compat.patch"],
    strip_prefix = "ocp-diag-core-e965ac0ac6db6686169678e2a6c77ede904fa82c/apis/c++",
    url = "https://github.com/opencomputeproject/ocp-diag-core/archive/e965ac0ac6db6686169678e2a6c77ede904fa82c.tar.gz",
)

# -------- Load and call dependencies of underlying libraries --------

load("@grpc_httpjson_transcoding//:repositories.bzl", "absl_repositories", "googleapis_repositories", "io_bazel_rules_docker", "protobuf_repositories", "protoconverter_repositories")

protoconverter_repositories()

googleapis_repositories()

protobuf_repositories()

absl_repositories()

io_bazel_rules_docker()

load("@com_google_googleapis//:repository_rules.bzl", "switched_rules_by_language")

switched_rules_by_language(
    name = "com_google_googleapis_imports",
    cc = True,
)

load("@rules_pkg//:deps.bzl", "rules_pkg_dependencies")

rules_pkg_dependencies()

load("@bazel_skylib//:workspace.bzl", "bazel_skylib_workspace")

bazel_skylib_workspace()

load("@com_google_protobuf//:protobuf_deps.bzl", "protobuf_deps")

protobuf_deps()
