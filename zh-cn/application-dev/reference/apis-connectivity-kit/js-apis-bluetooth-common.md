# @ohos.bluetooth.common (蓝牙common模块)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

本模块提供了蓝牙公共接口和参数类型。

> **说明：**
>
> 本模块首批接口从API version 21开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```js
import common from '@ohos.bluetooth.common';
```

## BluetoothAddress

描述蓝牙设备地址信息的参数类型。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

| 名称       | 类型   | 只读   | 可选   | 说明          |
| -------- | ------ | ---- | ---- | ----------- |
| address    | string      | 否    | 否    | 表示蓝牙设备的地址，例如："XX:XX:XX:XX:XX:XX"。|
| [addressType](#addresstype)     | int      | 否    | 否    | 表示地址类型为蓝牙设备的真实地址或虚拟地址。|

## addressType

枚举，表示地址类型为蓝牙设备的真实地址或虚拟地址。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

| 名称                 | 值  | 说明     |
| ------------------ | ---- | ------ |
| VIRTUAL        | 1    | 虚拟地址类型。|
| REAL       | 2    | 真实地址类型。|