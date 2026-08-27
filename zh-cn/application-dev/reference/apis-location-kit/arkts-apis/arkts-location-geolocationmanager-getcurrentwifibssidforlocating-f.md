# getCurrentWifiBssidForLocating

## 导入模块

```TypeScript
```

## getCurrentWifiBssidForLocating

```TypeScript
function getCurrentWifiBssidForLocating(): string
```

获取连接的Wi-Fi AP（Access Point）的Bssid（Basic Service Set Identifier）信息。如果当前设备未连接Wi-Fi，调用该接口将抛出错误码3301900。建议参考示例代码，通过 try-catch结构捕获异常。

**起始版本：** 14

**需要权限：** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**系统能力：** SystemCapability.Location.Location.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Wi-Fi Bssid |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.getCurrentWifiBssidForLocating()} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. |
| [3301900](../errorcode-geoLocationManager.md#3301900-由于wi-fi未连接导致获取wi-fi热点的mac地址失败) | Failed to obtain the BSSID of the Wi-Fi hotspot. The Wi-Fi network is not connected. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  let bssid: string = geoLocationManager.getCurrentWifiBssidForLocating();
  console.info("get wifi bssid:" + bssid);
} catch (error) {
  console.error("getCurrentWifiBssidForLocating: errCode" + error.code + ", errMessage" + error.message);
}
```
