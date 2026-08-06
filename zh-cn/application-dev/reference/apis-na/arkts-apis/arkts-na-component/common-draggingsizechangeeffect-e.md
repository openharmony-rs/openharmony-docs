# DraggingSizeChangeEffect

Define drag start animation effect from drag preview to the handle drag image

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum DraggingSizeChangeEffect--><!--Device-unnamed-export declare enum DraggingSizeChangeEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

Default effect, no transition.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DraggingSizeChangeEffect-DEFAULT = 0--><!--Device-DraggingSizeChangeEffect-DEFAULT = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SIZE_TRANSITION

```TypeScript
SIZE_TRANSITION = 1
```

Only scaled transition, this parameter take effect when PREVIEW\_MODE is not DISABLE\_SCALE.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DraggingSizeChangeEffect-SIZE_TRANSITION = 1--><!--Device-DraggingSizeChangeEffect-SIZE_TRANSITION = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SIZE_CONTENT_TRANSITION

```TypeScript
SIZE_CONTENT_TRANSITION = 2
```

Scaled and content transition together, this size transition take effect when PREVIEW\_MODE is not DISABLE\_SCALE.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DraggingSizeChangeEffect-SIZE_CONTENT_TRANSITION = 2--><!--Device-DraggingSizeChangeEffect-SIZE_CONTENT_TRANSITION = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

