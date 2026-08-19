# NavDestinationMode

NavDestination类型。

**起始版本：** 11

<!--Device-unnamed-declare enum NavDestinationMode--><!--Device-unnamed-declare enum NavDestinationMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## STANDARD

```TypeScript
STANDARD = 0
```

标准模式的NavDestination，适合常规的内容页面场景，如列表详情页、设置页面、表单页面等。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationMode-STANDARD = 0--><!--Device-NavDestinationMode-STANDARD = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DIALOG

```TypeScript
DIALOG = 1
```

默认透明。进出路由栈不影响下层NavDestination的可见性（onShown、onHidden等生命周期），只触发onActive、onInactive生命周期。 适合需要透明背景或悬浮效果的场景，如弹窗式页面、浮层提示、操作确认对话框等。 API version 13之前，默认无系统转场动画。从API version 13开始，支持系统转场动画。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationMode-DIALOG = 1--><!--Device-NavDestinationMode-DIALOG = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

