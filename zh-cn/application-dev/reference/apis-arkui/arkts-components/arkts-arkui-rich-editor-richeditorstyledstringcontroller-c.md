# RichEditorStyledStringController

使用属性字符串构建的RichEditor组件的控制器，继承自[RichEditorBaseController](arkts-arkui-rich-editor-richeditorbasecontroller-c.md)。

## 导入对象

```ts
controller: RichEditorStyledStringController = new RichEditorStyledStringController();
```

**继承/实现关系：** RichEditorStyledStringController extends [RichEditorBaseController](arkts-arkui-rich-editor-richeditorbasecontroller-c.md) implements [StyledStringController](../arkts-apis/arkts-arkui-text-common-styledstringcontroller-i.md)

**起始版本：** 12

<!--Device-unnamed-declare class RichEditorStyledStringController extends RichEditorBaseController implements StyledStringController--><!--Device-unnamed-declare class RichEditorStyledStringController extends RichEditorBaseController implements StyledStringController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getSelection

```TypeScript
getSelection(): RichEditorRange
```

获取富文本当前的选中区域范围。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorStyledStringController-getSelection(): RichEditorRange--><!--Device-RichEditorStyledStringController-getSelection(): RichEditorRange-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RichEditorRange](arkts-arkui-rich-editor-richeditorrange-i.md) | 选中区域范围。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## getStyledString

```TypeScript
getStyledString(): MutableStyledString
```

获取富文本组件显示的属性字符串。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorStyledStringController-getStyledString(): MutableStyledString--><!--Device-RichEditorStyledStringController-getStyledString(): MutableStyledString-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MutableStyledString](../arkts-apis/arkts-arkui-styled-string-mutablestyledstring-c.md) | 富文本组件显示的属性字符串。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## onContentChanged

```TypeScript
onContentChanged(listener: StyledStringChangedListener): void
```

注册文本内容变化回调，该回调仅在后端程序导致文本内容变更时触发，调用[setStyledString](arkts-arkui-rich-editor-richeditorstyledstringcontroller-c.md#setstyledstring-1)时不会触发。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorStyledStringController-onContentChanged(listener: StyledStringChangedListener): void--><!--Device-RichEditorStyledStringController-onContentChanged(listener: StyledStringChangedListener): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| listener | [StyledStringChangedListener](../arkts-apis/arkts-arkui-text-common-styledstringchangedlistener-i.md) | 是 | 文本内容变化回调监听器。 |

## setStyledString

```TypeScript
setStyledString(styledString: StyledString): void
```

设置富文本组件显示的属性字符串。

> **说明：**  
>  
> - 调用该接口时，会全量替换富文本组件的StyledString，并重新渲染。  
>  
> - 当内容超过组件本身区域时，组件会自动向上滚动内容直到末尾处可见。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorStyledStringController-setStyledString(styledString: StyledString): void--><!--Device-RichEditorStyledStringController-setStyledString(styledString: StyledString): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | [StyledString](../arkts-apis/arkts-arkui-styled-string-styledstring-c.md) | 是 | 属性字符串。<br/>**说明：** <br/>StyledString的子类[MutableStyledString](../arkts-apis/arkts-arkui-styled-string-mutablestyledstring-c.md)也可以作为入参值。 |

