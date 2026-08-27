# BreakpointsReference

设置栅格容器组件的断点参照物。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## WindowSize

```TypeScript
WindowSize = 0
```

以窗口为参照。断点计算基于应用窗口尺寸，适用于需要根据窗口整体大小变化进行响应式布局的场景。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ComponentSize

```TypeScript
ComponentSize = 1
```

以容器为参照。断点计算基于GridRow组件自身尺寸，适用于需要根据组件容器尺寸变化进行响应式布局的场景，例如GridRow嵌套在其他容器中时。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
