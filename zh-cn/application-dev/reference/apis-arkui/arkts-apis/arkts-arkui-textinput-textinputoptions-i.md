# TextInputOptions

TextInput初始化参数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface TextInputOptions--><!--Device-unnamed-export declare interface TextInputOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TextInputController
```

设置TextInput控制器。

**类型：** [TextInputController](arkts-arkui-textinput-textinputcontroller-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextInputOptions-controller?: TextInputController--><!--Device-TextInputOptions-controller?: TextInputController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

设置无输入时的提示文本。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextInputOptions-placeholder?: ResourceStr--><!--Device-TextInputOptions-placeholder?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr | Bindable<ResourceStr> | Bindable<Resource> | Bindable<string>
```

输入框文本内容。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md) \| [Bindable](../../apis-na/arkts-apis/arkts-na-common-bindable-i.md)&lt;[ResourceStr](arkts-arkui-resourcestr-t.md)&gt; \| [Bindable](../../apis-na/arkts-apis/arkts-na-common-bindable-i.md)&lt;[Resource](arkts-arkui-resource-t.md)&gt; \| [Bindable](../../apis-na/arkts-apis/arkts-na-common-bindable-i.md)&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextInputOptions-text?: ResourceStr | Bindable<ResourceStr> | Bindable<Resource> | Bindable<string>--><!--Device-TextInputOptions-text?: ResourceStr | Bindable<ResourceStr> | Bindable<Resource> | Bindable<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

