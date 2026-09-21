# getP2pLinkedInfo

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getP2pLinkedInfo

```TypeScript
function getP2pLinkedInfo(): Promise<WifiP2pLinkedInfo>
```

获取P2P连接信息。使用Promise异步回调。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getP2pLinkedInfo](arkts-connectivity-wifimanager-getp2plinkedinfo-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.P2P

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[WifiP2pLinkedInfo](arkts-connectivity-wifi-wifip2plinkedinfo-i.md)&gt; | Promise对象。表示P2P连接信息。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

wifi.getP2pLinkedInfo((err, data:wifi.WifiP2pLinkedInfo) => {
   if (err) {
       console.error("get p2p linked info error");
       return;
   }
  console.info("get wifi p2p linked info: " + JSON.stringify(data));
});

wifi.getP2pLinkedInfo().then(data => {
  console.info("get wifi p2p linked info: " + JSON.stringify(data));
});
```


<a id="getp2plinkedinfo-1"></a>

## getP2pLinkedInfo

```TypeScript
function getP2pLinkedInfo(callback: AsyncCallback<WifiP2pLinkedInfo>): void
```

获取P2P连接信息。使用callback异步回调。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getP2pLinkedInfo](arkts-connectivity-wifimanager-getp2plinkedinfo-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WifiP2pLinkedInfo](arkts-connectivity-wifi-wifip2plinkedinfo-i.md)&gt; | 是 | 回调函数。当操作成功时，err为0，data表示P2P连接信息。如果err为非0，表示处理出现错误。 |

**示例**

参见 [getP2pLinkedInfo](#getp2plinkedinfo)
