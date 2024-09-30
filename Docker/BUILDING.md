# Building the Lyrion Music Server Docker image

## Prerequisites
1. Git
2. Docker
3. Docker buildx
4. Docker registry credentials

## Build Process -- the Human way
1. Clone [slimserver](https://github.com/LMS-Community/slimserver) to `./server`
2. Clone [slimserver-platforms](https://github.com/LMS-Community/slimserver-platforms) to `./platforms`
2. Make sure both are pointed to the "same" branch (at least based on the same release)
3. Log in to the appropriate Docker registry, for example Github:
    ```sh
    docker login ghcr.io -u $github_username
    ```
4. Create a build directory, e.g. `mkdir build`
5. Run build script (will push image to registry!):
    ```sh
    ./platforms/buildme.pl --build=docker --buildDir=./build --sourceDir=. \
        --releaseType=nightly --registry=ghcr.io --namespace=$github_username
    ```
    * The Docker build defaults to a multi-arch image for 32-bit and 64-bit ARM plus 64-bit
    Intel. You can optionally specify `--x86_64` or `--arm` to build one or both architectures.


