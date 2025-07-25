# How OTA works in industry?


Industrial environments: building, energy, automation, and vehicles

- [How OTA works in industry?](#how-ota-works-in-industry)
  - [1. How IoT enables remote firmware updates (OTA)?](#1-how-iot-enables-remote-firmware-updates-ota)
  - [2. Before Involving Controller: test the server side first.](#2-before-involving-controller-test-the-server-side-first)


## 1. How IoT enables remote firmware updates (OTA)?
STEP1, The cloud send message to a controller:
```json
{
  "command": "update_firmware",
  "version": "v2.4.1",
  "url": "https://firmware.elevator.com/updates/ctrl_v2.4.1.bin",
  "checksum": "SHA256:abc123..."
}
```
STEP2, controller Downloads firmware via HTTPS(mostly) or MQTT chunking
-   | Downloads firmware from URL
-   | Validates signature
-   | Replaces old firmware
-   | Reboots
-   | Reports status back to cloud

## 2. Before Involving Controller: test the server side first.

You need to test the firmware server first to ensure your OTA infrastructure is working before involving the controller. This is very simple via web browsers or CLI tools:

If you have a firmware file hosted at this address:
```sh
https://firmware.a_controller.com/update_v2.1.bin
```

1. Simply paste the url into a browser address bar and press Enter, it'll download the .bin file. 
2. Use 'curl' command `curl -v https://firmware.a_controller.com/update_v2.1.bin
`

Next, you'll need to check the file's integrity with:
```sh
sha256sum update_v2.1.bin
You'll get

3a7f9c1d8e88d6a4d4c1fcdf203f11939bc7....
```