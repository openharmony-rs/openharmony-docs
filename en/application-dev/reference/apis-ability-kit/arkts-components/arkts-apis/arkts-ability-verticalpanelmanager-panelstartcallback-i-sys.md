# PanelStartCallback (System API)

The callback of start vertical panel.

@typedef PanelStartCallback

**Since:** 20

**System capability:** SystemCapability.Ability.AppExtension.VerticalPanel

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { verticalPanelManager } from '@kit.AbilityKit';
```

## onError

```TypeScript
onError: OnErrorFn
```

Called when some error occurred except disconnected from UIAbility or UIExtensionAbility.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppExtension.VerticalPanel

**System API:** This is a system API.

## onResult

```TypeScript
onResult?: OnResultFn
```

Called when UIExtensionAbility terminate with result.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppExtension.VerticalPanel

**System API:** This is a system API.
