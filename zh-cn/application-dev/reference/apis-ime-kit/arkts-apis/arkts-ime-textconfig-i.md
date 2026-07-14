# TextConfig

编辑框的配置信息。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## capitalizeMode

```TypeScript
capitalizeMode?: CapitalizeMode
```

编辑框设置大小写模式。如果没有设置或设置非法值，默认不进行任何首字母大写处理。

**类型：** CapitalizeMode

**默认值：** CapitalizeMode.NONE

**起始版本：** 20

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## cursorInfo

```TypeScript
cursorInfo?: CursorInfo
```

光标信息。

**类型：** CursorInfo

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## inputAttribute

```TypeScript
inputAttribute: InputAttribute
```

编辑框属性。

**类型：** InputAttribute

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## newEditBox

```TypeScript
newEditBox?: boolean
```

表示是否为新编辑框。true表示新编辑框，false表示非新编辑框。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## selection

```TypeScript
selection?: Range
```

文本选中的范围。

**类型：** Range

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## windowId

```TypeScript
windowId?: number
```

编辑框所在的窗口Id，该参数应为整数。

推荐使用[getWindowProperties](../../apis-arkui/arkts-apis/arkts-arkui-window-i.md#getwindowproperties-1)方法获取窗口id属性。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

