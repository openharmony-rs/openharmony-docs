# SatelliteStatusInfo

卫星状态信息。

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Gnss

## 导入模块

```TypeScript
```

## altitudes

```TypeScript
altitudes: Array<number>
```

表示卫星高度角信息。单位是“度”，取值范围为-90到90。

**类型：** Array&lt;number&gt;

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Gnss

## azimuths

```TypeScript
azimuths: Array<number>
```

表示方位角。单位是“度”，取值范围为0到360。

**类型：** Array&lt;number&gt;

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Gnss

## carrierFrequencies

```TypeScript
carrierFrequencies: Array<number>
```

表示载波频率。单位是Hz，取值范围为大于等于0。

**类型：** Array&lt;number&gt;

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Gnss

## carrierToNoiseDensitys

```TypeScript
carrierToNoiseDensitys: Array<number>
```

表示载波噪声功率谱密度比，即cn0。取值范围为大于0。

**类型：** Array&lt;number&gt;

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Gnss

## satelliteAdditionalInfo

```TypeScript
satelliteAdditionalInfo?: Array<number>
```

表示卫星的附加信息。每个比特位代表不同含义，具体定义参见[SatelliteAdditionalInfo](arkts-location-geolocationmanager-satelliteadditionalinfo-e.md)。

**类型：** Array&lt;number&gt;

**起始版本：** 12

**系统能力：** SystemCapability.Location.Location.Gnss

## satelliteConstellation

```TypeScript
satelliteConstellation?: Array<SatelliteConstellationCategory>
```

表示卫星星座类型。

**类型：** Array&lt;[SatelliteConstellationCategory](arkts-location-geolocationmanager-satelliteconstellationcategory-e.md)&gt;

**起始版本：** 12

**系统能力：** SystemCapability.Location.Location.Gnss

## satelliteIds

```TypeScript
satelliteIds: Array<number>
```

表示每个卫星的ID，数组类型。取值范围为大于等于0。

**类型：** Array&lt;number&gt;

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Gnss

## satellitesNumber

```TypeScript
satellitesNumber: number
```

表示卫星个数。取值范围为大于等于0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Gnss
