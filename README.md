# About

Ezthumb is a video thumbnail generator based on FFmpeg.

More information at: https://ezthumb.sourceforge.io/

# Motivation

The project has been dormant for a few years, and pre-built packages of it on popular Linux distributions are virtually non-existent.

Nevertheless, the app still works, and having a Flatpak package of it ensures the program stays "alive", while also making it easier for people to use.

# Installation

First, download the latest version from the [Releases page](https://github.com/guihkx/flatpak-app-ezthumb/releases).

To install the package for all users, open a terminal window and run:

```bash
flatpak install ezthumb_*-x86_64.flatpak
```

And you're good to go. You should find Ezthumb in your apps list.

# Caveats & tips

By default, Ezthumb will only be able to access your `~/Videos` folder.

If you want to give Ezthumb access to specific folders, you can run the following command:

```bash
flatpak --user override --filesystem=/media/Movies io.sourceforge.ezthumb
```

That will allow Ezthumb access to the `/media/Movies` folder. More examples [here](https://docs.flatpak.org/en/latest/sandbox-permissions.html#filesystem-access).

# Advanced

## Building

Before proceding, make sure both `flatpak` and `flatpak-builder` packages are installed.

64-bit AMD/Intel:

```bash
# Build
flatpak-builder --arch x86_64 --delete-build-dirs --force-clean --install-deps-from flathub --repo repo/ --sandbox builddir/ io.sourceforge.ezthumb.yaml
# Create a single-bundle file
flatpak build-bundle --arch x86_64 repo/ ezthumb-x86_64.flatpak io.sourceforge.ezthumb master
# Install it
flatpak install ezthumb-x86_64.flatpak
```

64-bit ARM:

```bash
# Build
flatpak-builder --arch aarch64 --delete-build-dirs --force-clean --install-deps-from flathub --repo repo/ --sandbox builddir/ io.sourceforge.ezthumb.yaml
# Create a single-bundle file
flatpak build-bundle --arch aarch64 repo/ ezthumb-aarch64.flatpak io.sourceforge.ezthumb master
# Install it
flatpak install ezthumb-aarch64.flatpak
```
