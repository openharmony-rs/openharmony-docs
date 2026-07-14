# WindowStatusType

窗口模式枚举。

**起始版本：** 11

**系统能力：** SystemCapability.Window.SessionManager

## UNDEFINED

```TypeScript
UNDEFINED = 0
```

表示APP未定义窗口模式。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

## FULL_SCREEN

```TypeScript
FULL_SCREEN = 1
```

表示APP全屏模式。

[自由窗口](../../../../windowmanager/window-terminology.md#自由窗口)状态下，窗口铺满整个屏幕，默认无dock栏、标题栏和状态栏显示。

可通过[maximize()](arkts-arkui-window-i.md#maximize-1)和
[setTitleAndDockHoverShown()](arkts-arkui-window-i.md#settitleanddockhovershown-1)配置，当hover到热区时是否显示标题栏和
dock栏。

当maximize()和setTitleAndDockHoverShown()接口都调用时，以最后调用设置的效果为准。

非[自由窗口](../../../../windowmanager/window-terminology.md#自由窗口)状态下，窗口铺满整个屏幕，无标题栏和dock栏显示。可通过
[setSpecificSystemBarEnabled()](arkts-arkui-window-i.md#setspecificsystembarenabled-1)配置是否显示状态栏。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

## MAXIMIZE

```TypeScript
MAXIMIZE = 2
```

表示APP窗口最大化模式，[自由窗口](../../../../windowmanager/window-terminology.md#自由窗口)状态下，窗口铺满整个屏幕，不需要hover就可以显示dock栏、状态栏和标题栏。非
[自由窗口](../../../../windowmanager/window-terminology.md#自由窗口)状态下，不存在该状态。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

## MINIMIZE

```TypeScript
MINIMIZE = 3
```

表示APP窗口最小化模式。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

## FLOATING

```TypeScript
FLOATING = 4
```

表示APP自由悬浮形式窗口模式。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

## SPLIT_SCREEN

```TypeScript
SPLIT_SCREEN = 5
```

表示APP分屏模式。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

