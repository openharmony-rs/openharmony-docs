# getMultiLinkedInfo

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getMultiLinkedInfo

```TypeScript
function getMultiLinkedInfo(): Array<WifiLinkedInfo>
```

获取MLO(Multi-Link Operation，多链路操作)Wi-Fi连接信息。

> **说明：** 
> 
> - 当macType是1（设备MAC地址），获取macAddress还需申请ohos.permission.GET_WIFI_LOCAL_MAC权限（API8-15仅面向系统应用开放。从API 16开始，在PC/2in1设备上面向普通应用开放，在其余设备上仍仅面向系统应用开放），无该权限时，macAddress返回为空。
> 
> - 如果应用申请了ohos.permission.GET_WIFI_PEERS_MAC权限，则返回结果中的bssid为真实BSSID地址，否则为随机设备地址。

**起始版本：** 18

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[WifiLinkedInfo](arkts-connectivity-wifimanager-wifilinkedinfo-i.md)&gt; | Wi-Fi连接信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |
| [2501001](../errorcode-wifi.md#2501001-sta功能未打开) | Wi-Fi STA disabled. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let linkedInfo = wifiManager.getMultiLinkedInfo();
    console.info("linkedInfo:" + JSON.stringify(linkedInfo));
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```
