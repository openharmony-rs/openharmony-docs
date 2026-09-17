# ContentCoverOptions

Inherited from [BindOptions](arkts-arkui-bindoptions-i.md).

Provides content options of the modal.

**Inheritance/Implementation:** ContentCoverOptions extends [BindOptions](arkts-arkui-bindoptions-i.md)

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableSafeArea

```TypeScript
enableSafeArea?: boolean
```

Whether the full-screen modal adapts to the safe area. **true** indicates the full-screen modal adapts to the safe area, restricting content within the safe area and avoiding the navigation and status bars. **false** indicates no processing is applied, maintaining the same style as before. The default value is **false**.

**Type:** boolean

**Default:** false

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## modalTransition

```TypeScript
modalTransition?: ModalTransition
```

System transition mode of the modal.

Default value: **ModalTransition.DEFAULT**.

**NOTE:** 

This property has no effect when it is set together with **transition**.

**Type:** [ModalTransition](arkts-arkui-modaltransition-e.md)

**Default:** ModalTransition.DEFAULT

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDismiss

```TypeScript
onWillDismiss?: Callback<DismissContentCoverAction>
```

Callback invoked to prevent a user attempt to dismiss the modal.

**NOTE:** 

After this callback is registered, touching the back button does not immediately dismiss the modal. You can use the **reason** parameter to determine the type of operation that triggers the dismiss and decide whether to dismiss the modal based on the reason. Nesting **onWillDismiss** callbacks is not allowed.

**Type:** [Callback](arkts-arkui-callback-i.md)&lt;[DismissContentCoverAction](arkts-arkui-dismisscontentcoveraction-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition?: TransitionEffect
```

Custom transition mode of the modal.

**Type:** [TransitionEffect](arkts-arkui-transitioneffect-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
