# GraalVM Container Images

To support container-based development, we provide container images for:
- Oracle GraalVM
- GraalVM Community Edition

## Oracle GraalVM Container Images

Oracle GraalVM container images are published in the [Oracle Container Registry](https://container-registry.oracle.com/ords/ocr/ba/graalvm) under the [GraalVM Free Terms and Conditions (GFTC) license](https://www.oracle.com/downloads/licenses/graal-free-license.html). 
Learn more at [Oracle Help Center](https://docs.oracle.com/en/graalvm/jdk/21/docs/getting-started/container-images/#oracle-graalvm-container-images).

## GraalVM Community Edition Container Images

GraalVM Community Edition container images are published in this GitHub Container Registry.
There are different GraalVM Community Edition container images provided depending on the architecture and the Java version.
The container images for the latest GraalVM version (GraalVM for JDK 23) have a `-community` suffix. 
These are: **native-image-community**, **jdk-community**, **truffleruby-community**, **nodejs-community**, and **graalpy-community**.
The container images are multi-arch, for AMD64 and AArch64 processor architectures, and Linux version.

These are GraalVM Community Edition container images for the latest versions:

| Package      | Description    |
|--------------|----------------|
| jdk-community          | A size compact GraalVM Community Edition container image with the GraalVM JDK. |
| graalvm-community   | A GraalVM Community Edition container image.                                                         |
| native-image-community | A size compact, RPM-based<sup>1</sup>, GraalVM Community Edition container image with the [Native Image](https://www.graalvm.org/reference-manual/native-image) support. |
| truffleruby-community  | A size compact, standalone<sup>2</sup>, GraalVM Community Edition container image with the Ruby runtime. It uses a standalone build of [TruffleRuby](https://github.com/oracle/truffleruby/releases). |
| nodejs-community       | A size compact, RPM-based<sup>1</sup>, GraalVM Community Edition container image with the [Node.js runtime](https://github.com/oracle/graaljs/blob/master/docs/user/NodeJS.md). |
| graalpy-community       | A size compact, standalone<sup>2</sup>, GraalVM Community Edition container image with the [GraalPy runtime](https://github.com/oracle/graalpython). It uses a standalone build of [GraalPy](https://github.com/oracle/graalpython/releases).  |

Below is the list of deprecated images that will only receive a last update for 22.3 before being archived:

| Package      | Description                                                                                                                                                | Type      |
|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| jdk          | A size compact GraalVM Community Edition container image with the GraalVM JDK pre-installed.                                                                       | RPM-based<sup>1</sup> |
| graalvm-ce   | A GraalVM Community Edition container image with the [`gu` utility](https://www.graalvm.org/reference-manual/graalvm-updater/) to install additional features.                                                          | GU-based  |
| native-image | A size compact GraalVM Community Edition container image with the [Native Image](https://www.graalvm.org/reference-manual/native-image) support.                   | RPM-based<sup>1</sup> |
| truffleruby  | A size compact GraalVM Community Edition container image with the Ruby runtime. It uses a standalone build of [TruffleRuby](https://github.com/oracle/truffleruby/releases). | Standalone<sup>2</sup> |
| nodejs       | A size compact GraalVM Community Edition container image with the [Node.js runtime](https://github.com/oracle/graaljs/blob/master/docs/user/NodeJS.md).                          | RPM-based<sup>1</sup> |
| graalpy       | A size compact GraalVM Community Edition container image with the [GraalPy runtime](https://github.com/oracle/graalpython).                          | Standalone<sup>2</sup> |

**1**: RPM-based GraalVM Community Edition container images are based on GraalVM components RPMs that are available for Oracle Linux 8, and Oracle Linux 9. Similar to any other available packages, you can install these components using`microdnf` on Oracle Linux 8 and 9 based images.

**2**: Standalone-based GraalVM Community Edition container images based on standalone builds of specific Truffle languages. These images are created as a drop-in replacement for other implementations, and do not contain a Java runtime.

## Tags 

There are multiple tags that let you choose the level of stability you need including the Java version, build number, and the Linux version. 
Image tags use the following naming convention:

```bash
$version[-muslib(for native image only)][-$platform][-$buildnumber]
```

The following tags are listed from the most-specific tag (at the top) to the least-specific tag (at the bottom). 
The most-specific tag is unique and always points to the same image, while the less-specific tags point to newer image variants over time.

```
23.0.2-ol9-20250121
23.0.2-ol9
23.0.2
23-ol9
23
```

To pull GraalVM for a specific JDK version, for example, 23, run from a command line:
```
$ docker pull ghcr.io/graalvm/graalvm-community:23
```
To use GraalVM JDK as base image in Dockerfile, use:
```
FROM ghcr.io/graalvm/graalvm-community:23
```

Read more about GraalVM Community Edition container images [here](https://www.graalvm.org/docs/getting-started/container-images/).

## Versioning and Update Policy

To allow users to control their update policy, we provide an update policy based on a tag version.
To fix the image and allow no updates, you need to use a full version with a release date:
```
ghcr.io/graalvm/$IMAGE_NAME[:][$java_version][-$os_version][-$date]
```

For example, `ghcr.io/graalvm/jdk-community:23.0.2-ol9-20250121`.

You can also set an image to a specific Java version that allows an update for a subversion to be pulled.
For instance, using `ghcr.io/graalvm/jdk-community:latest`, the image will be updated for 24.1.x releases, but not for 23.0.0.
Using `ghcr.io/graalvm/native-image-community` you will always get the latest update available for Native Image GraalVM Community Edition, the latest OS which is now Oracle Linux 9 and Oracle Linux 9 slim, and the latest Java version.

Note some terms and restrictions that may apply to the open source technology.
The container image you select and all of the software that it contains is licensed under one or more open source license that are provided in the container image. Your use of the container is subject to the terms of those licenses.