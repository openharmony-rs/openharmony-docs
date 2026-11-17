# P2pUpnpInfo

```TypeScript
interface P2pUpnpInfo
```

表示从对端设备收到的UPnP服务响应信息。

**起始版本：** 26.1.0

<!--Device-wifiManager-interface P2pUpnpInfo--><!--Device-wifiManager-interface P2pUpnpInfo-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## device

```TypeScript
device: WifiP2pDevice
```

响应该UPnP服务的对端设备。

**类型：** [WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-P2pUpnpInfo-device: WifiP2pDevice--><!--Device-P2pUpnpInfo-device: WifiP2pDevice-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## uniqueServiceNames

```TypeScript
uniqueServiceNames: Array<string>
```

已发现的唯一服务名称列表。单条数据记录的最大大小为1024字节，数据量与目标设备上的服务数量有关。

**类型：** Array&lt;string&gt;

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-P2pUpnpInfo-uniqueServiceNames: Array<string>--><!--Device-P2pUpnpInfo-uniqueServiceNames: Array<string>-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P
