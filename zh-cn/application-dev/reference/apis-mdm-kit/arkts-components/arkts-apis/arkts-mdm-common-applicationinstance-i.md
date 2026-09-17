# ApplicationInstance

应用的实例数据。

该接口目前在[addUserNonStopApps](arkts-mdm-applicationmanager-addusernonstopapps-f.md)、[removeUserNonStopApps](arkts-mdm-applicationmanager-removeusernonstopapps-f.md)、[addFreezeExemptedApps](arkts-mdm-applicationmanager-addfreezeexemptedapps-f.md)、[removeFreezeExemptedApps](arkts-mdm-applicationmanager-removefreezeexemptedapps-f.md)接口中作为入参使用。

**起始版本：** 22

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { common } from '@kit.MDMKit';
```

## accountId

```TypeScript
accountId: number
```

用户ID。取值范围：大于等于0的整数。accountId可以通过[getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)接口获取。

**类型：** number

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appIdentifier

```TypeScript
appIdentifier: string
```

应用[唯一标识符](../../apis-ability-kit/arkts-apis/arkts-ability-bundleinfo-signatureinfo-i.md)，可以通过接口[bundleManager.getBundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfo-f.md)获取bundleInfo.signatureInfo.appIdentifier。

**类型：** string

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appIndex

```TypeScript
appIndex: number
```

应用分身索引。取值范围：大于等于0的整数。

appIndex可以通过[getAppCloneIdentity](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getappcloneidentity-f.md)接口获取。

**类型：** number

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager
