# NFC Service Development Overview

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @amunra03-->
<!--Designer: @wenxiaolin-->
<!--Tester: @zs_111-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=aaafc9fd6ce220a97d41d65de36c3b10ebecc876 translatedAt=2026-06-01T12:49:58.805Z pushedAt=2026-06-02T07:46:18.698Z -->

## Overview

NFC, short for Near Field Communication, is a short-range high-frequency radio technology operating at 13.56 MHz, with a communication distance typically within 10 centimeters. NFC services provide functions such as NFC switch control, NFC tag read/write, and NFC card emulation.

## Module Introduction

### NFC Switch Module

The NFC switch module provides the functions of turning NFC on and off. Applications that turn NFC on or off need to declare the permission **ohos.permission.MANAGE_SECURE_SETTINGS**, which can only be declared by system applications. Therefore, only system applications can turn NFC on or off. For details, see [@ohos.nfc.controller](../../reference/apis-connectivity-kit/js-apis-nfcController.md).

### NFC Tag Read/Write Module

  The NFC tag read/write module provides the capability to discover NFC tags and dispatch them to applications, as well as the ability for applications to access NFC tags through the NFC tag read/write APIs. Applications need to declare the NFC tag read/write capability in the specified format. Only after declaration can applications receive NFC tag dispatches. For details, see [@ohos.nfc.tag](../../reference/apis-connectivity-kit/js-apis-nfcTag.md).

### NFC Card Emulation Module

  The NFC card emulation module provides NFC card services, allowing an electronic device to complete a card interaction with a card reader. Applications must declare the NFC card emulation capability in the specified format before they can use card emulation. For details, see [@ohos.nfc.cardEmulation API Reference](../../reference/apis-connectivity-kit/js-apis-cardEmulation.md).

<!--RP1-->

<!--RP1End-->