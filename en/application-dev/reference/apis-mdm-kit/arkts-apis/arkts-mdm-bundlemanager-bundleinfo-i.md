# BundleInfo

```TypeScript
interface BundleInfo
```

Describes the application bundle information.

**Since:** 20

<!--Device-bundleManager-interface BundleInfo--><!--Device-bundleManager-interface BundleInfo-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## appIndex

```TypeScript
readonly appIndex: number
```

Index of an application clone. It takes effect only for application clones.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfo-readonly appIndex: number--><!--Device-BundleInfo-readonly appIndex: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## appInfo

```TypeScript
readonly appInfo: ApplicationInfo
```

Application information.

**Type:** [ApplicationInfo](arkts-mdm-bundlemanager-applicationinfo-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfo-readonly appInfo: ApplicationInfo--><!--Device-BundleInfo-readonly appInfo: ApplicationInfo-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## firstInstallTime

```TypeScript
readonly firstInstallTime?: number
```

Timestamp for the initial installation of the application bundle. It measures the milliseconds elapsed since the Unix epoch (January 1, 1970, 08:00:00 UTC+8). For preinstalled applications, the initial installation timestamp is 1533657660000.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfo-readonly firstInstallTime?: number--><!--Device-BundleInfo-readonly firstInstallTime?: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## installTime

```TypeScript
readonly installTime: number
```

Timestamp for the installation of the application bundle. It measures the milliseconds elapsed since the Unix epoch (January 1, 1970, 08:00:00 UTC+8).

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfo-readonly installTime: number--><!--Device-BundleInfo-readonly installTime: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## minCompatibleVersionCode

```TypeScript
readonly minCompatibleVersionCode: number
```

Minimum compatible version of the application bundle in the distributed scenario. It corresponds to the **minCompatibleVersionCode** field in the [app.json5](../../../quick-start/app-configuration-file.md) file.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfo-readonly minCompatibleVersionCode: number--><!--Device-BundleInfo-readonly minCompatibleVersionCode: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## name

```TypeScript
readonly name: string
```

Name of the application bundle. It corresponds to the **bundleName** field in the [app.json5](../../../quick-start/app-configuration-file.md) file.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfo-readonly name: string--><!--Device-BundleInfo-readonly name: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## signatureInfo

```TypeScript
readonly signatureInfo: SignatureInfo
```

Signature information of the bundle.

**Type:** [SignatureInfo](arkts-mdm-bundlemanager-signatureinfo-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfo-readonly signatureInfo: SignatureInfo--><!--Device-BundleInfo-readonly signatureInfo: SignatureInfo-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## targetVersion

```TypeScript
readonly targetVersion: number
```

Target version of the application. It corresponds to the **targetAPIVersion** field in the [app.json5](../../../quick-start/app-configuration-file.md) file.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfo-readonly targetVersion: number--><!--Device-BundleInfo-readonly targetVersion: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## updateTime

```TypeScript
readonly updateTime: number
```

Timestamp for the last update of the application bundle. It measures the milliseconds elapsed since the Unix epoch (January 1, 1970, 08:00:00 UTC+8).

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfo-readonly updateTime: number--><!--Device-BundleInfo-readonly updateTime: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## vendor

```TypeScript
readonly vendor: string
```

Vendor of the application bundle. It corresponds to the **vendor** field in the [app.json5](../../../quick-start/app-configuration-file.md) file.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfo-readonly vendor: string--><!--Device-BundleInfo-readonly vendor: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## versionCode

```TypeScript
readonly versionCode: number
```

Version code of the application bundle. It corresponds to the **versionCode** field in the [app.json5](../../../quick-start/app-configuration-file.md) file.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfo-readonly versionCode: number--><!--Device-BundleInfo-readonly versionCode: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## versionName

```TypeScript
readonly versionName: string
```

Version description of the application bundle. It corresponds to the **versionName** field in the [app.json5](../../../quick-start/app-configuration-file.md) file.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfo-readonly versionName: string--><!--Device-BundleInfo-readonly versionName: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
