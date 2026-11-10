# getLocalP2pServices

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getLocalP2pServices

```TypeScript
function getLocalP2pServices(): Promise<Array<WifiP2pServiceInfo>>
```

查询本地P2P服务，使用Promise异步回调。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.GET_WIFI_INFO_INTERNAL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wifiManager-function getLocalP2pServices(): Promise<Array<WifiP2pServiceInfo>>--><!--Device-wifiManager-function getLocalP2pServices(): Promise<Array<WifiP2pServiceInfo>>-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[WifiP2pServiceInfo](arkts-connectivity-wifimanager-wifip2pserviceinfo-i.md)&gt;&gt; | Promise对象。用于返回已注册的本地P2P服务列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

wifiManager.getLocalP2pServices().then((data: wifiManager.WifiP2pServiceInfo[]) => {
  console.info("get local P2P services: " + JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.error("failed: " + JSON.stringify(error));
});
```
