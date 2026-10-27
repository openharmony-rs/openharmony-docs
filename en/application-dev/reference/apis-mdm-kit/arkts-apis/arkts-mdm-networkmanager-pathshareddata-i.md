# PathSharedData

```TypeScript
interface PathSharedData
```

Path shared data.

**Since:** 26.1.0

<!--Device-networkManager-interface PathSharedData--><!--Device-networkManager-interface PathSharedData-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## shareLimit

```TypeScript
shareLimit: number
```

The maximum number of users allowed to access this shared resource.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PathSharedData-shareLimit: number--><!--Device-PathSharedData-shareLimit: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## shareName

```TypeScript
shareName: string
```

Path sharing name.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PathSharedData-shareName: string--><!--Device-PathSharedData-shareName: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## shareUri

```TypeScript
shareUri: string
```

URI of the shared path.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PathSharedData-shareUri: string--><!--Device-PathSharedData-shareUri: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## userPathInfoList

```TypeScript
userPathInfoList: Array<UserPathInfo>
```

User path information list, used for permission management.

**Type:** Array&lt;[UserPathInfo](arkts-mdm-networkmanager-userpathinfo-i.md)&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PathSharedData-userPathInfoList: Array<UserPathInfo>--><!--Device-PathSharedData-userPathInfoList: Array<UserPathInfo>-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
