# TextInput

单行文本输入框组件，用于接收用户的单行文本输入。支持多种输入类型（如文本、密码、邮箱、数字等）、自定义样式（字体、颜色、下划线、装饰线等）、输入过滤、密码输入模式、自动填充等功能，适用于登录注册、搜索、表单填写等多种场景。能够解决文本 输入验证、格式化、安全输入等常见需求，简化开发流程、提升用户体验并增强数据安全性。 > **说明：** > > 该组件仅支持单文本样式，若需实现富文本样式，建议使用RichEditor组件。

## 子组件 无

## TextInput

```TypeScript
TextInput(value?: TextInputOptions)
```

定义单行文本输入组件构造函数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputInterface-(value?: TextInputOptions): TextInputAttribute--><!--Device-TextInputInterface-(value?: TextInputOptions): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextInputOptions](arkts-arkui-textinputoptions-i.md) | 否 | TextInput组件参数。默认值undefined。不设置该参数时，输入框初始化为空。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [PasswordIcon](arkts-arkui-passwordicon-i.md) | PasswordIcon对象。 |
| [SubmitEvent](arkts-arkui-submitevent-i.md) | 定义用户提交事件。 |
| [TextInputOptions](arkts-arkui-textinputoptions-i.md) | TextInput初始化参数。 |
| [UnderlineColor](arkts-arkui-underlinecolor-i.md) | 定义下划线颜色宽度属性。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnContentScrollCallback](arkts-arkui-oncontentscrollcallback-t.md) | 文本内容滚动回调。 |
| [OnPasteCallback](arkts-arkui-onpastecallback-t.md) | 粘贴回调。 |
| [OnSubmitCallback](arkts-arkui-onsubmitcallback-t.md) | 提交回调。 |
| [OnTextSelectionChangeCallback](arkts-arkui-ontextselectionchangecallback-t.md) | 文本选择变化回调或光标位置变化回调。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ContentType](arkts-arkui-contenttype-e.md) | 自动填充类型。 |
| [EnterKeyType](arkts-arkui-enterkeytype-e.md) | 输入法回车键类型。 |
| [InputType](arkts-arkui-inputtype-e.md) | 单行文本输入框类型。 |
| [TextInputStyle](arkts-arkui-textinputstyle-e.md) | 文本输入样式。 |

