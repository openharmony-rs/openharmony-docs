# StationInfo（系统接口）

WLAN站点信息。

**起始版本：** 23

<!--Device-wifiManager-interface StationInfo--><!--Device-wifiManager-interface StationInfo-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## ipAddress

```TypeScript
ipAddress: string
```

WLAN客户端的IP地址

**类型：** string

**起始版本：** 23

<!--Device-StationInfo-ipAddress: string--><!--Device-StationInfo-ipAddress: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## macAddress

```TypeScript
macAddress: string
```

WLAN客户端的MAC地址

**类型：** string

**起始版本：** 23

<!--Device-StationInfo-macAddress: string--><!--Device-StationInfo-macAddress: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## macAddressType

```TypeScript
macAddressType?: DeviceAddressType
```

WLAN客户端的MAC地址类型

**类型：** [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md)

**起始版本：** 23

<!--Device-StationInfo-macAddressType?: DeviceAddressType--><!--Device-StationInfo-macAddressType?: DeviceAddressType-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## name

```TypeScript
name: string
```

WLAN客户端的网络名称

**类型：** string

**起始版本：** 23

<!--Device-StationInfo-name: string--><!--Device-StationInfo-name: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

