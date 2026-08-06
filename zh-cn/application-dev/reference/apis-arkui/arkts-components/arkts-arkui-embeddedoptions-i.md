# EmbeddedOptions

用于在EmbeddedComponent创建时传递可选的构造参数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

<!--Device-unnamed-declare interface EmbeddedOptions--><!--Device-unnamed-declare interface EmbeddedOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## areaChangePlaceholder

```TypeScript
areaChangePlaceholder?: Record<string, ComponentContent>
```

设置尺寸变化占位符，在EmbeddedComponent尺寸发生变化并且内部渲染未完成时显示。key为尺寸变化场景类型（如"FOLD\_TO\_EXPAND"表示折叠展开场景），value为对应场景的占位符组件。 当前支持的键值包括：FOLD\_TO\_EXPAND。传入不支持的键值时，该占位符不生效。 默认值：null，表示不设置尺寸变化占位符。

**类型：** Record&lt;string, ComponentContent&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EmbeddedOptions-areaChangePlaceholder?: Record<string, ComponentContent>--><!--Device-EmbeddedOptions-areaChangePlaceholder?: Record<string, ComponentContent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dpiFollowStrategy

```TypeScript
dpiFollowStrategy?: EmbeddedDpiFollowStrategy
```

设置DPI，使其能够跟随宿主或EmbeddedUIExtensionAbility。 默认值：FOLLOW\_UI\_EXTENSION\_ABILITY\_DPI，表示跟随EmbeddedUIExtensionAbility。

**类型：** EmbeddedDpiFollowStrategy

**默认值：** EmbeddedDpiFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_DPI

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EmbeddedOptions-dpiFollowStrategy?: EmbeddedDpiFollowStrategy--><!--Device-EmbeddedOptions-dpiFollowStrategy?: EmbeddedDpiFollowStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ComponentContent
```

设置占位符，在EmbeddedComponent与EmbeddedUIExtensionAbility建立连接前显示。 默认值：null，表示不显示占位符。

**类型：** ComponentContent

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EmbeddedOptions-placeholder?: ComponentContent--><!--Device-EmbeddedOptions-placeholder?: ComponentContent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowModeFollowStrategy

```TypeScript
windowModeFollowStrategy?: EmbeddedWindowModeFollowStrategy
```

设置窗口模式，使其能够跟随宿主或EmbeddedUIExtensionAbility。 默认值：FOLLOW\_UI\_EXTENSION\_ABILITY\_WINDOW\_MODE，表示窗口模式跟随EmbeddedUIExtensionAbility。

**类型：** EmbeddedWindowModeFollowStrategy

**默认值：** EmbeddedWindowModeFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EmbeddedOptions-windowModeFollowStrategy?: EmbeddedWindowModeFollowStrategy--><!--Device-EmbeddedOptions-windowModeFollowStrategy?: EmbeddedWindowModeFollowStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

