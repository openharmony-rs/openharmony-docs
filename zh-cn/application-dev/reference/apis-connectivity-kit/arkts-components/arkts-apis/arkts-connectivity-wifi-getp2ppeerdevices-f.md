# getP2pPeerDevices

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getP2pPeerDevices

```TypeScript
function getP2pPeerDevices(): Promise<WifiP2pDevice[]>
```

获取P2P对端设备列表信息。使用Promise异步回调。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getP2pPeerDevices](arkts-connectivity-wifimanager-getp2ppeerdevices-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

**系统能力：** SystemCapability.Communication.WiFi.P2P

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[WifiP2pDevice](arkts-connectivity-wifi-wifip2pdevice-i.md)[]&gt; | Promise对象。表示对端设备列表信息。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

wifi.getP2pPeerDevices((err, data:wifi.WifiP2pDevice) => {
   if (err) {
       console.error("get P2P peer devices error");
       return;
   }
  console.info("get P2P peer devices: " + JSON.stringify(data));
});

wifi.getP2pPeerDevices().then(data => {
  console.info("get P2P peer devices: " + JSON.stringify(data));
});
```


## getP2pPeerDevices

```TypeScript
function getP2pPeerDevices(callback: AsyncCallback<WifiP2pDevice[]>): void
```

获取P2P对端设备列表信息。使用callback异步回调。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getP2pPeerDevices](arkts-connectivity-wifimanager-getp2ppeerdevices-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WifiP2pDevice](arkts-connectivity-wifi-wifip2pdevice-i.md)[]&gt; | 是 | 回调函数。当操作成功时，err为0，data表示对端设备列表信息。如果err为非0，表示处理出现错误。 |

**示例**

参见 [getP2pPeerDevices](#getp2ppeerdevices)
