# TextAreaOptions

Defines the options of TextArea.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface TextAreaOptions--><!--Device-unnamed-export declare interface TextAreaOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TextAreaController
```

Called when the position of the insertion cursor is set.

**类型：** TextAreaController

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextAreaOptions-controller?: TextAreaController--><!--Device-TextAreaOptions-controller?: TextAreaController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

The place holder text string. Text displayed when there is no input. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_NOTE\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_: \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_When only the placeholder attribute is set, the text selection handle is still available. \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_The caret stays at the beginning of the placeholder text when the handle is released. \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_

**类型：** ResourceStr

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextAreaOptions-placeholder?: ResourceStr--><!--Device-TextAreaOptions-placeholder?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr | Bindable<ResourceStr> | Bindable<Resource> | Bindable<string>
```

Sets the current value of TextArea.

**类型：** ResourceStr \| Bindable&lt;ResourceStr&gt; \| Bindable&lt;Resource&gt; \| Bindable&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextAreaOptions-text?: ResourceStr | Bindable<ResourceStr> | Bindable<Resource> | Bindable<string>--><!--Device-TextAreaOptions-text?: ResourceStr | Bindable<ResourceStr> | Bindable<Resource> | Bindable<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

