# SkillUri

Want匹配的Uri集合。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export interface SkillUri--><!--Device-unnamed-export interface SkillUri-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## host

```TypeScript
readonly host: string
```

标识 URI 主机地址部分，仅当 scheme 存在时才生效。

**类型：** string

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SkillUri-readonly host: string--><!--Device-SkillUri-readonly host: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## linkFeature

```TypeScript
readonly linkFeature: string
```

标识 URI 提供的\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_，用于实现应用间跳转，仅在AbilityInfo中存在。

**类型：** string

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SkillUri-readonly linkFeature: string--><!--Device-SkillUri-readonly linkFeature: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## maxFileSupported

```TypeScript
readonly maxFileSupported: int
```

对于指定类型的文件，标识一次能接收或打开的最大数量。取值范围：不小于0的整数。

**类型：** int

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SkillUri-readonly maxFileSupported: int--><!--Device-SkillUri-readonly maxFileSupported: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## path

```TypeScript
readonly path: string
```

标识 URI 路径部分，仅当 scheme 和 host 同时存在时才生效。

**类型：** string

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SkillUri-readonly path: string--><!--Device-SkillUri-readonly path: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## pathRegex

```TypeScript
readonly pathRegex: string
```

标识 URI 路径部分，用于正则匹配，仅当 scheme 和 host 同时存在时才生效。

**类型：** string

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SkillUri-readonly pathRegex: string--><!--Device-SkillUri-readonly pathRegex: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## pathStartWith

```TypeScript
readonly pathStartWith: string
```

标识 URI 路径部分，用于前缀匹配，仅当 scheme 和 host 同时存在时才生效。

**类型：** string

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SkillUri-readonly pathStartWith: string--><!--Device-SkillUri-readonly pathStartWith: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## port

```TypeScript
readonly port: int
```

标识 URI 端口，仅当 scheme 和 host 同时存在时才生效。

**类型：** int

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SkillUri-readonly port: int--><!--Device-SkillUri-readonly port: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## scheme

```TypeScript
readonly scheme: string
```

标识 URI 协议名，常见的有http、https、file、ftp等。

**类型：** string

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SkillUri-readonly scheme: string--><!--Device-SkillUri-readonly scheme: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## type

```TypeScript
readonly type: string
```

标识与Want相匹配的数据类型，使用MIME（Multipurpose?Internet?Mail?Extensions）类型规范和 [UniformDataType]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_类型规范。

**类型：** string

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SkillUri-readonly type: string--><!--Device-SkillUri-readonly type: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## utd

```TypeScript
readonly utd: string
```

标识与 Want 相匹配的 URI 的标准化数据类型，适用于分享等场景。

**类型：** string

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SkillUri-readonly utd: string--><!--Device-SkillUri-readonly utd: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

