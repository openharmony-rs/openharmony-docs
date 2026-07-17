# ExtensionAbilityFlag（系统接口）

扩展组件信息标志，指示需要获取的扩展组件信息的内容。

**起始版本：** 9

<!--Device-bundleManager-enum ExtensionAbilityFlag--><!--Device-bundleManager-enum ExtensionAbilityFlag-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_EXTENSION_ABILITY_INFO_DEFAULT

```TypeScript
GET_EXTENSION_ABILITY_INFO_DEFAULT = 0x00000000
```

用于获取默认extensionAbilityInfo。获取的extensionAbilityInfo不包含permission、metadata 和禁用的extensionAbilityInfo。

**起始版本：** 9

<!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_DEFAULT = 0x00000000--><!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_DEFAULT = 0x00000000-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_EXTENSION_ABILITY_INFO_WITH_PERMISSION

```TypeScript
GET_EXTENSION_ABILITY_INFO_WITH_PERMISSION = 0x00000001
```

用于获取包含permission的extensionAbilityInfo。

**起始版本：** 9

<!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_WITH_PERMISSION = 0x00000001--><!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_WITH_PERMISSION = 0x00000001-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_EXTENSION_ABILITY_INFO_WITH_APPLICATION

```TypeScript
GET_EXTENSION_ABILITY_INFO_WITH_APPLICATION = 0x00000002
```

用于获取包含applicationInfo的extensionAbilityInfo。

**起始版本：** 9

<!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_WITH_APPLICATION = 0x00000002--><!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_WITH_APPLICATION = 0x00000002-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_EXTENSION_ABILITY_INFO_WITH_METADATA

```TypeScript
GET_EXTENSION_ABILITY_INFO_WITH_METADATA = 0x00000004
```

用于获取包含metadata的extensionAbilityInfo。

**起始版本：** 9

<!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_WITH_METADATA = 0x00000004--><!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_WITH_METADATA = 0x00000004-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_EXTENSION_ABILITY_INFO_WITH_SKILL

```TypeScript
GET_EXTENSION_ABILITY_INFO_WITH_SKILL = 0x00000010
```

用于获取包含skills的extensionAbilityInfo。

**起始版本：** 12

<!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_WITH_SKILL = 0x00000010--><!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_WITH_SKILL = 0x00000010-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

