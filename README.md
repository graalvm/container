# GraalVM Community Edition Container Images

To support container-based development, GraalVM Community Edition container images are published in the GitHub Container Registry for each release.

There are different GraalVM Community Edition container images provided depending on the architecture and the Java version.
The images are multi-arch (`aarch64` or `amd64` depending on the host architecture).
Some images are `GU`-based (containing the [GraalVM Updater](https://github.com/oracle/graal/blob/master/docs/reference-manual/graalvm-updater.md) tool), some are RPM-based.
All images support the installation of extra features. The following container images are available:

| Package      | Description                                                                                                                                                | Type      |
|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| jdk-community          | A size compact GraalVM Community Edition container image with the GraalVM JDK pre-installed.                                                                       | RPM-based<sup>1</sup> |
| graalvm-community   | A GraalVM Community Edition container image with the [`gu` utility](https://www.graalvm.org/reference-manual/graalvm-updater/) to install additional features.                                                          | GU-based  |
| native-image-community | A size compact GraalVM Community Edition container image with the [Native Image](https://www.graalvm.org/reference-manual/native-image) support.                   | RPM-based<sup>1</sup> |
| truffleruby-community  | A size compact GraalVM Community Edition container image with the Ruby runtime. It uses a standalone build of [TruffleRuby](https://github.com/oracle/truffleruby/releases). | Standalone<sup>2</sup> |
| nodejs-community       | A size compact GraalVM Community Edition container image with the [Node.js runtime](https://github.com/oracle/graaljs/blob/master/docs/user/NodeJS.md).                          | RPM-based<sup>1</sup> |
| graalpy-community       | A size compact GraalVM Community Edition container image with the [GraalPy runtime](https://github.com/oracle/graalpython).                          | Standalone<sup>2</sup> |

Note the following images are deprecated and will only receive a last update for 22.3 before being archived

| Package      | Description                                                                                                                                                | Type      |
|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| jdk          | A size compact GraalVM Community Edition container image with the GraalVM JDK pre-installed.                                                                       | RPM-based<sup>1</sup> |
| graalvm-ce   | A GraalVM Community Edition container image with the [`gu` utility](https://www.graalvm.org/reference-manual/graalvm-updater/) to install additional features.                                                          | GU-based  |
| native-image | A size compact GraalVM Community Edition container image with the [Native Image](https://www.graalvm.org/reference-manual/native-image) support.                   | RPM-based<sup>1</sup> |
| truffleruby  | A size compact GraalVM Community Edition container image with the Ruby runtime. It uses a standalone build of [TruffleRuby](https://github.com/oracle/truffleruby/releases). | Standalone<sup>2</sup> |
| nodejs       | A size compact GraalVM Community Edition container image with the [Node.js runtime](https://github.com/oracle/graaljs/blob/master/docs/user/NodeJS.md).                          | RPM-based<sup>1</sup> |
| graalpy       | A size compact GraalVM Community Edition container image with the [GraalPy runtime](https://github.com/oracle/graalpython).                          | Standalone<sup>2</sup> |

**1**: RPM-based GraalVM Community Edition container images are based on GraalVM components RPMs that are available for Oracle Linux 7, Oracle Linux 8 and Oracle Linux 9. Similar to any other available packages, you can install these components using `yum` on Oracle Linux 7 or `microdnf` on the Oracle Linux 8 and Oracle Linux 9 based images.

**2**: Standalone-based GraalVM Community Edition container images based on standalone builds of specific Truffle languages. These images are created as a drop-in replacement for other implementations (TruffleRuby instead of MRI Ruby), and do not contain a Java runtime.

The images are tagged with the format `ghcr.io/graalvm/IMAGE_NAME:java_version`.
The version tag defines the level of specificity.
It is recommended that the most specific tag be used, for example, `21.0.0` or `21.0.0-ol9-date`, where the `` means the image required a patch and this specific build will never change.

You can pull a package by name or by name and version tag.
To install GraalVM JDK from the command line, use:
```
$ docker pull ghcr.io/graalvm/jdk-community:21.0.0
```
To use GraalVM JDK as base image in Dockerfile, use:
```
FROM ghcr.io/graalvm/jdk-community:21.0.0
```

Read more about GraalVM Community Edition container images [here](https://www.graalvm.org/docs/getting-started/container-images/).

## Versioning and Update Policy

To allow users to control their update policy, we provide an update policy based on a tag version.
To fix the image and allow no updates, you need to use a full version with a release date:
```
For an RPM-based image, use:

ghcr.io/graalvm/$IMAGE_NAME[:][$java_version][-$os_version][-$version][-$date]
```

For example, `ghcr.io/graalvm/jdk-community:21.0.0-ol9-20230919`.
You can also set an image to a specific java version that allows an update for a subversion to be pulled.
For instance, using `ghcr.io/graalvm/jdk-community:latest`, the image will be updated for 23.1.x releases, but not for 23.1.0.   
Using `ghcr.io/graalvm/native-image-community` you will always get the latest update available for Native Image community, the latest OS which is for now Oracle Linux 9 and Oracle Linux 9 slim, and the latest Java version.

For Standalone-based image, use:

ghcr.io/graalvm/$IMAGE_NAME[:][$graalvm_version][-$os_version][-$date]
```

For example, `ghcr.io/graalvm/graalvm-community:23.1.0-ol9-20230919`.
You can also set an image to a specific java version number that allows an update for a subversion to be pulled.
For instance, using `ghcr.io/graalvm/nodejs-community:latest`, the image will be updated for 23.1.x releases, but not for 23.1.0.
Using `ghcr.io/graalvm/nodejs-community` you will always get the latest update available for Node.js, the latest OS which is for now Oracle Linux 9 and Oracle Linux 9 slim, and the latest Java version.

Note some terms and restrictions that may apply to the open source technology.
The container image you select and all of the software that it contains is licensed under one or more open source license that are provided in the container image. Your use of the container is subject to the terms of those licenses.
