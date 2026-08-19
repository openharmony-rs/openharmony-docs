# removeDevice

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## removeDevice

```TypeScript
function removeDevice(id: int): void
```

通过networkId移除WLAN DeviceConfig。 WLAN DeviceConfig移除后，其配置将从WLAN配置列表中删除。 如果该WLAN DeviceConfig正在连接中，则连接将被中断。 应用只能删除自己创建的WLAN DeviceConfig。

**起始版本：** 23

**需要权限：** ohos.permission.SET_WIFI_INFO and (ohos.permission.MANAGE_WIFI_CONNECTION or ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION)

<!--Device-wifiManager-function removeDevice(id: int): void--><!--Device-wifiManager-function removeDevice(id: int): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | int | 是 | 表示WLAN DeviceConfig的ID。networkId的值不能小于0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |
| [2501001](../errorcode-wifi.md#2501001-sta功能未打开) | Wi-Fi STA disabled. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
  
    try {
      let id = 0;
      wifiManager.removeDevice(id);  
    }catch(error){
      console.error("failed:" + JSON.stringify(error));
    }
```

