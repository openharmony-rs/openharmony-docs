# TextAreaOptions

Defines the options of TextArea.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface TextAreaOptions--><!--Device-unnamed-export declare interface TextAreaOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TextAreaController
```

Called when the position of the insertion cursor is set.

**类型：** [TextAreaController](arkts-arkui-textarea-textareacontroller-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextAreaOptions-controller?: TextAreaController--><!--Device-TextAreaOptions-controller?: TextAreaController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

The place holder text string. Text displayed when there is no input. &lt;p&gt;&lt;strong&gt;NOTE&lt;/strong&gt;: &lt;br&gt;When only the placeholder attribute is set, the text selection handle is still available. &lt;br&gt;The caret stays at the beginning of the placeholder text when the handle is released. &lt;/p&gt;

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextAreaOptions-placeholder?: ResourceStr--><!--Device-TextAreaOptions-placeholder?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr | Bindable<ResourceStr> | Bindable<Resource> | Bindable<string>
```

Sets the current value of TextArea.

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md) \| [Bindable](../../apis-na/arkts-apis/arkts-na-common-bindable-i.md)&lt;[ResourceStr](arkts-arkui-resourcestr-t.md)&gt; \| [Bindable](../../apis-na/arkts-apis/arkts-na-common-bindable-i.md)&lt;[Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)&gt; \| [Bindable](../../apis-na/arkts-apis/arkts-na-common-bindable-i.md)&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextAreaOptions-text?: ResourceStr | Bindable<ResourceStr> | Bindable<Resource> | Bindable<string>--><!--Device-TextAreaOptions-text?: ResourceStr | Bindable<ResourceStr> | Bindable<Resource> | Bindable<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

