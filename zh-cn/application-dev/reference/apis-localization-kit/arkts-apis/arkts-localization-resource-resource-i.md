# Resource

本模块提供资源相关信息，包括应用包名、应用模块名、资源ID等。

**起始版本：** 9

**系统能力：** SystemCapability.Global.ResourceManager

## bundleName

```TypeScript
bundleName: string
```

应用包名。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

## id

```TypeScript
id: number
```

资源ID，取值如下：  
- 应用资源区间：[0x01000000, 0x06FFFFFF] 和 [0x08000000, 0xFFFFFFFF]，表示应用自身的资源ID。  
- 系统资源区间：[0x07000000, 0x07FFFFFF]，表示系统预置的资源ID。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

## moduleName

```TypeScript
moduleName: string
```

应用模块名。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

## params

```TypeScript
params?: any[]
```

资源参数，包括：资源名（string类型）、格式化接口替换值（按占位符顺序提供string或number）、复数接口量词（number类型，表示数量）。 格式化接口的替换值用于字符串格式化时的参数替换，复数接口的量词用于选择多语言环境下的复数形式。

**类型：** any[]

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

## type

```TypeScript
type?: number
```

资源类型，取值如下：   
- 10001: color   
- 10002: float   
- 10003: string   
- 10004: plural   
- 10005: boolean   
- 10006: intarray   
- 10007: integer   
- 10008: pattern   
- 10009: strarray   
- 20000: media   
- 30000: rawfile   
- 40000: symbol

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager
