# NavigationAnimatedTransition

```TypeScript
declare interface NavigationAnimatedTransition
```

Defines the custom transition animation protocol. You need to implement this protocol to define the redirection animation of the navigation route.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onTransitionEnd

```TypeScript
onTransitionEnd?: (success: boolean) => void
```

Callback invoked when the transition is complete.

**success**: whether the transition is successful.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| success | boolean | Yes |  |

## transition

```TypeScript
transition: (transitionProxy: NavigationTransitionProxy) => void
```

Callback for executing the custom transition animation.

**transitionProxy**: proxy for the custom transition animation.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transitionProxy | [NavigationTransitionProxy](arkts-arkui-navigation-comp-navigationtransitionproxy-i.md) | Yes |  |

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

## timeout

```TypeScript
timeout?: number
```

Animation timeout time.

Unit: ms

Value range: [0, +��)

Default value: no default value for interactive animations; 1000 ms for non-interactive animations.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
