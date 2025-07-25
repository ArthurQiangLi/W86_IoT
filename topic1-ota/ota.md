# How OTA works in industry?


Industrial environments: building, energy, automation, and vehicles


## Before

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