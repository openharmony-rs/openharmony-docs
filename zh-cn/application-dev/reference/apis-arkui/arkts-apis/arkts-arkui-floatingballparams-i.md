# FloatingBallParams

启动和更新闪控球的配置参数。

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

## backgroundColor

```TypeScript
backgroundColor?: string
```

闪控球背景颜色，为不带透明度的十六进制颜色格式（例如'#008EF5'或'#FF008EF5'），不传入时闪控球跟随系统深浅色模式的默认背景色。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

## content

```TypeScript
content?: string
```

闪控球内容，大小不超过64字节。不传入时默认为空字符串，不显示闪控球内容。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

## contentColor

```TypeScript
contentColor?: string
```

闪控球内容颜色，为不带透明度的十六进制颜色格式（例如'#008EF5'或'#FF008EF5'）。如果背景颜色没有指定，不允许指定内容颜色。

**类型：** string

**默认值：** Set different default values according to the 'backgroundColor'.
- If 'backgroundColor' is provided, when 'backgroundColor' is light color, default value is '#99FFFFFF',
otherwise is '#99000000'
- If 'backgroundColor' is not provided, default value is $r('sys.color.font_secondary')

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

## icon

```TypeScript
icon?: image.PixelMap
```

闪控球图标，图标像素的总字节数不超过192KB（图标像素的总字节数通过
[getPixelBytesNumber](../../apis-image-kit/arkts-apis/arkts-image-pixelmap-i.md#getpixelbytesnumber-1)获取）。
建议图标像素宽高为128px*128px。实际显示效果依赖于设备能力和闪控球UI样式。

**类型：** image.PixelMap

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

## template

```TypeScript
template: FloatingBallTemplate
```

闪控球模板。

**类型：** FloatingBallTemplate

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

## textUpdateAnimationType

```TypeScript
textUpdateAnimationType?: FloatingBallTextUpdateAnimationType
```

闪控球文本更新时的动画类型。默认为FloatingBallTextUpdateAnimationType.ANIMATION_NONE。

**类型：** FloatingBallTextUpdateAnimationType

**默认值：** FloatingBallTextUpdateAnimationType.ANIMATION_NONE

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

## title

```TypeScript
title: string
```

闪控球标题，不可为空字符串，大小不超过64字节。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

## titleColor

```TypeScript
titleColor?: string
```

闪控球标题颜色，为不带透明度的十六进制颜色格式（例如'#008EF5'或'#FF008EF5'）。如果背景颜色没有指定，不允许指定标题颜色。

**类型：** string

**默认值：** Set different default values according to the 'backgroundColor'.
- If 'backgroundColor' is provided, when 'backgroundColor' is light color, default value is '#E5FFFFFF',
otherwise is '#E5000000'.
- If 'backgroundColor' is not provided, default value is $r('sys.color.font_primary').

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

