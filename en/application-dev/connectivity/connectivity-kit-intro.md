# About This Kit

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

## Overview

Mobile devices have become an integral part of everyday life. For example, people listen to music with Bluetooth headphones, surf the Internet over Wi-Fi, and use their mobile phone as a transit pass or credit card.

In these applications, NFC implements short-range interactions like payments and access control, Bluetooth provides basic wireless connections for devices, such as headphones, wearables, and peripheral devices, and Wi-Fi provides high-speed Internet access.

You can use Connectivity Kit to design mobile applications to meet diverse user needs in their daily lives.

### Bluetooth

Bluetooth is a wireless communication technology that implements short-range data transmission. The Bluetooth technical specifications are formulated by the Bluetooth Special Interest Group (SIG). It can be used to connect a variety of devices, including smartphones, headsets, speakers, keyboards, mouse devices, and printers. Bluetooth features low power consumption, low cost, and ease of use.

Different Bluetooth modules provide APIs applicable to different scenarios, helping developers develop Bluetooth-related features.

- **ACCESS module**<br>
  Provides capabilities such as enabling and disabling Bluetooth and obtaining the Bluetooth status. You need to enable Bluetooth through this module before using other Bluetooth functions. For details, see [@ohos.bluetooth.access](../reference/apis-connectivity-kit/js-apis-bluetooth-access.md).

- **CONNECTION module**<br>
  Provides capabilities such as discovering and pairing Bluetooth devices, as well as obtaining information about the local and peer devices. For details, see [@ohos.bluetooth.connection](../reference/apis-connectivity-kit/js-apis-bluetooth-connection.md).

- **BLE module**<br>
  Provides Bluetooth Low Energy (BLE) capabilities, such as discovering devices, sending advertising packets, discovering services, and transmitting data. For details, see [@ohos.bluetooth.ble](../reference/apis-connectivity-kit/js-apis-bluetooth-ble.md).

- **SOCKET module**<br>
  Provides capabilities such as connecting and transmitting data between Bluetooth devices over Serial Port Profile (SPP). For details, see [@ohos.bluetooth.socket](../reference/apis-connectivity-kit/js-apis-bluetooth-socket.md).

- **A2DP module**<br>
  Establishes Bluetooth connections between devices and transmits high-quality audio over Advanced Audio Distribution Profile (A2DP). For example, this module enables transmission of audio data streams between a phone and audio peripherals (such as headsets and speakers) for music streaming playback. For details, see [@ohos.bluetooth.a2dp](../reference/apis-connectivity-kit/js-apis-bluetooth-a2dp.md).

- **HFP module**<br>
  Establishes connections between Bluetooth devices and enables hands-free calls over the Hands-Free Profile (HFP), supporting functions such as two-way voice call and control. For details, see [@ohos.bluetooth.hfp](../reference/apis-connectivity-kit/js-apis-bluetooth-hfp.md).

- **HID module**<br>
  Implements communication, wireless control, and data transmission between Bluetooth devices over Human Interface Device Profile (HID). For example, this module enables low-latency bidirectional communication between devices such as keyboards, mouse devices, and gamepads and hosts (such as phones, tablets, and PCs). For details, see [@ohos.bluetooth.hid](../reference/apis-connectivity-kit/js-apis-bluetooth-hid.md).

- **PAN module**<br>
  Implements network sharing between devices over Personal Area Network (PAN). For example, this module supports Internet sharing between a phone and a PC. For details, see [@ohos.bluetooth.pan](../reference/apis-connectivity-kit/js-apis-bluetooth-pan.md).

- **MAP module**<br>
  Implements message sharing between devices over Message Access Profile (MAP). For example, this module supports SMS message synchronization between a phone and a head unit. For details, see [@ohos.bluetooth.map](../reference/apis-connectivity-kit/js-apis-bluetooth-map.md).

