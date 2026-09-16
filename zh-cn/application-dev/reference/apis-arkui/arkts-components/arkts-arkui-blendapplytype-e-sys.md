# BlendApplyType

标识如何将指定的混合模式应用于视图的内容。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## OFFSCREEN_WITH_BACKGROUND

```TypeScript
OFFSCREEN_WITH_BACKGROUND = 2
```

创建离屏画布时，先拷贝一份带有背景的画布作为初始化底色（BlendApplyType.OFFSCREEN类型的画布初始为透明背景），再将此组件和子组件内容绘制到离屏画布上，然后整体进行混合。两者在其他功能特性上与BlendApplyType.OFFSCREEN保持一致。

**系统接口：** 此接口为系统接口。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
