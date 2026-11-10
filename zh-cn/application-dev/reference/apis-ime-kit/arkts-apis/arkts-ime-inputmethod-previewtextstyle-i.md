# PreviewTextStyle

```TypeScript
export interface PreviewTextStyle
```

预上屏文本的样式。

**起始版本：** 26.1.0

<!--Device-inputMethod-export interface PreviewTextStyle--><!--Device-inputMethod-export interface PreviewTextStyle-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## underlineColor

```TypeScript
underlineColor?: number
```

下划线颜色，格式为0xRRGGBB。可选参数，不传时下划线颜色应遵循应用主题颜色。若携带透明度，透明度无效，将被编辑器忽略。取值限定为整数。默认值：缺省行为：不传递颜色给编辑框，由编辑框处理，默认跟随光标色。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PreviewTextStyle-underlineColor?: int--><!--Device-PreviewTextStyle-underlineColor?: int-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## underlineStyle

```TypeScript
underlineStyle: UnderlineStyle
```

下划线样式。

**类型：** [UnderlineStyle](arkts-ime-inputmethod-underlinestyle-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PreviewTextStyle-underlineStyle: UnderlineStyle--><!--Device-PreviewTextStyle-underlineStyle: UnderlineStyle-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework
