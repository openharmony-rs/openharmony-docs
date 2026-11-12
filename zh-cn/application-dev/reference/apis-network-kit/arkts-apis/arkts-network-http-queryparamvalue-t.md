# QueryParamValue

```TypeScript
export type QueryParamValue = string | number | boolean | null | undefined
```

QueryParamObject中允许使用的单个参数值类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-http-export type QueryParamValue = string | int | boolean | null | undefined--><!--Device-http-export type QueryParamValue = string | int | boolean | null | undefined-End-->

**系统能力：** SystemCapability.Communication.NetStack

| 类型 | 说明 |
| --- | --- |
| string | String type. |
| int | Number type, which is converted into a string before being encoded. |
| boolean | Boolean type, which is converted into a string before being encoded. |
| null | Null type, which is serialized in the format of only the key without the = value. |
| undefined | Undefined type, which is serialized in the format of only the key without the = value. |
