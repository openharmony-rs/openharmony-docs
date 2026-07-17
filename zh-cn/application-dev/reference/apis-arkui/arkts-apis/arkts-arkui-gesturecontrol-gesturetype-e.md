# GestureType

定义手势类型。

**起始版本：** 11

<!--Device-GestureControl-enum GestureType--><!--Device-GestureControl-enum GestureType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TAP_GESTURE

```TypeScript
TAP_GESTURE = 0
```

点击手势。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureType-TAP_GESTURE = 0--><!--Device-GestureType-TAP_GESTURE = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LONG_PRESS_GESTURE

```TypeScript
LONG_PRESS_GESTURE = 1
```

长按手势。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureType-LONG_PRESS_GESTURE = 1--><!--Device-GestureType-LONG_PRESS_GESTURE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PAN_GESTURE

```TypeScript
PAN_GESTURE = 2
```

滑动手势。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureType-PAN_GESTURE = 2--><!--Device-GestureType-PAN_GESTURE = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PINCH_GESTURE

```TypeScript
PINCH_GESTURE = 3
```

捏合手势。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureType-PINCH_GESTURE = 3--><!--Device-GestureType-PINCH_GESTURE = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SWIPE_GESTURE

```TypeScript
SWIPE_GESTURE = 4
```

快滑手势。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureType-SWIPE_GESTURE = 4--><!--Device-GestureType-SWIPE_GESTURE = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ROTATION_GESTURE

```TypeScript
ROTATION_GESTURE = 5
```

旋转手势。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureType-ROTATION_GESTURE = 5--><!--Device-GestureType-ROTATION_GESTURE = 5-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DRAG

```TypeScript
DRAG = 6
```

拖拽。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureType-DRAG = 6--><!--Device-GestureType-DRAG = 6-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CLICK

```TypeScript
CLICK = 7
```

点击。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureType-CLICK = 7--><!--Device-GestureType-CLICK = 7-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BOX_SELECT_GESTURE

```TypeScript
BOX_SELECT_GESTURE = 8
```

滚动类容器鼠标框选手势，是一种特殊的滑动手势，用于在滚动容器中通过鼠标拖拽创建选择区域，批量选择多个元素。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-GestureType-BOX_SELECT_GESTURE = 8--><!--Device-GestureType-BOX_SELECT_GESTURE = 8-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## WEB_SCROLL_GESTURE

```TypeScript
WEB_SCROLL_GESTURE = 9
```

Web组件滚动手势，是一种特殊的滑动手势，用于控制Web组件内的滚动行为。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-GestureType-WEB_SCROLL_GESTURE = 9--><!--Device-GestureType-WEB_SCROLL_GESTURE = 9-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TEXT_FIELD_SELECT_GESTURE

```TypeScript
TEXT_FIELD_SELECT_GESTURE = 10
```

文本选择手势，是一种特殊的滑动手势，用于在输入框组件中通过拖拽选择文本内容。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-GestureType-TEXT_FIELD_SELECT_GESTURE = 10--><!--Device-GestureType-TEXT_FIELD_SELECT_GESTURE = 10-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CONTEXT_MENU_HOVER_GESTURE

```TypeScript
CONTEXT_MENU_HOVER_GESTURE = 11
```

上下文菜单悬停手势是一种特殊的长按手势，用于在长按过程中触发菜单的hoverScale动画效果（需启用[ContextMenuAnimationOptions](../arkts-components/arkts-arkui-common-contextmenuanimationoptions-i.md)的hoverScaleInterruption属性以支持该行为）。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-GestureType-CONTEXT_MENU_HOVER_GESTURE = 11--><!--Device-GestureType-CONTEXT_MENU_HOVER_GESTURE = 11-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

