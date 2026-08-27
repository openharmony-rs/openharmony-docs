# isGeocoderAvailable

## 导入模块

```TypeScript
```

## isGeocoderAvailable

```TypeScript
function isGeocoderAvailable(): boolean
```

判断地理编码与逆地理编码服务状态。

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true:地理编码与逆地理编码服务可用。false：地理编码与逆地理编码服务不可用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.isGeocoderAvailable} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  let isAvailable = geoLocationManager.isGeocoderAvailable();
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
