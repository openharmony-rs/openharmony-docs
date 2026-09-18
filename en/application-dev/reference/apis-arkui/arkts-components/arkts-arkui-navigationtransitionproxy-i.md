# NavigationTransitionProxy

Implements a custom transition animation proxy.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cancelTransition

```TypeScript
cancelTransition?(): void
```

Cancels this interactive transition animation, restoring the routing stack to its state before page redirection. (Non-interactive transition animations cannot be canceled.)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## finishTransition

```TypeScript
finishTransition(): void
```

Finishes this custom transition animation. This API must be manually called to end the animation. Otherwise, the system ends the animation when the timeout expires.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## updateTransition

```TypeScript
updateTransition?(progress: number): void
```

Updates the progress of this interactive transition animation. (Non-interactive animations do not support setting the animation progress).

> **NOTE:** 
> 
> You are not advised to use stack operations in aboutToAppear, as the
> page has not yet finished building at this stage, which may lead to issues such as white screens or navigation
> failures.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| progress | number | Yes | Progress percentage of the interactive transition animation. Value range: [0, 1]. |

## from

```TypeScript
from: NavContentInfo
```

Information about the exit page.

**Type:** [NavContentInfo](arkts-arkui-navcontentinfo-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isInteractive

```TypeScript
isInteractive?: boolean
```

Whether the transition animation is interactive.

**true**: yes; **false**: no

Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## to

```TypeScript
to: NavContentInfo
```

Information about the enter page.

**Type:** [NavContentInfo](arkts-arkui-navcontentinfo-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
