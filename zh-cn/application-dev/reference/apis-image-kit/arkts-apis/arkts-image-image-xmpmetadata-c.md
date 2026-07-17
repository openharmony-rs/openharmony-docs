# XMPMetadata

XMPMetadata instance.

**起始版本：** 26.0.0

<!--Device-image-class XMPMetadata--><!--Device-image-class XMPMetadata-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

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

<!--Device-XMPMetadata-public enumerateTags(
      callback: (path: string, tag: XMPTag) => boolean,
      rootPath?: string,
      options?: XMPEnumerateOptions
    ): void--><!--Device-XMPMetadata-public enumerateTags(
      callback: (path: string, tag: XMPTag) => boolean,
      rootPath?: string,
      options?: XMPEnumerateOptions
    ): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (path: string, tag: XMPTag) => boolean | 是 | Callback used to return the XMP node and the corresponding XMPTag.The callback receives a path argument that follows the XMP namespace:path format. |
| rootPath | string | 否 | Enumerate root path. If this parameter is not specified, the default value is root path. |
| options | [XMPEnumerateOptions](arkts-image-image-xmpenumerateoptions-i.md) | 否 | XMP enumerate option. |

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

<!--Device-XMPMetadata-public getBlob(): Promise<ArrayBuffer>--><!--Device-XMPMetadata-public getBlob(): Promise<ArrayBuffer>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ArrayBuffer> | A Promise instance used to return the ArrayBuffer of blob. |

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

<!--Device-XMPMetadata-public getTag(path: string): Promise<XMPTag | null>--><!--Device-XMPMetadata-public getTag(path: string): Promise<XMPTag | null>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | The specified path of the target XMP tag.(e.g., "dc:title"). |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<XMPTag \| null> | Promise used to return the XMP tag. |

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

<!--Device-XMPMetadata-public getTags(rootPath?: string, options?: XMPEnumerateOptions): Promise<Record<string, XMPTag>>--><!--Device-XMPMetadata-public getTags(rootPath?: string, options?: XMPEnumerateOptions): Promise<Record<string, XMPTag>>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rootPath | string | 否 | The specified path. If this parameter is not specified, the default value is root path. |
| options | [XMPEnumerateOptions](arkts-image-image-xmpenumerateoptions-i.md) | 否 | XMP enumerate option. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Record<string, XMPTag>> | A Promise instance used to return all XMP tags. |

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

<!--Device-XMPMetadata-public registerXMPNamespace(xmpNamespace: XMPNamespace): Promise<void>--><!--Device-XMPMetadata-public registerXMPNamespace(xmpNamespace: XMPNamespace): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xmpNamespace | [XMPNamespace](arkts-image-image-xmpnamespace-i.md) | 是 | The xmp namespace. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

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

<!--Device-XMPMetadata-public removeTag(path: string): Promise<void>--><!--Device-XMPMetadata-public removeTag(path: string): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | The specified path of the target XMP tag.(e.g., "dc:title"). |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

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

<!--Device-XMPMetadata-public setBlob(buffer: ArrayBuffer): Promise<void>--><!--Device-XMPMetadata-public setBlob(buffer: ArrayBuffer): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | blob data. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

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

<!--Device-XMPMetadata-public setValue(path: string, type: XMPTagType, value?: string): Promise<void>--><!--Device-XMPMetadata-public setValue(path: string, type: XMPTagType, value?: string): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | The specified path of the target XMP tag.(e.g., "dc:title"). |
| type | [XMPTagType](arkts-image-image-xmptagtype-e.md) | 是 | The specified XMP tag type. |
| value | string | 否 | The specified value. If this parameter is not specified, the default value is empty. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid argument. Possible causes: 1. Namespace is not registered.2. The path syntax is invalid. 3. The path does not match the type. 4. The value is invalid for the type. |

