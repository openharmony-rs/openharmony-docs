# ApplicationInstance

Defines application instance data.

It is used as an input parameter in the [addUserNonStopApps](arkts-mdm-applicationmanager-addusernonstopapps-f.md), [removeUserNonStopApps](arkts-mdm-applicationmanager-removeusernonstopapps-f.md), [addFreezeExemptedApps](arkts-mdm-applicationmanager-addfreezeexemptedapps-f.md), and [removeFreezeExemptedApps](arkts-mdm-applicationmanager-removefreezeexemptedapps-f.md) APIs.

**Since:** 22

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { common } from '@kit.MDMKit';
```

## accountId

```TypeScript
accountId: number
```

Account ID. The value is an integer greater than or equal to 0. You can obtain the account ID by calling the [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) API.

**Type:** number

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## appIdentifier

```TypeScript
appIdentifier: string
```

[Unique identifier](../../apis-ability-kit/arkts-apis/arkts-ability-bundleinfo-signatureinfo-i.md) of an application. You can call the [bundleManager.getBundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfo-f.md) API to obtain **bundleInfo.signatureInfo.appIdentifier**.

**Type:** string

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## appIndex

```TypeScript
appIndex: number
```

Index of the application clone. The value is an integer greater than or equal to 0.

You can obtain the index by calling the [getAppCloneIdentity](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getappcloneidentity-f.md) API.

**Type:** number

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
