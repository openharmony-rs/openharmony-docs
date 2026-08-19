# getP2pLinkedInfo

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getP2pLinkedInfo

```TypeScript
function getP2pLinkedInfo(): Promise<WifiP2pLinkedInfo>
```

获取P2P连接信息。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getP2pLinkedInfo](arkts-connectivity-wifimanager-getp2plinkedinfo-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function getP2pLinkedInfo(): Promise<WifiP2pLinkedInfo>--><!--Device-wifi-function getP2pLinkedInfo(): Promise<WifiP2pLinkedInfo>-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;WifiP2pLinkedInfo&gt; | P2P连接信息。 |


## getP2pLinkedInfo

```TypeScript
function getP2pLinkedInfo(callback: AsyncCallback<WifiP2pLinkedInfo>): void
```

获取P2P连接信息。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getP2pLinkedInfo](arkts-connectivity-wifimanager-getp2plinkedinfo-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function getP2pLinkedInfo(callback: AsyncCallback<WifiP2pLinkedInfo>): void--><!--Device-wifi-function getP2pLinkedInfo(callback: AsyncCallback<WifiP2pLinkedInfo>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;WifiP2pLinkedInfo&gt; | 是 |  |

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

