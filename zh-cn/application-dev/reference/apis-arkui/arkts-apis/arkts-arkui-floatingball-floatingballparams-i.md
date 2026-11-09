# FloatingBallParams

```TypeScript
interface FloatingBallParams
```

启动和更新闪控球的配置参数。

**起始版本：** 20

<!--Device-floatingBall-interface FloatingBallParams--><!--Device-floatingBall-interface FloatingBallParams-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { floatingBall } from '@kit.ArkUI';
```

## backgroundColor

```TypeScript
backgroundColor?: string
```

闪控球背景颜色，为不带透明度的十六进制颜色格式（例如'#008EF5'或'#FF008EF5'）。格式错误时返回错误码1300019。不传入时闪控球跟随系统深浅色模式的默认背景色。

**类型：** string

**起始版本：** 20

<!--Device-FloatingBallParams-backgroundColor?: string--><!--Device-FloatingBallParams-backgroundColor?: string-End-->

**系统能力：** SystemCapability.Window.SessionManager

## content

```TypeScript
content?: string
```

闪控球内容，大小不超过64字节。不传入时默认为空字符串，不显示闪控球内容。

**类型：** string

**起始版本：** 20

<!--Device-FloatingBallParams-content?: string--><!--Device-FloatingBallParams-content?: string-End-->

**系统能力：** SystemCapability.Window.SessionManager

## contentColor

```TypeScript
contentColor?: string
```

闪控球内容文字颜色，为不带透明度的十六进制颜色格式（例如'#008EF5'或'#FF008EF5'）。不传入时根据背景色色度自动填充，若背景色为亮色则填充黑色('#99000000')，若背景色为暗色则填充白色('#99FFFFFF')。配置此属性时，必须配置背景色backgroundColor，否则返回错误码1300019。

**类型：** string

**默认值：** 根据'backgroundColor'设置不同的默认值。当'backgroundColor'为亮色时，默认值为'#99000000'，否则为'#99FFFFFF'。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatingBallParams-contentColor?: string--><!--Device-FloatingBallParams-contentColor?: string-End-->

**系统能力：** SystemCapability.Window.SessionManager

## icon

```TypeScript
icon?: image.PixelMap
```

闪控球图标，图标像素的总字节数不超过192KB（图标像素的总字节数通过[getPixelBytesNumber](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md#getpixelbytesnumber)获取）。建议图标像素宽高为128px*128px。实际显示效果依赖于设备能力和闪控球UI样式。

**类型：** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**起始版本：** 20

<!--Device-FloatingBallParams-icon?: image.PixelMap--><!--Device-FloatingBallParams-icon?: image.PixelMap-End-->

**系统能力：** SystemCapability.Window.SessionManager

## template

```TypeScript
template: FloatingBallTemplate
```

闪控球模板。

**类型：** [FloatingBallTemplate](arkts-arkui-floatingball-floatingballtemplate-e.md)

**起始版本：** 20

<!--Device-FloatingBallParams-template: FloatingBallTemplate--><!--Device-FloatingBallParams-template: FloatingBallTemplate-End-->

**系统能力：** SystemCapability.Window.SessionManager

## textUpdateAnimationType

```TypeScript
textUpdateAnimationType?: FloatingBallTextUpdateAnimationType
```

闪控球文本更新时的动画类型。默认为FloatingBallTextUpdateAnimationType.ANIMATION_NONE。

**类型：** [FloatingBallTextUpdateAnimationType](arkts-arkui-floatingball-floatingballtextupdateanimationtype-e.md)

**默认值：** FloatingBallTextUpdateAnimationType.ANIMATION_NONE

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatingBallParams-textUpdateAnimationType?: FloatingBallTextUpdateAnimationType--><!--Device-FloatingBallParams-textUpdateAnimationType?: FloatingBallTextUpdateAnimationType-End-->

**系统能力：** SystemCapability.Window.SessionManager

## title

```TypeScript
title: string
```

闪控球标题，不可为空字符串，大小不超过64字节。

**类型：** string

**起始版本：** 20

<!--Device-FloatingBallParams-title: string--><!--Device-FloatingBallParams-title: string-End-->

**系统能力：** SystemCapability.Window.SessionManager

## titleColor

```TypeScript
titleColor?: string
```

闪控球标题文字颜色，为不带透明度的十六进制颜色格式（例如'#008EF5'或'#FF008EF5'）。不传入时根据背景色色度自动填充，若背景色为亮色则填充黑色('#E5000000')，若背景色为暗色则填充白色('#E5FFFFFF')。配置此属性时，必须配置背景色backgroundColor，否则返回错误码1300019。

**类型：** string

**默认值：** 根据'backgroundColor'设置不同的默认值。当'backgroundColor'为亮色时，默认值为'#E5000000'，否则为'#E5FFFFFF'。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatingBallParams-titleColor?: string--><!--Device-FloatingBallParams-titleColor?: string-End-->

**系统能力：** SystemCapability.Window.SessionManager
