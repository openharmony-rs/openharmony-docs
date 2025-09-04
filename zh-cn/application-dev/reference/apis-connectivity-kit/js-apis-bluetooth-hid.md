# @ohos.bluetooth.hid (蓝牙hid模块)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

本模块提供基于人机接口协议（Human Interface Device Profile，[HID](../../connectivity/terminology.md#hid)）技术的蓝牙人机交互能力，支持获取连接状态等方法。传统蓝牙HID和低功耗蓝牙[HOGP](../../connectivity/terminology.md#hogp)设备均可使用此模块API，相关功能都集成在此HID模块中。
> **说明：**
>
> 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```js
import { hid } from '@kit.ConnectivityKit';
```

## BaseProfile

type BaseProfile = baseProfile.BaseProfile

基础Profile接口定义，提供订阅和获取连接状态等公共能力。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

| 类型                            | 说明         |
| ----------------------------- | ---------- |
| [baseProfile.BaseProfile](js-apis-bluetooth-baseProfile.md#baseprofile) | 基础Profile接口定义。 |

## hid.createHidHostProfile

createHidHostProfile(): HidHostProfile

创建蓝牙[HID Host](../../connectivity/terminology.md#hid-host)实例。通过该实例可使用本端作为HID Host的接口，如：获取和其他设备间的蓝牙HID连接状态。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型                            | 说明         |
| ----------------------------- | ---------- |
| HidHostProfile | 返回HID Host实例。<br>- 该类继承于[BaseProfile](#baseprofile)，因此可以使用其父类中的方法。<br>- 和该实例角色相对应的是[HID Device](../../connectivity/terminology.md#hid-device)角色。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let hidHostProfile = hid.createHidHostProfile();
    console.info('hidHost success');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
