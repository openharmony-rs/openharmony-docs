# RouterPageState

routerPage生命周期触发时对应的状态。RouterPageState用于[RouterPageInfo](arkts-arkui-routerpageinfo-c.md)中，作为
[routerPageUpdate](uiObserver.on(type: 'routerPageUpdate', context: UIAbilityContext | UIContext, callback:
Callback<RouterPageInfo>))无感监听的返回值。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ABOUT_TO_APPEAR

```TypeScript
ABOUT_TO_APPEAR = 0
```

page即将显示。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ABOUT_TO_DISAPPEAR

```TypeScript
ABOUT_TO_DISAPPEAR = 1
```

page即将销毁。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ON_PAGE_SHOW

```TypeScript
ON_PAGE_SHOW = 2
```

page显示。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ON_PAGE_HIDE

```TypeScript
ON_PAGE_HIDE = 3
```

page隐藏。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ON_BACK_PRESS

```TypeScript
ON_BACK_PRESS = 4
```

page返回时。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

