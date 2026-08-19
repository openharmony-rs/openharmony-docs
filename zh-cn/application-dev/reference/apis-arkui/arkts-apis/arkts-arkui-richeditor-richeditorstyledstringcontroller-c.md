# RichEditorStyledStringController

使用属性字符串构建的RichEditor组件的控制器，继承自[RichEditorBaseController](arkts-arkui-richeditor-richeditorbasecontroller-c.md)。

**继承/实现关系：** RichEditorStyledStringController extends [RichEditorBaseController](arkts-arkui-richeditor-richeditorbasecontroller-c.md) implements StyledStringController

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class RichEditorStyledStringController--><!--Device-unnamed-export declare class RichEditorStyledStringController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getSelection

```TypeScript
getSelection(): RichEditorRange | undefined
```

获取富文本当前的选中区域范围。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorStyledStringController-getSelection(): RichEditorRange | undefined--><!--Device-RichEditorStyledStringController-getSelection(): RichEditorRange | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RichEditorRange](arkts-arkui-richeditor-richeditorrange-i.md) | 选中区域范围。<br/>返回undefined时表示controller未与组件绑定。 |

## getStyledString

```TypeScript
getStyledString(): MutableStyledString | undefined
```

获取富文本组件显示的属性字符串。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorStyledStringController-getStyledString(): MutableStyledString | undefined--><!--Device-RichEditorStyledStringController-getStyledString(): MutableStyledString | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MutableStyledString](arkts-arkui-styledstring-mutablestyledstring-c.md) | 富文本组件显示的属性字符串。<br/>返回undefined时表示controller未与组件绑定。 |

## onContentChanged

```TypeScript
onContentChanged(listener: StyledStringChangedListener): void
```

注册文本内容变化回调，该回调会在后端程序导致文本内容变更时触发。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorStyledStringController-onContentChanged(listener: StyledStringChangedListener): void--><!--Device-RichEditorStyledStringController-onContentChanged(listener: StyledStringChangedListener): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| listener | [StyledStringChangedListener](arkts-arkui-textcommon-styledstringchangedlistener-i.md) | 是 | 文本内容变化回调监听器。 |

## setStyledString

```TypeScript
setStyledString(styledString: StyledString): void
```

设置富文本组件显示的属性字符串。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorStyledStringController-setStyledString(styledString: StyledString): void--><!--Device-RichEditorStyledStringController-setStyledString(styledString: StyledString): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | [StyledString](arkts-arkui-styledstring-styledstring-c.md) | 是 | 属性字符串。<br/>**说明：** <br/>StyledString的子类 [MutableStyledString](arkts-arkui-mutablestyledstring-c.md)也可以作为入参值。 |

