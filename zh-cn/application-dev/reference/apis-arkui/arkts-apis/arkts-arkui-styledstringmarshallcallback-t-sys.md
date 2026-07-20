# StyledStringMarshallCallback（系统接口）

```TypeScript
declare type StyledStringMarshallCallback = (marshallableVal: StyledStringMarshallingValue) => ArrayBuffer
```

属性字符串[StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md)序列化回调类型。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare type StyledStringMarshallCallback = (marshallableVal: StyledStringMarshallingValue) => ArrayBuffer--><!--Device-unnamed-declare type StyledStringMarshallCallback = (marshallableVal: StyledStringMarshallingValue) => ArrayBuffer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| marshallableVal | [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md) | 是 | 属性字符串序列化对象。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md)序列化后的数据。  |

