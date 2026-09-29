# WirelessSignalFeature（系统接口）

```TypeScript
export interface WirelessSignalFeature
```

Wi-Fi指纹信息。

**起始版本：** 26.0.0

<!--Device-geoLocationManager-export interface WirelessSignalFeature--><!--Device-geoLocationManager-export interface WirelessSignalFeature-End-->

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## mac

```TypeScript
mac: Array<string>
```

表示设备MAC地址信息集合。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WirelessSignalFeature-mac: Array<string>--><!--Device-WirelessSignalFeature-mac: Array<string>-End-->

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

## rssiAvg

```TypeScript
rssiAvg: number
```

表示RSSI平均值。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WirelessSignalFeature-rssiAvg: int--><!--Device-WirelessSignalFeature-rssiAvg: int-End-->

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

## rssiStandardDeviation

```TypeScript
rssiStandardDeviation: number
```

表示RSSI标准差。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WirelessSignalFeature-rssiStandardDeviation: double--><!--Device-WirelessSignalFeature-rssiStandardDeviation: double-End-->

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。
