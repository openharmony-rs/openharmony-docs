# KeyGeneratorFunc

```TypeScript
type KeyGeneratorFunc<T> = (item: T, index: int) => string
```

键值生成函数类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type KeyGeneratorFunc<T> = (item: T, index: int) => string--><!--Device-unnamed-type KeyGeneratorFunc<T> = (item: T, index: int) => string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | T | 是 | \_\_\_INLINE\_CODE\_USD\_0\_\_\_数组中的数据项。  |
| index | int | 是 | \_\_\_INLINE\_CODE\_USD\_0\_\_\_数组中的数据项索引。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | key value. |

