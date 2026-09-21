# @ohos.wifiext(WLAN扩展接口)

该模块主要提供Wi-Fi扩展接口，供非通用类型产品使用。

> **说明：** 
> 
> 从API version 9开始，该接口不再维护，推荐使用[@ohos.wifiManagerExt (WLAN扩展接口)](arkts-connectivity-wifimanagerext.md)等相关接口。

**起始版本：** 8

**系统能力：** SystemCapability.Communication.WiFi.AP.Extension

## 导入模块

```TypeScript
import { wifiext } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [disableHotspot](arkts-connectivity-wifiext-disablehotspot-f.md) | 禁用Wi-Fi热点。 |
| [enableHotspot](arkts-connectivity-wifiext-enablehotspot-f.md) | 启用Wi-Fi热点。 |
| [getPowerModel](arkts-connectivity-wifiext-getpowermodel-f.md#getpowermodel) | 获取功率模式，使用Promise异步回调。 |
| [getPowerModel](arkts-connectivity-wifiext-getpowermodel-f.md#getpowermodel-1) | 获取功率模式。使用callback异步回调。 |
| [getSupportedPowerModel](arkts-connectivity-wifiext-getsupportedpowermodel-f.md#getsupportedpowermodel) | 获取支持的功率模式。使用Promise异步回调。 |
| [getSupportedPowerModel](arkts-connectivity-wifiext-getsupportedpowermodel-f.md#getsupportedpowermodel-1) | 获取支持的功率模式。使用callback异步回调。 |
| [setPowerModel](arkts-connectivity-wifiext-setpowermodel-f.md) | 设置功率模式。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [PowerModel](arkts-connectivity-wifiext-powermodel-e.md) | 表示功率模式的枚举。 |
