# EmbeddedOptions

用于在EmbeddedComponent创建时传递可选的构造参数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface EmbeddedOptions--><!--Device-unnamed-export declare interface EmbeddedOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## areaChangePlaceholder

```TypeScript
areaChangePlaceholder?: Record<string, ComponentContentBase>
```

设置尺寸变化占位符，在EmbeddedComponent尺寸发生变化并且内部渲染未完成时显示。<br/>key为尺寸变化场景类型（如"FOLD_TO_EXPAND"表示折叠展开场景），value为对应场景的占位符组件。 当前支持的键值包括：FOLD_TO_EXPAND。传入不支持的键值时，该占位符不生效。<br/>默认值：undefined，不设置尺寸变化占位符。

**类型：** Record&lt;string, [ComponentContentBase](arkts-na-componentcontent-componentcontentbase-c.md)&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EmbeddedOptions-areaChangePlaceholder?: Record<string, ComponentContentBase>--><!--Device-EmbeddedOptions-areaChangePlaceholder?: Record<string, ComponentContentBase>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dpiFollowStrategy

```TypeScript
dpiFollowStrategy?: EmbeddedDpiFollowStrategy
```

设置DPI，使其能够跟随宿主或EmbeddedUIExtensionAbility。

**类型：** [EmbeddedDpiFollowStrategy](arkts-na-embeddedcomponent-embeddeddpifollowstrategy-e.md)

**默认值：** EmbeddedDpiFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_DPI

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EmbeddedOptions-dpiFollowStrategy?: EmbeddedDpiFollowStrategy--><!--Device-EmbeddedOptions-dpiFollowStrategy?: EmbeddedDpiFollowStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ComponentContentBase
```

设置占位符，在EmbeddedComponent与EmbeddedUIExtensionAbility建立连接前显示。<br/>默认值：undefined，不设置占位符。

**类型：** [ComponentContentBase](arkts-na-componentcontent-componentcontentbase-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EmbeddedOptions-placeholder?: ComponentContentBase--><!--Device-EmbeddedOptions-placeholder?: ComponentContentBase-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowModeFollowStrategy

```TypeScript
windowModeFollowStrategy?: EmbeddedWindowModeFollowStrategy
```

设置窗口模式，使其能够跟随宿主或EmbeddedUIExtensionAbility。

**类型：** [EmbeddedWindowModeFollowStrategy](arkts-na-embeddedcomponent-embeddedwindowmodefollowstrategy-e.md)

**默认值：** EmbeddedWindowModeFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EmbeddedOptions-windowModeFollowStrategy?: EmbeddedWindowModeFollowStrategy--><!--Device-EmbeddedOptions-windowModeFollowStrategy?: EmbeddedWindowModeFollowStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

