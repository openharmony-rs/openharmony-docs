# ContextMenuAnimationOptions

```TypeScript
interface ContextMenuAnimationOptions
```

Defines the style for displaying a long-press preview.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hoverScale

```TypeScript
hoverScale?: AnimationRange<number>
```

In the custom preview (**preview** is of the CustomBuilder type) and menu displayed in long-press (**responseType** is set to **LongPress**) scenarios, **hoverScale** is used to set two parameters for the screenshot floating animation of the bound component: the start and end scale ratios relative to the original preview image. After **hoverScale** is set, the floating animation and preview image are switched with a transition effect.

**NOTE:** 

If the value is less than or equal to **0**, this parameter does not take effect.

This API does not take effect in [bindContextMenu&lt;sup&gt;12+&lt;/sup&gt;](arkts-arkui-common-comp-commonmethod-c.md#bindcontextmenu-1) scenarios.

This API does not take effect when **transition** is set.

If this API and the **scale** API are used at the same time, the start value of the **scale** API does not take effect.

To ensure the optimal experience, it is not recommended that the final preview image size be smaller than the size of the original component snapshot. The width and height of the preview animation are affected by the component snapshot and the custom preview size. Verify the display effect based on the actual use case.

**Type:** [AnimationRange](arkts-arkui-common-comp-animationrange-t.md)&lt;number&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hoverScaleInterruption

```TypeScript
hoverScaleInterruption?: boolean
```

Whether lifting the finger before triggering the drag effect allows preview menu pop-up cancellation in scenarios where **preview** is of the CustomBuilder type (custom preview image), **responseType** is set to **LongPress** (display is triggered by a long-press action), and **hoverScaleInterruption** is set to **true**. The options are **true** (yes) and **false** (no).

Default value: **false**

**NOTE:** 

If the **hoverScale** API is not set or the **transition** API is set, this parameter does not take effect. If the finger is lifted before the long-press duration is sufficient to trigger the drag effect, the **hoverScale** effect of the preview menu will revert, the preview menu will not pop up, and gesture events such as click bound to the original component can still be triggered. If the finger is lifted after the long-press duration is sufficient to trigger the drag effect, the preview menu will pop up properly, and gesture events such as click bound to the original component will no longer be triggered.

**Type:** boolean

**Default:** false

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale?: AnimationRange<number>
```

Relative scale ratio at the start and end of the animation compared to the original preview image.

Default value: **[0.95, 1.1]**

**NOTE:** 

The scale ratio must be set based on the specific use case. It is recommended that it be less than the width of the preview image or the maximum constraint of the layout.

**Type:** [AnimationRange](arkts-arkui-common-comp-animationrange-t.md)&lt;number&gt;

**Default:** 
- API version 11: [0.95, 1.1]

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition?: TransitionEffect
```

Transition effect for the entrance and exit of the menu.

**NOTE:** 

If the screen orientation is switched during the exit animation of a menu, the menu will avoid obstacles. Level-2 menus do not inherit custom animations. The level-2 menu can be clicked during the display process, but not during the execution of the exit animation.

For details, see [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md).

**Type:** [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
