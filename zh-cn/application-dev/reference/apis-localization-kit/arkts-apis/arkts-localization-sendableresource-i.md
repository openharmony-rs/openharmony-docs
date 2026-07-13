# SendableResource

本模块提供SendableResource资源相关信息，包括应用包名、应用模块名、资源类型等。

**继承/实现关系：** SendableResource extends [lang.ISendable](../../apis-arkts/arkts-apis/arkts-arkts-isendable-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.Global.ResourceManager

## bundleName

```TypeScript
bundleName: string
```

应用的bundle名称。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

## id

```TypeScript
id: number
```

资源的id值，取值如下：
<br>- 应用资源区间：[0x01000000, 0x06FFFFFF] 和 [0x08000000, 0xFFFFFFFF]
<br>- 系统资源区间：[0x07000000, 0x07FFFFFF]

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

## moduleName

```TypeScript
moduleName: string
```

应用的module名称。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

## params

```TypeScript
params?: collections.Array <string | number>
```

其他资源参数，包括资源名、格式化接口的替换值、复数接口的量词。

**类型：** collections.Array <string | number>

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

## type

```TypeScript
type?: number
```

资源的类型，取值如下：
<br>- 10001：color
<br>- 10002：float
<br>- 10003：string
<br>- 10004：plural
<br>- 10005：boolean
<br>- 10006：intarray
<br>- 10007：integer
<br>- 10008：pattern
<br>- 10009：strarray
<br>- 20000：media
<br>- 30000：rawfile
<br>- 40000：symbol

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

