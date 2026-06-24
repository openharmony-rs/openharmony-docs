# StyledString

StyledString

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## marshalling

```TypeScript
static marshalling(styledString: StyledString, callback: StyledStringMarshallCallback): ArrayBuffer
```

序列化属性字符串，通过定义回调来序列化属性字符串的[StyledStringMarshallingValue](arkts-arkui-styled-string-styledstringmarshallingvalue-t-sys.md#StyledStringMarshallingValue)。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | StyledString | 是 | 属性字符串参数。 |
| callback | StyledStringMarshallCallback | 是 | 如何序列化[StyledStringMarshallingValue](arkts-arkui-styled-string-styledstringmarshallingvalue-t-sys.md#StyledStringMarshallingValue)的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | 序列化后的buffer信息。<br/>**说明：**<br/>目前支持文本和图片。 |

## marshalling

```TypeScript
static marshalling(styledString: StyledString): ArrayBuffer
```

序列化属性字符串。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | StyledString | 是 | 属性字符串参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | 序列化后的buffer信息。<br/>**说明：**<br/>目前支持文本和图片。 |

## unmarshalling

```TypeScript
static unmarshalling(buffer: ArrayBuffer, callback: StyledStringUnmarshallCallback): Promise<StyledString>
```

反序列化后得到属性字符串，通过定义回调来反序列化[StyledStringMarshallingValue](arkts-arkui-styled-string-styledstringmarshallingvalue-t-sys.md#StyledStringMarshallingValue)。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | 是 | 属性字符串序列化后的数据。 |
| callback | StyledStringUnmarshallCallback | 是 | 如何反序列化ArrayBuffer的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;StyledString&gt; | Promise对象，返回属性字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [170002](../../errorcode-universal.md#170002-Styled) | Styled string decode error. |

## unmarshalling

```TypeScript
static unmarshalling(buffer: ArrayBuffer): Promise<StyledString>
```

反序列化后得到属性字符串。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | 是 | 属性字符串序列化后的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;StyledString&gt; | Promise对象，返回属性字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [170002](../../errorcode-universal.md#170002-Styled) | Styled string decode error. |

