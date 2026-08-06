# SignatureInfo

描述应用包的签名信息。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export interface SignatureInfo--><!--Device-unnamed-export interface SignatureInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## appId

```TypeScript
readonly appId: string
```

应用的appId，表示应用的唯一标识，详情信息可参考\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** string

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SignatureInfo-readonly appId: string--><!--Device-SignatureInfo-readonly appId: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## appIdentifier

```TypeScript
readonly appIdentifier: string
```

应用的唯一标识。详情信息可参考\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** string

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

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

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

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

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SignatureInfo-readonly fingerprint: string--><!--Device-SignatureInfo-readonly fingerprint: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

