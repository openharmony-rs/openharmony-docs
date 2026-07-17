# WordBreak

断词策略枚举。

**起始版本：** 12

<!--Device-text-enum WordBreak--><!--Device-text-enum WordBreak-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## NORMAL

```TypeScript
NORMAL = 0
```

默认的换行规则。依据各自语言的规则，允许在字间发生换行。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-WordBreak-NORMAL = 0--><!--Device-WordBreak-NORMAL = 0-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## BREAK_ALL

```TypeScript
BREAK_ALL = 1
```

对于Non-CJK（非中文，日文，韩文）文本允许在任意字符内发生换行。该值适合包含一些非亚洲文本的亚洲文本，比如使连续的英文字符断行。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-WordBreak-BREAK_ALL = 1--><!--Device-WordBreak-BREAK_ALL = 1-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## BREAK_WORD

```TypeScript
BREAK_WORD = 2
```

对于Non-CJK的文本可在任意2个字符间断行，一行文本中有断行破发点（如空白符）时，优先按破发点换行，保障单词优先完整显示。若整一行文本均无断行破发点时，则在任意2个字符间断行。对于CJK与NORMAL效果一致。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-WordBreak-BREAK_WORD = 2--><!--Device-WordBreak-BREAK_WORD = 2-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## BREAK_HYPHEN

```TypeScript
BREAK_HYPHEN = 3
```

每行末尾单词尝试通过连字符“-”进行断行，若无法添加连字符“-”，则跟`BREAK_WORD`保持一致。

使用此断词策略时，需与[TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)中`locale`属性配合使用，通过locale定义语言环境共同作用影响断词效果。

**起始版本：** 18

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-WordBreak-BREAK_HYPHEN = 3--><!--Device-WordBreak-BREAK_HYPHEN = 3-End-->

**系统能力：** SystemCapability.Graphics.Drawing

