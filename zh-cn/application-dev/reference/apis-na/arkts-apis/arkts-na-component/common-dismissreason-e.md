# DismissReason

关闭原因类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum DismissReason--><!--Device-unnamed-export declare enum DismissReason-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PRESS_BACK

```TypeScript
PRESS_BACK = 0
```

点击三键back、侧滑（左滑/右滑）、键盘ESC。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DismissReason-PRESS_BACK = 0--><!--Device-DismissReason-PRESS_BACK = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TOUCH_OUTSIDE

```TypeScript
TOUCH_OUTSIDE = 1
```

点击遮障层时。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DismissReason-TOUCH_OUTSIDE = 1--><!--Device-DismissReason-TOUCH_OUTSIDE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CLOSE_BUTTON

```TypeScript
CLOSE_BUTTON = 2
```

点击关闭按钮。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DismissReason-CLOSE_BUTTON = 2--><!--Device-DismissReason-CLOSE_BUTTON = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SLIDE_DOWN

```TypeScript
SLIDE_DOWN = 3
```

下拉关闭。 **说明：** 该接口仅支持在[半模态转场]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_中使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DismissReason-SLIDE_DOWN = 3--><!--Device-DismissReason-SLIDE_DOWN = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SLIDE

```TypeScript
SLIDE = 4
```

侧滑（左滑/右滑）关闭。默认表示向右滑动关闭，镜像场景表示向左滑动关闭，不支持选择向左或向右滑动。 **说明：** 该接口仅支持在[半模态转场]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_中使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DismissReason-SLIDE = 4--><!--Device-DismissReason-SLIDE = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

