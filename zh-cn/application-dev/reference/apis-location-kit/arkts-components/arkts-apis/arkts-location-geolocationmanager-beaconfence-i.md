# BeaconFence

```TypeScript
export interface BeaconFence
```

beacon围栏的参数配置。

**起始版本：** 20

<!--Device-geoLocationManager-export interface BeaconFence--><!--Device-geoLocationManager-export interface BeaconFence-End-->

**系统能力：** SystemCapability.Location.Location.Geofence

## 导入模块

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## beaconFenceInfoType

```TypeScript
beaconFenceInfoType: BeaconFenceInfoType
```

beacon围栏信息类型。

**类型：** [BeaconFenceInfoType](arkts-location-geolocationmanager-beaconfenceinfotype-e.md)

**起始版本：** 20

**原子化服务API（仅ArkTS-Dyn）：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-BeaconFence-beaconFenceInfoType: BeaconFenceInfoType--><!--Device-BeaconFence-beaconFenceInfoType: BeaconFenceInfoType-End-->

**系统能力：** SystemCapability.Location.Location.Geofence

## identifier

```TypeScript
identifier: string
```

beacon围栏标识。可自行定义，如："123", "beaconName"。

**类型：** string

**起始版本：** 20

**原子化服务API（仅ArkTS-Dyn）：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-BeaconFence-identifier: string--><!--Device-BeaconFence-identifier: string-End-->

**系统能力：** SystemCapability.Location.Location.Geofence

## manufactureData

```TypeScript
manufactureData?: BeaconManufactureData
```

beacon设备制造商数据。

**类型：** [BeaconManufactureData](arkts-location-geolocationmanager-beaconmanufacturedata-i.md)

**起始版本：** 20

**原子化服务API（仅ArkTS-Dyn）：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-BeaconFence-manufactureData?: BeaconManufactureData--><!--Device-BeaconFence-manufactureData?: BeaconManufactureData-End-->

**系统能力：** SystemCapability.Location.Location.Geofence
