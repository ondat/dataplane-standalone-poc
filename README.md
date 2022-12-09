# README for dataplane-standalone-poc

## Machine setup

This is tested on Fedora 37. It's containerised and any Red Hat-like system
with a fully-working Podman installation should work equally well.

The `target_core_user` kernel module must be installed.

```sh
$ sudo dnf -y install podman-*
$ mkdir -p ~/git
```

## Grab the poc runner

```sh
$ cd ~/git
$ git clone https://github.com/andrelucas/dataplane-standalone-poc.git dps
$ cd dps
```

## Copy necessary files

```sh
# Matching CA certificate and key.
$ cp PATH/TO/ca.{crt,key} ca/
# Dataplane artifact binaries.
$ cp PATH/TO/staging.tgz .
$ make stage-from-tarball
```

## Build and run

This will take a while the first time, as it will download a fairly big Docker
image, and then build the test environment.

```sh
# Kill any existing environment, create a new one, and log into it.
$ make down up shell
```
