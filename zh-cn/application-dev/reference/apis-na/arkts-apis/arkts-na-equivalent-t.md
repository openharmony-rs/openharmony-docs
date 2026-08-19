# Equivalent

```TypeScript
export type Equivalent<T> = (oldV: T, newV: T) => boolean
```

Determine whether two values are equal.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type Equivalent<T> = (oldV: T, newV: T) => boolean--><!--Device-unnamed-export type Equivalent<T> = (oldV: T, newV: T) => boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oldV | T | 是 | the old value |
| newV | T | 是 | the new value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns the comparison result between old value and new value, if they are equal, return true; otherwise, return false. |

