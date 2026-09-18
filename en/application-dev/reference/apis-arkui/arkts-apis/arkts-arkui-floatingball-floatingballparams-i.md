# FloatingBallParams

Describes the parameters for starting and updating the floating ball.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { floatingBall } from '@kit.ArkUI';
```

## backgroundColor

```TypeScript
backgroundColor?: string
```

Background color of the floating ball, in hexadecimal format without opacity (for example, **'#008EF5'** or **'#FF008EF5'**). If this parameter is not specified, the default background color of the system (light or dark mode) is used.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## content

```TypeScript
content?: string
```

Content of the floating ball. It cannot exceed 64 bytes. The default value is an empty string, and no content is displayed on the floating ball.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## contentColor

```TypeScript
contentColor?: string
```

The color of the floating ball content, in hexadecimal format without opacity (e.g., **'#008EF5'** or **'#FF008EF5'**). Providing contentColor is not allowed if 'backgroundColor' is not provided.

**Type:** string

**Default:** Set different default values according to the 'backgroundColor'.
- If 'backgroundColor' is provided, when 'backgroundColor' is light color, default value is '#99FFFFFF',
otherwise is '#99000000'
- If 'backgroundColor' is not provided, default value is $r('sys.color.font_secondary')

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## icon

```TypeScript
icon?: image.PixelMap
```

Icon of the floating ball. The total number of bytes of the icon pixels cannot exceed 192 KB (which is obtained through [getPixelBytesNumber](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md#getpixelbytesnumber)). The recommended size is 128 px * 128 px. Actual display may vary based on the device capability and floating ball UI style.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## template

```TypeScript
template: FloatingBallTemplate
```

Floating ball template.

**Type:** [FloatingBallTemplate](arkts-arkui-floatingball-floatingballtemplate-e.md)

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## textUpdateAnimationType

```TypeScript
textUpdateAnimationType?: FloatingBallTextUpdateAnimationType
```

Animation type used when the floating ball text is updated. The default value is **FloatingBallTextUpdateAnimationType.ANIMATION_NONE**.

**Type:** [FloatingBallTextUpdateAnimationType](arkts-arkui-floatingball-floatingballtextupdateanimationtype-e.md)

**Default:** FloatingBallTextUpdateAnimationType.ANIMATION_NONE

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## title

```TypeScript
title: string
```

Title of the floating ball. It cannot be an empty string and cannot exceed 64 bytes.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## titleColor

```TypeScript
titleColor?: string
```

The color of the floating ball title, in hexadecimal format without opacity (e.g., **'#008EF5'** or **'#FF008EF5'**). Providing titleColor is not allowed if 'backgroundColor' is not provided.

**Type:** string

**Default:** Set different default values according to the 'backgroundColor'.
- If 'backgroundColor' is provided, when 'backgroundColor' is light color, default value is '#E5FFFFFF',
otherwise is '#E5000000'.
- If 'backgroundColor' is not provided, default value is $r('sys.color.font_primary').

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager
