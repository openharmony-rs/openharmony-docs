# BlendApplyType

Enum for BlendApplyType. Indicate how to apply specified blend mode to the view's content.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare enum BlendApplyType--><!--Device-unnamed-export declare enum BlendApplyType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FAST

```TypeScript
FAST = 0
```

The content of the view is blended in sequence on the target image.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendApplyType-FAST = 0--><!--Device-BlendApplyType-FAST = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## OFFSCREEN

```TypeScript
OFFSCREEN = 1
```

The content of the component and its child components are drawn on the offscreen canvas, and then blended with the existing content on the canvas.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendApplyType-OFFSCREEN = 1--><!--Device-BlendApplyType-OFFSCREEN = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

