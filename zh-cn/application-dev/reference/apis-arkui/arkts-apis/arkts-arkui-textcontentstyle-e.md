# TextContentStyle

```TypeScript
declare enum TextContentStyle
```

文本框多态样式。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

默认风格。光标宽度为1.5vp，光标高度与文本选中高亮高度和字体大小相关。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## INLINE

```TypeScript
INLINE = 1
```

内联输入风格，也称内联模式。文本选中高亮高度与输入框高度相同。

内联输入是在有明显的编辑态/非编辑态的区分场景下使用，例如：文件列表视图中的重命名。

不支持showError属性。

内联模式下，不支持拖入文本。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
