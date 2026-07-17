# SignatureInfo

描述应用包的签名信息。

**起始版本：** 9

<!--Device-unnamed-export interface SignatureInfo--><!--Device-unnamed-export interface SignatureInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## appId

```TypeScript
readonly appId: string
```

应用的appId，表示应用的唯一标识，详情信息可参考[什么是appId](../../../../quick-start/common-problem-of-application.md#什么是appid)。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SignatureInfo-readonly appId: string--><!--Device-SignatureInfo-readonly appId: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## appIdentifier

```TypeScript
readonly appIdentifier: string
```

应用的唯一标识。详情信息可参考[什么是appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SignatureInfo-readonly appIdentifier: string--><!--Device-SignatureInfo-readonly appIdentifier: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## certificate

```TypeScript
readonly certificate?: string
```

应用的证书公钥。

**类型：** string

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-SignatureInfo-readonly certificate?: string--><!--Device-SignatureInfo-readonly certificate?: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## fingerprint

```TypeScript
readonly fingerprint: string
```

应用包的指纹信息，由签名证书通过SHA-256算法计算哈希值生成。使用的签名证书发生变化时，该字段也会发生变化。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SignatureInfo-readonly fingerprint: string--><!--Device-SignatureInfo-readonly fingerprint: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

