# ApplicationInstance

应用实例。

**起始版本：** 20

<!--Device-securityManager-export interface ApplicationInstance--><!--Device-securityManager-export interface ApplicationInstance-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## accountId

```TypeScript
accountId: number
```

Account ID, which must be greater than or equal to 0. You can call [getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) of **@ohos.account.osAccount** to obtain the account ID.

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInstance-accountId: number--><!--Device-ApplicationInstance-accountId: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appIdentifier

```TypeScript
appIdentifier: string
```

应用[唯一标识符](../../apis-ability-kit/arkts-apis/arkts-ability-bundleinfo-signatureinfo-i.md)，如果应用没有appIdentifier可使用appId代替，可以通过接口[bundleManager.getBundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfo-f.md#getbundleinfo)获取bundleInfo.signatureInfo.appIdentifier和bundleInfo.signatureInfo.appId。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInstance-appIdentifier: string--><!--Device-ApplicationInstance-appIdentifier: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appIndex

```TypeScript
appIndex: number
```

表示分身应用的索引，默认值为0。

appIndex为0时，表示主应用。appIndex大于0时，表示指定的分身应用。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInstance-appIndex: number--><!--Device-ApplicationInstance-appIndex: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

