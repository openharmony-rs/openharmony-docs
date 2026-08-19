# UIExtensionOptions(System API)（系统接口）

该接口用于在构造时设置UIExtensionComponentAttribute的选项。

**起始版本：** 11

<!--Device-unnamed-declare interface UIExtensionOptions--><!--Device-unnamed-declare interface UIExtensionOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## areaChangePlaceholder

```TypeScript
areaChangePlaceholder?: Record<string, ComponentContent>
```

设置尺寸变化占位符，在UIExtensionComponent尺寸发生变化并且UIExtensionAbility内部渲染未完成时显示。 key值仅支持"FOLD_TO_EXPAND"（折叠展开尺寸变化）、"UNDEFINED"（默认尺寸变化），传入其他key值时不生效。不设置时默认不显示尺寸变化占位内容。

**类型：** Record&lt;string, ComponentContent&gt;

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionOptions-areaChangePlaceholder?: Record<string, ComponentContent>--><!--Device-UIExtensionOptions-areaChangePlaceholder?: Record<string, ComponentContent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## dpiFollowStrategy

```TypeScript
dpiFollowStrategy?: DpiFollowStrategy
```

设置UIExtensionComponent内容的DPI跟随策略。 默认值：**FOLLOW_UI_EXTENSION_ABILITY_DPI**

**类型：** [DpiFollowStrategy](arkts-arkui-dpifollowstrategy-e-sys.md)

**默认值：** DpiFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_DPI

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionOptions-dpiFollowStrategy?: DpiFollowStrategy--><!--Device-UIExtensionOptions-dpiFollowStrategy?: DpiFollowStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## isTransferringCaller

```TypeScript
isTransferringCaller?: boolean
```

在使用UIExtensionComponent嵌套时，设置当前UIExtensionComponent是否转发上一级的Caller信息。true表示转发上一级的Caller信息，false表示不转发上一级的Caller信息。 默认值：**false**

**类型：** boolean

**默认值：** false

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionOptions-isTransferringCaller?: boolean--><!--Device-UIExtensionOptions-isTransferringCaller?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## placeholder

```TypeScript
placeholder?: ComponentContent
```

设置占位符。 如果设置了占位ComponentContent，则在连接未建立时显示占位节点。

**类型：** ComponentContent

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionOptions-placeholder?: ComponentContent--><!--Device-UIExtensionOptions-placeholder?: ComponentContent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## windowModeFollowStrategy

```TypeScript
windowModeFollowStrategy?: WindowModeFollowStrategy
```

设置UIExtensionComponent内容的窗口模式跟随策略。 默认值：**FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE**

**类型：** [WindowModeFollowStrategy](arkts-arkui-windowmodefollowstrategy-e-sys.md)

**默认值：** WindowModeFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionOptions-windowModeFollowStrategy?: WindowModeFollowStrategy--><!--Device-UIExtensionOptions-windowModeFollowStrategy?: WindowModeFollowStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

