# TextInputStyle

文本输入样式。

**起始版本：** 9

<!--Device-unnamed-declare enum TextInputStyle--><!--Device-unnamed-declare enum TextInputStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Default

```TypeScript
Default = 0
```

默认风格，光标宽1.5vp，光标高度与文本选中底板高度和字体大小相关。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputStyle-Default = 0--><!--Device-TextInputStyle-Default = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Inline

```TypeScript
Inline = 1
```

内联输入风格。文本选中底板高度与输入框高度相同。

内联输入是在有明显的编辑态/非编辑态的区分场景下使用，例如：文件列表视图中的重命名。

不支持showError属性。

[内联模式](../../../ui/arkts-common-components-text-input.md#内联模式)下，不支持拖入文本。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputStyle-Inline = 1--><!--Device-TextInputStyle-Inline = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

