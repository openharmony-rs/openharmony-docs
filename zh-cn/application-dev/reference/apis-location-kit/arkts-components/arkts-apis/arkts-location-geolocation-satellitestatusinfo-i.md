# SatelliteStatusInfo

卫星状态信息。

@interface SatelliteStatusInfo

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [SatelliteStatusInfo](arkts-location-geolocationmanager-satellitestatusinfo-i.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Gnss

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## altitudes

```TypeScript
altitudes: Array<number>
```

表示卫星高度角信息。单位是“度”，取值范围为-90到90。

**类型：** Array&lt;number&gt;

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [altitudes](arkts-location-geolocationmanager-satellitestatusinfo-i.md#altitudes)

**系统能力：** SystemCapability.Location.Location.Gnss

## azimuths

```TypeScript
azimuths: Array<number>
```

表示方位角。单位是“度”，取值范围为0到360。

**类型：** Array&lt;number&gt;

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [azimuths](arkts-location-geolocationmanager-satellitestatusinfo-i.md#azimuths)

**系统能力：** SystemCapability.Location.Location.Gnss

## carrierFrequencies

```TypeScript
carrierFrequencies: Array<number>
```

表示载波频率。单位是Hz，取值范围为大于等于0。

**类型：** Array&lt;number&gt;

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [carrierFrequencies](arkts-location-geolocationmanager-satellitestatusinfo-i.md#carrierfrequencies)

**系统能力：** SystemCapability.Location.Location.Gnss

## carrierToNoiseDensitys

```TypeScript
carrierToNoiseDensitys: Array<number>
```

表示载波噪声功率谱密度比，即cn0。取值范围为大于0。

**类型：** Array&lt;number&gt;

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [carrierToNoiseDensitys](arkts-location-geolocationmanager-satellitestatusinfo-i.md#carriertonoisedensitys)

**系统能力：** SystemCapability.Location.Location.Gnss

## satelliteIds

```TypeScript
satelliteIds: Array<number>
```

表示每个卫星的ID，数组类型。取值范围为大于等于0。

**类型：** Array&lt;number&gt;

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [satelliteIds](arkts-location-geolocationmanager-satellitestatusinfo-i.md#satelliteids)

**系统能力：** SystemCapability.Location.Location.Gnss

## satellitesNumber

```TypeScript
satellitesNumber: number
```

表示卫星个数。取值范围为大于等于0。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [satellitesNumber](arkts-location-geolocationmanager-satellitestatusinfo-i.md#satellitesnumber)

**系统能力：** SystemCapability.Location.Location.Gnss
