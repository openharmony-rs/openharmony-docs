# CanvasDirection

```TypeScript
declare type CanvasDirection = "inherit" | "ltr" | "rtl"
```

定义当前文本方向的类型。取值类型为下表类型中的并集。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| "inherit" | 继承canvas组件通用属性已设定的文本方向，若canvas组件未设置direction属性，则跟随系统文字方向。 |
| "ltr" | 从左往右。 |
| "rtl" | 从右往左。 |

