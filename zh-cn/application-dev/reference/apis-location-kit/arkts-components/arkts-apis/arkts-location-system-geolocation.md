# @system.geolocation

## 导入模块

```TypeScript
import { Geolocation, GeolocationResponse, GetLocationOption, GetLocationTypeOption, GetLocationTypeResponse, SubscribeLocationOption } from '@kit.LocationKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Geolocation](arkts-location-system-geolocation-geolocation-c.md) |  |

### 接口

| 名称 | 说明 |
| --- | --- |
| [GeolocationResponse](arkts-location-system-geolocation-geolocationresponse-i.md) | 位置信息，包含经度、纬度、定位精度等信息。 |
| [GetLocationOption](arkts-location-system-geolocation-getlocationoption-i.md) | 单次定位请求的配置参数。 |
| [GetLocationTypeOption](arkts-location-system-geolocation-getlocationtypeoption-i.md) | 查询定位类型接口的入参，用于存放回调函数，在查询成功或者失败时接收查询结果。 |
| [GetLocationTypeResponse](arkts-location-system-geolocation-getlocationtyperesponse-i.md) | 当前设备支持的定位类型列表 |
| [SubscribeLocationOption](arkts-location-system-geolocation-subscribelocationoption-i.md) | 持续定位请求的配置参数。 |
