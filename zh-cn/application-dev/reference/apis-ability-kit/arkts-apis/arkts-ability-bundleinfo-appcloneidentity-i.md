# AppCloneIdentity

```TypeScript
export interface AppCloneIdentity
```

描述应用包的身份信息。

**起始版本：** 14

<!--Device-unnamed-export interface AppCloneIdentity--><!--Device-unnamed-export interface AppCloneIdentity-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## appIndex

```TypeScript
readonly appIndex: number
```

应用包的分身索引信息。取值为整数，范围：[0-5]，0表示主应用，1-5等表示分身应用。

**类型：** number

**起始版本：** 14

<!--Device-AppCloneIdentity-readonly appIndex: int--><!--Device-AppCloneIdentity-readonly appIndex: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## bundleName

```TypeScript
readonly bundleName: string
```

应用的bundleName。

**类型：** string

**起始版本：** 14

<!--Device-AppCloneIdentity-readonly bundleName: string--><!--Device-AppCloneIdentity-readonly bundleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core
