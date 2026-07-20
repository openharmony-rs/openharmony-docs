# EmbeddedOptions

该接口用于在构造时设置EmbeddedComponentAttribute的选项。

**起始版本：** 26.0.0

<!--Device-unnamed-declare interface EmbeddedOptions--><!--Device-unnamed-declare interface EmbeddedOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## areaChangePlaceholder

```TypeScript
areaChangePlaceholder?: Record<string, ComponentContent>
```

设置区域变化占位符。如果设置了区域变化占位ComponentContent，在EmbeddedComponent尺寸变化完成之前显示占位节点。

**类型：** Record&lt;string, ComponentContent&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EmbeddedOptions-areaChangePlaceholder?: Record<string, ComponentContent>--><!--Device-EmbeddedOptions-areaChangePlaceholder?: Record<string, ComponentContent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dpiFollowStrategy

```TypeScript
dpiFollowStrategy?: EmbeddedDpiFollowStrategy
```

设置EmbeddedComponent内容的DPI跟随策略。

**类型：** EmbeddedDpiFollowStrategy

**默认值：** EmbeddedDpiFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_DPI

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EmbeddedOptions-dpiFollowStrategy?: EmbeddedDpiFollowStrategy--><!--Device-EmbeddedOptions-dpiFollowStrategy?: EmbeddedDpiFollowStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ComponentContent
```

设置占位符。如果设置了占位ComponentContent，在连接未建立时显示占位节点。

**类型：** ComponentContent

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EmbeddedOptions-placeholder?: ComponentContent--><!--Device-EmbeddedOptions-placeholder?: ComponentContent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowModeFollowStrategy

```TypeScript
windowModeFollowStrategy?: EmbeddedWindowModeFollowStrategy
```

设置EmbeddedComponent内容的窗口模式跟随策略。

**类型：** EmbeddedWindowModeFollowStrategy

**默认值：** EmbeddedWindowModeFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EmbeddedOptions-windowModeFollowStrategy?: EmbeddedWindowModeFollowStrategy--><!--Device-EmbeddedOptions-windowModeFollowStrategy?: EmbeddedWindowModeFollowStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

