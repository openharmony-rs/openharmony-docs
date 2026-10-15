# WindowPosition

```TypeScript
enum WindowPosition
```

主窗口z序调整的目标位置枚举。

**起始版本：** 26.0.1

<!--Device-window-enum WindowPosition--><!--Device-window-enum WindowPosition-End-->

**系统能力：** SystemCapability.Window.SessionManager

## BOTTOM

```TypeScript
BOTTOM = -1
```

将主窗口置于所有应用主窗口的底部，仅单次调整生效。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowPosition-BOTTOM = -1--><!--Device-WindowPosition-BOTTOM = -1-End-->

**系统能力：** SystemCapability.Window.SessionManager

## NOT_TOPMOST

```TypeScript
NOT_TOPMOST = -3
```

非置顶，普通状态。作为独立操作时用于取消主窗口的全局置顶状态，取消全局置顶状态需要ohos.permission.WINDOW_TOPMOST权限。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowPosition-NOT_TOPMOST = -3--><!--Device-WindowPosition-NOT_TOPMOST = -3-End-->

**系统能力：** SystemCapability.Window.SessionManager

## TOP

```TypeScript
TOP = 0
```

将主窗口置于所有应用主窗口的顶部，仅单次调整生效。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowPosition-TOP = 0--><!--Device-WindowPosition-TOP = 0-End-->

**系统能力：** SystemCapability.Window.SessionManager

## TOPMOST

```TypeScript
TOPMOST = -2
```

全局置顶。设置该值时需要ohos.permission.WINDOW_TOPMOST权限。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowPosition-TOPMOST = -2--><!--Device-WindowPosition-TOPMOST = -2-End-->

**系统能力：** SystemCapability.Window.SessionManager
