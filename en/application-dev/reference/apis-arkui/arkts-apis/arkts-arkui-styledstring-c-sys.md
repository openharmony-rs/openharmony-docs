# StyledString

```TypeScript
declare class StyledString
```

StyledString

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## marshalling

```TypeScript
static marshalling(styledString: StyledString, callback: StyledStringMarshallCallback): ArrayBuffer
```

Marshals a styled string by defining a callback to marshal [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md).

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| styledString | [StyledString](arkts-arkui-styledstring-c.md) | Yes | Styled string to marshal. |
| callback | [StyledStringMarshallCallback](arkts-arkui-styledstringmarshallcallback-t-sys.md) | Yes | Callback defining how to marshal [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| ArrayBuffer | Buffer information after marshalling.<br>**NOTE:** <br>Currently, text and images are supported. |

<a id="marshalling-1"></a>

## marshalling

```TypeScript
static marshalling(styledString: StyledString): ArrayBuffer
```

Marshals a styled string.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| styledString | [StyledString](arkts-arkui-styledstring-c.md) | Yes | Styled string to marshal. |

**Return value:**

| Type | Description |
| --- | --- |
| ArrayBuffer | Buffer information after marshalling.<br>**NOTE:** <br>Currently, text and images are supported. |

## unmarshalling

```TypeScript
static unmarshalling(buffer: ArrayBuffer, callback: StyledStringUnmarshallCallback): Promise<StyledString>
```

Unmarshals a styled string by defining a callback to [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md).

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | Yes | Data marshaled from a styled string. |
| callback | [StyledStringUnmarshallCallback](arkts-arkui-styledstringunmarshallcallback-t-sys.md) | Yes | Callback defining how to marshal **ArrayBuffer**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[StyledString](arkts-arkui-styledstring-c.md)&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [170002](../errorcode-styled-string.md#170002-styled-string-decoding-error) | Styled string decode error. |

<a id="unmarshalling-1"></a>

## unmarshalling

```TypeScript
static unmarshalling(buffer: ArrayBuffer): Promise<StyledString>
```

Unmarshals a buffer to obtain a styled string.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | Yes | Data marshaled from a styled string. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[StyledString](arkts-arkui-styledstring-c.md)&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [170002](../errorcode-styled-string.md#170002-styled-string-decoding-error) | Styled string decode error. |
