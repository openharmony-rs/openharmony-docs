# RecoverComponentType（系统接口）

```TypeScript
export enum RecoverComponentType
```

标识恢复时功能组件类型。

**起始版本：** 26.1.0

<!--Device-appControl-export enum RecoverComponentType--><!--Device-appControl-export enum RecoverComponentType-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## EXTENSION

```TypeScript
EXTENSION = 1
```

服务扩展能力类型。仅支持service类型的[ExtensionAbility](../../../quick-start/module-configuration-file.md#extensionabilities标签)。

被拉起的ExtensionAbility通过want中bundleName、moduleName、abilityName字段共同确定。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RecoverComponentType-EXTENSION = 1--><!--Device-RecoverComponentType-EXTENSION = 1-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## UI_EXTENSION

```TypeScript
UI_EXTENSION = 2
```

UI扩展能力类型。

被拉起的UIExtensionAbility通过want中bundleName、moduleName、abilityName字段共同确定，同时want.parameters中的ability.want.params.uiExtensionType字段需要配置为[UIExtensionAbility](../../../application-models/uiextensionability-sys.md)的类型。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RecoverComponentType-UI_EXTENSION = 2--><!--Device-RecoverComponentType-UI_EXTENSION = 2-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。
