load("//tools/bzl:junit.bzl", "junit_tests")
load(
    "//tools/bzl:plugin.bzl",
    "gerrit_plugin",
    "PLUGIN_DEPS",
    "PLUGIN_TEST_DEPS",
)

gerrit_plugin(
    name = "high-availability",
    srcs = glob(["src/main/java/**/*.java"]),
    manifest_entries = [
        "Gerrit-PluginName: high-availability",
        "Gerrit-Module: com.ericsson.gerrit.plugins.highavailability.Module",
        "Gerrit-HttpModule: com.ericsson.gerrit.plugins.highavailability.HttpModule",
        "Implementation-Title: high-availability plugin",
        "Implementation-URL: https://gerrit-review.googlesource.com/#/admin/projects/plugins/high-availability",
    ],
    resources = glob(["src/main/resources/**/*"]),
)

junit_tests(
    name = "high_availability_tests",
    srcs = glob(["src/test/java/**/*.java"]),
    resources = glob(["src/test/resources/**/*"]),
    tags = [
        "high-availability",
        "local",
    ],
    deps = PLUGIN_DEPS + PLUGIN_TEST_DEPS + [
        ":high-availability__plugin_test_deps",
        ":high-availability__plugin",
    ],
)

java_library(
    name = "high-availability__plugin_test_deps",
    visibility = ["//visibility:public"],
    exports = [
        "@byte-buddy//jar",
        "@mockito//jar",
        "@objenesis//jar",
        "@wiremock//jar",
    ],
)