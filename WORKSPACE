load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

git_repository(
    name = "io_bazel_rules_go",
    remote = "https://github.com/bazelbuild/rules_go.git",
    tag = "0.16.6",
)

# Go Rules
load(
    "@io_bazel_rules_go//go:def.bzl",
    "go_rules_dependencies",
    "go_register_toolchains",
)

go_rules_dependencies()

go_register_toolchains()

# Gazelle
git_repository(
    name = "bazel_gazelle",
    remote = "https://github.com/bazelbuild/bazel-gazelle.git",
    tag = "0.16.0",
)

load(
    "@bazel_gazelle//:deps.bzl",
    "gazelle_dependencies",
)

gazelle_dependencies()

# Docker Rules
git_repository(
    name = "io_bazel_rules_docker",
    remote = "https://github.com/bazelbuild/rules_docker.git",
    tag = "v0.7.0",
)

load(
    "@io_bazel_rules_docker//container:container.bzl",
    "container_pull",
)

container_pull(
    name = "distroless_base_image",
    registry = "gcr.io",
    repository = "distroless/base",
    digest = "sha256:628939ac8bf3f49571d05c6c76b8688cb4a851af6c7088e599388259875bde20",
)

load(
    "@io_bazel_rules_docker//go:image.bzl",
    _go_image_repos = "repositories",
)

_go_image_repos()

# Load the macro that allows you to customize the docker toolchain configuration.
load("@io_bazel_rules_docker//toolchains/docker:toolchain.bzl",
    docker_toolchain_configure="toolchain_configure"
)

docker_toolchain_configure(
  name = "docker_config",
  # Replace this with a path to a directory which has a custom docker client
  # config.json. Docker allows you to specify custom authentication credentials
  # in the client configuration JSON file.
  # See https://docs.docker.com/engine/reference/commandline/cli/#configuration-files
  # for more details.
  client_config="/Users/a13778/Documents/workspace/src/github.com/cre8ivejp/multi-project/creds",
)
