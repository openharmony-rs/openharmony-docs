# AttributeWithTagCb

```TypeScript
type AttributeWithTagCb = (tagName: string, key: string, value: string) => boolean
```

ParseOptions中attributeWithTagCallbackFunction的回调方法，三个字符串参数都是由XML解析器在解析过程中自动提取的，开发者无法直接自定义这些值。开发者只能在回调函数中通过返回值来决定如何处
理这些已存在的属性。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tagName | string | 是 | 当前属性所属XML元素的标签名。 |
| key | string | 是 | 当前属性所属XML元素的名称。 |
| value | string | 是 | 当前属性所属XML元素的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否继续解析xml数据，true表示继续解析数据，false表示结束解析。 |

