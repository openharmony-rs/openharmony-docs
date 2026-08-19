# createGroup

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## createGroup

```TypeScript
function createGroup(config: WifiP2PConfig): void
```

创建P2P群组。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifiManager-function createGroup(config: WifiP2PConfig): void--><!--Device-wifiManager-function createGroup(config: WifiP2PConfig): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | WifiP2PConfig | 是 | 表示群组的配置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: 1.Incorrect parameter types. 2.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p模块异常) | Wi-Fi STA disabled. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let config:wifiManager.WifiP2PConfig = {
      deviceAddress: "****",
      netId: 0,
      passphrase: "*****",
      groupName: "****",
      goBand: 0
    }
    wifiManager.createGroup(config);  
    
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

