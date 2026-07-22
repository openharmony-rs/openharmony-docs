# StyledStringController

定义StyledString控制器。

**起始版本：** 12

<!--Device-unnamed-declare interface StyledStringController--><!--Device-unnamed-declare interface StyledStringController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getStyledString

```TypeScript
getStyledString(): MutableStyledString
```

获取富文本组件显示的属性字符串。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-StyledStringController-getStyledString(): MutableStyledString--><!--Device-StyledStringController-getStyledString(): MutableStyledString-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MutableStyledString](arkts-arkui-mutablestyledstring-c.md) | 富文本组件显示的属性字符串。 |

## setStyledString

```TypeScript
setStyledString(styledString: StyledString): void
```

设置富文本组件显示的属性字符串。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-StyledStringController-setStyledString(styledString: StyledString): void--><!--Device-StyledStringController-setStyledString(styledString: StyledString): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | [StyledString](arkts-arkui-styledstring-c.md) | 是 | 属性字符串。<br/>**说明：** <br/>StyledString的子类[MutableStyledString](arkts-arkui-mutablestyledstring-c.md)也可以作为入参值。 |

