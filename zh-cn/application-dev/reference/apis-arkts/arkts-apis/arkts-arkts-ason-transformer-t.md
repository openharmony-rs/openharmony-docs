# Transformer

```TypeScript
type Transformer = (this: ISendable, key: string,
      value: ISendable | undefined | null) => ISendable | undefined | null
```

用于转换结果函数的类型。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ASON-type Transformer = (this: ISendable, key: string,      value: ISendable | undefined | null) => ISendable | undefined | null--><!--Device-ASON-type Transformer = (this: ISendable, key: string,      value: ISendable | undefined | null) => ISendable | undefined | null-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| this | ISendable | 是 | 所解析的键值对所属的对象。 |
| key | string | 是 | 属性名。 |
| value | ISendable \| undefined \| null | 是 | 所解析的键值对的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ISendable \| undefined \| null | 返回转换结果后的ISendable对象或undefined或null。 |

