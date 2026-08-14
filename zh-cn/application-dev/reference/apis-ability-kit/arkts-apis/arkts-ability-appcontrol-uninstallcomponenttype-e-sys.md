# UninstallComponentType（系统接口）

标识卸载时功能组件类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-appControl-export enum UninstallComponentType--><!--Device-appControl-export enum UninstallComponentType-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## EXTENSION

```TypeScript
EXTENSION = 1
```

服务扩展能力类型。仅支持service类型的[ExtensionAbility](../../../quick-start/module-configuration-file.md#extensionabilities标签) 。 被拉起的ExtensionAbility通过want中bundleName、moduleName、abilityName字段共同确定。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-UninstallComponentType-EXTENSION = 1--><!--Device-UninstallComponentType-EXTENSION = 1-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## UI_EXTENSION

```TypeScript
UI_EXTENSION = 2
```

UI扩展能力类型。 被拉起的UIExtensionAbility通过want中bundleName、moduleName、abilityName字段共同确定，同时want.parameters中的 ability.want.params.uiExtensionType字段需要配置为 [UIExtensionAbility](../../../application-models/uiextensionability-sys.md)的类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-UninstallComponentType-UI_EXTENSION = 2--><!--Device-UninstallComponentType-UI_EXTENSION = 2-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

