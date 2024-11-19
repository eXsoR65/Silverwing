# Silverwing &nbsp; [![bluebuild build badge](https://github.com/exsor65/silverwing/actions/workflows/build.yml/badge.svg)](https://github.com/exsor65/silverwing/actions/workflows/build.yml)

__Silverwing__ is a variation of [Wayblue](https://github.com/wayblueorg/wayblue) Hyprland Fedora Atomic OS with my own changes like adding KVM with Virt-Manager to run tradisional VM's. 

> I highly recommend you check out [Wayblue](https://github.com/wayblueorg/wayblue) and if you have questions join Wayblue [Discord](https://discord.gg/86fM55XfEq)


## To-do list:
  - [ ] Document all changes in Silverwing compared to Wayblue Hyprland. 


##### *If you want to learn about creating your own variation using BlueBuild template like I did, see the [BlueBuild docs](https://blue-build.org/how-to/setup/) for instructions.*


## Installation

> **Warning**  
> [This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/exsor65/silverwing:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/exsor65/silverwing:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

The `latest` tag will automatically point to the latest build. That build will still always use the Fedora version specified in `recipe.yml`, so you won't get accidentally updated to the next major version.

## ISO

If build on Fedora Atomic, you can generate an offline ISO with the instructions available [here](https://blue-build.org/learn/universal-blue/#fresh-install-from-an-iso). These ISOs cannot unfortunately be distributed on GitHub for free due to large sizes, so for public projects something else has to be used for hosting.

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/exsor65/silverwing
```
