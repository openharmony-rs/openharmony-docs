# isBeaconFenceSupported

## 导入模块

```TypeScript
```

## isBeaconFenceSupported

```TypeScript
function isBeaconFenceSupported(): boolean
```

判断当前设备是否支持beacon围栏。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：支持beacon围栏。false：不支持beacon围栏。 |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  let isBeaconFenceSupported = geoLocationManager.isBeaconFenceSupported();
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
