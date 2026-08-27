# isPoiServiceSupported

## 导入模块

```TypeScript
```

## isPoiServiceSupported

```TypeScript
function isPoiServiceSupported(): boolean
```

查询系统（即软件）是否支持POI服务。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true:POI服务可用。 false:POI服务不可用。 |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

let poiServiceState = geoLocationManager.isPoiServiceSupported();
console.info("poiServiceState:" + poiServiceState);
```
