# ApplicationInfo

Defines the application information.

**Since:** 20

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## accessTokenId

```TypeScript
readonly accessTokenId: number
```

Access token ID of the application, which is used in the [checkAccessToken](../../apis-ability-kit/arkts-apis/arkts-ability-abilityaccessctrl-atmanager-i.md#checkaccesstoken).

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## appDistributionType

```TypeScript
readonly appDistributionType: string
```

Distribution type of the application signing certificate. For details, see the **appProvisionType** field in [ApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md).

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## appIndex

```TypeScript
readonly appIndex: number
```

Index of an application clone. It takes effect only for application clones.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## appProvisionType

```TypeScript
readonly appProvisionType: string
```

Type of the application signing certificate file. The options are **debug** and **release**.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## codePath

```TypeScript
readonly codePath: string
```

Installation directory of the application.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## dataUnclearable

```TypeScript
readonly dataUnclearable: boolean
```

Whether the application data is unclearable. The value **true** means that the application data is unclearable, and **false** means the opposite.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## debug

```TypeScript
readonly debug: boolean
```

Whether the application is running in debug mode. **true** if in debug mode, **false** otherwise.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## description

```TypeScript
readonly description: string
```

Description of the application. It corresponds to the **description** field in [app.json5](../../../quick-start/app-configuration-file.md). For details about **description**, see the **descriptionResource** field in this table.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## descriptionId

```TypeScript
readonly descriptionId: number
```

Resource ID of the application description. It is automatically generated during compilation and build based on the description configured for the application.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## descriptionResource

```TypeScript
readonly descriptionResource: Resource
```

Resource information of the application description, including the bundle name, module name, and ID of the resource.

**Type:** [Resource](arkts-mdm-bundlemanager-resource-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## enabled

```TypeScript
readonly enabled: boolean
```

Whether the application is enabled. **true** if enabled, **false** otherwise.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## icon

```TypeScript
readonly icon: string
```

Application icon. It corresponds to the **icon** field in the [app.json5](../../../quick-start/app-configuration-file.md) file. For details about **icon**, see the **iconResource** field in this table.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## iconData

```TypeScript
readonly iconData: string
```

Application icon, which is in Base64 encoding format.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## iconId

```TypeScript
readonly iconId: number
```

Resource ID of the application icon. It is automatically generated during compilation and build based on the icon configured for the application.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## iconResource

```TypeScript
readonly iconResource: Resource
```

Resource information of the application icon, including the bundle name, module name, and ID of the resource.

**Type:** [Resource](arkts-mdm-bundlemanager-resource-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## installSource

```TypeScript
readonly installSource: string
```

Installation source of the application. The options are as follows:

- **pre-installed**: The application is a preset application installed at initial device startup.  
- **ota**: The application is a preset application added during system upgrade.  
- **recovery**: The preset application is uninstalled and then restored.  
- **bundleName**: The application corresponding to the bundle name is installed.  
- **unknown**: The installation source is unknown.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## label

```TypeScript
readonly label: string
```

Application label.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## labelId

```TypeScript
readonly labelId: number
```

Resource ID of the application label. It is automatically generated during compilation and build based on the label configured for the application.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## labelResource

```TypeScript
readonly labelResource: Resource
```

Resource information of the application label, including the bundle name, module name, and ID of the resource.

**Type:** [Resource](arkts-mdm-bundlemanager-resource-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## name

```TypeScript
readonly name: string
```

Name of the application bundle. It corresponds to the **bundleName** field in the [app.json5](../../../quick-start/app-configuration-file.md) file.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## nativeLibraryPath

```TypeScript
readonly nativeLibraryPath: string
```

Local library file path of the application.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## process

```TypeScript
readonly process: string
```

Process name.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## releaseType

```TypeScript
readonly releaseType: string
```

Release type of the SDK used for application packing. Currently, the SDK release types include Canary, Beta, and Release. Each of the Canary and Beta releases can be distinguished by a sequential number, such as Canary1, Canary2, Beta1, and Beta2. You can compare the SDK release type on which application packaging depends and the OS release type (specified by [deviceInfo.distributionOSReleaseType](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-deviceinfo.md)) to determine the compatibility.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## removable

```TypeScript
readonly removable: boolean
```

Whether the application is removable. **true** if removable, **false** otherwise.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## systemApp

```TypeScript
readonly systemApp: boolean
```

Whether the application is a system application. **true** if it is a system application, **false** otherwise.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## uid

```TypeScript
readonly uid: number
```

UID of the application.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
