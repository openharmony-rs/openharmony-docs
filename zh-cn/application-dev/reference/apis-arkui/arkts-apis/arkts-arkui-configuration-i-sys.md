# Configuration

创建子窗口或系统窗口时的参数。

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## defaultDensityEnabled

```TypeScript
defaultDensityEnabled?: boolean
```

是否使用系统默认Density，使用系统默认Density之后，窗口不会跟随系统显示大小变化重新布局。

当创建的系统窗口设置此参数为true时，表示当前窗口使用系统默认Density，且不会受到
[setDefaultDensityEnabled()](../../../../reference/apis-arkui/arkts-apis-window-WindowStage.md#setdefaultdensityenabled12)
和[setCustomDensity()](../../../../reference/apis-arkui/arkts-apis-window-WindowStage.md#setcustomdensity15)设置的主窗口以及
[setDefaultDensityEnabled()](arkts-arkui-window-i-sys.md#setdefaultdensityenabled-1)设置的本窗口的相关影响。

当创建的系统窗口设置此参数为false时，表示当前窗口不使用系统默认Density，且会受到
[setDefaultDensityEnabled()](../../../../reference/apis-arkui/arkts-apis-window-WindowStage.md#setdefaultdensityenabled12)
和[setCustomDensity()](../../../../reference/apis-arkui/arkts-apis-window-WindowStage.md#setcustomdensity15)设置的主窗口以及
[setDefaultDensityEnabled()](arkts-arkui-window-i-sys.md#setdefaultdensityenabled-1)设置的本窗口的相关影响。

默认为false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## zIndex

```TypeScript
zIndex?: number
```

当前系统窗口的层级，仅在[WindowType](arkts-arkui-windowtype-e.md)为TYPE_DYNAMIC时生效。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

