# getP2pGroups（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getP2pGroups

```TypeScript
function getP2pGroups(): Promise<Array<WifiP2pGroupInfo>>
```

获取群组信息。

**起始版本：** 10

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.P2P

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Array &lt;WifiP2pGroupInfo&gt;&gt; | 返回群组信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

wifiManager.getP2pGroups((err: BusinessError, data:wifiManager.WifiP2pGroupInfo[]) => {
if (err) {
    console.error("get P2P groups error");
    return;
}
  console.info("get P2P groups: " + JSON.stringify(data));
});

wifiManager.getP2pGroups().then(data => {
  console.info("get P2P groups: " + JSON.stringify(data));
});
```


## getP2pGroups

```TypeScript
function getP2pGroups(callback: AsyncCallback<Array<WifiP2pGroupInfo>>): void
```

获取群组信息。

**起始版本：** 10

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.P2P

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;WifiP2pGroupInfo&gt;&gt; | 是 | 表示回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p功能未打开) | Wi-Fi STA disabled. |

**示例**

参见 [getP2pGroups](#getp2pgroups)
