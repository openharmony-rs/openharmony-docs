# TabBarStyle

```TypeScript
declare enum TabBarStyle
```

枚举标签栏的显示样式。

**起始版本：** 26.0.1

<!--Device-unnamed-declare enum TabBarStyle--><!--Device-unnamed-declare enum TabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BOTTOM

```TypeScript
BOTTOM = 0
```

底部标签栏样式。标签栏的位置可以通过**Tabs***的**垂直**属性来调整。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-TabBarStyle-BOTTOM = 0--><!--Device-TabBarStyle-BOTTOM = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SIDEBAR

```TypeScript
SIDEBAR = 1
```

侧边栏样式。标签栏显示为侧边栏。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-TabBarStyle-SIDEBAR = 1--><!--Device-TabBarStyle-SIDEBAR = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SIDEBAR_ADAPTABLE

```TypeScript
SIDEBAR_ADAPTABLE = 2
```

可适应的侧边栏样式。标签栏可以在底部标签栏和侧边栏模式之间切换基于Tabs容器的大小。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-TabBarStyle-SIDEBAR_ADAPTABLE = 2--><!--Device-TabBarStyle-SIDEBAR_ADAPTABLE = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TOP

```TypeScript
TOP = 3
```

顶部浮动页签栏样式。页签栏始终以浮动形式显示在顶部。使用此样式时，**BarPosition**设置将被忽略。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-TabBarStyle-TOP = 3--><!--Device-TabBarStyle-TOP = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TOP_ADAPTABLE

```TypeScript
TOP_ADAPTABLE = 4
```

自适应的顶部浮动页签栏样式。页签栏的位置会自动切换到基于Tabs容器大小断点的顶部和底部浮动。使用此样式时，**BarPosition**设置将被忽略。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-TabBarStyle-TOP_ADAPTABLE = 4--><!--Device-TabBarStyle-TOP_ADAPTABLE = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
