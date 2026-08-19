# TabBarOptions

设置页签内的图片和文字内容。 > **说明：** > > 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface TabBarOptions--><!--Device-unnamed-export declare interface TabBarOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## badge

```TypeScript
badge?: BadgeParamWithNumber | BadgeParamWithString
```

TabBar 信息标记组件。

**类型：** BadgeParamWithNumber \| BadgeParamWithString

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TabBarOptions-badge?: BadgeParamWithNumber | BadgeParamWithString--><!--Device-TabBarOptions-badge?: BadgeParamWithNumber | BadgeParamWithString-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: string | Resource
```

页签内的图片内容。未设置时不显示图片。

**类型：** string \| [Resource](../../apis-arkui/arkts-apis/arkts-arkui-resource-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TabBarOptions-icon?: string | Resource--><!--Device-TabBarOptions-icon?: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: string | Resource
```

页签内的文字内容。未设置时不显示文字。

**类型：** string \| [Resource](../../apis-arkui/arkts-apis/arkts-arkui-resource-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TabBarOptions-text?: string | Resource--><!--Device-TabBarOptions-text?: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

