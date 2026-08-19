# getCandidateConfigs

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getCandidateConfigs

```TypeScript
function getCandidateConfigs(): Array<WifiDeviceConfig>
```

获取自己添加的所有已存在的候选WLAN配置列表。 只能获取自己在应用上创建的WLAN配置。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-wifiManager-function getCandidateConfigs(): Array<WifiDeviceConfig>--><!--Device-wifiManager-function getCandidateConfigs(): Array<WifiDeviceConfig>-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;WifiDeviceConfig&gt; | 返回您在应用上创建的所有已存在的WLAN配置列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let configs = wifiManager.getCandidateConfigs();
    console.info("configs:" + JSON.stringify(configs));
    let len = configs.length;
        console.info("result len: " + len);
    if(len > 0){
      for (let i = 0; i < len; ++i) {
        console.info("ssid: " + configs[i].ssid);
        console.info("bssid: " + configs[i].bssid);
      }
    }  
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

