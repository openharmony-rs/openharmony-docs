# NFC Development

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @amunra03-->
<!--Designer: @wenxiaolin-->
<!--Tester: @zs_111-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=dcae6f10c07044342acb5b2dc0416e100c5bcaa2 translatedAt=2026-06-17T06:38:32.867Z pushedAt=2026-06-22T02:51:20.461Z -->

## Overview

NFC, short for Near Field Communication, is a short-range high-frequency radio technology operating at 13.56 MHz, with a communication distance typically within 10 centimeters. NFC services provide functions such as NFC switch control, NFC tag read/write, and NFC card emulation.

## Module Introduction

### NFC Switch Module

  The NFC switch module provides APIs for enabling and disabling NFC. Applications that enable or disable NFC must declare the **ohos.permission.MANAGE_SECURE_SETTINGS** permission. Since only system applications can declare this permission, only system applications can enable or disable NFC. For details, see [@ohos.nfc.controller](../../reference/apis-connectivity-kit/js-apis-nfcController.md).

### NFC Tag Read/Write Module

  The NFC tag module provides capabilities for discovering NFC tags, dispatching them to applications, and allowing applications to access NFC tags through tag read/write APIs. Applications must declare NFC tag read/write capabilities in the required format before they can receive dispatched NFC tags. For details, see [@ohos.nfc.tag](../../reference/apis-connectivity-kit/js-apis-nfcTag.md).

### NFC Card Emulation Module

  The NFC card emulation module provides card emulation capabilities, allowing an electronic device to interact with an NFC reader by tapping it. Applications must declare NFC card emulation capabilities in the required format before they can perform card emulation. For details, see [@ohos.nfc.cardEmulation](../../reference/apis-connectivity-kit/js-apis-cardEmulation.md).

<!--RP1-->

<!--RP1End-->