# FloatViewState

标准悬浮窗状态的枚举。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Window.SessionManager

## STARTED

```TypeScript
STARTED = 1
```

标准悬浮窗已启动并显示。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

## HIDDEN

```TypeScript
HIDDEN = 2
```

标准悬浮窗已隐藏。上滑进入多任务界面时触发、使用
[setFloatViewVisibilityInApp](arkts-arkui-floatviewcontroller-i.md#setfloatviewvisibilityinapp-1)接口设置了应用在前台时隐藏标准悬浮窗且
应用处于前台时触发。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

## STOPPED

```TypeScript
STOPPED = 3
```

标准悬浮窗已停止。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

## IN_SIDEBAR

```TypeScript
IN_SIDEBAR = 4
```

标准悬浮窗在侧边栏中。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

## IN_FLOATING_BALL

```TypeScript
IN_FLOATING_BALL = 5
```

标准悬浮窗切换为闪控球。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

## ERROR

```TypeScript
ERROR = 6
```

标准悬浮窗发生异常。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

