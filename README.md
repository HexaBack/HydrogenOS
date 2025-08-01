> Important note: I am taking a small break from this project, if something breaks, just let me know and I'll try my best to fix it

# HydrogenOS: the best of the past, remade for the future &nbsp; [![bluebuild build badge](https://github.com/hexaback/hydrogenos/actions/workflows/build.yml/badge.svg)](https://github.com/hexaback/hydrogenos/actions/workflows/build.yml)

HydrogenOS is a beautiful and feature-rich KDE-based operating system, with a strong focus on the Oxygen design language and rock-solid stability.

## HydrogenOS-specific notes:
- If you want KDE/Qt apps to look consitent with Oxygen theming, install them via the `rpm-ostree install applicaition-name` command. Oxygen theming for Flatpaks is being figured out meanwhile.

## Installation

> ISO images, the recommended way to install, are coming soon

> [!WARNING]  
> [The following is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/hexaback/hydrogenos:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/hexaback/hydrogenos:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

The `latest` tag will automatically point to the latest build. That build will still always use the Fedora version specified in `recipe.yml`, so you won't get accidentally updated to the next major version.

- If the desktop does not look any different, or you want to keep the desktop theming up to date, use the `keepmeup` command.
> NOTE: `keepmeup` WILL overwrite some of your configurations, back up files as necessary.

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/hexaback/hydrogenos
```
