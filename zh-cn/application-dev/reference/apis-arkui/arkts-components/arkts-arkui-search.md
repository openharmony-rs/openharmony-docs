# Search

搜索框组件，支持搜索图标、清除按钮、搜索按钮、placeholder提示文本、自定义键盘等功能配置，适用于浏览器的搜索内容输入框、应用内搜索等场景。 > **说明：** > > 该组件仅支持单文本样式，若需实现富文本样式，建议使用RichEditor组件。

## 子组件 无

## Search

```TypeScript
Search(options?: SearchOptions)
```

定义搜索组件构造函数。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchInterface-(options?: SearchOptions): SearchAttribute--><!--Device-SearchInterface-(options?: SearchOptions): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SearchOptions](arkts-arkui-searchoptions-i.md) | 否 | 搜索框组件初始化选项。当需要设置搜索框的初始值、提示文本、图标或控制器时传入此参数，不传入时使用默认配置。 |

## 汇总

- [CancelButtonOptions](arkts-arkui-cancelbuttonoptions-i.md)
- [IconOptions](arkts-arkui-iconoptions-i.md)
- [SearchButtonOptions](arkts-arkui-searchbuttonoptions-i.md)
- [SearchOptions](arkts-arkui-searchoptions-i.md)
- [SearchSubmitCallback](arkts-arkui-searchsubmitcallback-t.md)
- [CancelButtonStyle](arkts-arkui-cancelbuttonstyle-e.md)
- [SearchType](arkts-arkui-searchtype-e.md)
