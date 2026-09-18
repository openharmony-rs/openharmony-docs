# AppClonePreference (System API)

Defines the application clone preference configuration.

**Since:** 26.0.0

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## appIndex

```TypeScript
appIndex?: number
```

Index of the application clone. This value is valid only when the mode is CLONE_APP. The value ranges from 1 to 5 (maximum 5 clones are supported). The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## mode

```TypeScript
mode: bundleManager.AppClonePreferenceMode
```

Preference mode for application cloning.

**Type:** [bundleManager.AppClonePreferenceMode](arkts-ability-bundlemanager-appclonepreferencemode-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
