# SendableTransformer

```TypeScript
type SendableTransformer = (this: ISendable, key: string,
    value: ISendable | undefined | null) => ISendable | undefined | null
```

定义Sendable JSON解析的转换结果函数类型。

用于Sendable JSON解析转换结果的函数类型，与[ArkTSUtils.ASON.Transformer](arkts-arkts-json-transformer-t.md)一致：this、value及返回值均为ISendable（而非Object），因为[parseSendable](arkts-arkts-json-parsesendable-f.md)的产物为可跨线程共享的Sendable对象。当前[parseSendable](arkts-arkts-json-parsesendable-f.md)仅接受undefined，传入函数会抛出TypeError。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-json-type SendableTransformer = (this: ISendable, key: string,    value: ISendable | undefined | null) => ISendable | undefined | null--><!--Device-json-type SendableTransformer = (this: ISendable, key: string,    value: ISendable | undefined | null) => ISendable | undefined | null-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| this | [ISendable](arkts-arkts-json-isendable-t.md) | 是 | 解析中的键值对所属的ISendable对象。 |
| key | string | 是 | 属性名。 |
| value | [ISendable](arkts-arkts-json-isendable-t.md) &#124; undefined &#124; null | 是 | 解析中的键值对的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ISendable](arkts-arkts-json-isendable-t.md) &#124; undefined &#124; null | 返回修改后的ISendable、undefined或null。 |
