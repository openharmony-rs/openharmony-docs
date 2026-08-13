# TextConfig

编辑框的配置信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-inputMethod-export interface TextConfig--><!--Device-inputMethod-export interface TextConfig-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## capitalizeMode

```TypeScript
capitalizeMode?: CapitalizeMode
```

编辑框设置大小写模式。如果没有设置或设置非法值，默认不进行任何首字母大写处理。

**类型：** CapitalizeMode

**默认值：** CapitalizeMode.NONE

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TextConfig-capitalizeMode?: CapitalizeMode--><!--Device-TextConfig-capitalizeMode?: CapitalizeMode-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## cursorInfo

```TypeScript
cursorInfo?: CursorInfo
```

光标信息。

**类型：** [CursorInfo](arkts-ime-inputmethod-cursorinfo-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TextConfig-cursorInfo?: CursorInfo--><!--Device-TextConfig-cursorInfo?: CursorInfo-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## inputAttribute

```TypeScript
inputAttribute: InputAttribute
```

编辑框属性。

**类型：** [InputAttribute](arkts-ime-inputmethod-inputattribute-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TextConfig-inputAttribute: InputAttribute--><!--Device-TextConfig-inputAttribute: InputAttribute-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## newEditBox

```TypeScript
newEditBox?: boolean
```

表示是否为新编辑框。true表示新编辑框，false表示非新编辑框。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TextConfig-newEditBox?: boolean--><!--Device-TextConfig-newEditBox?: boolean-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## selection

```TypeScript
selection?: Range
```

文本选中的范围。

**类型：** Range

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TextConfig-selection?: Range--><!--Device-TextConfig-selection?: Range-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## windowId

```TypeScript
windowId?: int
```

编辑框所在的窗口Id，该参数应为整数。 推荐使用[getWindowProperties](../../apis-arkui/arkts-apis/arkts-arkui-window-window-i.md#getWindowProperties)方法获取窗口id属性。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TextConfig-windowId?: int--><!--Device-TextConfig-windowId?: int-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

