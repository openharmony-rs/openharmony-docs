# RecoverComponentType (System API)

```TypeScript
export enum RecoverComponentType
```

Enumerates the types of abilities during recovery.

**Since:** 26.1.0

<!--Device-appControl-export enum RecoverComponentType--><!--Device-appControl-export enum RecoverComponentType-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## EXTENSION

```TypeScript
EXTENSION = 1
```

ExtensionAbility component. Only [ExtensionAbility](../../../quick-start/module-configuration-file.md#extensionabilities) components of the service type is supported.

The ExtensionAbility component is determined by bundleName, moduleName, and abilityName in want.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RecoverComponentType-EXTENSION = 1--><!--Device-RecoverComponentType-EXTENSION = 1-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## UI_EXTENSION

```TypeScript
UI_EXTENSION = 2
```

UIExtensionAbility component.

The UIExtensionAbility is determined by bundleName, moduleName, and abilityName in want, and the **ability.want.params.uiExtensionType** field in **want.parameters** is set to [UIExtensionAbility](../../../application-models/uiextensionability-sys.md).

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RecoverComponentType-UI_EXTENSION = 2--><!--Device-RecoverComponentType-UI_EXTENSION = 2-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.
