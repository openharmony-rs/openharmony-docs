# AccessibilityCustomAction

```TypeScript
declare interface AccessibilityCustomAction
```

Custom accessibility action API.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onAction

```TypeScript
onAction: VoidCallback
```

Callback for handling the custom action.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: ResourceStr
```

Name of the custom action, used to identify and bind the action callback.

**Note:** <br>The text length of the name must be within 128 bytes. The excess part will be truncated.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
