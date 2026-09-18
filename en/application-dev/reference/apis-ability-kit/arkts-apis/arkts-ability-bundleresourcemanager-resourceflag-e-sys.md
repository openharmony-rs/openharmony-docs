# ResourceFlag (System API)

Enumerates the resource information flags, which indicate the type of resource information to obtain.

**Since:** 11

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

## GET_RESOURCE_INFO_ALL

```TypeScript
GET_RESOURCE_INFO_ALL = 0x00000001
```

Both the application icon and label are obtained.

**Since:** 11

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

## GET_RESOURCE_INFO_WITH_LABEL

```TypeScript
GET_RESOURCE_INFO_WITH_LABEL = 0x00000002
```

Only the application label is obtained.

**Since:** 11

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

## GET_RESOURCE_INFO_WITH_ICON

```TypeScript
GET_RESOURCE_INFO_WITH_ICON = 0x00000004
```

Only the application icon is obtained.

**Since:** 11

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

## GET_RESOURCE_INFO_WITH_SORTED_BY_LABEL

```TypeScript
GET_RESOURCE_INFO_WITH_SORTED_BY_LABEL = 0x00000008
```

The obtained information is sorted by label. It must be used together with **GET_RESOURCE_INFO_ALL** or **GET_RESOURCE_INFO_WITH_LABEL**.

**Since:** 11

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

## GET_RESOURCE_INFO_WITH_DRAWABLE_DESCRIPTOR

```TypeScript
GET_RESOURCE_INFO_WITH_DRAWABLE_DESCRIPTOR = 0x00000010
```

The drawableDescriptor object of the application icon is obtained.

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

## GET_RESOURCE_INFO_ONLY_WITH_MAIN_ABILITY

```TypeScript
GET_RESOURCE_INFO_ONLY_WITH_MAIN_ABILITY = 0x00000020
```

The resource information about abilities that show icons only on the home screen is obtained. It is valid only in the [getLauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-getlauncherabilityresourceinfo-f-sys.md) and [getAllLauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-getalllauncherabilityresourceinfo-f-sys.md) APIs.

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.
