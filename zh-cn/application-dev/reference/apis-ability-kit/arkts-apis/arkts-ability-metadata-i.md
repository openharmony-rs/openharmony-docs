# Metadata

元数据对象，可以通过 [bundleManager.getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf) 获取，其中参数bundleFlags至少包含GET_BUNDLE_INFO_WITH_METADATA。此对象在ApplicationInfo、 HapModuleInfo、AbilityInfo、 [ExtensionAbilityInfo](arkts-ability-extensionabilityinfo-i.md#ExtensionAbilityInfo)中均包含。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface Metadata--><!--Device-unnamed-export interface Metadata-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
name: string
```

Indicates the metadata name

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Metadata-name: string--><!--Device-Metadata-name: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## resource

```TypeScript
resource: string
```

Indicates the metadata resource

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Metadata-resource: string--><!--Device-Metadata-resource: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## value

```TypeScript
value: string
```

Indicates the metadata value

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Metadata-value: string--><!--Device-Metadata-value: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## valueId

```TypeScript
readonly valueId?: long
```

Indicates the value id of the metadata

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Metadata-readonly valueId?: long--><!--Device-Metadata-readonly valueId?: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

