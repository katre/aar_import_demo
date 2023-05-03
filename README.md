# With native Android rules

```
$ USE_BAZEL_VERSION=last_green bazelisk cquery --output=starlark --starlark:expr='providers(target).keys()' @maven_no_starlark//:androidx_appcompat_appcompat_resources
2023/05/03 12:54:46 Using unreleased version at commit 38e08c2a477c36c6f41933d5e04912eb3840e618
["InstrumentedFilesInfo", "AndroidResourcesInfo", "AndroidManifestInfo", "AndroidAssetsInfo", "DataBindingV2Info", "ProguardSpecProvider", "AndroidNativeLibsInfo", "JavaInfo", "FileProvider", "FilesToRunProvider", "OutputGroupInfo"]
```

# With Starlark Android rules

```
$ USE_BAZEL_VERSION=last_green bazel cquery --output=starlark --starlark:expr='providers(target).keys()' @maven_starlark//:androidx_appcompat_appcompat_resources
2023/05/03 12:54:12 Using unreleased version at commit 38e08c2a477c36c6f41933d5e04912eb3840e618
["AndroidLibraryResourceClassJarProvider", "JavaInfo", "AndroidNativeLibsInfo", "ProguardSpecProvider", "AndroidIdeInfo", "FileProvider", "FilesToRunProvider", "OutputGroupInfo"]
```

