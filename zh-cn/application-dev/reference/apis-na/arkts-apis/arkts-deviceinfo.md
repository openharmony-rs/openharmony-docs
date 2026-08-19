# @ohos.deviceInfo

本模块提供终端设备信息查询，开发者不可配置。 > **说明：** > > 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > 部分参数返回值为default的，会在正式发布的版本中配置。 > 本模块接口返回设备常量信息，建议应用只调用一次，不需要频繁调用。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace deviceInfo--><!--Device-unnamed-declare namespace deviceInfo-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [apiAvailable](arkts-na-deviceinfo-apiavailable-f.md) | 检查指定的API版本在当前设备上是否可用。 此方法提供跨不同OpenHarmony/分布式操作系统版本的兼容性检查。它会根据输入格式和API版本范围自动选择合适的版本检查方法。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DeviceTypes](arkts-na-deviceinfo-devicetypes-e.md) | 设备类型枚举值，可用于校验deviceType的返回值。 |
| [PerformanceClassLevel](arkts-na-deviceinfo-performanceclasslevel-e.md) | 表示设备能力定级的枚举。 |

