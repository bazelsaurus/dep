load("@io_bazel_rules_go//go:def.bzl", "go_library", "go_test")

package(default_visibility = ["//visibility:public"])

load("@bazel_gazelle//:def.bzl", "gazelle")

gazelle(
    name = "gazelle",
    external = "vendored",
    prefix = "github.com/golang/dep",
)

go_library(
    name = "go_default_library",
    srcs = [
        "analyzer.go",
        "context.go",
        "doc.go",
        "lock.go",
        "manifest.go",
        "project.go",
        "txn_writer.go",
    ],
    importpath = "github.com/golang/dep",
    deps = [
        "//gps:go_default_library",
        "//gps/paths:go_default_library",
        "//gps/pkgtree:go_default_library",
        "//internal/fs:go_default_library",
        "//vendor/github.com/pelletier/go-toml:go_default_library",
        "//vendor/github.com/pkg/errors:go_default_library",
    ],
)

go_test(
    name = "go_default_test",
    srcs = [
        "analyzer_test.go",
        "context_test.go",
        "lock_test.go",
        "manifest_test.go",
        "project_test.go",
        "test_project_context_test.go",
        "txn_writer_test.go",
    ] + select({
        "@io_bazel_rules_go//go/platform:android": [
            "analyzer_notwindows_test.go",
        ],
        "@io_bazel_rules_go//go/platform:darwin": [
            "analyzer_notwindows_test.go",
        ],
        "@io_bazel_rules_go//go/platform:dragonfly": [
            "analyzer_notwindows_test.go",
        ],
        "@io_bazel_rules_go//go/platform:freebsd": [
            "analyzer_notwindows_test.go",
        ],
        "@io_bazel_rules_go//go/platform:linux": [
            "analyzer_notwindows_test.go",
        ],
        "@io_bazel_rules_go//go/platform:nacl": [
            "analyzer_notwindows_test.go",
        ],
        "@io_bazel_rules_go//go/platform:netbsd": [
            "analyzer_notwindows_test.go",
        ],
        "@io_bazel_rules_go//go/platform:openbsd": [
            "analyzer_notwindows_test.go",
        ],
        "@io_bazel_rules_go//go/platform:plan9": [
            "analyzer_notwindows_test.go",
        ],
        "@io_bazel_rules_go//go/platform:solaris": [
            "analyzer_notwindows_test.go",
        ],
        "@io_bazel_rules_go//go/platform:windows": [
            "analyzer_windows_test.go",
        ],
        "//conditions:default": [],
    }),
    data = glob(["testdata/**"]),
    embed = [":go_default_library"],
    importpath = "github.com/golang/dep",
    deps = [
        "//gps:go_default_library",
        "//internal/test:go_default_library",
        "//vendor/github.com/pkg/errors:go_default_library",
    ],
)
