# getP2pLinkedInfo

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getP2pLinkedInfo

```TypeScript
function getP2pLinkedInfo(): Promise<WifiP2pLinkedInfo>
```

获取P2P连接信息。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifiManager-function getP2pLinkedInfo(): Promise<WifiP2pLinkedInfo>--><!--Device-wifiManager-function getP2pLinkedInfo(): Promise<WifiP2pLinkedInfo>-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;WifiP2pLinkedInfo&gt; | 返回P2P连接信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |


## getP2pLinkedInfo

```TypeScript
function getP2pLinkedInfo(callback: AsyncCallback<WifiP2pLinkedInfo>): void
```

获取P2P连接信息。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifiManager-function getP2pLinkedInfo(callback: AsyncCallback<WifiP2pLinkedInfo>): void--><!--Device-wifiManager-function getP2pLinkedInfo(callback: AsyncCallback<WifiP2pLinkedInfo>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;WifiP2pLinkedInfo&gt; | 是 | 表示回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p模块异常) | Wi-Fi STA disabled. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  wifiManager.getP2pLinkedInfo((err, data:wifiManager.WifiP2pLinkedInfo) => {
    if (err) {
        console.error("get p2p linked info error");
        return;
    }
    console.info("get wifi p2p linked info: " + JSON.stringify(data));
  });

  wifiManager.getP2pLinkedInfo().then(data => {
    console.info("get wifi p2p linked info: " + JSON.stringify(data));
  });
```

