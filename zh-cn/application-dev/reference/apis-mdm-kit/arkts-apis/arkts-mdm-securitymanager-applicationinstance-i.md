# ApplicationInstance

应用实例。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

<!--Device-securityManager-export interface ApplicationInstance--><!--Device-securityManager-export interface ApplicationInstance-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## accountId

```TypeScript
accountId: number
```

用户ID，指定具体用户，取值范围：大于等于0。accountId可以通过@ohos.account.osAccount中的 [getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId)等接口来获取。

**类型：** number

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInstance-accountId: number--><!--Device-ApplicationInstance-accountId: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appIdentifier

```TypeScript
appIdentifier: string
```

应用[唯一标识符](../../apis-ability-kit/arkts-apis/arkts-ability-bundleinfo-signatureinfo-i.md#SignatureInfo)，如果应用没有appIdentifier可使用appId代替，可以通过接口 [bundleManager.getBundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfo-f.md#getBundleInfo)获取 bundleInfo.signatureInfo.appIdentifier和bundleInfo.signatureInfo.appId。

**类型：** string

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInstance-appIdentifier: string--><!--Device-ApplicationInstance-appIdentifier: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appIndex

```TypeScript
appIndex: number
```

表示分身应用的索引，默认值为0。 appIndex为0时，表示主应用。appIndex大于0时，表示指定的分身应用。

**类型：** number

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInstance-appIndex: number--><!--Device-ApplicationInstance-appIndex: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

