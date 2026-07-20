# TypographicBounds

文本行的排版边界。文本行排版边界与排版字体、排版字号有关，与字符本身无关，例如字符串为" a b "，'a'字符前面有1个空格，'b'字符后面有1个空格，排版边界就包括行首和末尾空格的边界。例如字符串为"j"或"E"，排版边界相同，即与字符本身无关。

> **说明：**  
>  
> 示意图展示文本行排版参数：width（包含左右空格的文本行宽度）、ascent（上升高度最高点）、descent（下降高度最低点）、leading（行间距）、top（当前行最高点）、baseline（字符基线）、bottom（  
> 当前行最低点）、next line top（下一行最高点）。  
>  
> ![zh-ch_image_Typographic.png](docroot://reference/apis-arkgraphics2d/figures/zh-ch_image_Typographic.png)  
>  
> 示意图展示了字符串为" a b "的排版边界。  
>  
> !  
> [zh-ch_image_TypographicBounds.png](docroot://reference/apis-arkgraphics2d/figures/zh-ch_image_TypographicBounds.png)  
>  
> 示意图展示了字符串为"j"或"E"的排版边界。  
>  
> !  
> [zh-ch_image_TypographicBounds_Character.png](docroot://reference/apis-arkgraphics2d/figures/zh-ch_image_TypographicBounds_Character.png)

**起始版本：** 18

<!--Device-text-interface TypographicBounds--><!--Device-text-interface TypographicBounds-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## ascent

```TypeScript
ascent: number
```

文本行的上升高度，浮点数，单位为物理像素px。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TypographicBounds-ascent: double--><!--Device-TypographicBounds-ascent: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## descent

```TypeScript
descent: number
```

文本行的下降高度，浮点数，单位为物理像素px。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TypographicBounds-descent: double--><!--Device-TypographicBounds-descent: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## leading

```TypeScript
leading: number
```

文本行的行间距，浮点数，单位为物理像素px。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TypographicBounds-leading: double--><!--Device-TypographicBounds-leading: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## width

```TypeScript
width: number
```

排版边界的总宽度，浮点数，单位为物理像素px。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TypographicBounds-width: double--><!--Device-TypographicBounds-width: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

