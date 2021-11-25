# GraalVM Community Container Images

To support container-based development, GraalVM Community container images are published in the GitHub Container Registry for each release.

There are different GraalVM Community container images provided depending on the architecture and the Java version.
The images are multi-arch (`aarch64` or `amd64` depending on the host architecture).
Some images are `gu`-based (containing the [GraalVM Updater](https://github.com/oracle/graal/blob/master/docs/reference-manual/graalvm-updater.md) tool), some are RPM-based.
You can find complete images, compact images without additional features, or images with specific features included.
All images allow to install extra features. You can find the following packages available:

| Package      | Description                                                                                                                                                | Type      |
|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| jdk          | GraalVM Community compact JDK container image without additional features.                                                                                 | RMP-based |
| graalvm-ce   | GraalVM Community Edition image with GraalVM Updater                                                                                                       | GU-based  |
| native-image |  GraalVM Community compact image with Native Image.                                                                                                        | RMP-based |
| truffleruby  | GraalVM Community compact image with the Ruby runtime. The image uses a standalone build of [TruffleRuby](https://github.com/oracle/truffleruby/releases). | RMP-based |
| nodejs       | GraalVM Community compact image with the Node.js runtime.                                                                                                  | RMP-based |

The images are tagged with the format `ghcr.io/graalvm/IMAGE_NAME:version`, where `IMAGE_NAME` is a package name.
The version tag defines the level of peculiarity.
It is recommended to use the most specific tag, e.g., `java17-21.3.0` or `java17-21.3.0-b1`, where the
`-b1` means the image required a patch and this specific build will never change.

You can pull a package by name or by name and version tag.
To install GraalVM JDK from the command line, use:
```
$ docker pull ghcr.io/graalvm/jdk:latest
```
To use GraalVM JDK as base image in Dockerfile, use:
```
FROM ghcr.io/graalvm/jdk:latest
```

Read more about running GraalVM Community container images [here](https://www.graalvm.org/docs/getting-started/container-images).

## Versioning and Update Policy

To allow users to control their update policy, we provide an update policy based on a tag version.
To fix the image and allow no updates you need to use a full version with a build number:
```
ghcr.io/graalvm/$IMAGE_NAME[:][$os_version][-$java_version][-$version][-$build_number]
```
For example, `ghcr.io/graalvm/jdk:java17-21.3.0-b1`.
You can also set an image to a specific version number that allows an update for a subversion to be pulled.
For instance, using `ghcr.io/graalvm/jdk:java11-21.2`, the image will be updated for 21.2.x releases, but not for 21.3.0.
Using `ghcr.io/graalvm/native-image` you will always get the latest update available for Native Image, latest OS, Java version and GraalVM version.

Note some terms and restrictions that may apply to the open source technology.
The container image you select and all of the software that it contains is licensed under one or more open source license that are provided in the container image. Your use of the container is subject to the terms of those licenses.
