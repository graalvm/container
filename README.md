# GraalVM Community Edition Container Images

To support container-based development, GraalVM Community Edition container images are published in the GitHub Container Registry for each release.

There are different GraalVM Community Edition container images provided depending on the architecture and the Java version.
The images are multi-arch (`aarch64` or `amd64` depending on the host architecture).
Some images are `gu`-based (containing the [GraalVM Updater](https://github.com/oracle/graal/blob/master/docs/reference-manual/graalvm-updater.md) tool), some are RPM-based.
All images support the installation of extra features. The following container images are available:

| Package      | Description                                                                                                                                                | Type      |
|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| jdk          | GraalVM Community compact JDK container image without additional features.                                                                                 | RPM-based |
| graalvm-ce   | GraalVM Community Edition image with GraalVM Updater                                                                                                       | GU-based  |
| native-image |  GraalVM Community compact image with Native Image.                                                                                                        | RPM-based |
| truffleruby  | GraalVM Community compact image with the Ruby runtime. The image uses a standalone build of [TruffleRuby](https://github.com/oracle/truffleruby/releases). | RPM-based |
| nodejs       | GraalVM Community compact image with the Node.js runtime.                                                                                                  | RPM-based |

The images are tagged with the format `ghcr.io/graalvm/IMAGE_NAME:version`.
The version tag defines the level of specificity.
It is recommended that the most specific tag be used, e.g., `java17-21.3.0` or `java17-21.3.0-b1`, where the `-b1` means the image required a patch and this specific build will never change.

You can pull a package by name or by name and version tag.
To install GraalVM JDK from the command line, use:
```
$ docker pull ghcr.io/graalvm/jdk:java17-21.3.0
```
To use GraalVM JDK as base image in Dockerfile, use:
```
FROM ghcr.io/graalvm/jdk:java17-21.3.0
```

Read more about running GraalVM Community Edition container images [here](https://www.graalvm.org/docs/getting-started/container-images).

## Versioning and Update Policy

To allow users to control their update policy, we provide an update policy based on a tag version.
To fix the image and allow no updates, you need to use a full version with a build number:
```
ghcr.io/graalvm/$IMAGE_NAME[:][$os_version][-$java_version][-$version][-$build_number]
```
For example, `ghcr.io/graalvm/jdk:java17-21.3.0-b1`.
You can also set an image to a specific version number that allows an update for a subversion to be pulled.
For instance, using `ghcr.io/graalvm/jdk:java11-21.2`, the image will be updated for 21.2.x releases, but not for 21.3.0.
Using `ghcr.io/graalvm/native-image` you will always get the latest update available for Native Image, the latest OS, the latest Java version, and the latest GraalVM version.

Note some terms and restrictions that may apply to the open source technology.
The container image you select and all of the software that it contains is licensed under one or more open source license that are provided in the container image. Your use of the container is subject to the terms of those licenses.
