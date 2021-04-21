
# Truffleruby

TruffleRuby is the [GraalVM](http://graalvm.org/) high-performance implementation of the [Ruby programming language](https://www.ruby-lang.org/en/).  

# How to use these images

The images are intended for use in the **FROM** field of a downstream Dockerfile. For example, specify `FROM ghcr.io/graalvm/truffleruby:latest` or a version tag.

# Supported tags

[`GRAALVM_VERSION/ol8/ol8-GRAALVM_VERSION/latest`](https://github.com/graalvm/container/blob/master/truffleruby/Dockerfile.ol8).  

[`slim/slim-GRAALVM_VERSION/ol8-slim/ol8-slim-GRAALVM_VERSION`](https://github.com/graalvm/container/blob/master/truffleruby/Dockerfile.ol8-slim).  

[`ol7/ol7-GRAALVM_VERSION`](https://github.com/graalvm/container/blob/master/truffleruby/Dockerfile).  

[`ol7-slim/ol7-slim-GRAALVM_VERSION`](https://github.com/graalvm/container/blob/master/truffleruby/Dockerfile.slim).  


# Building the images

For building a Truffleruby image use:

```
docker build --build-arg GRAALVM_VERSION=<GraalVM Version> -t ghcr.io/graalvm/truffleruby:TAG -f Dockerfile .
```
