# @ohos.bluetooth.constant (蓝牙constant模块)(系统接口)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

constant模块提供了蓝牙中常量的定义，包括访问权限等枚举常量，用于在蓝牙通信过程中统一标识和区分不同的状态与类型，适用于蓝牙连接管理等场景。

> **说明：**
>
> 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.bluetooth.constant (蓝牙constant模块)](js-apis-bluetooth-constant.md)。

## 导入模块

```js
import { constant } from '@kit.ConnectivityKit';
```

## AccessAuthorization<sup>11+</sup>

枚举，蓝牙访问授权状态。表示对端蓝牙设备访问本端蓝牙Profile（如电话簿、消息等）的授权状态，用于蓝牙数据访问授权场景。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

| 名称                 | 值  | 说明     |
| ------------------ | ---- | ------ |
| UNKNOWN | 0    | 未知。<br/>此接口为系统接口。  |
| ALLOWED | 1    | 允许。<br/>此接口为系统接口。  |
| REJECTED | 2    | 拒绝。<br/>此接口为系统接口。 |