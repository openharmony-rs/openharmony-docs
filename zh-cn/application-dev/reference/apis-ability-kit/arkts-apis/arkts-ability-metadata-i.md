# Metadata

```TypeScript
export interface Metadata
```

元数据对象，可以通过[bundleManager.getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md)获取，其中参数bundleFlags至少包含GET_BUNDLE_INFO_WITH_METADATA。此对象在[ApplicationInfo](arkts-ability-applicationinfo-depr-i.md)、[HapModuleInfo](arkts-ability-hapmoduleinfo-depr-i.md)、[AbilityInfo](arkts-ability-abilityinfo-depr-i.md)、[ExtensionAbilityInfo](arkts-ability-extensionabilityinfo-i.md)中均包含。

**起始版本：** 9

<!--Device-unnamed-export interface Metadata--><!--Device-unnamed-export interface Metadata-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
name: string
```

元数据名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-Metadata-name: string--><!--Device-Metadata-name: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## resource

```TypeScript
resource: string
```

元数据资源描述符，参考示例$profile:config_file，表示profile目录下配置了config_file.json文件。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-Metadata-resource: string--><!--Device-Metadata-resource: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## value

```TypeScript
value: string
```

元数据值。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-Metadata-value: string--><!--Device-Metadata-value: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## valueId

```TypeScript
readonly valueId?: number
```

元数据值id。当valueId不为0时，表示当前元数据值为自定义配置，需要使用valueId去资源管理获取对应的值。 当valueId为0时，表示当前元数据值为固定字符串。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-Metadata-readonly valueId?: long--><!--Device-Metadata-readonly valueId?: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core
