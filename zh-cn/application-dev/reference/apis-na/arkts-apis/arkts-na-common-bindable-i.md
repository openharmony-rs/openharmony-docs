# Bindable

Defines a bindable property

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface Bindable--><!--Device-unnamed-export declare interface Bindable-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
readonly onChange: Callback<T>
```

Defines the callback of the bindable property which will be invoked when the property is changed.

**类型：** [Callback](arkts-na-callback-t.md)&lt;T&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Bindable-readonly onChange: Callback<T>--><!--Device-Bindable-readonly onChange: Callback<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
readonly value: T
```

Defines value of the bindable property.

**类型：** T

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Bindable-readonly value: T--><!--Device-Bindable-readonly value: T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

