# @ohos.nearlink.advertising(星闪广播能力)

本模块提供了发送星闪广播的相关功能，包括启动广播、停止广播、订阅广播状态等。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { advertising } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [offAdvertisingStateChange](arkts-connectivity-advertising-offadvertisingstatechange-f.md) | 取消订阅星闪广播状态变化事件。使用callback异步回调。 |
| [onAdvertisingStateChange](arkts-connectivity-advertising-onadvertisingstatechange-f.md) | 订阅星闪广播状态变化事件。使用callback异步回调。当调用[advertising.startAdvertising](arkts-connectivity-advertising-startadvertising-f.md)启动广播或[advertising.stopAdvertising](arkts-connectivity-advertising-stopadvertising-f.md)停止广播时，回调函数会被触发，返回对应的广播ID与广播状态。需与[advertising.offAdvertisingStateChange](arkts-connectivity-advertising-offadvertisingstatechange-f.md)配对使用。 |
| [startAdvertising](arkts-connectivity-advertising-startadvertising-f.md) | 发送星闪广播。使用Promise异步回调。适用于设备发现、设备信息广播等需要将本端设备能力或数据对外发布的业务场景，配合[advertising.onAdvertisingStateChange](arkts-connectivity-advertising-onadvertisingstatechange-f.md)可监听广播启停状态。 |
| [stopAdvertising](arkts-connectivity-advertising-stopadvertising-f.md) | 停止发送星闪广播。使用Promise异步回调。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AdvertisingData](arkts-connectivity-advertising-advertisingdata-i.md) | 表示广播数据包。 |
| [AdvertisingParams](arkts-connectivity-advertising-advertisingparams-i.md) | 表示发送广播携带的参数。 |
| [AdvertisingSettings](arkts-connectivity-advertising-advertisingsettings-i.md) | 表示广播配置参数。 |
| [AdvertisingStateChangeInfo](arkts-connectivity-advertising-advertisingstatechangeinfo-i.md) | 表示广播启停状态变化信息。 |
| [ManufacturerData](arkts-connectivity-advertising-manufacturerdata-i.md) | 表示厂商数据。 |
| [ServiceData](arkts-connectivity-advertising-servicedata-i.md) | 表示服务相关数据。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AdvertisingState](arkts-connectivity-advertising-advertisingstate-e.md) | 表示广播状态，为枚举值。 |
| [TxPowerMode](arkts-connectivity-advertising-txpowermode-e.md) | 表示广播发送模式，为枚举值。 |
