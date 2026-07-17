# CanvasTextBaseline

```TypeScript
declare type CanvasTextBaseline = "alphabetic" | "bottom" | "hanging" | "ideographic" | "middle" | "top"
```

定义文本基线类型。取值类型为下表类型中的并集。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare type CanvasTextBaseline = "alphabetic" | "bottom" | "hanging" | "ideographic" | "middle" | "top"--><!--Device-unnamed-declare type CanvasTextBaseline = "alphabetic" | "bottom" | "hanging" | "ideographic" | "middle" | "top"-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| "alphabetic" | 文本基线是标准的字母基线。 |
| "bottom" | 文本基线在文本块的底部。与ideographic基线的区别在于ideographic基线不需要考虑下行字母。 |
| "hanging" | 文本基线是悬挂基线。 |
| "ideographic" | 文字基线是表意字基线；如果字符本身超出了alphabetic基线，那么ideographic基线位置在字符本身的底部。 |
| "middle" | 文本基线在文本块的中间。 |
| "top" | 文本基线在文本块的顶部。 |

