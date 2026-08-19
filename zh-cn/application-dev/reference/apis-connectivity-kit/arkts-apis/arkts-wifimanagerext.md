# @ohos.wifiManagerExt

提供WLAN扩展接口，供非通用类型产品使用。 &lt;p&gt;本文件涉及的接口为非通用接口。这些扩展接口仅供部分产品类型使用，例如路由器。普通产品不应使用这些接口。&lt;/p&gt;

**起始版本：** 9

<!--Device-unnamed-declare namespace wifiManagerExt--><!--Device-unnamed-declare namespace wifiManagerExt-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Extension

## 导入模块

```TypeScript
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [disableHotspot](arkts-connectivity-wifimanagerext-disablehotspot-f.md) | 去使能WLAN热点。 如果禁用WLAN热点后Wi-Fi处于启用状态，则Wi-Fi可能会被重新启用。 |
| [enableHotspot](arkts-connectivity-wifimanagerext-enablehotspot-f.md) | 使能WLAN热点。 该方法为异步方法。启用WLAN热点后，Wi-Fi可能会被禁用。 |
| [getPowerMode](arkts-connectivity-wifimanagerext-getpowermode-f.md) | 获取功率模式。 |
| [getPowerMode](arkts-connectivity-wifimanagerext-getpowermode-f.md) | 获取功率模式。 |
| [getSupportedPowerMode](arkts-connectivity-wifimanagerext-getsupportedpowermode-f.md) | 获取支持的功率模式。 |
| [getSupportedPowerMode](arkts-connectivity-wifimanagerext-getsupportedpowermode-f.md) | 获取支持的功率模式。 |
| [setPowerMode](arkts-connectivity-wifimanagerext-setpowermode-f.md) | 设置功率模式。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [PowerMode](arkts-connectivity-wifimanagerext-powermode-e.md) | 表示功率模式的枚举。 |

