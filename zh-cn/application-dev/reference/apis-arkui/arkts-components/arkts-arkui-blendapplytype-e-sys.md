# BlendApplyType

指示如何将指定的混合模式应用于视图的内容。

**起始版本：** 12

<!--Device-unnamed-declare enum BlendApplyType--><!--Device-unnamed-declare enum BlendApplyType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## OFFSCREEN_WITH_BACKGROUND

```TypeScript
OFFSCREEN_WITH_BACKGROUND = 2
```

创建离屏画布时，先拷贝一份背景初始化画布，再将此组件和子组件内容绘制到离屏画布上，然后整体进行混合。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendApplyType-OFFSCREEN_WITH_BACKGROUND = 2--><!--Device-BlendApplyType-OFFSCREEN_WITH_BACKGROUND = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

