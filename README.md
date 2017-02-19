# aosc-appstream-data
Distro-specific Appstream data XMLs for software frontends running on AOSC OS. Two of the most used examples are:

- GNOME Software  https://wiki.gnome.org/Apps/Software
- KDE Discover    https://www.kde.org/announcements/plasma-5.4.95.php

And all these requires an AppStream standardized XML catalog. More about the standard of this file can be found at http://www.freedesktop.org/wiki/Distributions/AppStream/.

**This is a repository containing automatically generated data, generated by `appstream-glib`.**

## Directories
A generic directory walk through.

- `xmls/` contains all XML catalogs.
- `icons/aosc` contains cached icon files.

And all to be installed to `/usr/share/app-info` and provided by a package available to AOSC OS users. Check https://github.com/AOSC-Dev/aosc-os-abbs for more updates.

## Generation
This repository is designed to update once a week (or on-call) by the BuildBot (as we call it) kindly provided by [OSSPlanet](https://github.com/OSSPlanet).

The current generation command is shown as below.

```bash
appstream-builder --api-version=0.8 \
                  --add-cache-id \
                  --cache-dir=/repodata/cache \
                  --log-dir=/tmp/logs \
                  --packages-dir=/appstream-worker/os3-rpm \
                  --temp-dir=/tmp \
                  --output-dir=/repodata \
                  --basename=appstream \
                  --origin=aosc \
                  --enable-hidpi \
                  --verbose \
                  --include-failed \
                  --max-threads=1
```

Where...

- /repodata contains all that can be found in this repository.
