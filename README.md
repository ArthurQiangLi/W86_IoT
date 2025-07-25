# W86_IoT
MQTT/AT/Home Assistant/SIM7600/

![home remote](00-media/94.jpg)

Key takeaways:
1. both 'Smart Home' and 'IIoT' use MQTT widely.

## SIM7600

- [official site](https://www.simcom.com/product/SIM7600X.html).
- [digikey sim7600 link](https://www.digikey.com/en/products/detail/simcom-wireless-solutions-limited/SIM7600SA/15841464) // [model list and price](https://www.digikey.com/en/products/filter/rf-transceiver-modules-and-modems/872?s=N4IgTCBcDaIMoEkCyB2AbABgyAugXyA).
- [waveshare SIM7600E-H 4G HAT page](https://www.waveshare.com/wiki/SIM7600E-H_4G_HAT). // [Industrial Grade SIM7600G-H 4G DTU](https://www.waveshare.com/product/sim7600g-h-4g-dtu.htm?sku=21137)

- [pdfs in 'sim7600-info' folder](./sim7600-info/).

## Home Assistant

- [Seed Studio link (see h.w. prices)](https://www.seeedstudio.com/home-assistant). //[The big display](https://wiki.seeedstudio.com/reTerminal_Home_Assistant/)
- [NABU CASA: commercial part of Home Assistance](https://support.nabucasa.com/hc/en-us) (it sells h.w. and cloud).


## Topic1: [How is OTA achieved in IIoT?](topic1-ota/ota.md)

## Topic2: [How Cryptographic chip ATECC608b works?](./topic2-crypto-chip/crypto.md)

## Topic3: MQTT is for small data, HTTP can be for large data chunk

small data exmaple like control data:

```json
{
  "current_floor": 5,
  "direction": "UP",
  "door_state": "CLOSED",
  "fault_code": "NONE",
  "in_service": true
}
```




