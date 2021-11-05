
# TruffleRuby

TruffleRuby is the [GraalVM](http://graalvm.org/) high-performance implementation of the [Ruby programming language](https://www.ruby-lang.org/en/).  

## Docker images

See https://github.com/graalvm/container/pkgs/container/truffleruby

## Supported tags

* Oracle Linux 8: [`latest`/`VERSION`](https://github.com/graalvm/container/blob/master/truffleruby/Dockerfile.ol8).  

* Oracle Linux 8 slim: [`slim`/`slim-VERSION`](https://github.com/graalvm/container/blob/master/truffleruby/Dockerfile.ol8-slim).  

* Oracle Linux 7: [`ol7`/`ol7-VERSION`](https://github.com/graalvm/container/blob/master/truffleruby/Dockerfile).  

* Oracle Linux 7 slim: [`ol7-slim`/`ol7-slim-VERSION`](https://github.com/graalvm/container/blob/master/truffleruby/Dockerfile.slim).  

* Debian 10: [`debian`/`debian-VERSION`](https://github.com/graalvm/container/blob/master/truffleruby/Dockerfile.debian).

## How to use these images

The images are intended for use in the **FROM** field of a downstream Dockerfile.  
For example, specify `FROM ghcr.io/graalvm/truffleruby:latest` or a another tag.

## Installing system packages

### Oracle Linux 8

Use `microdnf install some-package`.

### Oracle Linux 7

Use `yum install some-package`.

### Debian

Use `apt update` and `apt install some-package`.

---

#### Manually Building the images

For manually building a TruffleRuby image from one of these Dockerfiles, use:

```
docker build --build-arg GRAALVM_VERSION=<GraalVM Version> -t ghcr.io/graalvm/truffleruby:TAG -f Dockerfile .
```
