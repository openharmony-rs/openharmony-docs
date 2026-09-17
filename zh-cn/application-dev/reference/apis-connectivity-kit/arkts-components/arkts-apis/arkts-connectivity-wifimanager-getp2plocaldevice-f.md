# getP2pLocalDevice

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getP2pLocalDevice

```TypeScript
function getP2pLocalDevice(): Promise<WifiP2pDevice>
```

获取P2P本端设备信息，使用Promise异步回调。

**起始版本：** 9

**需要权限：** 
- API版本11+：ohos.permission.GET_WIFI_INFO
- API版本9-10：ohos.permission.GET_WIFI_INFO and ohos.permission.GET_WIFI_CONFIG

**系统能力：** SystemCapability.Communication.WiFi.P2P

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md)&gt; | Promise对象。表示本端设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |

**示例**

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


## getP2pLocalDevice

```TypeScript
function getP2pLocalDevice(callback: AsyncCallback<WifiP2pDevice>): void
```

获取P2P本端设备信息，使用callback异步回调。

**起始版本：** 9

**需要权限：** 
- API版本11+：ohos.permission.GET_WIFI_INFO
- API版本9-10：ohos.permission.GET_WIFI_INFO and ohos.permission.GET_WIFI_CONFIG

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md)&gt; | 是 | 回调函数。当操作成功时，err为0，data表示本端设备信息。如果err为非0，表示处理出现错误。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p功能未打开) | Wi-Fi STA disabled. |

**示例**

参见 [getP2pLocalDevice](#getp2plocaldevice)
