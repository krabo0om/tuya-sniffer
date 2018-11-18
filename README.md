# tuyapi sniffer

Builds a Docker image running the [tuyapi/cli](https://github.com/TuyaAPI/cli) to extract keys and IDs of Tuya devices.

This image targets ARM 32-bit architectures like the Raspberry Pi family. For x86, just change the `FROM` command to use a x86 base image.

## Usage

### prerequist

- Tuya's Smart Switch app installed
- devices set up in the app
- know how to set up a HTTP proxy on your phone (not a VPN)

### steps

- First, build the Docker image.

`docker build -f tuya-sniffer.arm32v7 -t tuya-sniffer:arm32v7 .`

- Then run it.

`docker run --rm --name tuya-sniffer -p 8001:8001 -it tuya-sniffer:arm32v7`

- Scan the QR code to download the temporary certificate (remove it after you got the keys!).
- Set up the proxy on your phone for the WiFi (proxy address below QR code).
- Open the Smart Switch app and pull down the devices list to refresh them.
- IDs and keys should show up in the terminal.

If you have any questions or problems with the process itself, please refer to the [original sources](https://github.com/codetheweb/tuyapi/blob/master/docs/SETUP.md).
