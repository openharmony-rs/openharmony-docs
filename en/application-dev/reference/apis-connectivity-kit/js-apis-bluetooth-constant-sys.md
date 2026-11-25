# @ohos.bluetooth.constant (Bluetooth constant Module) (System API)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=4f824c67b9f4e04b01e793c0dcb9c04799653b39 translatedAt=2026-09-15T02:39:19.012Z pushedAt=2026-09-16T02:10:49.530Z -->

The **constant** module provides the definitions of Bluetooth constants, including enumeration constants such as access permission. These constants are used to identify and distinguish different states and types during Bluetooth communication. This module is applicable to scenarios such as Bluetooth connection management.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.bluetooth.constant (Bluetooth constant Module)](js-apis-bluetooth-constant.md).

## Modules to Import

```js
import { constant } from '@kit.ConnectivityKit';
```

## AccessAuthorization<sup>11+</sup>

Enumerates the Bluetooth access authorization states. This method can be used to indicate the authorization state for a peer Bluetooth device to access the local Bluetooth profile (such as contacts and messages), which can be used in Bluetooth data access authorization scenarios.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.Bluetooth.Core

| Name                | Value | Description    |
| ------------------ | ---- | ------ |
| UNKNOWN | 0    | Unknown.<br>This is a system API. |
| ALLOWED | 1    | Access allowed.<br>This is a system API. |
| REJECTED | 2    | Access rejected.<br>This is a system API.|