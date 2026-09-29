# GetLocationTypeResponse

```TypeScript
export interface GetLocationTypeResponse
```

当前设备支持的定位类型列表

**起始版本：** 3

**废弃版本：** 9

<!--Device-unnamed-export interface GetLocationTypeResponse--><!--Device-unnamed-export interface GetLocationTypeResponse-End-->

**系统能力：** SystemCapability.Location.Location.Lite

## 导入模块

```TypeScript
import { Geolocation, GeolocationResponse, GetLocationOption, GetLocationTypeOption, GetLocationTypeResponse, SubscribeLocationOption } from '@kit.LocationKit';
```

## types

```TypeScript
types: Array<string>
```

可选的定位类型['gps', 'network']。

**类型：** Array&lt;string&gt;

**起始版本：** 3

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-GetLocationTypeResponse-types: Array<string>--><!--Device-GetLocationTypeResponse-types: Array<string>-End-->

**系统能力：** SystemCapability.Location.Location.Lite
