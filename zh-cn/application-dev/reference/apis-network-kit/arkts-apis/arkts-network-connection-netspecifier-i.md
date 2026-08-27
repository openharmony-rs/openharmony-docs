# NetSpecifier

提供承载数据网络能力的实例。

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
```

## bearerPrivateIdentifier

```TypeScript
bearerPrivateIdentifier?: string
```

网络标识符，蜂窝网络的标识符是"slot0"（对应SIM卡1）、"slot1"（对应SIM卡2）。从API12开始可以通过传递注册的WLAN热点信息表示应用希望激活的指定的WLAN网络。

**类型：** string

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

## netCapabilities

```TypeScript
netCapabilities: NetCapabilities
```

存储数据网络的传输能力和承载类型。

**类型：** [NetCapabilities](arkts-network-connection-netcapabilities-i.md)

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let config: wifiManager.WifiDeviceConfig = {
  ssid: "TEST",
  preSharedKey: "**********",
  securityType: wifiManager.WifiSecurityType.WIFI_SEC_TYPE_PSK
};
// 通过wifiManager.addCandidateConfig获取注册WLAN的networkId。
wifiManager.addCandidateConfig(config,(error,networkId) => {
 let netConnectionWlan = connection.createNetConnection({
   netCapabilities: {
     bearerTypes: [connection.NetBearType.BEARER_WIFI]
   },
   bearerPrivateIdentifier: `${networkId}`
 });
 netConnectionWlan.register((error: BusinessError) => {
   console.error(`Failed to register. Code:${error.code}, message:${error.message}`);
 });
});
```
