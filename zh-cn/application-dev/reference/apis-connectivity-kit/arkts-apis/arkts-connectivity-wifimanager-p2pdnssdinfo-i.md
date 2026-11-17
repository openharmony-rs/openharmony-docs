# P2pDnsSdInfo

```TypeScript
interface P2pDnsSdInfo
```

表示从对端设备收到的DNS-SD服务响应信息。

**起始版本：** 26.1.0

<!--Device-wifiManager-interface P2pDnsSdInfo--><!--Device-wifiManager-interface P2pDnsSdInfo-End-->

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

<!--Device-P2pDnsSdInfo-device: WifiP2pDevice--><!--Device-P2pDnsSdInfo-device: WifiP2pDevice-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## instanceName

```TypeScript
instanceName: string
```

已发现的Bonjour服务实例名。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-P2pDnsSdInfo-instanceName: string--><!--Device-P2pDnsSdInfo-instanceName: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## registrationType

```TypeScript
registrationType: string
```

已发现的Bonjour服务注册类型。其前缀与[addDnsSdLocalP2pService](arkts-connectivity-wifimanager-adddnssdlocalp2pservice-f.md)的入参serviceType相同，末尾追加".local."。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-P2pDnsSdInfo-registrationType: string--><!--Device-P2pDnsSdInfo-registrationType: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P
