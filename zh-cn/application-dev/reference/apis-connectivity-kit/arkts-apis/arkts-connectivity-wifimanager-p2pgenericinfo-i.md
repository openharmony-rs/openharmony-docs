# P2pGenericInfo

```TypeScript
interface P2pGenericInfo
```

表示从对端设备收到的通用服务响应信息。

**起始版本：** 26.1.0

<!--Device-wifiManager-interface P2pGenericInfo--><!--Device-wifiManager-interface P2pGenericInfo-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## device

```TypeScript
device: WifiP2pDevice
```

响应该服务的对端设备。

**类型：** [WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-P2pGenericInfo-device: WifiP2pDevice--><!--Device-P2pGenericInfo-device: WifiP2pDevice-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## protocolType

```TypeScript
protocolType: P2pServiceProtocolType
```

响应的服务协议类型。

**类型：** [P2pServiceProtocolType](arkts-connectivity-wifimanager-p2pserviceprotocoltype-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-P2pGenericInfo-protocolType: P2pServiceProtocolType--><!--Device-P2pGenericInfo-protocolType: P2pServiceProtocolType-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## responseData

```TypeScript
responseData: Uint8Array
```

来自对端设备的原始响应数据。最大长度为1024。

**类型：** Uint8Array

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-P2pGenericInfo-responseData: Uint8Array--><!--Device-P2pGenericInfo-responseData: Uint8Array-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P
