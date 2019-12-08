# tuyapi sniffer

Builds a Docker image running the [tuyapi/cli](https://github.com/TuyaAPI/cli) to extract keys and IDs of Tuya devices.

This image targets ARM 32-bit architectures, like the Raspberry Pi family, and x86\_64. Select the appropriate Dockerfile.

## Usage

### prerequist

- Tuya's Smart Switch app installed
- devices set up in the app
- know how to set up a HTTP proxy on your phone (not a VPN)

### steps

- First, build the Docker image.

```bash
docker build -f tuya-sniffer.arm32v7 -t tuya-sniffer:arm32v7 .
or
docker build -f tuya-sniffer.amd64 -t tuya-sniffer:amd64 .
```

- Then run it.

```
docker run --rm --name tuya-sniffer --net=host -it tuya-sniffer:arm32v7
or
docker run --rm --name tuya-sniffer --net=host -it tuya-sniffer:amd64
```

- Scan the QR code to download the temporary certificate (remove it after you got the keys!).
- Set up the proxy on your phone for __WiFi__ (proxy address below QR code).
- Open the Smart Switch app and pull down the devices list to refresh them.
- IDs and keys should show up in the terminal.

If you have any questions or problems with the process itself, please refer to the [original sources](https://github.com/codetheweb/tuyapi/blob/master/docs/SETUP.md).
