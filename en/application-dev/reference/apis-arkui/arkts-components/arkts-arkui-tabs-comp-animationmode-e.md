# AnimationMode

```TypeScript
declare enum AnimationMode
```

Enumerates the animation forms for switching **TabContent** when a [TabBar](arkts-arkui-tabcontent-comp-attribute.md#tabbar1) tab is tapped.

**Since:** 12

<!--Device-unnamed-declare enum AnimationMode--><!--Device-unnamed-declare enum AnimationMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ACTION_FIRST

```TypeScript
ACTION_FIRST = 1
```

Starts the switching animation first, and then loads the content of the target page. For this to take effect, both the height and width of **Tabs** must not be set to **auto**. This is suitable for scenarios where the user operation must be responded to immediately and the animation starts quickly. It is recommended for scenarios where content loads slowly but quick visual feedback is desired.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AnimationMode-ACTION_FIRST = 1--><!--Device-AnimationMode-ACTION_FIRST = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ACTION_FIRST_WITH_JUMP

```TypeScript
ACTION_FIRST_WITH_JUMP = 4
```

Jumps to the vicinity of the target page without animation first, then jumps to the target page with animation, and finally loads the content of the target page. For this to take effect, both the **height** and **width** of **Tabs** must not be set to **auto**.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-AnimationMode-ACTION_FIRST_WITH_JUMP = 4--><!--Device-AnimationMode-ACTION_FIRST_WITH_JUMP = 4-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CONTENT_FIRST

```TypeScript
CONTENT_FIRST = 0
```

Loads the content of the target page first, and then starts the switching animation. This is suitable for scenarios where the content must be loaded before the animation is displayed, avoiding blank content during the animation. It is recommended for scenarios where content loads quickly and a smooth transition is required.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AnimationMode-CONTENT_FIRST = 0--><!--Device-AnimationMode-CONTENT_FIRST = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CONTENT_FIRST_WITH_JUMP

```TypeScript
CONTENT_FIRST_WITH_JUMP = 3
```

Loads the content of the target page first, then jumps to the vicinity of the target page without animation, and finally jumps to the target page with animation.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-AnimationMode-CONTENT_FIRST_WITH_JUMP = 3--><!--Device-AnimationMode-CONTENT_FIRST_WITH_JUMP = 3-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NO_ANIMATION

```TypeScript
NO_ANIMATION = 2
```

Disables the default animation. This enum value does not take effect when the [changeIndex](arkts-arkui-tabs-comp-tabscontroller-c.md#changeindex) API of **TabsController** is called to switch **TabContent**.

You can set [animationDuration](arkts-arkui-tabs-comp-attribute.md#animationduration) to **0** to switch without animation when calling the **changeIndex** API of **TabsController**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AnimationMode-NO_ANIMATION = 2--><!--Device-AnimationMode-NO_ANIMATION = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
