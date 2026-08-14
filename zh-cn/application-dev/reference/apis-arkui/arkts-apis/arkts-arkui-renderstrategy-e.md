# RenderStrategy

RenderStrategy 的枚举。 定义图形渲染策略。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

<!--Device-unnamed-declare enum RenderStrategy--><!--Device-unnamed-declare enum RenderStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FAST

```TypeScript
FAST = 0
```

当前组件及其子组件将直接绘制到画布上，并应用圆角效果。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-RenderStrategy-FAST = 0--><!--Device-RenderStrategy-FAST = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## OFFSCREEN

```TypeScript
OFFSCREEN = 1
```

当前组件及其子组件会先被画到一个离屏画布上， 然后进行一些图形渲染操作，最后绘制到主画布上。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-RenderStrategy-OFFSCREEN = 1--><!--Device-RenderStrategy-OFFSCREEN = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

