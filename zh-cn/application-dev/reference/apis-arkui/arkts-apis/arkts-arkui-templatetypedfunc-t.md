# TemplateTypedFunc

```TypeScript
declare type TemplateTypedFunc<T> = (item: T, index: number) => string
```

渲染模版类型字符串获取函数类型。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type TemplateTypedFunc<T> = (item: T, index: number) => string--><!--Device-unnamed-declare type TemplateTypedFunc<T> = (item: T, index: number) => string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | T | 是 | arr中每一个数据项。T为开发者传入的数据类型。<br/>缺省时默认忽略该参数，请勿在闭包函数的实现中使用该参数，否则会编译报错。  |
| index | number | 是 | 当前数据项对应的索引。<br/>缺省时默认忽略该参数，请勿在闭包函数的实现中使用该参数，否则会编译报错。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | template type.  |

