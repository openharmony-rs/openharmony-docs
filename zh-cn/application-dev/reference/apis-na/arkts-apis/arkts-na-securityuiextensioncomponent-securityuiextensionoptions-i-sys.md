# SecurityUIExtensionOptions（系统接口）

用于构造SecurityUIExtensionComponent时传递参数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare interface SecurityUIExtensionOptions--><!--Device-unnamed-export declare interface SecurityUIExtensionOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## dpiFollowStrategy

```TypeScript
dpiFollowStrategy?: SecurityDpiFollowStrategy
```

设置SecurityUIExtensionComponent内容分辨率跟随策略，用于控制嵌入的UIExtensionAbility内容是跟随宿主应用的分辨率还是使用自身的分辨率。

**类型：** [SecurityDpiFollowStrategy](arkts-na-securityuiextensioncomponent-securitydpifollowstrategy-e-sys.md)

**默认值：** SecurityDpiFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_DPI

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionOptions-dpiFollowStrategy?: SecurityDpiFollowStrategy--><!--Device-SecurityUIExtensionOptions-dpiFollowStrategy?: SecurityDpiFollowStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## isTransferringCaller

```TypeScript
isTransferringCaller?: boolean
```

在使用SecurityUIExtensionComponent嵌套时，设置当前组件是否转发上一级调用方的Caller信息（即发起调用的Ability身份信息），用于支持多级嵌套场景下的调用链传递。&lt;br/&gt; true：转发上一级的Caller信息；false：不转发上一级的Caller信息。&lt;br/&gt; 默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionOptions-isTransferringCaller?: boolean--><!--Device-SecurityUIExtensionOptions-isTransferringCaller?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## placeholder

```TypeScript
placeholder?: ComponentContent
```

设置占位符，在SecurityUIExtensionComponent与UIExtensionAbility建立连接前显示。 未设置时不显示占位符。

**类型：** [ComponentContent](arkts-na-componentcontent-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionOptions-placeholder?: ComponentContent--><!--Device-SecurityUIExtensionOptions-placeholder?: ComponentContent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

