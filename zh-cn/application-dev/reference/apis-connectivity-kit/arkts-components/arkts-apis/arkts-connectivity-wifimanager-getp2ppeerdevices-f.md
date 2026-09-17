# getP2pPeerDevices

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getP2pPeerDevices

```TypeScript
function getP2pPeerDevices(): Promise<WifiP2pDevice[]>
```

获取P2P对端设备列表信息。使用Promise异步回调。

**起始版本：** 9

**需要权限：** 
- API版本10+：ohos.permission.GET_WIFI_INFO
- API版本9：ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**系统能力：** SystemCapability.Communication.WiFi.P2P

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md)[]&gt; | Promise对象。表示对端设备列表信息。如果应用申请了ohos.permission.GET_WIFI_PEERS_MAC权限，则返回结果中的deviceAddress为真实设备地址，否则为随机设备地址。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
  // p2p发现阶段完成，才能正常获取到对端设备列表信息
  wifiManager.getP2pPeerDevices((err, data:wifiManager.WifiP2pDevice[]) => {
    if (err) {
        console.error("get P2P peer devices error");
        return;
    }
    console.info("get P2P peer devices: " + JSON.stringify(data));
  });

  wifiManager.getP2pPeerDevices().then(data => {
    console.info("get P2P peer devices: " + JSON.stringify(data));
  });
```


## getP2pPeerDevices

```TypeScript
function getP2pPeerDevices(callback: AsyncCallback<WifiP2pDevice[]>): void
```

获取P2P对端设备列表信息。使用callback异步回调。

**起始版本：** 9

**需要权限：** 
- API版本10+：ohos.permission.GET_WIFI_INFO
- API版本9：ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md)[]&gt; | 是 | 回调函数。当操作成功时，err为0，data表示对端设备列表信息。如果err为非0，表示处理出现错误。如果应用申请了ohos.permission.GET_WIFI_PEERS_MAC权限，则返回结果中的deviceAddress为真实设备地址，否则为随机设备地址。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p功能未打开) | Wi-Fi STA disabled. |

**示例**

参见 [getP2pPeerDevices](#getp2ppeerdevices)
