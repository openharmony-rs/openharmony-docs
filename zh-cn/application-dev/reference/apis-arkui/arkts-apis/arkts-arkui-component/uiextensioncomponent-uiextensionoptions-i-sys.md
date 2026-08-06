# UIExtensionOptions（系统接口）

用于在UIExtensionComponent进行构造时传递可选的构造参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface UIExtensionOptions--><!--Device-unnamed-export declare interface UIExtensionOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## areaChangePlaceholder

```TypeScript
areaChangePlaceholder?: Record<string, ComponentContentBase>
```

设置尺寸变化占位符，在UIExtensionComponent尺寸发生变化并且UIExtensionAbility内部渲染未完成时显示，key值仅支持"FOLD\_TO\_EXPAND"（折叠展开尺寸变化）、 "UNDEFINED"（默认尺寸变化），传入其他key值时不生效。不设置时默认不显示尺寸变化占位内容。

**类型：** Record&lt;string, ComponentContentBase&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionOptions-areaChangePlaceholder?: Record<string, ComponentContentBase>--><!--Device-UIExtensionOptions-areaChangePlaceholder?: Record<string, ComponentContentBase>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## dpiFollowStrategy

```TypeScript
dpiFollowStrategy?: DpiFollowStrategy
```

提供接口支持设置DPI跟随宿主或跟随UIExtensionAbility。

**类型：** DpiFollowStrategy

**默认值：** DpiFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_DPI

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionOptions-dpiFollowStrategy?: DpiFollowStrategy--><!--Device-UIExtensionOptions-dpiFollowStrategy?: DpiFollowStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## isTransferringCaller

```TypeScript
isTransferringCaller?: boolean
```

在使用UIExtensionComponent嵌套时，设置当前UIExtensionComponent是否转发上一级的Caller信息。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_ true表示转发上一级的Caller信息，false表示不转发上一级的Caller信息。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_ 默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionOptions-isTransferringCaller?: boolean--><!--Device-UIExtensionOptions-isTransferringCaller?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## placeholder

```TypeScript
placeholder?: ComponentContentBase
```

设置占位符，在UIExtensionComponent与UIExtensionAbility建立连接前显示。当需要在连接建立前向用户展示加载状态或提示内容时传入此参数，不设置时默认不显示占位内容。

**类型：** ComponentContentBase

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionOptions-placeholder?: ComponentContentBase--><!--Device-UIExtensionOptions-placeholder?: ComponentContentBase-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## windowModeFollowStrategy

```TypeScript
windowModeFollowStrategy?: WindowModeFollowStrategy
```

提供接口以支持设置窗口Mode，使其能够跟随宿主或UIExtensionAbility。

**类型：** WindowModeFollowStrategy

**默认值：** WindowModeFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionOptions-windowModeFollowStrategy?: WindowModeFollowStrategy--><!--Device-UIExtensionOptions-windowModeFollowStrategy?: WindowModeFollowStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

