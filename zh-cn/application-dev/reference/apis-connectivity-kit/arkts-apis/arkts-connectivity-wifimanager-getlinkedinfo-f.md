# getLinkedInfo

## getLinkedInfo

```TypeScript
function getLinkedInfo(): Promise<WifiLinkedInfo>
```

获取WLAN连接信息。如果未获取ohos.permission.GET_WIFI_PEERS_MAC权限，返回随机bssid。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_WIFI_INFO

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-wifiManager-function getLinkedInfo(): Promise<WifiLinkedInfo>--><!--Device-wifiManager-function getLinkedInfo(): Promise<WifiLinkedInfo>-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;WifiLinkedInfo&gt; | 返回WLAN连接信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |
| [2501001](../errorcode-wifi.md#2501001-sta功能未打开) | Wi-Fi STA disabled. |


## getLinkedInfo

```TypeScript
function getLinkedInfo(callback: AsyncCallback<WifiLinkedInfo>): void
```

获取WLAN连接信息。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifiManager-function getLinkedInfo(callback: AsyncCallback<WifiLinkedInfo>): void--><!--Device-wifiManager-function getLinkedInfo(callback: AsyncCallback<WifiLinkedInfo>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;WifiLinkedInfo&gt; | 是 | 表示回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |
| [2501001](../errorcode-wifi.md#2501001-sta功能未打开) | Wi-Fi STA disabled. |

## 示例

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

wifiManager.getLinkedInfo().then((data: wifiManager.WifiLinkedInfo) => {
    console.info("get wifi linked info: " + JSON.stringify(data));
}).catch((error: Error) => {
    console.error("get linked info error: ", error);
});
```

