# ExtensionAbilityInfo

ExtensionAbility信息，可以通过[bundleManager.getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getbundleinfoforself)获取自身的ExtensionAbility信息，其中参数[bundleFlags](arkts-ability-bundlemanager-bundleflag-e.md)至少包含GET_BUNDLE_INFO_WITH_HAP_MODULE和GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY。

**起始版本：** 9

<!--Device-unnamed-export interface ExtensionAbilityInfo--><!--Device-unnamed-export interface ExtensionAbilityInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## appIndex

```TypeScript
readonly appIndex: number
```

应用包的分身索引标识，仅在分身应用中生效。

**类型：** number

**起始版本：** 12

<!--Device-ExtensionAbilityInfo-readonly appIndex: int--><!--Device-ExtensionAbilityInfo-readonly appIndex: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## applicationInfo

```TypeScript
readonly applicationInfo: ApplicationInfo
```

应用程序的配置信息<!--Del-->，可以通过调用[queryExtensionAbilityInfo](arkts-ability-bundlemanager-queryextensionabilityinfo-f-sys.md#queryextensionabilityinfo)接口，extensionAbilityFlags参数传入GET_EXTENSION_ABILITY_INFO_WITH_APPLICATION获取<!--DelEnd-->。

[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getbundleinfoforself)或者[getBundleInfo](arkts-ability-bundlemanager-getbundleinfo-f.md#getbundleinfo)接口获取ExtensionAbilityInfo信息时不会返回该字段内容，可以通过获取[bundleInfo](arkts-ability-bundleinfo-i.md).appInfo对象来获取相关信息。

**类型：** ApplicationInfo

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ExtensionAbilityInfo-readonly applicationInfo: ApplicationInfo--><!--Device-ExtensionAbilityInfo-readonly applicationInfo: ApplicationInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## bundleName

```TypeScript
readonly bundleName: string
```

应用Bundle名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ExtensionAbilityInfo-readonly bundleName: string--><!--Device-ExtensionAbilityInfo-readonly bundleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## descriptionId

```TypeScript
readonly descriptionId: number
```

ExtensionAbility的描述资源ID。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ExtensionAbilityInfo-readonly descriptionId: long--><!--Device-ExtensionAbilityInfo-readonly descriptionId: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## enabled

```TypeScript
readonly enabled: boolean
```

ExtensionAbility是否可用，取值为true表示ExtensionAbility可用，取值为false表示ExtensionAbility不可用。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ExtensionAbilityInfo-readonly enabled: boolean--><!--Device-ExtensionAbilityInfo-readonly enabled: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## exported

```TypeScript
readonly exported: boolean
```

判断ExtensionAbility是否可以被其他应用调用，取值为true表示ExtensionAbility可以被其他应用调用，取值为false表示ExtensionAbility不可以被其他应用调用。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ExtensionAbilityInfo-readonly exported: boolean--><!--Device-ExtensionAbilityInfo-readonly exported: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## extensionAbilityType

```TypeScript
readonly extensionAbilityType: bundleManager.ExtensionAbilityType
```

ExtensionAbility类型。

**类型：** bundleManager.ExtensionAbilityType

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ExtensionAbilityInfo-readonly extensionAbilityType: bundleManager.ExtensionAbilityType--><!--Device-ExtensionAbilityInfo-readonly extensionAbilityType: bundleManager.ExtensionAbilityType-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## extensionAbilityTypeName

```TypeScript
readonly extensionAbilityTypeName: string
```

ExtensionAbility的类型名称，取值请参考[extensionabilities标签下的type字段](../../../quick-start/module-configuration-file.md#extensionabilities标签)。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ExtensionAbilityInfo-readonly extensionAbilityTypeName: string--><!--Device-ExtensionAbilityInfo-readonly extensionAbilityTypeName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## iconId

```TypeScript
readonly iconId: number
```

ExtensionAbility的图标资源ID。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ExtensionAbilityInfo-readonly iconId: long--><!--Device-ExtensionAbilityInfo-readonly iconId: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## labelId

```TypeScript
readonly labelId: number
```

ExtensionAbility的标签资源ID。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ExtensionAbilityInfo-readonly labelId: long--><!--Device-ExtensionAbilityInfo-readonly labelId: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## metadata

```TypeScript
readonly metadata: Array<Metadata>
```

ExtensionAbility的元信息。通过调用[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getbundleinfoforself)接口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_HAP_MODULE、GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY和GET_BUNDLE_INFO_WITH_METADATA获取。

**类型：** Array&lt;Metadata&gt;

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ExtensionAbilityInfo-readonly metadata: Array<Metadata>--><!--Device-ExtensionAbilityInfo-readonly metadata: Array<Metadata>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## moduleName

```TypeScript
readonly moduleName: string
```

ExtensionAbility所属的HAP的名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ExtensionAbilityInfo-readonly moduleName: string--><!--Device-ExtensionAbilityInfo-readonly moduleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

ExtensionAbility名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ExtensionAbilityInfo-readonly name: string--><!--Device-ExtensionAbilityInfo-readonly name: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## permissions

```TypeScript
readonly permissions: Array<string>
```

被其他应用ExtensionAbility调用时需要申请的权限集合。

**类型：** Array&lt;string&gt;

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ExtensionAbilityInfo-readonly permissions: Array<string>--><!--Device-ExtensionAbilityInfo-readonly permissions: Array<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## readPermission

```TypeScript
readonly readPermission: string
```

读取ExtensionAbility数据所需的权限。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ExtensionAbilityInfo-readonly readPermission: string--><!--Device-ExtensionAbilityInfo-readonly readPermission: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## skills

```TypeScript
readonly skills: Array<Skill>
```

ExtensionAbility的Skills信息。

**类型：** Array&lt;Skill&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ExtensionAbilityInfo-readonly skills: Array<Skill>--><!--Device-ExtensionAbilityInfo-readonly skills: Array<Skill>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## writePermission

```TypeScript
readonly writePermission: string
```

向ExtensionAbility写数据所需的权限。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ExtensionAbilityInfo-readonly writePermission: string--><!--Device-ExtensionAbilityInfo-readonly writePermission: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

