# StyledString

属性字符串。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare class StyledString--><!--Device-unnamed-declare class StyledString-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## marshalling

```TypeScript
static marshalling(styledString: StyledString, callback: StyledStringMarshallCallback): ArrayBuffer
```

序列化属性字符串，通过定义回调来序列化属性字符串的[StyledStringMarshallingValue]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。 当属性字符串包含UserDataSpan等自定义样式，需要自定义序列化逻辑时使用此方法；不包含自定义样式时使用基础版marshalling方法即可。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyledString-static marshalling(styledString: StyledString, callback: StyledStringMarshallCallback): ArrayBuffer--><!--Device-StyledString-static marshalling(styledString: StyledString, callback: StyledStringMarshallCallback): ArrayBuffer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 待序列化的属性字符串对象，包含文本内容及样式信息。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 用于序列化[StyledStringMarshallingValue]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_的回调函数。回调函数签名：(marshallableVal: StyledStringMarshallingValue) => ArrayBuffer，其中marshallableVal为需要序列化的对象，返回值为序列化后的ArrayBuffer数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | 序列化后的buffer信息。 |

## marshalling

```TypeScript
static marshalling(styledString: StyledString): ArrayBuffer
```

序列化属性字符串。适用于将属性字符串持久化存储或跨进程、跨组件传递时使用。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyledString-static marshalling(styledString: StyledString): ArrayBuffer--><!--Device-StyledString-static marshalling(styledString: StyledString): ArrayBuffer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要序列化的属性字符串对象，包含文本内容及样式信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | 序列化后的buffer信息。 |

## unmarshalling

```TypeScript
static unmarshalling(buffer: ArrayBuffer, callback: StyledStringUnmarshallCallback): Promise<StyledString>
```

反序列化后得到属性字符串，通过定义回调来反序列化[StyledStringMarshallingValue]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。 当需要从序列化数据中恢复包含UserDataSpan等自定义样式的属性字符串时使用此方法；恢复不含自定义样式的属性字符串时使用基础版unmarshalling方法即可。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyledString-static unmarshalling(buffer: ArrayBuffer, callback: StyledStringUnmarshallCallback): Promise<StyledString>--><!--Device-StyledString-static unmarshalling(buffer: ArrayBuffer, callback: StyledStringUnmarshallCallback): Promise<StyledString>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | 是 | 属性字符串序列化后的数据。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 用于反序列化ArrayBuffer的回调函数。回调函数签名：(buf: ArrayBuffer) => StyledStringMarshallingValue，其中buf为序列化后的数据，返回值为反序列化得到的StyledStringMarshallingValue对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;StyledString&gt; | Promise对象，成功时返回属性字符串，失败时返回错误码，详见错误码部分。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 2. Incorrect parameters types.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 3. Parameter verification failed. |
| [170002](../errorcode-styled-string.md#170002-属性字符串解码错误) | Styled string decode error. |

## unmarshalling

```TypeScript
static unmarshalling(buffer: ArrayBuffer): Promise<StyledString>
```

反序列化后得到属性字符串。 适用于从已序列化的数据中恢复属性字符串时使用，如从本地存储读取或接收跨进程传递的数据后恢复属性字符串。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyledString-static unmarshalling(buffer: ArrayBuffer): Promise<StyledString>--><!--Device-StyledString-static unmarshalling(buffer: ArrayBuffer): Promise<StyledString>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | 是 | 属性字符串序列化后的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;StyledString&gt; | Promise对象，成功时返回属性字符串，失败时返回错误码，详见错误码部分。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 2. Incorrect parameters types.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 3. Parameter verification failed. |
| [170002](../errorcode-styled-string.md#170002-属性字符串解码错误) | Styled string decode error. |

