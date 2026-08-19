# getLinkedInfo

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getLinkedInfo

```TypeScript
function getLinkedInfo(): Promise<WifiLinkedInfo>
```

获取WLAN连接信息。使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [getLinkedInfo](arkts-connectivity-wifimanager-getlinkedinfo-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function getLinkedInfo(): Promise<WifiLinkedInfo>--><!--Device-wifi-function getLinkedInfo(): Promise<WifiLinkedInfo>-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;WifiLinkedInfo&gt; | 表示WLAN连接信息。 |


## getLinkedInfo

```TypeScript
function getLinkedInfo(callback: AsyncCallback<WifiLinkedInfo>): void
```

获取WLAN连接信息。使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [getLinkedInfo](arkts-connectivity-wifimanager-getlinkedinfo-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function getLinkedInfo(callback: AsyncCallback<WifiLinkedInfo>): void--><!--Device-wifi-function getLinkedInfo(callback: AsyncCallback<WifiLinkedInfo>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;WifiLinkedInfo&gt; | 是 |  |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

wifi.getLinkedInfo((err, data:wifi.WifiLinkedInfo) => {
    if (err) {
        console.error("get linked info error");
        return;
    }
    console.info("get wifi linked info: " + JSON.stringify(data));
});

wifi.getLinkedInfo().then(data => {
    console.info("get wifi linked info: " + JSON.stringify(data));
}).catch((error:number) => {
    console.info("get linked info error");
});
```

