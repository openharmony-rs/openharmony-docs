# StyledStringController

定义StyledString控制器。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface StyledStringController--><!--Device-unnamed-export declare interface StyledStringController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getStyledString

```TypeScript
getStyledString(): MutableStyledString | undefined
```

ArkTS-Sta: getStyledString(): MutableStyledString | undefined 获取富文本组件显示的属性字符串。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyledStringController-getStyledString(): MutableStyledString | undefined--><!--Device-StyledStringController-getStyledString(): MutableStyledString | undefined-End-->

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MutableStyledString](arkts-arkui-styledstring-mutablestyledstring-c.md) | 富文本组件显示的属性字符串。 |

## setStyledString

```TypeScript
setStyledString(styledString: StyledString): void
```

设置富文本组件显示的属性字符串。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyledStringController-setStyledString(styledString: StyledString): void--><!--Device-StyledStringController-setStyledString(styledString: StyledString): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | [StyledString](arkts-arkui-styledstring-styledstring-c.md) | 是 | 属性字符串。<br/>**说明：** <br/>StyledString的子类 [MutableStyledString](../../../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#mutablestyledstring) 也可以作为入参值。 |

