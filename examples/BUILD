load("/third_party/grpc/grpc_proto", "proto_library")
load("/tools/build_defs/docker/docker", "docker_build")

proto_library(
  name = "helloworld",
  src = "helloworld.proto",
  has_service = True,
  generate_cc = True,
  generate_java = True,
  generate_python = True,
)

cc_binary(
  name = "greeter_client",
  srcs = [
    "greeter_client.cc",
  ],
  deps = [
    ":helloworld",
  ],
)

cc_binary(
  name = "greeter_server",
  srcs = [
    "greeter_server.cc",
  ],
  deps = [
    ":helloworld",
  ],
)

cc_binary(
  name = "greeter_async_client",
  srcs = [
    "greeter_async_client.cc",
  ],
  deps = [
    ":helloworld",
  ],
)

cc_binary(
  name = "greeter_async_server",
  srcs = [
    "greeter_async_server.cc",
  ],
  deps = [
    ":helloworld",
  ],
)

java_binary(
  name = "greeter_client_java",
  srcs = [
    "java/io/grpc/examples/helloworld/HelloWorldClient.java"
  ],
  main_class = "io.grpc.examples.helloworld.HelloWorldClient",
  deps = [
    ":helloworld_java",
    "//third_party/java/grpc-java",
  ]
)

java_binary(
  name = "greeter_server_java",
  srcs = [
    "java/io/grpc/examples/helloworld/HelloWorldServer.java"
  ],
  main_class = "io.grpc.examples.helloworld.HelloWorldServer",
  deps = [
    ":helloworld_java",
    "//third_party/java/grpc-java",
  ]
)

docker_build(
  name = "greeter_server_java_docker",
  base = "//third_party/debian:java",
  files = [":greeter_server_java_deploy.jar"],
)


docker_build(
  name = "greeter_client_java_docker",
  base = "//third_party/debian:java",
  files = [":greeter_client_java_deploy.jar"],
)

