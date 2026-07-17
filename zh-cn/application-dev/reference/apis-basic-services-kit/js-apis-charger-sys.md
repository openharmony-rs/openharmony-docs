# @ohos.charger (充电类型)(系统接口)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->

充电类型模块用于获取当前设备的充电类型信息，支持识别有线充电（正常、快速、超级快速）和无线充电（正常、快速、超级快速）等多种充电模式，适用于需要根据充电类型进行功率管理、充电策略调整或充电状态展示等场景，帮助开发者精准感知设备充电能力，优化充电相关功能的用户体验。

> **说明：**
>
> 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块为系统接口。


## 导入模块

```js
import { charger } from '@kit.BasicServicesKit';
```

## ChargeType

表示充电类型的枚举。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.PowerManager.BatteryManager.Core

| 名称       | 值  | 说明              |
| -------- | ---- | ----------------- |
| NONE                 | 0    | 表示无充电类型，即设备当前未处于充电状态。      |
| WIRED_NORMAL         | 1    | 表示有线正常充电类型。 |
| WIRED_QUICK          | 2    | 表示有线快速充电类型。   |
| WIRED_SUPER_QUICK    | 3    | 表示有线超级快速充电类型。 |
| WIRELESS_NORMAL      | 4    | 表示无线正常充电类型。 |
| WIRELESS_QUICK       | 5    | 表示无线快速充电类型。 |
| WIRELESS_SUPER_QUICK | 6    | 表示无线超级快速充电类型。 |
