# StyledStringUnmarshallCallback（系统接口）

```TypeScript
declare type StyledStringUnmarshallCallback = (buf: ArrayBuffer) => StyledStringMarshallingValue
```

属性字符串反序列化ArrayBuffer得到[StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md)回调类型。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md)序列化后的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| StyledStringMarshallingValue | 反序列化得到的[StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md) 。 |

