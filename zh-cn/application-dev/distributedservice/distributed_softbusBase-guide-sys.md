# 设备感知开发指南（仅对系统应用开放）
<!--Kit: Distributed Service Kit-->
<!--Subsystem: Communication-->
<!--Owner: @Lucky-M-->
<!--Designer: @Lucky-M-->
<!--Tester: @openharmony_ci-->
<!--Adviser: @hu-zhiqiong-->

## 简介

随着分布式协同场景的发展，设备间的协同唤醒需求日益增长。OpenHarmony 基于分布式软总线，提供设备感知能力（softbusBase），支持系统应用通过自定义数据广播唤醒周边协同设备，并通过扫描发现周边感知设备。

该模块包含感知广播（advertising）的启停、高频切换、感知扫描（scanning）的启停以及已发现设备列表查询等核心能力，使系统应用能够在近场设备间进行低功耗、高效的协同唤醒与发现。

### 实现原理

设备感知能力基于 BLE 广播/扫描实现，无需设备预先组网。广播端通过 `startPerceptionAdv` 携带自定义数据广播自身，扫描端通过 `startPerceptionScan` 发现周边感知设备，并经 `getPerceptionDeviceList` 获取设备列表。广播端在协同唤醒等短时高频场景可调用 `setPerceptionAdvHighFreq` 切换高频 10 秒。

应用通过感知类型（`PerceptionType`）区分业务场景（如协同唤醒），通过保活周期（`PerceptionCycle`）控制扫描功耗档位。

### 约束与限制

- 需要配置 `ohos.permission.ACCESS_SOFTBUS_SYS_HAP` 和 `ohos.permission.DISTRIBUTED_DATASYNC` 权限。
- 仅系统应用可用。
- 需开启设备蓝牙（BLE）能力。
- 自定义数据 `customData` 最大长度 5 字节；设备 ID `deviceId` 最大长度 6 字节，网络字节序（大端）。
- 该能力从 API 版本 26.0.1 开始支持。

## 环境准备

### 环境要求

确保参与感知的设备已开启蓝牙。

### 搭建环境

1. 在开发 PC 上安装 [DevEco Studio](https://developer.huawei.com/cn/download/deveco-studio)，版本要求在 4.1 及以上。
2. 将 public-SDK 更新到 API 26.0.1 或以上，具体操作参见[更新指南](../tools/openharmony-sdk-upgrade-assistant.md)。
3. 用 USB 线缆将调测设备连接到开发 PC。
4. 确保设备已开启蓝牙。

## 接口说明

常用接口说明如下表。具体接口说明详见 API 参考 `@ohos.distributed.softbusBase`。

| 接口名 | 功能描述 |
| --- | --- |
| startPerceptionAdv(type: PerceptionType, customData?: ArrayBuffer) | 启动感知广播或更新当前所有者的自定义数据。 |
| setPerceptionAdvHighFreq(type: PerceptionType, customData?: ArrayBuffer) | 将活跃感知广播切换为高频 10 秒，可同时更新自定义数据。 |
| stopPerceptionAdv(type: PerceptionType) | 停止当前所有者的感知广播。 |
| startPerceptionScan(type: PerceptionType, cycle: PerceptionCycle) | 以指定保活周期启动当前所有者的感知扫描。 |
| stopPerceptionScan(type: PerceptionType) | 停止感知扫描并清空已发现设备列表。 |
| getPerceptionDeviceList(type: PerceptionType) | 获取感知扫描发现的设备列表。 |

### PerceptionType 枚举

| 名称 | 值 | 说明 |
| --- | --- | --- |
| PERCEPTION_TYPE_COLLABORATIVE_WAKE | 0 | 协同唤醒。该类型的感知广播或扫描用于跨设备协同唤醒。 |

### PerceptionCycle 枚举

| 名称 | 值 | 说明 |
| --- | --- | --- |
| PERCEPTION_CYCLE_LOW | 0 | 低档位。保活周期最长。 |
| PERCEPTION_CYCLE_MEDIUM | 1 | 中档位。保活周期中等。 |
| PERCEPTION_CYCLE_HIGH | 2 | 高档位。保活周期最短。 |

### PerceptionDeviceInfo 结构体

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| deviceType | number | 设备类型，取值为整数，具体取值及含义请参考系统设备类型相关定义。 |
| deviceId | ArrayBuffer | 设备 ID，最大长度 6 字节，网络字节序（大端）。 |
| customData | ArrayBuffer | 广播携带的自定义数据，最大长度 5 字节。 |

## 设备感知开发指导

- 广播端调用 startPerceptionAdv() 携带自定义数据启动广播；如需短时高频，调用 setPerceptionAdvHighFreq()。
- 扫描端调用 startPerceptionScan() 启动扫描，调用 getPerceptionDeviceList() 获取已发现设备。
- 不再使用时分别调用 stopPerceptionAdv() / stopPerceptionScan() 停止。

### 广播端开发指导

**1. 导入所需的模块**（完整工程还需导入 `BusinessError`、`Logger` 等，见 sample）。

<!-- @[import_softbus_base](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedSoftbusBase/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import softbusBase from '@ohos.distributed.softbusBase';
```

**2. 在 module.json5 配置文件中配置权限。**

```json
{
  "module": {
    "requestPermissions": [
      {
        "name": "ohos.permission.ACCESS_SOFTBUS_SYS_HAP"
      },
      {
        "name": "ohos.permission.DISTRIBUTED_DATASYNC",
        "reason": "$string:reason_distributed_datasync",
        "usedScene": {
          "abilities": [
            "EntryAbility"
          ],
          "when": "inuse"
        }
      }
    ]
  }
}
```

**3. 启动感知广播，携带自定义数据。**

<!-- @[start_adv](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedSoftbusBase/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
const type = softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE;
const customData = this.buildCustomData();
await softbusBase.startPerceptionAdv(type, customData);
```

**4. （可选）切换高频 10 秒并更新自定义数据。**

<!-- @[set_high_freq](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedSoftbusBase/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
const type = softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE;
const customData = this.buildCustomData();
await softbusBase.setPerceptionAdvHighFreq(type, customData);
```

**5. 停止感知广播。**

<!-- @[stop_adv](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedSoftbusBase/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
const type = softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE;
await softbusBase.stopPerceptionAdv(type);
```

### 扫描端开发指导

**1. 导入所需的模块**（与广播端一致）。

<!-- @[import_softbus_base](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedSoftbusBase/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import softbusBase from '@ohos.distributed.softbusBase';
```

**2. 在 module.json5 配置文件中配置权限**（与广播端一致，参见上文）。

**3. 启动感知扫描，指定保活周期。**

<!-- @[start_scan](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedSoftbusBase/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
const type = softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE;
const cycle = softbusBase.PerceptionCycle.PERCEPTION_CYCLE_MEDIUM;
await softbusBase.startPerceptionScan(type, cycle);
```

**4. 获取感知扫描发现的设备列表。**

<!-- @[get_device_list](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedSoftbusBase/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
const type = softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE;
const devices = await softbusBase.getPerceptionDeviceList(type);
```

**5. 停止感知扫描并清空设备列表。**

<!-- @[stop_scan](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedSoftbusBase/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
const type = softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE;
await softbusBase.stopPerceptionScan(type);
```
