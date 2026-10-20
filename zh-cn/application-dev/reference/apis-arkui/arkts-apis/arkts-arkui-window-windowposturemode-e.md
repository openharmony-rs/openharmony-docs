# WindowPostureMode

```TypeScript
enum WindowPostureMode
```

窗口姿态模式枚举。

**起始版本：** 26.0.0

<!--Device-window-enum WindowPostureMode--><!--Device-window-enum WindowPostureMode-End-->

**系统能力：** SystemCapability.Window.SessionManager

## DESKTOP_MODE

```TypeScript
DESKTOP_MODE = 0
```

桌面模式。当满足以下条件时处于桌面模式：
1. 当前设备折叠状态为半折叠状态（FoldStatus.FOLD_STATUS_HALF_FOLDED）；
2. 窗口所在屏幕通过getLiveCreaseRegion()获取的creaseRects宽度大于高度；
3. 窗口模式为全屏模式（WindowStatusType.FULL_SCREEN）或最大化模式（WindowStatusType.MAXIMIZE）。
4. 屏幕折痕区域位于窗口显示区域内。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowPostureMode-DESKTOP_MODE = 0--><!--Device-WindowPostureMode-DESKTOP_MODE = 0-End-->

**系统能力：** SystemCapability.Window.SessionManager
