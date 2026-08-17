# getP2pLocalDevice

## getP2pLocalDevice

```TypeScript
function getP2pLocalDevice(): Promise<WifiP2pDevice>
```

获取本设备的信息。 如果未获取ohos.permission.GET_WIFI_LOCAL_MAC权限，返回的WifiP2pDevice中的DeviceAddress将设置为"00:00:00:00:00:00"。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifiManager-function getP2pLocalDevice(): Promise<WifiP2pDevice>--><!--Device-wifiManager-function getP2pLocalDevice(): Promise<WifiP2pDevice>-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;WifiP2pDevice&gt; | 返回本设备的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |


## getP2pLocalDevice

```TypeScript
function getP2pLocalDevice(callback: AsyncCallback<WifiP2pDevice>): void
```

获取本设备的信息。 如果未获取ohos.permission.GET_WIFI_LOCAL_MAC权限，返回的WifiP2pDevice中的DeviceAddress将设置为"00:00:00:00:00:00"。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifiManager-function getP2pLocalDevice(callback: AsyncCallback<WifiP2pDevice>): void--><!--Device-wifiManager-function getP2pLocalDevice(callback: AsyncCallback<WifiP2pDevice>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;WifiP2pDevice&gt; | 是 | 表示回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p模块异常) | Wi-Fi STA disabled. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

## 示例

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
  // p2p已经建组或者连接成功，才能正常获取到本端设备信息
  wifiManager.getP2pLocalDevice((err, data:wifiManager.WifiP2pDevice) => {
    if (err) {
        console.error("get P2P local device error");
        return;
    }
    console.info("get P2P local device: " + JSON.stringify(data));
  });

  wifiManager.getP2pLocalDevice().then(data => {
    console.info("get P2P local device: " + JSON.stringify(data));
  });
```

