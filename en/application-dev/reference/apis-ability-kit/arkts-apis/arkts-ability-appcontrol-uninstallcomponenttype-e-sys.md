# UninstallComponentType (System API)

Enumerates the types of abilities during uninstallation.

**Since:** 15

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## EXTENSION

```TypeScript
EXTENSION = 1
```

ExtensionAbility component. Only [ExtensionAbility](../../../quick-start/module-configuration-file.md#extensionabilities) components of the service type is supported.

The ExtensionAbility component is determined by bundleName, moduleName, and abilityName in want.

**Since:** 15

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## UI_EXTENSION

```TypeScript
UI_EXTENSION = 2
```

UIExtensionAbility component.

The UIExtensionAbility is determined by bundleName, moduleName, and abilityName in want, and the **ability.want.params.uiExtensionType** field in **want.parameters** is set to [UIExtensionAbility](../../../application-models/uiextensionability-sys.md).

**Since:** 22

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.
