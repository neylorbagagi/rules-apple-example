load("@rules_apple//apple:ios.bzl", "ios_application")
load("@rules_swift//swift:swift.bzl", "swift_library")
load("@rules_xcodeproj//xcodeproj:defs.bzl", "top_level_target", "xcodeproj")

swift_library(
    name = "lib",
    srcs = glob(["Sources/*.swift"]),
)

ios_application(
    name = "iOSApp",
    bundle_id = "build.bazel.rules-apple-example",
    #provisioning_profile = "7087d178-e954-4288-a350-332059877af7.mobileprovision",
    families = ["iphone", "ipad"],
    infoplists = ["Resources/Info.plist"],
    visibility = ["//visibility:public"],
    minimum_os_version = "17.0",
    deps = [":lib"],
)

xcodeproj(
    name = "xcodeproj",
    project_name = "iOSApp",
    tags = ["manual"],
    top_level_targets = [
        top_level_target(
            ":iOSApp",
            target_environments = ["simulator"],
        ),
    ],
)
