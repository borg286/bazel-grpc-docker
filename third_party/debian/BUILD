licenses(["notice"])
load("/tools/build_defs/docker/docker", "docker_build")

package(default_visibility = ["//visibility:public"])

filegroup(
    name = "openjdk-jre-headless",
    #srcs = ["openjdk-7-jre-headless.deb"],
    srcs = ["openjdk-8-jre-headless_8u45-b14-1_amd64.deb"]
)

filegroup(
    name = "libc6",
    #srcs = ["libc6-udeb_2.19-22_amd64.deb"],
    #srcs = ["libc6-udeb_2.21-0ubuntu4_amd64.deb"],
    srcs = ["libc6-udeb_2.15-0ubuntu10.12_amd64.deb"],
)

filegroup(
    name = "python2.7",
    srcs = glob(["python2.7-deps/*.deb"]),
)

filegroup(
    name = "wheezy_tar",
    srcs = ["wheezy_tar.tar"],
)

docker_build(
    name = "wheezy",
    tars = [":wheezy_tar"],
)

docker_build(
    name = "base",
    base = ":wheezy",
    debs  = [":libc6"],
    symlinks = {"/lib/x86_64-linux-gnu/ld-linux-x86-64.so.2":"/lib/ld-linux-x86-64.so.2", "/lib/x86_64-linux-gnu/libcrypt.so.1":"/lib/libcrypt.so.1", "/lib/x86_64-linux-gnu/libc.so.6":"/lib/libc.so.6", "/lib/x86_64-linux-gnu/libdl.so.2":"/lib/libdl.so.2", "/lib/x86_64-linux-gnu/libm.so.6":"/lib/libm.so.6", "/lib/x86_64-linux-gnu/libpthread.so.0":"/lib/libpthread.so.0", "/lib/x86_64-linux-gnu/libresolv.so.2":"/lib/libresolv.so.2", "/lib/x86_64-linux-gnu/librt.so.1":"/lib/librt.so.1", "/lib/x86_64-linux-gnu/libutil.so.1":"/lib/libutil.so.1"}
)

docker_build(
    name = "java",
    base = ":base",
    debs = [":openjdk-jre-headless"],
    symlinks = {"/usr/bin/java":"/usr/lib/jvm/java-8-openjdk-amd64/bin/java"},
)

docker_build(
    name = "python",
    base = ":base",
    debs = [":python2.7"],
)

