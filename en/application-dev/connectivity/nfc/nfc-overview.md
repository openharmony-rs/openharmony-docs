# NFC Development

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @yh1719-->
<!--Designer: @wenxiaolin-->
<!--Tester: @zs_111-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=67487829468179127107f74c0916ca5ae8660edf translatedAt=2026-09-01T02:08:44.184Z pushedAt=2026-09-01T11:01:30.619Z -->

## Overview
NFC, short for Near Field Communication, is a short-range high-frequency radio technology operating at 13.56 MHz, with a communication distance typically within 10 centimeters. NFC services provide functions such as NFC switch control, NFC tag read/write, and NFC card emulation.

## Module Introduction

### NFC Switch Module
  Provides APIs for enabling and disabling NFC. Applications that enable or disable NFC must declare the `ohos.permission.MANAGE_SECURE_SETTINGS` permission. Since only system applications can declare this permission, only system applications can enable or disable NFC. For details, see [@ohos.nfc.controller (Standard NFC)](../../reference/apis-connectivity-kit/js-apis-nfcController.md).

### NFC Tag Read/Write Module
  Provides capabilities for discovering NFC tags, dispatching them to applications, and allowing applications to access NFC tags through tag read/write APIs. Applications must declare NFC tag read/write capabilities in the required format before they can receive dispatched NFC tags. For details, see [@ohos.nfc.tag (Standard NFC Tags)](../../reference/apis-connectivity-kit/js-apis-nfcTag.md).

### NFC Card Emulation Module
  Provides card emulation capabilities, allowing electronic devices to complete card transactions by tapping an NFC reader. Applications must declare NFC card emulation capabilities in the required format before they can perform card emulation. For details, see [@ohos.nfc.cardEmulation (Standard NFC Card Emulation)](../../reference/apis-connectivity-kit/js-apis-cardEmulation.md).

<!--RP1-->

<!--RP1End-->