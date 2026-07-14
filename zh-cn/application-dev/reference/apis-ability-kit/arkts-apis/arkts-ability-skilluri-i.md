# SkillUri

Want匹配的Uri集合。

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## host

```TypeScript
readonly host: string
```

标识 URI 主机地址部分，仅当 scheme 存在时才生效。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## linkFeature

```TypeScript
readonly linkFeature: string
```

标识 URI 提供的[功能类型](../../../../application-models/app-uri-config.md#linkfeature标签说明)，用于实现应用间跳转，仅在AbilityInfo中存在。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## maxFileSupported

```TypeScript
readonly maxFileSupported: number
```

对于指定类型的文件，标识一次能接收或打开的最大数量。取值范围：不小于0的整数。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## path

```TypeScript
readonly path: string
```

标识 URI 路径部分，仅当 scheme 和 host 同时存在时才生效。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## pathRegex

```TypeScript
readonly pathRegex: string
```

标识 URI 路径部分，用于正则匹配，仅当 scheme 和 host 同时存在时才生效。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## pathStartWith

```TypeScript
readonly pathStartWith: string
```

标识 URI 路径部分，用于前缀匹配，仅当 scheme 和 host 同时存在时才生效。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## port

```TypeScript
readonly port: number
```

标识 URI 端口，仅当 scheme 和 host 同时存在时才生效。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## scheme

```TypeScript
readonly scheme: string
```

标识 URI 协议名，常见的有http、https、file、ftp等。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## type

```TypeScript
readonly type: string
```

标识与Want相匹配的数据类型，使用MIME（Multipurpose?Internet?Mail?Extensions）类型规范和
[UniformDataType](./../@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型规范。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## utd

```TypeScript
readonly utd: string
```

标识与 Want 相匹配的 URI 的标准化数据类型，适用于分享等场景。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

