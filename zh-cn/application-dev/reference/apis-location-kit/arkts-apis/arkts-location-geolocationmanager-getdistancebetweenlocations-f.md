# getDistanceBetweenLocations

## 导入模块

```TypeScript
```

## getDistanceBetweenLocations

```TypeScript
function getDistanceBetweenLocations(location1: Location, location2: Location): number
```

获取两个位置之间的直线距离。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| location1 | Location | 是 | 位置1。 |
| location2 | Location | 是 | 位置2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 两个位置之间的直线距离，单位为米。 |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  let location1: geoLocationManager.Location = {
    "latitude": 30.12,
    "longitude": 120.11,
    "altitude": 0,
    "accuracy": 0,
    "speed": 0,
    "timeStamp": 0,
    "direction": 0,
    "timeSinceBoot": 0,
    "additionSize": 0
  }
  let location2: geoLocationManager.Location = {
    "latitude": 31.12,
    "longitude": 121.11,
    "altitude": 0,
    "accuracy": 0,
    "speed": 0,
    "timeStamp": 0,
    "direction": 0,
    "timeSinceBoot": 0,
    "additionSize": 0
  }
  let distance = geoLocationManager.getDistanceBetweenLocations(location1, location2);
  console.info("distance:" + distance);
} catch (error) {
  console.error("getDistanceBetweenLocations: errCode" + error.code + ", errMessage" + error.message);
}
```
