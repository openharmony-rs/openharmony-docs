# @ohos.nearlink.advertising

提供与广播相关的方法。附近的设备可以扫描并发现该设备。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [offAdvertisingStateChange](arkts-connectivity-offadvertisingstatechange-f.md#offadvertisingstatechange-1) | 取消订阅广播状态变更事件。 |
| [onAdvertisingStateChange](arkts-connectivity-onadvertisingstatechange-f.md#onadvertisingstatechange-1) | 订阅广播状态变化事件。只有授予了ohos.permission.NEARLINK_ACCESS权限的系统应用程序才能访问此事件。 |
| [startAdvertising](arkts-connectivity-startadvertising-f.md#startadvertising-1) | 开始广播。 |
| [stopAdvertising](arkts-connectivity-stopadvertising-f.md#stopadvertising-1) | 停止广播ID对应的广播。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AdvertisingData](arkts-connectivity-advertisingdata-i.md) | 广播数据。 |
| [AdvertisingParams](arkts-connectivity-advertisingparams-i.md) | 广播参数。 |
| [AdvertisingSettings](arkts-connectivity-advertisingsettings-i.md) | 广播设置。 |
| [AdvertisingStateChangeInfo](arkts-connectivity-advertisingstatechangeinfo-i.md) | 广播状态变化信息。 |
| [ManufacturerData](arkts-connectivity-manufacturerdata-i.md) | 描述制造商数据。 |
| [ServiceData](arkts-connectivity-servicedata-i.md) | 服务数据。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AdvertisingState](arkts-connectivity-advertisingstate-e.md) | 广播状态的枚举。 |
| [TxPowerMode](arkts-connectivity-txpowermode-e.md) | 广播模式的枚举。 |

