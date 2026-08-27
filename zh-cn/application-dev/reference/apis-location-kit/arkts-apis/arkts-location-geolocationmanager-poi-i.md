# Poi

POI(Point of Interest, 兴趣点)信息。

**起始版本：** 19

**系统能力：** SystemCapability.Location.Location.Core

## 导入模块

```TypeScript
```

## additionalInfo

```TypeScript
additionalInfo?: string
```

表示POI附加信息，本字符串为JSON格式。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## address

```TypeScript
address: string
```

表示POI的详细地址。

**类型：** string

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## administrativeArea

```TypeScript
administrativeArea: string
```

表示POI所在的国家以下的一级行政区，一般是省/州。

**类型：** string

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## confidence

```TypeScript
confidence: number
```

表示POI信息的置信度。置信度越高，用户离该POI信息点越近。取值范围为0到1。

**类型：** number

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## id

```TypeScript
id: string
```

表示POI的ID。

**类型：** string

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## latitude

```TypeScript
latitude: number
```

表示POI所在的纬度。取值范围为-90到90。

**类型：** number

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## locality

```TypeScript
locality: string
```

表示POI所在的城市信息，一般是市。

**类型：** string

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## longitude

```TypeScript
longitude: number
```

表示POI所在的经度。取值范围为-180到180。

**类型：** number

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## name

```TypeScript
name: string
```

表示POI的名称。

**类型：** string

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## subAdministrativeArea

```TypeScript
subAdministrativeArea: string
```

表示POI所在的国家以下的二级行政区，一般是市。

**类型：** string

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## subLocality

```TypeScript
subLocality: string
```

表示POI所在的子城市信息，一般是区/县。

**类型：** string

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core
