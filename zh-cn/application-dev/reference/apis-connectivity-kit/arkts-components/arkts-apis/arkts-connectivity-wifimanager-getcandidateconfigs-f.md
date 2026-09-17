# getCandidateConfigs

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getCandidateConfigs

```TypeScript
function getCandidateConfigs(): Array<WifiDeviceConfig>
```

获取候选网络配置。

- 候选网络是指曾经连接过或者手动添加的网络配置。  
- 该接口返回当前应用添加的所有已保存但当前未连接的Wi-Fi候选网络配置。  
- 用于展示可连接的网络列表。

**起始版本：** 9

**需要权限：** 
- API版本10+：ohos.permission.GET_WIFI_INFO
- API版本9：ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i.md)&gt; | 候选网络配置数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
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
