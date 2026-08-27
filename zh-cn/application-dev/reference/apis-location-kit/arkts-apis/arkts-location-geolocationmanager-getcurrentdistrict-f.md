# getCurrentDistrict

## 导入模块

```TypeScript
```

## getCurrentDistrict

```TypeScript
function getCurrentDistrict(params?: DistrictRequestParams): Promise<DistrictInfo>
```

获取当前设备所在区域的信息。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.APPROXIMATELY_LOCATION

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Geocoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [DistrictRequestParams](arkts-location-geolocationmanager-districtrequestparams-i.md) | 否 | 设置区域信息请求参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DistrictInfo](arkts-location-geolocationmanager-districtinfo-i.md)&gt; | Promise对象，当前设备所在区域的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.getCurrentDistrict} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. |
| [3301500](../errorcode-geoLocationManager.md#3301500-区域信息包含国家码查询失败) | Failed to query the area information because the reverse geocoding server returns an error. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';
// 参数配置一：指定语言/国家/超时时间
try {
  let params: geoLocationManager.DistrictRequestParams = {
    locale: "en",
    timeoutMs: 5000
  }
  geoLocationManager.getCurrentDistrict(params).then((res) => {
    if (res) {
      console.info("getCurrentDistrict result:" + res);
    }
  })
  .catch((error: BusinessError) => {
    console.error('promise, getCurrentDistrict: error=' + JSON.stringify(error));
  });
} catch (error) {
  console.error("getCurrentDistrict: errCode" + error.code + ", errMessage" + error.message);
}
// 参数配置二：使用默认值
try {
  geoLocationManager.getCurrentDistrict().then((res) => {
    if (res) {
      console.info("getCurrentDistrict result:" + res);
    }
  })
  .catch((error: BusinessError) => {
    console.error('promise, getCurrentDistrict: error=' + JSON.stringify(error));
  });
} catch (error) {
  console.error("getCurrentDistrict: errCode" + error.code + ", errMessage" + error.message);
}
```
