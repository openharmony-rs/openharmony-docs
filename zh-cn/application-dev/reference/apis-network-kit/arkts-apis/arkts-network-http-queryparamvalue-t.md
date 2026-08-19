# QueryParamValue

```TypeScript
export type QueryParamValue = string | int | boolean | null | undefined
```

QueryParamObject中允许使用的单个参数值类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-http-export type QueryParamValue = string | int | boolean | null | undefined--><!--Device-http-export type QueryParamValue = string | int | boolean | null | undefined-End-->

**系统能力：** SystemCapability.Communication.NetStack

| 类型 | 说明 |
| --- | --- |
| string | 字符串类型。 |
| int | 数字类型，会先转为字符串再参与编码。 |
| boolean | 布尔类型，会先转为字符串再参与编码。 |
| null | 空值类型，会按仅key不带`=`值的形式序列化。 |
| undefined | 未定义类型，会按仅key不带`=`值的形式序列化。 |

