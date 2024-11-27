workspace(
    name = "cosmo_cc_bazel_toolchain",
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive", "http_file")

http_archive(
    name = "platforms",
    sha256 = "5308fc1d8865406a49427ba24a9ab53087f17f5266a7aabbfc28823f3916e1ca",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/platforms/releases/download/0.0.6/platforms-0.0.6.tar.gz",
        "https://github.com/bazelbuild/platforms/releases/download/0.0.6/platforms-0.0.6.tar.gz",
    ],
)

http_archive(
    name = "rules_cc",
    sha256 = "2037875b9a4456dce4a79d112a8ae885bbc4aad968e6587dca6e64f3a0900cdf",
    strip_prefix = "rules_cc-0.0.9",
    urls = ["https://github.com/bazelbuild/rules_cc/releases/download/0.0.9/rules_cc-0.0.9.tar.gz"],
)

load("@rules_cc//cc:repositories.bzl", "rules_cc_dependencies", "rules_cc_toolchains")

rules_cc_dependencies()

http_archive(
    name = "cosmocc",
    workspace_file_content = "workspace(name=\"cosmocc\")",
    build_file_content = """
package(default_visibility = ["//visibility:public"])

filegroup(
    name = "x86_64-full",
    srcs = [
        "//:x86_64-bin",
        "//:libexec/gcc/x86_64-linux-cosmo/14.1.0",
        "//:include",
        "//:x86_64-lib",
    ],
)

# include

filegroup(
    name = "include",
    srcs = glob(["include/**/*"]),
)

# bin

filegroup(
    name = "x86_64-bin",
    srcs = [
        "x86_64-ar",
        "x86_64-gcc",
        "x86_64-g++",
        "x86_64-strip",
        "x86_64-objcopy",
        "x86_64-objdump",
        "x86_64-addr2line",
        "x86_64-elfedit",
        "x86_64-nm",
        "x86_64-ranlib",
        "x86_64-readelf",
        "x86_64-size",
        "x86_64-c++filt",
    ],
)

filegroup(name = "x86_64-ar", srcs = ["bin/x86_64-linux-cosmo-ar"])
filegroup(name = "x86_64-gcc", srcs = ["bin/x86_64-linux-cosmo-gcc"])
filegroup(name = "x86_64-g++", srcs = ["bin/x86_64-linux-cosmo-g++"])
filegroup(name = "x86_64-strip", srcs = ["bin/x86_64-linux-cosmo-strip"])
filegroup(name = "x86_64-objcopy", srcs = ["bin/x86_64-linux-cosmo-objcopy"])
filegroup(name = "x86_64-objdump", srcs = ["bin/x86_64-linux-cosmo-objdump"])
filegroup(name = "x86_64-addr2line", srcs = ["bin/x86_64-linux-cosmo-addr2line"])
filegroup(name = "x86_64-elfedit", srcs = ["bin/x86_64-linux-cosmo-elfedit"])
filegroup(name = "x86_64-nm", srcs = ["bin/x86_64-linux-cosmo-nm"])
filegroup(name = "x86_64-ranlib", srcs = ["bin/x86_64-linux-cosmo-ranlib"])
filegroup(name = "x86_64-readelf", srcs = ["bin/x86_64-linux-cosmo-readelf"])
filegroup(name = "x86_64-size", srcs = ["bin/x86_64-linux-cosmo-size"])
filegroup(name = "x86_64-c++filt", srcs = ["bin/x86_64-linux-cosmo-c++filt"])

alias(name = "x86_64-c++", actual = ":x86_64-g++")
alias(name = "x86_64-cc", actual = ":x86_64-gcc")
alias(name = "x86_64-cpp", actual = ":x86_64-gcc")

# libexec

filegroup(
    name = "libexec/gcc/x86_64-linux-cosmo/14.1.0",
    srcs = glob(["libexec/gcc/x86_64-linux-cosmo/14.1.0/**/*"]),
)

alias(name = "x86_64-ld", actual = ":x86_64-ld.bfd")

# lib

filegroup(
    name = "x86_64-lib",
    srcs = glob(["x86_64-linux-cosmo/lib/**/*"]),
)

filegroup(name = "x86_64-libstdc++.a", srcs = ["x86_64-linux-cosmo/lib/libstdc++.a"])

    """,
    sha256 = "3f559555d08ece35bab1a66293a2101f359ac9841d563419756efa9c79f7a150",
    url = "https://github.com/jart/cosmopolitan/releases/download/3.9.7/cosmocc-3.9.7.zip",
)
