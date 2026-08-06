# StyledStringMarshallCallback（系统接口）

```TypeScript
declare type StyledStringMarshallCallback = (marshallableVal: StyledStringMarshallingValue) => ArrayBuffer
```

属性字符串[StyledStringMarshallingValue]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_序列化回调类型。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare type StyledStringMarshallCallback = (marshallableVal: StyledStringMarshallingValue) => ArrayBuffer--><!--Device-unnamed-declare type StyledStringMarshallCallback = (marshallableVal: StyledStringMarshallingValue) => ArrayBuffer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| marshallableVal | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 属性字符串中需要自定义序列化的UserDataSpan对象。开发者在回调函数中根据此参数的类型，选择对应的序列化接口将 其转换为ArrayBuffer。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | [StyledStringMarshallingValue]{ |

