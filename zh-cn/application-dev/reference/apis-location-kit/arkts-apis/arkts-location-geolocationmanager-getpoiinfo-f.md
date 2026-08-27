# getPoiInfo

## 导入模块

```TypeScript
```

## getPoiInfo

```TypeScript
function getPoiInfo(): Promise<PoiInfo>
```

获取当前位置附近的POI信息。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PoiInfo](arkts-location-geolocationmanager-poiinfo-i.md)&gt; | 当前位置附近的POI信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.getPoiInfo} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  if (geoLocationManager.isPoiServiceSupported()) {
    geoLocationManager.getPoiInfo().then((poiInfo) => {
      if (poiInfo !== undefined) {
        console.info("get PoiInfo:" + JSON.stringify(poiInfo));
      }
    })
  }
} catch (error) {
  console.error("getPoiInfo errCode:" + error.code + ", errMessage:" + error.message);
}
```
