# @ohos.boardInfo (Board Hardware Information)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Startup-->
<!--Owner: @chenjinxiang3-->
<!--Designer: @chenjinxiang3-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=86a581c1a7acb7614d9053a166e9416f60afc7ca translatedAt=2026-11-04T01:51:11.045Z pushedAt=2026-11-04T03:10:43.223Z nl=1 -->

This module provides the board-level hardware information query capability, supporting the retrieval of hardware information such as CPU, mainboard, and BIOS. It applies to scenarios such as device identification, asset management, and compatibility judgment. Developers cannot configure this information.

> **NOTE**
>
> The initial APIs of this module are supported since API version 26.0.1. Newly added APIs will be marked with a superscript to indicate their earliest API version.</br>
> The APIs of this module start a temporary process during execution, which may cause blocking when the system load is high. To ensure the responsiveness of the application main thread, avoid calling these APIs in the main thread. Hardware information varies by device and remains fixed. You can cache it locally after the first retrieval to avoid repeated retrieval on each use and improve performance.</br>
> The APIs of this module can be used only in the Stage model.

## Modules to Import

```ts
import { boardInfo } from '@kit.BasicServicesKit';
```

## Constants

**System capability:** SystemCapability.Startup.BoardInfo

**Model restriction:** The APIs of this module can be used only in the Stage model.

**Required permissions**: The items in the table below require different system capabilities.

**Since:** 26.0.1

| Name | Type | Read-Only | Description |
| -------- | -------- | -------- | -------- |
| cpuId | string | Yes | CPU ID.<br>Example: AA AA AA AA 00 00 00 00 (hexadecimal string) |
| cpuArch | string | Yes | CPU architecture.<br>Example: aarch64 |
| cpuVendor | string | Yes | CPU vendor information.<br>Example: HISILICON |
| boardSn | string | Yes | Mainboard serial number.<br>**Required permission:** ohos.permission.ACCESS_BOARD_INFO<br>Example: 0123456789ABCDEF |
| boardVendor | string | Yes | Mainboard vendor.<br>Example: HUAWEI |
| boardName | string | Yes | Mainboard product name.<br>Example: HAD-PCB |
| biosVendor | string | Yes | BIOS vendor.<br>Example: HUAWEI |
| biosVersion | string | Yes | BIOS version.<br>Example: 1.00 |
| biosDate | string | Yes | BIOS release date.<br>Example: 2026/01/01 08:00:00 |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
|---------|---------|
| 201 | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { boardInfo } from '@kit.BasicServicesKit';

let cpuId: string = boardInfo.cpuId;
// Output result: the value of boardInfo cpuId is :AA AA AA AA 00 00 00 00
console.info('the value of boardInfo cpuId is :' + cpuId);

let cpuArch: string = boardInfo.cpuArch;
// Output result: the value of boardInfo cpuArch is :aarch64
console.info('the value of boardInfo cpuArch is :' + cpuArch);

let cpuVendor: string = boardInfo.cpuVendor;
// Output result: the value of boardInfo cpuVendor is :HISILICON
console.info('the value of boardInfo cpuVendor is :' + cpuVendor);

let boardSn: string = boardInfo.boardSn;
// Output result: the value of boardInfo boardSn is :0123456789ABCDEF
console.info('the value of boardInfo boardSn is :' + boardSn);

let boardVendor: string = boardInfo.boardVendor;
// Output result: the value of boardInfo boardVendor is :HUAWEI
console.info('the value of boardInfo boardVendor is :' + boardVendor);

let boardName: string = boardInfo.boardName;
// Output result: the value of boardInfo boardName is :HAD-PCB
console.info('the value of boardInfo boardName is :' + boardName);

let biosVendor: string = boardInfo.biosVendor;
// Output result: the value of boardInfo biosVendor is :HUAWEI
console.info('the value of boardInfo biosVendor is :' + biosVendor);

let biosVersion: string = boardInfo.biosVersion;
// Output result: the value of boardInfo biosVersion is :1.00
console.info('the value of boardInfo biosVersion is :' + biosVersion);

let biosDate: string = boardInfo.biosDate;
// Output result: the value of boardInfo biosDate is :2026/01/01 08:00:00
console.info('the value of boardInfo biosDate is :' + biosDate);
```
