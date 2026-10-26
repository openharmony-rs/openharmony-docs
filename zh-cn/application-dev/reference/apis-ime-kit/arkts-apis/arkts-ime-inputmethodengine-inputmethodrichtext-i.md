# InputMethodRichText

```TypeScript
export interface InputMethodRichText
```

定义富文本。

**起始版本：** 26.1.0

<!--Device-inputMethodEngine-export interface InputMethodRichText--><!--Device-inputMethodEngine-export interface InputMethodRichText-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## getSpans

```TypeScript
getSpans(): Array<RichTextSpan>
```

获取组成富文本的span。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputMethodRichText-getSpans(): Array<RichTextSpan>--><!--Device-InputMethodRichText-getSpans(): Array<RichTextSpan>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[RichTextSpan](arkts-ime-inputmethodengine-richtextspan-i.md)&gt; | 组成富文本的span数组。 |

## getString

```TypeScript
getString(): string
```

从富文本中提取纯文本。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputMethodRichText-getString(): string--><!--Device-InputMethodRichText-getString(): string-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 从富文本中提取的纯文本。 |
