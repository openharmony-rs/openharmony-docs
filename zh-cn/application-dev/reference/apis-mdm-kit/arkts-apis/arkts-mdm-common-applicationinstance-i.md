# ApplicationInstance

应用的实例数据。 该接口目前在[addUserNonStopApps](arkts-mdm-applicationmanager-addusernonstopapps-f.md#addUserNonStopApps)、 [removeUserNonStopApps](arkts-mdm-applicationmanager-removeusernonstopapps-f.md#removeUserNonStopApps)、 [addFreezeExemptedApps](arkts-mdm-applicationmanager-addfreezeexemptedapps-f.md#addFreezeExemptedApps)、 [removeFreezeExemptedApps](arkts-mdm-applicationmanager-removefreezeexemptedapps-f.md#removeFreezeExemptedApps)接口 中作为入参使用。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

<!--Device-common-export interface ApplicationInstance--><!--Device-common-export interface ApplicationInstance-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## accountId

```TypeScript
accountId: number
```

用户ID。取值范围：大于等于0的整数。 accountId可以通过[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId)接 口获取。

**类型：** number

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInstance-accountId: number--><!--Device-ApplicationInstance-accountId: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appIdentifier

```TypeScript
appIdentifier: string
```

应用[唯一标识符](../../apis-ability-kit/arkts-apis/arkts-ability-bundleinfo-signatureinfo-i.md#SignatureInfo)，可以通过接口 [bundleManager.getBundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfo-f.md#getBundleInfo)获取 bundleInfo.signatureInfo.appIdentifier。

**类型：** string

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInstance-appIdentifier: string--><!--Device-ApplicationInstance-appIdentifier: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appIndex

```TypeScript
appIndex: number
```

应用分身索引。取值范围：大于等于0的整数。 appIndex可以通过[getAppCloneIdentity](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getappcloneidentity-f.md#getAppCloneIdentity)接口获取。

**类型：** number

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInstance-appIndex: number--><!--Device-ApplicationInstance-appIndex: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

