# Resource

本模块提供资源相关信息，包括应用包名、应用模块名、资源ID等。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export interface Resource--><!--Device-unnamed-export interface Resource-End-->

**系统能力：** SystemCapability.Global.ResourceManager

## bundleName

```TypeScript
bundleName: string
```

应用包名。

**类型：** string

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Resource-bundleName: string--><!--Device-Resource-bundleName: string-End-->

**系统能力：** SystemCapability.Global.ResourceManager

## id

```TypeScript
id: long
```

资源ID，取值如下： - 应用资源区间：[0x01000000, 0x06FFFFFF] 和 [0x08000000, 0xFFFFFFFF]，表示应用自身的资源ID。 - 系统资源区间：[0x07000000, 0x07FFFFFF]，表示系统预置的资源ID。

**类型：** long

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Resource-id: long--><!--Device-Resource-id: long-End-->

**系统能力：** SystemCapability.Global.ResourceManager

## moduleName

```TypeScript
moduleName: string
```

应用模块名。

**类型：** string

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Resource-moduleName: string--><!--Device-Resource-moduleName: string-End-->

**系统能力：** SystemCapability.Global.ResourceManager

## params

```TypeScript
params?: any[]
```

资源参数，包括：资源名（string类型）、格式化接口替换值（按占位符顺序提供string或number）、复数接口量词（number类型，表示数量）。 格式化接口的替换值用于字符串格式化时的参数替换，复数接口的量词用于选择多语言环境下的复数形式。

**类型：** any[]

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Resource-params?: any[]--><!--Device-Resource-params?: any[]-End-->

**系统能力：** SystemCapability.Global.ResourceManager

## type

```TypeScript
type?: int
```

资源类型，取值如下： \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_- 10001: color \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_- 10002: float \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_- 10003: string \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_- 10004: plural \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_- 10005: boolean \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_- 10006: intarray \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_- 10007: integer \_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_- 10008: pattern \_\_\_HTML\_TAG\_DESC\_USD\_8\_\_\_- 10009: strarray \_\_\_HTML\_TAG\_DESC\_USD\_9\_\_\_- 20000: media \_\_\_HTML\_TAG\_DESC\_USD\_10\_\_\_- 30000: rawfile \_\_\_HTML\_TAG\_DESC\_USD\_11\_\_\_- 40000: symbol

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Resource-type?: int--><!--Device-Resource-type?: int-End-->

**系统能力：** SystemCapability.Global.ResourceManager

