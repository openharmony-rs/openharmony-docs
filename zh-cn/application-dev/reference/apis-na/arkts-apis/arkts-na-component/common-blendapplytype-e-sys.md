# BlendApplyType

Enum for BlendApplyType. Indicate how to apply specified blend mode to the view's content.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum BlendApplyType--><!--Device-unnamed-export declare enum BlendApplyType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## OFFSCREEN_WITH_BACKGROUND

```TypeScript
OFFSCREEN_WITH_BACKGROUND = 2
```

The content of the component and its child components are drawn on the offscreen canvas, and then blended with the existing content on the canvas. The offscreen canvas will copy background to initialize itself when created.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendApplyType-OFFSCREEN_WITH_BACKGROUND = 2--><!--Device-BlendApplyType-OFFSCREEN_WITH_BACKGROUND = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

