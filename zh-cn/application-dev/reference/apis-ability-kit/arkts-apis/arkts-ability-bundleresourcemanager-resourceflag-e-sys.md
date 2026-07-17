# ResourceFlag（系统接口）

资源信息标志，指示需要获取的资源信息的内容。

**起始版本：** 11

<!--Device-bundleResourceManager-enum ResourceFlag--><!--Device-bundleResourceManager-enum ResourceFlag-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

## GET_RESOURCE_INFO_ALL

```TypeScript
GET_RESOURCE_INFO_ALL = 0x00000001
```

用于同时获取icon和label信息。

**起始版本：** 11

<!--Device-ResourceFlag-GET_RESOURCE_INFO_ALL = 0x00000001--><!--Device-ResourceFlag-GET_RESOURCE_INFO_ALL = 0x00000001-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

## GET_RESOURCE_INFO_WITH_LABEL

```TypeScript
GET_RESOURCE_INFO_WITH_LABEL = 0x00000002
```

用于获取仅包含label信息，icon信息为空。

**起始版本：** 11

<!--Device-ResourceFlag-GET_RESOURCE_INFO_WITH_LABEL = 0x00000002--><!--Device-ResourceFlag-GET_RESOURCE_INFO_WITH_LABEL = 0x00000002-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

## GET_RESOURCE_INFO_WITH_ICON

```TypeScript
GET_RESOURCE_INFO_WITH_ICON = 0x00000004
```

用于获取仅包含icon信息，label信息为空。

**起始版本：** 11

<!--Device-ResourceFlag-GET_RESOURCE_INFO_WITH_ICON = 0x00000004--><!--Device-ResourceFlag-GET_RESOURCE_INFO_WITH_ICON = 0x00000004-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

## GET_RESOURCE_INFO_WITH_SORTED_BY_LABEL

```TypeScript
GET_RESOURCE_INFO_WITH_SORTED_BY_LABEL = 0x00000008
```

用于获取根据label排序后的信息。它不能单独使用需要与GET_RESOURCE_INFO_ALL 或 GET_RESOURCE_INFO_WITH_LABEL一起使用。

**起始版本：** 11

<!--Device-ResourceFlag-GET_RESOURCE_INFO_WITH_SORTED_BY_LABEL = 0x00000008--><!--Device-ResourceFlag-GET_RESOURCE_INFO_WITH_SORTED_BY_LABEL = 0x00000008-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

## GET_RESOURCE_INFO_WITH_DRAWABLE_DESCRIPTOR

```TypeScript
GET_RESOURCE_INFO_WITH_DRAWABLE_DESCRIPTOR = 0x00000010
```

用于获取应用图标的[drawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-drawabledescriptor.md)对象。

**起始版本：** 12

<!--Device-ResourceFlag-GET_RESOURCE_INFO_WITH_DRAWABLE_DESCRIPTOR = 0x00000010--><!--Device-ResourceFlag-GET_RESOURCE_INFO_WITH_DRAWABLE_DESCRIPTOR = 0x00000010-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

## GET_RESOURCE_INFO_ONLY_WITH_MAIN_ABILITY

```TypeScript
GET_RESOURCE_INFO_ONLY_WITH_MAIN_ABILITY = 0x00000020
```

用于获取仅在桌面上展示图标的Ability资源，它仅在[getLauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-getlauncherabilityresourceinfo-f-sys.md#getlauncherabilityresourceinfo-1)和[getAllLauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-getalllauncherabilityresourceinfo-f-sys.md#getalllauncherabilityresourceinfo-1)接口中生效。

**起始版本：** 20

<!--Device-ResourceFlag-GET_RESOURCE_INFO_ONLY_WITH_MAIN_ABILITY = 0x00000020--><!--Device-ResourceFlag-GET_RESOURCE_INFO_ONLY_WITH_MAIN_ABILITY = 0x00000020-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

