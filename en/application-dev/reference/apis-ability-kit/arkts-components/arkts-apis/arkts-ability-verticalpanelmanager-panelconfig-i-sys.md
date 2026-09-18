# PanelConfig (System API)

Indicates the panel config

@interface PanelConfig

**Since:** 20

**System capability:** SystemCapability.Ability.AppExtension.VerticalPanel

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { verticalPanelManager } from '@kit.AbilityKit';
```

## sourceAppInfo

```TypeScript
sourceAppInfo: Record<string, string>
```

Indicates the info about source app

<p>**NOTE:** <br>1. The values of the following keys are assigned by the system. Manual settings do not take effect, since the system automatically changes the values to the actual values during data transfer. -SOURCE_APP_BUNDLE_NAME: bundle name of the caller. The value is a string. -SOURCE_APP_MODULE_NAME: module name of the caller. The value is a string. -SOURCE_APP_ABILITY_NAME: ability name of the caller. The value is a string. -SOURCE_APP_WINDOW_ID: the window ID of the caller. The value is a string. -SOURCE_APP_SCREEN_MODE: the screen mode of the split screen. The value is a string. The value is "1".

**Type:** Record&lt;string, string&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppExtension.VerticalPanel

**System API:** This is a system API.

## type

```TypeScript
type: VerticalType
```

The type of vertical domain

**Type:** [VerticalType](arkts-ability-verticalpanelmanager-verticaltype-e-sys.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppExtension.VerticalPanel

**System API:** This is a system API.
