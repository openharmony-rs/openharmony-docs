# FocusMovement

Sets the target component for focus movement based on key presses. If it is not specified, the default focus movement logic applies.

> **NOTE:** 
> 
> Directly using **focusControl** can lead to the issue of
> [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain the
> [UIContext](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) object using the **getUIContext()** API and then obtain the
> **focusControl** bound to the instance using the
> [getFocusController](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#getfocuscontroller) API.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backward

```TypeScript
backward?: string
```

ID of the component to focus on when **Shift+Tab** is pressed.

The default value resets **backward** to empty.

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## down

```TypeScript
down?: string
```

ID of the component to focus on when the down arrow key is pressed.

The default value resets **down** to empty.

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## forward

```TypeScript
forward?: string
```

ID of the component to focus on when the **Tab** key is pressed.

The default value resets **forward** to empty.

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## left

```TypeScript
left?: string
```

ID of the component to focus on when the left arrow key is pressed.

The default value resets **left** to empty.

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## right

```TypeScript
right?: string
```

ID of the component to focus on when the right arrow key is pressed.

The default value resets **right** to empty.

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## up

```TypeScript
up?: string
```

ID of the component to focus on when the up arrow key is pressed.

The default value resets **up** to empty.

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
