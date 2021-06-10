# Bird with multiarch Debian images
Testing tool for Multiarch Debian images for Docker. Currently we are testing:
1. armhf
2. ppc64el
3. mips

## Install Docker
The first step would be to install
[Docker](https://docs.docker.com/engine/install/).

## Setup dbhi/qus
Next we need **qemu** binaries (included in the image). These binaries will be
loaded and registered and container will exit. After that, images for
foreign architectures can be executed.
```
docker run --rm --privileged aptman/qus -s -- -p [ARCH]
```
You can also load and register all available targets:
```
docker run --rm --privileged aptman/qus -s -- -p
```

### Available architectures
You can find list of available archs [here](https://github.com/dbhi/qus).

## Testing the mips
Now you can run an `arm64` image from your `x86_64` Docker host:
```
./build -a mips
Setting /qus/bin/qemu-mips-static as binfmt interpreter for mips
Sending build context to Docker daemon  81.92kB
Step 1/12 : ARG IMAGE
...
```

## Other tags
Also check the
[other tags](https://hub.docker.com/r/multiarch/debian-debootstrap/tags)
by `multiarch`

