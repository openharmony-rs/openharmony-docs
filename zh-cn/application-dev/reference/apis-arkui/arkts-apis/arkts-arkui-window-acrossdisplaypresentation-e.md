# AcrossDisplayPresentation

在可折叠的2in1设备的半折叠状态下，最大化窗口时用于控制瀑布流模式切换策略的枚举。

**起始版本：** 26.0.0

<!--Device-window-enum AcrossDisplayPresentation--><!--Device-window-enum AcrossDisplayPresentation-End-->

**系统能力：** SystemCapability.Window.SessionManager

## FOLLOW_ACROSS_DISPLAY_SETTING

```TypeScript
FOLLOW_ACROSS_DISPLAY_SETTING = 0
```

表示跟随当前的最大化瀑布流模式切换的策略。如果未设置跨屏显示，则应用默认的系统策略：在设备对折状态下，窗口进入单屏最大化（即最大化时，窗口只显示在屏幕的上半部分或下半部分）。在展开状态下，窗口最大化，并在折回为对折时保持瀑布模式。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AcrossDisplayPresentation-FOLLOW_ACROSS_DISPLAY_SETTING = 0--><!--Device-AcrossDisplayPresentation-FOLLOW_ACROSS_DISPLAY_SETTING = 0-End-->

**系统能力：** SystemCapability.Window.SessionManager

## ENTER_ACROSS_DISPLAY_MODE

```TypeScript
ENTER_ACROSS_DISPLAY_MODE = 1
```

在设备的半折状态下，窗口可以直接进入瀑布模式。在展开状态下，窗口最大化，并在折回一半时保持瀑布模式。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AcrossDisplayPresentation-ENTER_ACROSS_DISPLAY_MODE = 1--><!--Device-AcrossDisplayPresentation-ENTER_ACROSS_DISPLAY_MODE = 1-End-->

**系统能力：** SystemCapability.Window.SessionManager

## EXIT_ACROSS_DISPLAY_MODE

```TypeScript
EXIT_ACROSS_DISPLAY_MODE = 2
```

在设备对折状态下，窗口退出瀑布模式，进入单屏最大化（即最大化时，窗口仅显示在屏幕的上半部分或下半部分）。在展开状态下，窗口最大化，重新进入半折后将退出瀑布模式。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AcrossDisplayPresentation-EXIT_ACROSS_DISPLAY_MODE = 2--><!--Device-AcrossDisplayPresentation-EXIT_ACROSS_DISPLAY_MODE = 2-End-->

**系统能力：** SystemCapability.Window.SessionManager

