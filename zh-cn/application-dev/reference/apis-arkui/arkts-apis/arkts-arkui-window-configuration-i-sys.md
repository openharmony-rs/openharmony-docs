# Configuration

创建子窗口或系统窗口时的参数。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-window-interface Configuration--><!--Device-window-interface Configuration-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## defaultDensityEnabled

```TypeScript
defaultDensityEnabled?: boolean
```

是否使用系统默认Density，使用系统默认Density之后，窗口不会跟随系统显示大小变化重新布局。 当创建的系统窗口设置此参数为true时，表示当前窗口使用系统默认Density，且不会受到 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 和\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_设置的主窗口以及 [setDefaultDensityEnabled()]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_设置的本窗口的相关影响。 当创建的系统窗口设置此参数为false时，表示当前窗口不使用系统默认Density，且会受到 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_ 和\_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_设置的主窗口以及 [setDefaultDensityEnabled()]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_设置的本窗口的相关影响。 默认为false。

**类型：** boolean

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-Configuration-defaultDensityEnabled?: boolean--><!--Device-Configuration-defaultDensityEnabled?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## zIndex

```TypeScript
zIndex?: int
```

当前系统窗口的层级，仅在[WindowType]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_为TYPE\_DYNAMIC时生效。

**类型：** int

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-Configuration-zIndex?: int--><!--Device-Configuration-zIndex?: int-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

