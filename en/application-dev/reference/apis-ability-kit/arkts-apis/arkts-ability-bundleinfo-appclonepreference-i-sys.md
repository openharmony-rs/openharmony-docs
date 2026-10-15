# AppClonePreference (System API)

```TypeScript
export interface AppClonePreference
```

App clone preference, used to configure the selection policy between the main app and the clone app at app startup.

**Since:** 26.0.0

<!--Device-unnamed-export interface AppClonePreference--><!--Device-unnamed-export interface AppClonePreference-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## appIndex

```TypeScript
appIndex?: number
```

Index of the app clone.<br>This parameter is mandatory when **mode** is set to **AppClonePreferenceMode.CLONE_APP**, and is used to specify a specific clone app. The value is an integer ranging from 1 to 5 (the system supports a maximum of 5 clones).

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AppClonePreference-appIndex?: int--><!--Device-AppClonePreference-appIndex?: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## mode

```TypeScript
mode: bundleManager.AppClonePreferenceMode
```

Mode of the app clone preference settings.

**Type:** [bundleManager.AppClonePreferenceMode](arkts-ability-bundlemanager-appclonepreferencemode-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AppClonePreference-mode: bundleManager.AppClonePreferenceMode--><!--Device-AppClonePreference-mode: bundleManager.AppClonePreferenceMode-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
