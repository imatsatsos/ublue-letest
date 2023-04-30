# ublue - Le Test
## An opinionated Fedora Silverblue spin using uBlue-os tooling

[![build-ublue](https://github.com/imatsatsos/ublue-letest/actions/workflows/build.yml/badge.svg)](https://github.com/imatsatsos/ublue-letest/actions/workflows/build.yml)

This repo generates a customized Fedora Silverblue image, with some added (and removed) packages to suit my (imatsatsos) personal preferences.  
  
- Base image: [ublue-silverblue-nvidia](https://github.com/ublue-os/nvidia/pkgs/container/silverblue-nvidia/89476750?tag=latest)  
- What is added on top: syncthing, intel-undervolt, fastfetch, btop, virtualization-group (includes: virt-install, libvirt-daemon-config-network, libvirt-daemon-kvm, qemu-kvm, virt-manager, virt-viewer)  
  
For more info, check out the [uBlue homepage](https://ublue.it/) and the [main uBlue repo](https://github.com/ublue-os/main/).

## Building your own

You're not me, so you probably want something different.

See the [Make Your Own page in the documentation](https://ublue.it/making-your-own/) for quick setup instructions for setting up your own repository based on the upstream template.

Don't worry, it only requires some basic knowledge about using the terminal and git.

## Installation

> **Warning**
> This is an experimental feature and should not be used in production, try it in a VM for a while!

To rebase an existing Silverblue/Kinoite installation to the latest build:

```
sudo rpm-ostree rebase ostree-unverified-registry:ghcr.io/imatsatsos/ublue-letest:latest
```

This repository builds date tags as well, so if you want to rebase to a particular day's build:

```
sudo rpm-ostree rebase ostree-unverified-registry:ghcr.io/imatsatsos/ublue-letest:20230403
```

The `latest` tag will automatically point to the latest build. That build will still always use the Fedora version specified in `release.yml`, so you won't get accidentally updated to the next major version.

## Verification

These images are signed with sigstore's [cosign](https://docs.sigstore.dev/cosign/overview/). You can verify the signature by downloading the `cosign.pub` key from this repo and running the following command:

    cosign verify --key cosign.pub ghcr.io/imatsatsos/ublue-letest
