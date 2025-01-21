
# truffleruby-community

truffleruby-community is the [GraalVM](http://graalvm.org/) high-performance implementation of the [Ruby programming language](https://www.ruby-lang.org/en/).  

## Docker images

See https://github.com/graalvm/container/pkgs/container/truffleruby-community

## Supported tags

* Oracle Linux 9: [`latest`/`VERSION`](https://github.com/graalvm/container/blob/master/truffleruby-community/Dockerfile.ol9).

* Oracle Linux 9 no toolchain: [`slim`/`slim-VERSION`](https://github.com/graalvm/container/blob/master/truffleruby-community/Dockerfile.ol9-slim).

* Oracle Linux 8: [`ol8`/`ol8-VERSION`](https://github.com/graalvm/container/blob/master/truffleruby-community/Dockerfile.ol8).  

* Oracle Linux 8 no toolchain: [`ol8-slim`/`ol8-slim-VERSION`](https://github.com/graalvm/container/blob/master/truffleruby-community/Dockerfile.ol8-slim).  

* Debian 10: [`debian`/`debian-VERSION`](https://github.com/graalvm/container/blob/master/truffleruby-community/Dockerfile.debian).

The `no toolchain` variants mean the GraalVM LLVM toolchain and its dependencies needed to install C extensions are not included to save space.
It is still possible to use gems with C extensions, but the gems must be installed before for instance using a multi-stage build, see [Multi-stage build for the no-toolchain images](#multi-stage-build-for-the-no-toolchain-images) below.

## How to use these images

The images are intended for use in the **FROM** field of a downstream Dockerfile.  
For example, specify `FROM ghcr.io/graalvm/truffleruby-community:latest` or another tag.

Here is an example `Dockerfile`:
```Dockerfile
FROM ghcr.io/graalvm/truffleruby-community:latest

# Copy app, Gemfile and Gemfile.lock
COPY . /app
WORKDIR /app

RUN bundle config --local path vendor/bundle
RUN bundle install
RUN bundle exec ruby app.rb
```

### Multi-stage build for the no-toolchain images

```Dockerfile
# Builder image with the toolchain to install gems
FROM ghcr.io/graalvm/truffleruby-community:latest AS builder

# Copy app, Gemfile and Gemfile.lock
COPY . /app
WORKDIR /app

RUN bundle config --local path vendor/bundle
RUN bundle install

# Resulting image without the toolchain and including the gems
FROM ghcr.io/graalvm/truffleruby-community:ol9-slim

COPY --from=builder /app /app
WORKDIR /app

RUN bundle exec ruby app.rb
```

## Installing system packages

### Oracle Linux 8 and 9

Use `microdnf install some-package`.

### Debian

Use `apt update` and `apt install some-package`.

---

#### Manually Building the images

For manually building a truffleruby-community image from one of these Dockerfiles, use:

```
docker build --build-arg GRAALVM_VERSION=<GraalVM Version> -t ghcr.io/graalvm/truffleruby-community:TAG -f Dockerfile .
```
