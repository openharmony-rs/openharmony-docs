# ApplicationInstance

应用的实例数据。 该接口目前在[addUserNonStopApps]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_、 [removeUserNonStopApps]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_、 [addFreezeExemptedApps]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_、 [removeFreezeExemptedApps]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_接口 中作为入参使用。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

<!--Device-common-export interface ApplicationInstance--><!--Device-common-export interface ApplicationInstance-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## accountId

```TypeScript
accountId: number
```

用户ID。取值范围：大于等于0的整数。 accountId可以通过[getOsAccountLocalId]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接 口获取。

**类型：** number

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInstance-accountId: number--><!--Device-ApplicationInstance-accountId: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appIdentifier

```TypeScript
appIdentifier: string
```

应用[唯一标识符]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_，可以通过接口 [bundleManager.getBundleInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_获取 bundleInfo.signatureInfo.appIdentifier。

**类型：** string

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInstance-appIdentifier: string--><!--Device-ApplicationInstance-appIdentifier: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appIndex

```TypeScript
appIndex: number
```

应用分身索引。取值范围：大于等于0的整数。 appIndex可以通过[getAppCloneIdentity]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口获取。

**类型：** number

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInstance-appIndex: number--><!--Device-ApplicationInstance-appIndex: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

