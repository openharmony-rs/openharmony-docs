# StyledString

属性字符串

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class StyledString--><!--Device-unnamed-export declare class StyledString-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## marshalling

```TypeScript
static marshalling(styledString: StyledString, callback: StyledStringMarshallCallback):
        ArrayBuffer | undefined
```

序列化属性字符串，通过定义回调来序列化属性字符串的StyledStringMarshallingValue。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyledString-static marshalling(styledString: StyledString, callback: StyledStringMarshallCallback):        ArrayBuffer | undefined--><!--Device-StyledString-static marshalling(styledString: StyledString, callback: StyledStringMarshallCallback):        ArrayBuffer | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | [StyledString](arkts-arkui-styledstring-styledstring-c.md) | 是 | 属性字符串参数。 |
| callback | [StyledStringMarshallCallback](arkts-arkui-styledstringmarshallcallback-t-sys.md) | 是 | 如何序列化StyledStringMarshallingValue的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer |  |

## marshalling

```TypeScript
static marshalling(styledString: StyledString): ArrayBuffer | undefined
```

序列化属性字符串。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyledString-static marshalling(styledString: StyledString): ArrayBuffer | undefined--><!--Device-StyledString-static marshalling(styledString: StyledString): ArrayBuffer | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | [StyledString](arkts-arkui-styledstring-styledstring-c.md) | 是 | 属性字符串参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer |  |

## unmarshalling

```TypeScript
static unmarshalling(buffer: ArrayBuffer, callback: StyledStringUnmarshallCallback):
        Promise<StyledString | undefined>
```

反序列化后得到属性字符串，通过定义回调来反序列化StyledStringMarshallingValue。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyledString-static unmarshalling(buffer: ArrayBuffer, callback: StyledStringUnmarshallCallback):        Promise<StyledString | undefined>--><!--Device-StyledString-static unmarshalling(buffer: ArrayBuffer, callback: StyledStringUnmarshallCallback):        Promise<StyledString | undefined>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | 是 | 属性字符串序列化后的数据。 |
| callback | [StyledStringUnmarshallCallback](arkts-arkui-styledstringunmarshallcallback-t-sys.md) | 是 | 如何反序列化ArrayBuffer的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[StyledString](arkts-arkui-styledstring-styledstring-c.md) \| undefined&gt; |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [170002](../errorcode-styled-string.md#170002-属性字符串解码错误) | Styled string decode error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## unmarshalling

```TypeScript
static unmarshalling(buffer: ArrayBuffer): Promise<StyledString | undefined>
```

反序列化后得到属性字符串。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyledString-static unmarshalling(buffer: ArrayBuffer): Promise<StyledString | undefined>--><!--Device-StyledString-static unmarshalling(buffer: ArrayBuffer): Promise<StyledString | undefined>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | 是 | 属性字符串序列化后的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[StyledString](arkts-arkui-styledstring-styledstring-c.md) \| undefined&gt; |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [170002](../errorcode-styled-string.md#170002-属性字符串解码错误) | Styled string decode error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

