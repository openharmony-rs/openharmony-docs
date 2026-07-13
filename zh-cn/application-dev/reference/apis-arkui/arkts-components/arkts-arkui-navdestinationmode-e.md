# NavDestinationMode

NavDestination类型。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## STANDARD

```TypeScript
STANDARD = 0
```

标准模式的NavDestination。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DIALOG

```TypeScript
DIALOG = 1
```

默认透明，进出路由栈不影响下层NavDestination的可见性（onShown、onHidden等生命周期），只会触发onActive、onInactive这两个生命周期。

API version 13之前，默认无系统转场动画。从API version 13开始，支持系统转场动画。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

