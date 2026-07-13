# WindowStageEventType

WindowStage生命周期状态枚举。

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## SHOWN

```TypeScript
SHOWN = 1
```

前台状态，例如点击应用图标启动，无论是首次启动还是从后台启动均会触发。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## ACTIVE

```TypeScript
ACTIVE = 2
```

获焦状态，例如应用窗口处理点击事件后的状态、应用启动后的状态。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## INACTIVE

```TypeScript
INACTIVE = 3
```

失焦状态，例如打开新应用或点击其他窗口后，原获焦窗口的状态。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## HIDDEN

```TypeScript
HIDDEN = 4
```

后台状态，例如应用上滑退出、应用窗口关闭。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## RESUMED

```TypeScript
RESUMED = 5
```

前台可交互状态，例如打开应用后，应用处于前台，且可以与用户交互的状态。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## PAUSED

```TypeScript
PAUSED = 6
```

前台不可交互状态，例如应用在前台时，进入多任务界面，应用依然处于前台但不可以与用户交互的状态。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

