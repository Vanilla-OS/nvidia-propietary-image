# Vanilla OS Nvidia Propietary Image

Containerfile for building a Vanilla OS Desktop + Nvidia Propietary (for old GPUs) image.

> [!NOTE]
> This image will be enabled in the Vanilla OS installer only if [this](https://github.com/Vanilla-OS/nvidia-image/pull/43) gets merged, making the main NVIDIA image using the official open-source drivers.

This image is based on top of [`vanillaos/desktop`](https://github.com/Vanilla-OS/desktop-image/pkgs/container/desktop) and offers the default Vanilla OS Desktop experience with GNOME and Nvidia drivers.

## Build

> [!NOTE]
> The fsguard compiled plugin `.so` file should be downloaded from the [latest release](https://github.com/Vanilla-OS/vib-fsguard/releases/latest) and be placed under a `plugins` directory beside the `recipe.yml` file.

```bash
vib build recipe.yml
podman image build -t vanillaos/nvidia .
```

## Verify Image Build Provenance Attestation

All the image builds/pushes are attested for build provenance and integrity using the [attest-build-provenance](https://github.com/actions/attest-build-provenance) action. The attestations can be verified [here](https://github.com/Vanilla-OS/nvidia-image/attestations) or by having the latest version of [GitHub CLI](https://github.com/cli/cli/releases/latest) installed in your system. Then, execute the following command:

```sh
gh attestation verify oci://ghcr.io/vanilla-os/nvidia:main --owner Vanilla-OS
```