- **PBAP module**<br>
  Implements phone book data sharing between devices over Phone Book Access Profile (PBAP). For example, this module supports synchronization of contact and call log data between a phone and a head unit. For details, see [@ohos.bluetooth.pbap](../reference/apis-connectivity-kit/js-apis-bluetooth-pbap.md).

### WLAN

A wireless local area network (WLAN) uses the radio, infrared, or other technologies to transmit data between devices that are not physically connected with each other. It is widely used in offices and public places where mobile devices are used.

The WLAN system provides users with WLAN access (STA mode), peer-to-peer data transmission (P2P mode), and hotspot sharing (AP mode).

- STA mode<br>
  STA mode, or Station mode, can be understood as a workstation, that is, a client, within a network. When a device has this capability, it can connect to another routing network, such as a home router, and is typically used to provide data uplink services. For details, see [@ohos.wifiManager (WLAN)](../reference/apis-connectivity-kit/js-apis-wifiManager.md).

- P2P mode<br>
  P2P mode is also known as Wi-Fi Direct. Wi-Fi Direct is a peer-to-peer connection technology that allows two STAs to establish a TCP/IP connection directly without requiring an AP. One STA acts as a traditional AP, referred to as the Group Owner (GO), while the other STA acts as the Group Client (GC) and connects to the GO in the same way that it connects to an AP. For details, see [@ohos.wifiManager (WLAN)](../reference/apis-connectivity-kit/js-apis-wifiManager.md).

- AP mode<br>
  AP mode provides downlink data services for member devices (that is, clients) joining a WLAN. It enables the wireless formation of a WLAN, functioning as the central device of the WLAN. For details, see [@ohos.wifiManager (WLAN)](../reference/apis-connectivity-kit/js-apis-wifiManager.md).

### NFC

The Near Field Communication (NFC) service provides functionalities such as NFC switch control, NFC tag reading and writing, and NFC card emulation.

- **NFC switch control**<br/>
  Provides the functions of enabling and disabling NFC. Applications that enable or disable NFC need to declare the **ohos.permission.MANAGE_SECURE_SETTINGS** permission, which can only be declared by system applications. Therefore, only system applications can enable or disable NFC. For details, see [@ohos.nfc.controller (Standard NFC)](../reference/apis-connectivity-kit/js-apis-nfcController.md).

- NFC tag reading and writing<br>
  Provides the capabilities of discovering NFC tags and distributing them to applications, as well as allowing applications to access NFC tags through the NFC tag read/write API. Applications need to declare the NFC tag read/write capability in the specified format. Only after the declaration can applications receive NFC tag distributions. For details, see [@ohos.nfc.tag (Standard NFC Tags)](../reference/apis-connectivity-kit/js-apis-nfcTag.md).

- NFC card emulation<br>
  Provides NFC card emulation capabilities and allows electronic devices to complete card-based interactions by tapping the device against an NFC reader. Applications must declare NFC card emulation capabilities in the required format before they can support card emulation features. For details, see [@ohos.nfc.cardEmulation (Standard NFC Card Emulation)](../reference/apis-connectivity-kit/js-apis-cardEmulation.md).

### Converged Short-Range Communication

The converged short-range communication service provides unified management of short-range communication technologies in the OpenHarmony system.

- **PartnerAgent service module**<br/>
  Provides interworking services between partner devices and OpenHarmony devices. Within the module, interworking services such as media control, phone call reverse control, and health monitoring can be implemented. For details, see [@ohos.FusionConnectivity.partnerAgent](../reference/apis-connectivity-kit/js-apis-fusionConnectivity-partnerAgent.md).

### Working Principles

Connectivity Kit provides basic communication services for applications. Before a communication service is used by an application, the related feature must be enabled or a connection must be set up. When the service ends, the connection must be closed actively.

### Constraints

Device capabilities can be used only after the related switch is enabled after user authorization. Otherwise, the system does not provide services for third-party applications.

### Related Samples

The following samples are provided to help you better understand how to develop Bluetooth-related services:

- [bluetooth](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Connectivity/Bluetooth)