# SABnzbd for Olares

A community Olares package for [SABnzbd](https://sabnzbd.org/), using the pinned [LinuxServer.io image](https://docs.linuxserver.io/images/docker-sabnzbd/).

## Verified on Olares

SABnzbd 5.1.3 installs and opens through the private Olares entrance. Provider setup and a complete download to local Olares storage passed.

In one download-only test, 35.91 GB completed in 273 seconds. SABnzbd reported an average of **125.4 MiB/s (about 1.05 Gbit/s)** with 50 Eweka connections over SSL on port 563 and a 256 MB article cache. This is a measured result from one installation, not a provider speed guarantee. Repair, unpacking and peak memory use were not measured in this test.

See the [validation record](docs/VALIDATION.md) for checks and remaining limits.

![Queue on Olares](docs/screenshots/queue.jpg)

![Initial setup](docs/screenshots/setup.jpg)

These are actual application screenshots captured before adding provider credentials or personal downloads.

## Build and install

Requires Olares 1.12.6 or newer. From the apps repository root:

```sh
olares-cli chart lint sabnzbd
olares-cli chart package sabnzbd -o dist
```

In Market, open **My Olares > Upload custom app package** and select the generated package. Open SABnzbd and configure your own Usenet provider.

## Storage and resources

- Configuration: persistent Olares AppData.
- Downloads: `Home/Downloads/SABnzbd/{incomplete,complete,watched}` on Olares.
- Incomplete and complete downloads share one volume for efficient moves.
- Initial article cache: 256 MB. Memory request: 128 MiB; container limit: 2 GiB. Actual use depends on downloading, repair and unpacking.
- No GPU, host networking or privileged container is required.

Browser authentication is provided by the private Olares gateway. SABnzbd allows proxied web access; hostname validation and API key protection remain enabled. Do not expose the container directly without configuring SABnzbd authentication.

The first-start configuration is not rewritten on later upgrades. Keep provider credentials and API keys out of source code, screenshots and issue reports.

## Upstream

- [SABnzbd](https://github.com/sabnzbd/sabnzbd), GPL-2.0
- [LinuxServer.io container](https://github.com/linuxserver/docker-sabnzbd)
- [Olares packaging](https://www.olares.com/docs/developer/develop/package/manifest)

Names and logos belong to their respective owners. This is a community Olares package.
