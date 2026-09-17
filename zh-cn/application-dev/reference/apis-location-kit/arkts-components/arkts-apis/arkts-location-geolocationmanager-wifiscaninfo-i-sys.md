# WifiScanInfo（系统接口）

WiFi扫描信息，包含扫描到的WiFi热点的ssid、bssid和rssi等信息。

**起始版本：** 10

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## bssid

```TypeScript
bssid: string
```

WiFi热点的BSSID。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

## frequency

```TypeScript
frequency: number
```

WiFi热点的频率。单位是赫兹。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

## rssi

```TypeScript
rssi: number
```

WiFi热点的信号强度(dBm)。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

## ssid

```TypeScript
ssid: string
```

WiFi热点的SSID，编码格式为UTF-8。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

## timestamp

```TypeScript
timestamp: number
```

时间戳，单位微秒。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。
