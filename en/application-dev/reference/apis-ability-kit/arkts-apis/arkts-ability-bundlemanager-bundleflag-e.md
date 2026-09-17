# BundleFlag

Enumerates the bundle flags, which indicate the type of bundle information to obtain.

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_DEFAULT

```TypeScript
GET_BUNDLE_INFO_DEFAULT = 0x00000000
```

Used to obtain the default bundle information. The obtained information does not contain information about the signature, application, HAP module, ability, ExtensionAbility, or permission.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_APPLICATION

```TypeScript
GET_BUNDLE_INFO_WITH_APPLICATION = 0x00000001
```

Used to obtain the bundle information with application information. The obtained information does not contain information about the signature, HAP module, ability, ExtensionAbility, or permission.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_HAP_MODULE

```TypeScript
GET_BUNDLE_INFO_WITH_HAP_MODULE = 0x00000002
```

Used to obtain the bundle information with HAP module information. The obtained information does not contain information about the signature, application, ability, ExtensionAbility, or permission.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_ABILITY

```TypeScript
GET_BUNDLE_INFO_WITH_ABILITY = 0x00000004
```

Used to obtain the bundle information with ability information. The obtained information does not contain information about the signature, application, ExtensionAbility, or permission. It must be used together with **GET_BUNDLE_INFO_WITH_HAP_MODULE**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY

```TypeScript
GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY = 0x00000008
```

Used to obtain the bundle information with ExtensionAbility information. The obtained information does not contain information about the signature, application, ability, or permission. It must be used together with **GET_BUNDLE_INFO_WITH_HAP_MODULE**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION

```TypeScript
GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION = 0x00000010
```

Used to obtain the bundle information with permission information. The obtained information does not contain information about the signature, application, HAP module, ability, or ExtensionAbility.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_METADATA

```TypeScript
GET_BUNDLE_INFO_WITH_METADATA = 0x00000020
```

Used to obtain the metadata contained in the application, module, ability, or ExtensionAbility information. It must be used together with **GET_BUNDLE_INFO_WITH_APPLICATION**, **GET_BUNDLE_INFO_WITH_HAP_MODULE**, **GET_BUNDLE_INFO_WITH_ABILITY**, and **GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY**.

- To obtain the metadata contained in the application information, it must be used together with  
**GET_BUNDLE_INFO_WITH_APPLICATION**.  
- To obtain the metadata contained in the module information, it must be used together with  
**GET_BUNDLE_INFO_WITH_HAP_MODULE**.  
- To obtain the metadata contained in the ability information, it must be used together with  
**GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_ABILITY**.  
- To obtain the metadata contained in the ExtensionAbility information, it must be used together with  
**GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_DISABLE

```TypeScript
GET_BUNDLE_INFO_WITH_DISABLE = 0x00000040
```

Used to obtain the information about disabled bundles and abilities of a bundle. The obtained information does not contain information about the signature, application, HAP module, ability, ExtensionAbility, or permission.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_SIGNATURE_INFO

```TypeScript
GET_BUNDLE_INFO_WITH_SIGNATURE_INFO = 0x00000080
```

Used to obtain the bundle information with signature information. The obtained information does not contain information about the application, HAP module, ability, ExtensionAbility, or permission.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_MENU

```TypeScript
GET_BUNDLE_INFO_WITH_MENU = 0x00000100
```

Used to obtain the bundle information with the file context menu configuration. It must be used together with **GET_BUNDLE_INFO_WITH_HAP_MODULE**.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_ROUTER_MAP

```TypeScript
GET_BUNDLE_INFO_WITH_ROUTER_MAP = 0x00000200
```

Used to obtain the bundle information with the router map. It must be used together with **GET_BUNDLE_INFO_WITH_HAP_MODULE**.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_SKILL

```TypeScript
GET_BUNDLE_INFO_WITH_SKILL = 0x00000800
```

Used to obtain the bundle information with the skills. It must be used together with **GET_BUNDLE_INFO_WITH_HAP_MODULE**, **GET_BUNDLE_INFO_WITH_ABILITY**, and **GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY**.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_ONLY_WITH_LAUNCHER_ABILITY

```TypeScript
GET_BUNDLE_INFO_ONLY_WITH_LAUNCHER_ABILITY = 0x00001000
```

Used to obtain the bundle information of the application that has only a home screen icon.

**Since:** 26.2.0

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_ENTRY_MODULE

```TypeScript
GET_BUNDLE_INFO_WITH_ENTRY_MODULE = 0x00010000
```

Used to obtain the bundle information with the HAP module information. It is valid only for bundleInfo.hapModulesInfo corresponding to the entry module. If the entry module does not exist, the bundleInfo.hapModulesInfo list is empty. The obtained bundle information does not contain information about the signature, application, ability, ExtensionAbility, or permission.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
