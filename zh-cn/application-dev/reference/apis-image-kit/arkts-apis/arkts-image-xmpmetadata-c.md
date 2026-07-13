# XMPMetadata

XMPMetadata instance.

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Image.Core

## enumerateTags

```TypeScript
public enumerateTags(
      callback: (path: string, tag: XMPTag) => boolean,
      rootPath?: string,
      options?: XMPEnumerateOptions
    ): void
```

Enumerate the XMP tags from specified path and uses a callback to return the result.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (path: string, tag: XMPTag) =&gt; boolean | 是 | Callback used to return the XMP node and the corresponding XMPTag.The callback receives a path argument that follows the XMP namespace:path format. |
| rootPath | string | 否 | Enumerate root path. If this parameter is not specified, the default value is rootpath. |
| options | XMPEnumerateOptions | 否 | XMP enumerate option. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid argument. Possible causes: 1. Namespace is not registered.2. The rootPath syntax is invalid. |

## getBlob

```TypeScript
public getBlob(): Promise<ArrayBuffer>
```

Obtains the XMP metadata as a blob.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | A Promise instance used to return the ArrayBuffer of blob. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Memory alloc failed. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Memory copy failed. |

## getTag

```TypeScript
public getTag(path: string): Promise<XMPTag | null>
```

Get a single XMP tag from specified path.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | The specified path of the target XMP tag.(e.g., "dc:title"). |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;XMPTag \| null&gt; | Promise used to return the XMP tag. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid argument. Possible causes: 1. Namespace is not registered.2. The path syntax is invalid. |

## getTags

```TypeScript
public getTags(rootPath?: string, options?: XMPEnumerateOptions): Promise<Record<string, XMPTag>>
```

Get all XMP tags from specified path.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rootPath | string | 否 | The specified path. If this parameter is not specified, the default value is rootpath. |
| options | XMPEnumerateOptions | 否 | XMP enumerate option. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;string, XMPTag&gt;&gt; | A Promise instance used to return all XMP tags. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid argument. Possible causes: 1. Namespace is not registered.2. The rootPath syntax is invalid. |

## registerXMPNamespace

```TypeScript
public registerXMPNamespace(xmpNamespace: XMPNamespace): Promise<void>
```

Register a new namespace according to the xml namespace and prefix.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xmpNamespace | XMPNamespace | 是 | The xmp namespace. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, anerror message is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid argument. Possible causes: 1. Invalid namespace format.2. The uri is already registered. 3. The prefix is already registered. |

## removeTag

```TypeScript
public removeTag(path: string): Promise<void>
```

Remove the XMP tag from specified path.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | The specified path of the target XMP tag.(e.g., "dc:title"). |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, anerror message is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid argument. Possible causes: 1. Namespace is not registered.2. The path syntax is invalid. |

## setBlob

```TypeScript
public setBlob(buffer: ArrayBuffer): Promise<void>
```

Set a blob into the XMP metadata.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | 是 | blob data. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, anerror message is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid argument. Possible causes: 1. The buffer is empty or invalid. |

## setValue

```TypeScript
public setValue(path: string, type: XMPTagType, value?: string): Promise<void>
```

Set the XMP type and value of the XMP tag in the specified path.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | The specified path of the target XMP tag.(e.g., "dc:title"). |
| type | XMPTagType | 是 | The specified XMP tag type. |
| value | string | 否 | The specified value. If this parameter is not specified, the default value is empty. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, anerror message is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid argument. Possible causes: 1. Namespace is not registered.2. The path syntax is invalid. 3. The path does not match the type. 4. The value is invalid for the type. |

