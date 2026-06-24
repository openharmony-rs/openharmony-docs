# StyledStringController

定义StyledString控制器。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getStyledString

```TypeScript
getStyledString(): MutableStyledString
```

获取富文本组件显示的属性字符串。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| MutableStyledString | 富文本组件显示的属性字符串。 |

## setStyledString

```TypeScript
setStyledString(styledString: StyledString): void
```

设置富文本组件显示的属性字符串。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | StyledString | 是 | 属性字符串。<br/>**说明：**<br/>StyledString的子类<br/>[MutableStyledString](arkts-arkui-styled-string-mutablestyledstring-c.md#MutableStyledString)也可以作为入参值。 |

