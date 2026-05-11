# NFC服务开发概述

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @amunra03-->
<!--Designer: @wenxiaolin-->
<!--Tester: @zs_111-->
<!--Adviser: @zhang_yixin13-->

## 概述
NFC英文全称Near Field Communication，是一种短距高频的无线电技术，在13.56MHz频率运行，通信距离一般在10厘米距离内。NFC服务提供NFC开关控制、NFC标签读写、NFC卡模拟等业务功能。

## 模块介绍

### NFC开关模块
  NFC开关模块，提供了打开NFC和关闭NFC功能。打开或关闭NFC的应用程序，需要声明权限"ohos.permission.MANAGE_SECURE_SETTINGS"，该权限只有系统应用才能声明。因此，只有系统应用才能打开或关闭NFC。详情请参考[@ohos.nfc.controller API参考](../../reference/apis-connectivity-kit/js-apis-nfcController.md)。

### NFC标签读写模块
  NFC标签读写模块，提供了NFC标签的发现和分发给应用程序，以及应用程序通过NFC标签读写接口访问NFC标签的能力。应用程序需要按照规定的格式来声明NFC标签读写能力，只有声明后应用程序才能收到NFC标签的分发。详情请参考[@ohos.nfc.tag API参考](../../reference/apis-connectivity-kit/js-apis-nfcTag.md)。

### NFC卡模拟模块
  NFC卡模拟模块，提供了NFC的刷卡业务，电子设备和读卡器触碰完成刷卡。应用程序需要按照规定的格式来声明NFC卡模拟能力，只有声明后应用程序才能够具备刷卡能力。详情请参考[@ohos.nfc.cardEmulation API参考](../../reference/apis-connectivity-kit/js-apis-cardEmulation.md)。

<!--RP1-->

<!--RP1End-->