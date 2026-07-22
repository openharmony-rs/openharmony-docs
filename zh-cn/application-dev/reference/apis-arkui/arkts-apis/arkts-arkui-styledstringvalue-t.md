# StyledStringValue

```TypeScript
declare type StyledStringValue = TextStyle | DecorationStyle | BaselineOffsetStyle | LetterSpacingStyle |
TextShadowStyle | GestureStyle | ImageAttachment | ParagraphStyle | LineHeightStyle | UrlStyle | CustomSpan |
UserDataSpan | BackgroundColorStyle | LineSpacingStyle
```

样式对象类型，用于设置属性字符串的样式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type StyledStringValue = TextStyle | DecorationStyle | BaselineOffsetStyle | LetterSpacingStyle |TextShadowStyle | GestureStyle | ImageAttachment | ParagraphStyle | LineHeightStyle | UrlStyle | CustomSpan |UserDataSpan | BackgroundColorStyle | LineSpacingStyle--><!--Device-unnamed-declare type StyledStringValue = TextStyle | DecorationStyle | BaselineOffsetStyle | LetterSpacingStyle |TextShadowStyle | GestureStyle | ImageAttachment | ParagraphStyle | LineHeightStyle | UrlStyle | CustomSpan |UserDataSpan | BackgroundColorStyle | LineSpacingStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| TextStyle | 文本字体样式。 |
| DecorationStyle | 文本装饰线样式。 |
| BaselineOffsetStyle | 文本基线偏移量样式。 |
| LetterSpacingStyle | 文本字符间距样式。 |
| TextShadowStyle | 文本阴影样式。 |
| GestureStyle | 事件手势样式。 |
| ImageAttachment | 图片样式。 |
| ParagraphStyle | 文本段落样式。 |
| LineHeightStyle | 文本行高样式。 |
| UrlStyle | 超链接样式。 [since 14] |
| CustomSpan | 自定义绘制Span样式。 |
| UserDataSpan | UserDataSpan样式。 |
| BackgroundColorStyle | 文本背景颜色样式。 [since 14] |
| LineSpacingStyle | 文本行间距。 [since 26.0.0] |

