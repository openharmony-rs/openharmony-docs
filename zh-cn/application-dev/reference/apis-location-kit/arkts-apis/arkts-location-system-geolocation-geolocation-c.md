# Geolocation

**起始版本：** 3

**废弃版本：** 9

**替代接口：** [geoLocationManager/geoLocationManager](arkts-geolocationmanager.md)

**系统能力：** SystemCapability.Location.Location.Lite

## 导入模块

```TypeScript
import { Geolocation, GeolocationResponse, GetLocationOption, GetLocationTypeOption, GetLocationTypeResponse, SubscribeLocationOption } from '@kit.LocationKit';
```

## getLocation

```TypeScript
static getLocation(options?: GetLocationOption): void
```

获取设备的地理位置。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** [getCurrentLocation](arkts-location-geolocationmanager-getcurrentlocation-f.md)

**需要权限：** ohos.permission.LOCATION

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Location.Location.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GetLocationOption](arkts-location-system-geolocation-getlocationoption-i.md) | 否 |  |

## getLocationType

```TypeScript
static getLocationType(options?: GetLocationTypeOption): void
```

获取当前设备支持的定位类型。

**起始版本：** 3

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Location.Location.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GetLocationTypeOption](arkts-location-system-geolocation-getlocationtypeoption-i.md) | 否 |  |

## getSupportedCoordTypes

```TypeScript
static getSupportedCoordTypes(): Array<string>
```

获取设备支持的坐标系类型。

**起始版本：** 3

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Location.Location.Lite

**返回值：**

| 类型 | 说明 |
| --- | --- |
## subscribe

```TypeScript
static subscribe(options: SubscribeLocationOption): void
```

订阅设备的地理位置信息。多次调用的话，只有最后一次的调用生效。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** locationChange

**需要权限：** ohos.permission.LOCATION

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Location.Location.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SubscribeLocationOption](arkts-location-system-geolocation-subscribelocationoption-i.md) | 是 |  |

## unsubscribe

```TypeScript
static unsubscribe(): void
```

取消订阅设备的地理位置信息。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** locationChange

**需要权限：** ohos.permission.LOCATION

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Location.Location.Lite
