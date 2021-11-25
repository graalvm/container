# GraalVM Community Container Images

To support container-based development, GraalVM Community container images are published in the GitHub Container Registry for each release.

There are different GraalVM Community container images provided depending on the architecture and the Java version.
The images are multi-arch (aarch64 or amd64 will be pulled depending on Docker host architecture).
You can find a complete GraalVM Community image, a compact image without additional features, or GraalVM Community image with specific features like the Node.js runtime.

The images are tagged with the format `ghcr.io/OWNER/IMAGE_NAME:version`, where `OWNER` is the repository name, `graalvm` in this case, `IMAGE_NAME` is the package name.
The version tag defines the level of specificity.
It is recommended to use the most specific tag.
The `_b1` means the image required a patch and was rebuilt.

You can find the following packages available:

| Package      | Description                                                                                                                                  |
|--------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| graalvm-ce   | GraalVM Community Edition image with GraalVM Updater which allows to install and manage additional features like Native Image, Node.js, etc. |
| truffleruby  | GraalVM Community compact image with the Ruby runtime.                                                                                       |
| native-image |  GraalVM Community compact image with Native Image.                                                                                          |
| community    | GraalVM Community Edition image with GraalVM Updater which allows to install and manage additional features like Native Image, Node.js, etc. |
| jdk          | GraalVM Community compact JDK container image without additional features.                                                                   |
| nodejs       | GraalVM Community compact image with the Node.js runtime.                                                                                    |

You can pull a package by name or by name and version tag.
To install from the command line, use:
```
$ docker pull ghcr.io/graalvm/jdk:java17-21.3.0-b1
```
To use GraalVM JDK as base image in Dockerfile, use:
```
FROM ghcr.io/graalvm/jdk:java17-21.3.0-b1
```

Learn more about running GraalVM Community container images and some examples [here](https://www.graalvm.org/docs/getting-started/container-images/).

Note some terms and restrictions that may apply to the open source technology.
The container image you select and all of the software that it contains is licensed under one or more open source license that are provided in the container image. Your use of the container is subject to the terms of those licenses.
