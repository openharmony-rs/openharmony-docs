# Transformer

```TypeScript
type Transformer = (this: ISendable, key: string,
      value: ISendable | undefined | null) => ISendable | undefined | null
```

转换结果函数的类型。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ASON-type Transformer = (this: ISendable, key: string,      value: ISendable | undefined | null) => ISendable | undefined | null--><!--Device-ASON-type Transformer = (this: ISendable, key: string,      value: ISendable | undefined | null) => ISendable | undefined | null-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| this | [ISendable](arkts-arkts-ason-isendable-t.md) | 是 | 所解析的键值对所属的ISendable对象。  |
| key | string | 是 | 属性名。  |
| value | [ISendable](arkts-arkts-ason-isendable-t.md) \| undefined \| null | 是 | 所解析的键值对的值。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ISendable](arkts-arkts-ason-isendable-t.md) \| undefined \| null | 返回修改后的ISendable对象或undefined或null。  |

