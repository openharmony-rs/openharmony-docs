# @ohos.nearlink.advertising

提供与广播相关的方法。附近的设备可以扫描并发现该设备。

**起始版本：** 26.0.0

<!--Device-unnamed-declare namespace advertising--><!--Device-unnamed-declare namespace advertising-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { advertising } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [offAdvertisingStateChange](arkts-connectivity-advertising-offadvertisingstatechange-f.md#offadvertisingstatechange) | 取消订阅广播状态变更事件。 |
| [onAdvertisingStateChange](arkts-connectivity-advertising-onadvertisingstatechange-f.md#onadvertisingstatechange) | 订阅广播状态变化事件。  只有授予了ohos.permission.NEARLINK_ACCESS权限的系统应用程序才能访问此事件。 |
| [startAdvertising](arkts-connectivity-advertising-startadvertising-f.md#startadvertising) | 开始广播。 |
| [stopAdvertising](arkts-connectivity-advertising-stopadvertising-f.md#stopadvertising) | 停止广播ID对应的广播。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AdvertisingData](arkts-connectivity-advertising-advertisingdata-i.md) | 广播数据。 |
| [AdvertisingParams](arkts-connectivity-advertising-advertisingparams-i.md) | 广播参数。 |
| [AdvertisingSettings](arkts-connectivity-advertising-advertisingsettings-i.md) | 广播设置。 |
| [AdvertisingStateChangeInfo](arkts-connectivity-advertising-advertisingstatechangeinfo-i.md) | 广播状态变化信息。 |
| [ManufacturerData](arkts-connectivity-advertising-manufacturerdata-i.md) | 描述制造商数据。 |
| [ServiceData](arkts-connectivity-advertising-servicedata-i.md) | 服务数据。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AdvertisingState](arkts-connectivity-advertising-advertisingstate-e.md) | 广播状态的枚举。 |
| [TxPowerMode](arkts-connectivity-advertising-txpowermode-e.md) | 广播模式的枚举。 |

