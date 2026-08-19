# getCurrentGroup

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getCurrentGroup

```TypeScript
function getCurrentGroup(): Promise<WifiP2pGroupInfo>
```

获取当前群组信息。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getCurrentGroup](arkts-connectivity-wifimanager-getcurrentgroup-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

<!--Device-wifi-function getCurrentGroup(): Promise<WifiP2pGroupInfo>--><!--Device-wifi-function getCurrentGroup(): Promise<WifiP2pGroupInfo>-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;WifiP2pGroupInfo&gt; | 当前群组信息。 |


## getCurrentGroup

```TypeScript
function getCurrentGroup(callback: AsyncCallback<WifiP2pGroupInfo>): void
```

获取当前群组信息。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getCurrentGroup](arkts-connectivity-wifimanager-getcurrentgroup-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

<!--Device-wifi-function getCurrentGroup(callback: AsyncCallback<WifiP2pGroupInfo>): void--><!--Device-wifi-function getCurrentGroup(callback: AsyncCallback<WifiP2pGroupInfo>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;WifiP2pGroupInfo&gt; | 是 |  |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

wifi.getCurrentGroup((err, data:wifi.WifiP2pGroupInfo) => {
   if (err) {
       console.error("get current P2P group error");
       return;
   }
  console.info("get current P2P group: " + JSON.stringify(data));
});

wifi.getCurrentGroup().then(data => {
  console.info("get current P2P group: " + JSON.stringify(data));
});
```

