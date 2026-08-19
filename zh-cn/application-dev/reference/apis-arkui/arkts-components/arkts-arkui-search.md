# Search

搜索框组件，支持搜索图标、清除按钮、搜索按钮、placeholder提示文本、自定义键盘等功能配置，适用于浏览器的搜索内容输入框、应用内搜索等场景。 > **说明：** > > 该组件仅支持单文本样式，若需实现富文本样式，建议使用RichEditor组件。

## 子组件 无

## Search

```TypeScript
Search(options?: SearchOptions)
```

定义搜索组件构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchInterface-(options?: SearchOptions): SearchAttribute--><!--Device-SearchInterface-(options?: SearchOptions): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SearchOptions](arkts-arkui-searchoptions-i.md) | 否 | 搜索框组件初始化选项。当需要设置搜索框的初始值、提示文本、图标或控制器时传入此参数，不传入时使用默认配置。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [CancelButtonOptions](arkts-arkui-cancelbuttonoptions-i.md) | 定义清除按钮选项。 |
| [IconOptions](arkts-arkui-iconoptions-i.md) | 定义图标选项。 |
| [SearchButtonOptions](arkts-arkui-searchbuttonoptions-i.md) | 定义搜索按钮选项。 |
| [SearchOptions](arkts-arkui-searchoptions-i.md) | Search初始化参数。 @since版本号高于内层元素版本号的情况，但这不影响接口的使用。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [SearchSubmitCallback](arkts-arkui-searchsubmitcallback-t.md) | 点击搜索图标、搜索按钮或者按下软键盘搜索按钮时的回调事件。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CancelButtonStyle](arkts-arkui-cancelbuttonstyle-e.md) | 清除按钮样式枚举。 |
| [SearchType](arkts-arkui-searchtype-e.md) | 搜索输入框类型。 |

