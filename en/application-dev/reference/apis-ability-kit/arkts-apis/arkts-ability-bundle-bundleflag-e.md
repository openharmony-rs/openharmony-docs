# BundleFlag


> **NOTE:** 
> 
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use
> [bundleManager.BundleFlag](arkts-ability-bundlemanager-bundleflag-e.md) instead.

Enumerates the bundle flags, which indicate the type of bundle information to obtain.

If an API does not match the flag, the flag is ignored. For example, using **GET_ABILITY_INFO_WITH_PERMISSION** to obtain the application information does not affect the result.

Flags can be used together. For example, you can use the combination of **GET_APPLICATION_INFO_WITH_PERMISSION** and **GET_APPLICATION_INFO_WITH_DISABLE** to obtain the result that contains both application permission information and disabled application information.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [BundleFlag](arkts-ability-bundlemanager-bundleflag-e.md)

**System capability:** SystemCapability.BundleManager.BundleFramework

## GET_BUNDLE_DEFAULT

```TypeScript
GET_BUNDLE_DEFAULT = 0x00000000
```

Obtains the default application information.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [GET_BUNDLE_INFO_DEFAULT](arkts-ability-bundlemanager-bundleflag-e.md#get_bundle_info_default)

**System capability:** SystemCapability.BundleManager.BundleFramework

## GET_BUNDLE_WITH_ABILITIES

```TypeScript
GET_BUNDLE_WITH_ABILITIES = 0x00000001
```

Obtains the bundle information with the ability information.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [GET_BUNDLE_INFO_WITH_ABILITY](arkts-ability-bundlemanager-bundleflag-e.md#get_bundle_info_with_ability)

**System capability:** SystemCapability.BundleManager.BundleFramework

## GET_ABILITY_INFO_WITH_PERMISSION

```TypeScript
GET_ABILITY_INFO_WITH_PERMISSION = 0x00000002
```

Obtains the ability information with the permission information.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [GET_ABILITY_INFO_WITH_PERMISSION](arkts-ability-bundlemanager-abilityflag-e.md#get_ability_info_with_permission)

**System capability:** SystemCapability.BundleManager.BundleFramework

## GET_ABILITY_INFO_WITH_APPLICATION

```TypeScript
GET_ABILITY_INFO_WITH_APPLICATION = 0x00000004
```

Obtains the ability information with the application information.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [GET_ABILITY_INFO_WITH_APPLICATION](arkts-ability-bundlemanager-abilityflag-e.md#get_ability_info_with_application)

**System capability:** SystemCapability.BundleManager.BundleFramework

## GET_APPLICATION_INFO_WITH_PERMISSION

```TypeScript
GET_APPLICATION_INFO_WITH_PERMISSION = 0x00000008
```

Installation conflict. (The basic information of the application to update is inconsistent with that of the existing application.)

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework

## GET_BUNDLE_WITH_REQUESTED_PERMISSION

```TypeScript
GET_BUNDLE_WITH_REQUESTED_PERMISSION = 0x00000010
```

Obtains the bundle information with the information about the required permissions.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION](arkts-ability-bundlemanager-bundleflag-e.md#get_bundle_info_with_requested_permission)

**System capability:** SystemCapability.BundleManager.BundleFramework

## GET_ALL_APPLICATION_INFO

```TypeScript
GET_ALL_APPLICATION_INFO = 0xFFFF0000
```

Installation conflict. (The basic information of the application to update is inconsistent with that of the existing application.)

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework

## GET_ABILITY_INFO_WITH_METADATA

```TypeScript
GET_ABILITY_INFO_WITH_METADATA = 0x00000020
```

Obtains the ability metadata information.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [GET_ABILITY_INFO_WITH_METADATA](arkts-ability-bundlemanager-abilityflag-e.md#get_ability_info_with_metadata)

**System capability:** SystemCapability.BundleManager.BundleFramework

## GET_APPLICATION_INFO_WITH_METADATA

```TypeScript
GET_APPLICATION_INFO_WITH_METADATA = 0x00000040
```

No uninstallation permission.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework

## GET_ABILITY_INFO_SYSTEMAPP_ONLY

```TypeScript
GET_ABILITY_INFO_SYSTEMAPP_ONLY = 0x00000080
```

Obtains the ability information of system applications.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [GET_ABILITY_INFO_ONLY_SYSTEM_APP](arkts-ability-bundlemanager-abilityflag-e.md#get_ability_info_only_system_app)

**System capability:** SystemCapability.BundleManager.BundleFramework

## GET_ABILITY_INFO_WITH_DISABLE

```TypeScript
GET_ABILITY_INFO_WITH_DISABLE = 0x00000100
```

Obtains information about disabled abilities.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [GET_ABILITY_INFO_WITH_DISABLE](arkts-ability-bundlemanager-abilityflag-e.md#get_ability_info_with_disable)

**System capability:** SystemCapability.BundleManager.BundleFramework

## GET_APPLICATION_INFO_WITH_DISABLE

```TypeScript
GET_APPLICATION_INFO_WITH_DISABLE = 0x00000200
```

No uninstallation permission.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework
