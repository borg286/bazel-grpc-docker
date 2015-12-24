package(default_visibility = ["//visibility:public"])

load("/tools/build_rules/py_rules", "py_library", "py_binary")
load("/tools/build_defs/docker/docker", "docker_build")

py_library(
    name = "lib",
    srcs = ["lib.py"],
)

py_binary(
    name = "bin",
    srcs = ["bin.py"],
    deps = [":lib"],
)

filegroup(
    name = "srcs",
    srcs = ["BUILD"] + glob(["**/*.py"]),
)

docker_build(
  name = "python_fib",
  base = "//third_party/debian:base",
  files = [":bin"],
)

