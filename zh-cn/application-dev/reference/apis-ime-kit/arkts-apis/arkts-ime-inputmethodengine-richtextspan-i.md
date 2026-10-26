# RichTextSpan

```TypeScript
export interface RichTextSpan
```

定义富文本中的跨度。

**起始版本：** 26.1.0

<!--Device-inputMethodEngine-export interface RichTextSpan--><!--Device-inputMethodEngine-export interface RichTextSpan-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## getContent

```TypeScript
getContent(): string
```

获取span的内容。<br> <br>  
> **注意** <br> <br> &gt;如果span类型为图片，则内容为图片插入ArkUI富文本组件时携带的标签信息。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichTextSpan-getContent(): string--><!--Device-RichTextSpan-getContent(): string-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | span的内容。 |

## getRange

```TypeScript
getRange(): Range
```

获取富文本中span的范围。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichTextSpan-getRange(): Range--><!--Device-RichTextSpan-getRange(): Range-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Range](arkts-ime-inputmethodengine-range-i.md) | 富文本中span的范围，由开始和结束位置表示。 |

## getType

```TypeScript
getType(): SpanType
```

获取span的类型。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichTextSpan-getType(): SpanType--><!--Device-RichTextSpan-getType(): SpanType-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SpanType](arkts-ime-inputmethodengine-spantype-e.md) | span的类型。 |
