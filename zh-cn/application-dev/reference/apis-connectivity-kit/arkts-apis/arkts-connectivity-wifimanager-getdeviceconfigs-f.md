# getDeviceConfigs

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getDeviceConfigs

```TypeScript
function getDeviceConfigs(): Array<WifiDeviceConfig>
```

获取所有已存在的WLAN配置列表。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.GET_WIFI_CONFIG

<!--Device-wifiManager-function getDeviceConfigs(): Array<WifiDeviceConfig>--><!--Device-wifiManager-function getDeviceConfigs(): Array<WifiDeviceConfig>-End-->

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
      let configs = wifiManager.getDeviceConfigs();
      console.info("configs:" + JSON.stringify(configs));
    }catch(error){
      console.error("failed:", error.code, error.message);
    }
```

