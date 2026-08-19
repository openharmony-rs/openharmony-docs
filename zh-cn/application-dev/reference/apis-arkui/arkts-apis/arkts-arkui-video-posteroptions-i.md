# PosterOptions

用于描述当前视频是否配置首帧送显。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface PosterOptions--><!--Device-unnamed-export declare interface PosterOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentTransitionEffect

```TypeScript
contentTransitionEffect?: ContentTransitionEffect
```

当前视频的预览图内容变化时的转场动效。配置showFirstFrame为true（即配置开启首帧送显时）， 或未配置有效的VideoOptions的previewUri时，该字段不生效。 默认值：ContentTransitionEffect.IDENTITY。 设置为undefined或null时，取值为ContentTransitionEffect.IDENTITY。

**类型：** [ContentTransitionEffect](../arkts-components/arkts-arkui-contenttransitioneffect-c.md)

**默认值：** ContentTransitionEffect.IDENTITY

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PosterOptions-contentTransitionEffect?: ContentTransitionEffect--><!--Device-PosterOptions-contentTransitionEffect?: ContentTransitionEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showFirstFrame

```TypeScript
showFirstFrame?: boolean
```

当前视频是否配置首帧送显，当开启首帧送显时，VideoOptions中的previewUri字段不生效。 true：开启首帧送显；false：关闭首帧送显。 默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PosterOptions-showFirstFrame?: boolean--><!--Device-PosterOptions-showFirstFrame?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

