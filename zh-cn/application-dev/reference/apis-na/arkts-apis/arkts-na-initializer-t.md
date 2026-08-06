# Initializer

```TypeScript
export type Initializer<T> = (...params: FixedArray<RecordData>) => T
```

可以将属性更新到本地的修饰器。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type Initializer<T> = (...params: FixedArray<RecordData>) => T--><!--Device-unnamed-export type Initializer<T> = (...params: FixedArray<RecordData>) => T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | FixedArray&lt;RecordData&gt; | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

