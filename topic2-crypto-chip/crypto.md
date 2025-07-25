# Crypto Chip ATECC608b for Authentification


- [Crypto Chip ATECC608b for Authentification](#crypto-chip-atecc608b-for-authentification)
  - [1. ATECC608b $0.5 🌎 Official link.](#1-atecc608b-05--official-link)
  - [2. The key is to give each chip a UNIQUE identity (https://www.youtube.com/watch?v=vZn2FU5Mn8Y)](#2-the-key-is-to-give-each-chip-a-unique-identity-httpswwwyoutubecomwatchvvzn2fu5mn8y)
  - [3. Background knowledge: Asymmetric encryption](#3-background-knowledge-asymmetric-encryption)
  - [4. What's the process? How it works?](#4-whats-the-process-how-it-works)
    - [Case: Controller want to send a temperature data to the cloud via MQTT, the controller has a crypto chip inside. The cloud wants to verify: “Who are you? Are you the real device123? Prove it!”](#case-controller-want-to-send-a-temperature-data-to-the-cloud-via-mqtt-the-controller-has-a-crypto-chip-inside-the-cloud-wants-to-verify-who-are-you-are-you-the-real-device123-prove-it)



## 1. [ATECC608b $0.5 🌎 Official link.](https://www.microchip.com/en-us/product/atecc608b)

<img src="image-2.png" width="300">

![price](image-1.png)

## 2. The key is to give each chip a UNIQUE identity (https://www.youtube.com/watch?v=vZn2FU5Mn8Y)




<img src="image-4.png" width="600">
<img src="image-3.png" width="600">


<img src="image-5.png" width="600">

<img src="image-6.png" width="600">


## 3. Background knowledge: Asymmetric encryption



1. What is 'RSA': The RSA (Rivest–Shamir–Adleman) cryptosystem is a public-key cryptosystem, one of the oldest widely used for secure data transmission.
2. RSA is the algorthim to do Encryption and Decryption, there are others.
3. RSA is public
4. The public key is public
5. The private key is private 


<img src="image-8.png" width="500">

<img src="image-7.png" width="500">

<img src="image-9.png" width="500">


-  https://www.youtube.com/watch?v=AQDCe585Lnc
-  https://www.youtube.com/watch?v=o_g-M7UBqI8


## 4. What's the process? How it works?

### Case: Controller want to send a temperature data to the cloud via MQTT, the controller has a crypto chip inside. The cloud wants to verify: “Who are you? Are you the real device123? Prove it!”

STEP1: ATECC608B chip has private key, which never leaves the chip. The paired public key is shared with cloud (How? you controller can read the public key from the chip, you put the public key into the cloud registration system: `{
  "device_id": "device123",
  "public_key": "04AA98C3...EEAF"
}`, the cloud has a **database** to store it.)

STEP2: Controller prepare payload (plain text):
```json
{
  "device_id": "device123",
  "temp": 24.7,
  "timestamp": 1724568000
}
```

STEP3: Controller hashes the payload into code:
```c
SHA256(data) = 0xFA9C123...ZZ45
```

STEP4: Controller send the sha value to crypto chip to get the signature.
```c
signature = send_data_to_sign(0xFA9C123...ZZ45);
>>signature = 0x8A34...BEEF;
```

STEP5: Controller arrange and send the new payload
```json
{
  "device_id": "device123",
  "temp": 24.7,
  "timestamp": 1724568000,
  "signature": "8A34...BEEF"
}
```

STEP5: Cloud verifies signature. It already knows the public key for `device123`. If ok, the message is accepted, if not it's rejected. 

