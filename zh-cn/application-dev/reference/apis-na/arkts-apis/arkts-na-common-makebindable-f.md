# makeBindable

## makeBindable

```TypeScript
export declare function makeBindable<T>(value: T, onChange: Callback<T>): Bindable<T>
```

Create a bindable property instance.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function makeBindable<T>(value: T, onChange: Callback<T>): Bindable<T>--><!--Device-unnamed-export declare function makeBindable<T>(value: T, onChange: Callback<T>): Bindable<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | indicates the value of a state property. |
| onChange | [Callback](arkts-na-callback-t.md)&lt;T&gt; | 是 | indicates the invoked callback when the property is changed. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Bindable](arkts-na-common-bindable-i.md)&lt;T&gt; | bindable property instance. |

