# IncrementalScope

Define the IncrementalScope interface to manage state management.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface IncrementalScope<Value>--><!--Device-unnamed-export declare interface IncrementalScope<Value>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## param

```TypeScript
param<T>(index: int, value: T): ReadableState<T>
```

创建状态变量参数

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IncrementalScope-param<T>(index: int, value: T): ReadableState<T>--><!--Device-IncrementalScope-param<T>(index: int, value: T): ReadableState<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 |  |
| value | T | 是 | 初始值 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | return state variable Value |

## recache

```TypeScript
recache(newValue?: Value): Value
```

Internal value updated after the computation.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IncrementalScope-recache(newValue?: Value): Value--><!--Device-IncrementalScope-recache(newValue?: Value): Value-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | new value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | return the Value from cached |

## cached

```TypeScript
get cached(): Value
```

State variable cache, internal value if it is already computed

**类型：** Value

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IncrementalScope-get cached(): Value--><!--Device-IncrementalScope-get cached(): Value-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## unchanged

```TypeScript
get unchanged(): boolean
```

Get the flag whether the state variable is changed, true if internal value can be returned as is

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IncrementalScope-get unchanged(): boolean--><!--Device-IncrementalScope-get unchanged(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

