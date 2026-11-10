# removeLocalP2pService

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## removeLocalP2pService

```TypeScript
function removeLocalP2pService(srvInfo: WifiP2pServiceInfo): void
```

移除通过[addDnsSdLocalP2pService](arkts-connectivity-wifimanager-adddnssdlocalp2pservice-f.md)或[addUpnpLocalP2pService](arkts-connectivity-wifimanager-addupnplocalp2pservice-f.md)添加的已注册本地服务。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.GET_WIFI_INFO_INTERNAL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wifiManager-function removeLocalP2pService(srvInfo: WifiP2pServiceInfo): void--><!--Device-wifiManager-function removeLocalP2pService(srvInfo: WifiP2pServiceInfo): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srvInfo | [WifiP2pServiceInfo](arkts-connectivity-wifimanager-wifip2pserviceinfo-i.md) | 是 | 与已注册服务一致的服务描述。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p功能未打开) | Wi-Fi STA disabled. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

  wifiManager.getLocalP2pServices().then((data: wifiManager.WifiP2pServiceInfo[]) => {
    data.forEach((item: wifiManager.WifiP2pServiceInfo) => {
      if (item.serviceName === "serviceName") {
        wifiManager.removeLocalP2pService(item);
      }
    });
  }).catch((error: BusinessError) => {
    console.error("failed: " + JSON.stringify(error));
  });
```
