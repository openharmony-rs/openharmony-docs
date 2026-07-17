# OnDidChangeCallback

```TypeScript
declare type OnDidChangeCallback = (rangeBefore: TextRange, rangeAfter: TextRange) => void
```

文本变换后回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnDidChangeCallback = (rangeBefore: TextRange, rangeAfter: TextRange) => void--><!--Device-unnamed-declare type OnDidChangeCallback = (rangeBefore: TextRange, rangeAfter: TextRange) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rangeBefore | TextRange | 是 | 文本变化前将要被替换的文本范围。 |
| rangeAfter | TextRange | 是 | 文本变化后新增内容的文本范围。 |

