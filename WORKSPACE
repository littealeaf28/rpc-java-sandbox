workspace(name = "sandbox")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "rules_jvm_external",
    sha256 = "c21ce8b8c4ccac87c809c317def87644cdc3a9dd650c74f41698d761c95175f3",
    strip_prefix = "rules_jvm_external-1498ac6ccd3ea9cdb84afed65aa257c57abf3e0a",
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/1498ac6ccd3ea9cdb84afed65aa257c57abf3e0a.zip",
)

load("@rules_jvm_external//:defs.bzl", "maven_install")
load("//:repositories.bzl", "IO_GRPC_GRPC_JAVA_ARTIFACTS", "IO_GRPC_GRPC_JAVA_OVERRIDE_TARGETS", "grpc_java_repositories")

grpc_java_repositories()

load("@com_google_protobuf//:protobuf_deps.bzl", "PROTOBUF_MAVEN_ARTIFACTS", "protobuf_deps")
protobuf_deps()

maven_install(
    artifacts = [
        "com.google.api.grpc:grpc-google-cloud-pubsub-v1:0.1.24",
        "com.google.api.grpc:proto-google-cloud-pubsub-v1:0.1.24",
    ] + IO_GRPC_GRPC_JAVA_ARTIFACTS + PROTOBUF_MAVEN_ARTIFACTS,
    generate_compat_repositories = True,
    override_targets = IO_GRPC_GRPC_JAVA_OVERRIDE_TARGETS,
    repositories = [
        "https://repo.maven.apache.org/maven2/",
    ],
)

load("@maven//:compat.bzl", "compat_repositories")

compat_repositories()