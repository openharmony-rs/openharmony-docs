# TextArea

多行文本输入框组件，当输入的文本内容超过组件宽度时会自动换行显示，适用于评论输入、反馈表单、内容编辑等需要多行文本输入的场景。 高度未设置时，组件无默认高度，自适应内容高度。宽度未设置时，默认撑满最大宽度。

## 子组件 无

## TextArea

```TypeScript
TextArea(value?: TextAreaOptions)
```

定义TextArea组件构造函数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaInterface-(value?: TextAreaOptions): TextAreaAttribute--><!--Device-TextAreaInterface-(value?: TextAreaOptions): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextAreaOptions](arkts-arkui-textareaoptions-i.md) | 否 | TextArea组件参数。默认值：详见TextAreaOptions。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [TextAreaOptions](arkts-arkui-textareaoptions-i.md) | TextArea初始化参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [TextAreaSubmitCallback](arkts-arkui-textareasubmitcallback-t.md) | 软键盘按下回车键时的回调事件。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [TextAreaType](arkts-arkui-textareatype-e.md) | 多行文本输入框类型。 |

