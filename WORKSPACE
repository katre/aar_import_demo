workspace(name = "aar_import_demo")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

## rules_jvm_external

http_archive(
    name = "rules_jvm_external",
    sha256 = "cd1a77b7b02e8e008439ca76fd34f5b07aecb8c752961f9640dea15e9e5ba1ca",
    strip_prefix = "rules_jvm_external-4.2",
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/4.2.zip",
)

load("@rules_jvm_external//:defs.bzl", "maven_install")

maven_install(
    name = "maven_starlark",
    aar_import_bzl_label = "@build_bazel_rules_android//rules:rules.bzl",
    artifacts = [
        "androidx.appcompat:appcompat:1.5.1",
        "androidx.constraintlayout:constraintlayout:2.1.4",
        # Needed to enforce version conflict resolution
        "androidx.savedstate:savedstate:1.2.0",
        "androidx.lifecycle:lifecycle-livedata-core:2.5.1",
        "androidx.lifecycle:lifecycle-livedata:2.5.1",
        "androidx.lifecycle:lifecycle-process:2.5.1",
        "androidx.lifecycle:lifecycle-runtime:2.5.1",
        "androidx.lifecycle:lifecycle-service:2.5.1",
        "androidx.lifecycle:lifecycle-viewmodel-savedstate:2.5.1",
        "androidx.lifecycle:lifecycle-viewmodel:2.5.1",
    ],
    repositories = [
        "https://maven.google.com",
        "https://repo1.maven.org/maven2",
    ],
    use_starlark_android_rules = True,
)

maven_install(
    name = "maven_no_starlark",
    artifacts = [
        "androidx.appcompat:appcompat:1.5.1",
        "androidx.constraintlayout:constraintlayout:2.1.4",
        # Needed to enforce version conflict resolution
        "androidx.savedstate:savedstate:1.2.0",
        "androidx.lifecycle:lifecycle-livedata-core:2.5.1",
        "androidx.lifecycle:lifecycle-livedata:2.5.1",
        "androidx.lifecycle:lifecycle-process:2.5.1",
        "androidx.lifecycle:lifecycle-runtime:2.5.1",
        "androidx.lifecycle:lifecycle-service:2.5.1",
        "androidx.lifecycle:lifecycle-viewmodel-savedstate:2.5.1",
        "androidx.lifecycle:lifecycle-viewmodel:2.5.1",
    ],
    repositories = [
        "https://maven.google.com",
        "https://repo1.maven.org/maven2",
    ],
    use_starlark_android_rules = False,
)

## Android

RULES_ANDROID_COMMIT = "03aee31a691be8c4b61d3c32581435a77c81f9f8"

RULES_ANDROID_SHA = "5cc8d2b7c1d4e91192a280db60f87498bb68ce9972825791d13af233a6041907"

http_archive(
    name = "build_bazel_rules_android",
    sha256 = RULES_ANDROID_SHA,
    strip_prefix = "rules_android-%s" % RULES_ANDROID_COMMIT,
    url = "https://github.com/bazelbuild/rules_android/archive/%s.zip" % RULES_ANDROID_COMMIT,
)

load("@build_bazel_rules_android//:prereqs.bzl", "rules_android_prereqs")

rules_android_prereqs()

load("@build_bazel_rules_android//:defs.bzl", "rules_android_workspace")

rules_android_workspace()

register_toolchains(
    "@build_bazel_rules_android//toolchains/android:android_default_toolchain",
    "@build_bazel_rules_android//toolchains/android_sdk:android_sdk_tools",
)

load("@build_bazel_rules_android//rules:rules.bzl", "android_sdk_repository")

android_sdk_repository(name = "androidsdk")
