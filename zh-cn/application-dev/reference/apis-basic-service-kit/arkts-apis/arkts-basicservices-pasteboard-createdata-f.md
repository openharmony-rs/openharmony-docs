# createData

## createData

```TypeScript
function createData(mimeType: string, value: ValueType): PasteData
```

构建一个指定类型的剪贴板内容对象，根据传入的MIME类型和数据内容创建PasteData实例。 调用此方法后，系统将验证MIME类型有效性，封装数据内容，并返回可用于后续剪贴板操作的PasteData对象。 参数mimeType长度不能超过1024字节，value类型需与mimeType匹配。当需要将单一类型的数据（如纯文本、HTML、图片等）放入剪贴板时使用此方法。 mimeType优先使用已定义的常量类型（如MIMETYPE_TEXT_PLAIN），若需要传递自定义格式数据，可使用自定义MIME类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-pasteboard-function createData(mimeType: string, value: ValueType): PasteData--><!--Device-pasteboard-function createData(mimeType: string, value: ValueType): PasteData-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mimeType | string | 是 | 剪贴板数据对应的MIME类型， 可以是[常量](arkts-pasteboard.md#常量)中已定义的类型， 包括HTML类型，Want类型，纯文本类型，URI类型，PixelMap类型；也可以是自定义的MIME类型，开发者可自定义此参数值，mimeType长度不能超过1024字节。 |
| value | ValueType | 是 | 自定义数据内容。建议根据实际场景选择合适的数据类型，使用过大的数据对象会影响应用复制粘贴性能和内存占用。 对于ArrayBuffer类型，建议合理设置数据大小；对于PixelMap类型，建议及时释放不再使用的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PasteData](arkts-basicservices-pasteboard-pastedata-i.md) | 剪贴板内容对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed. |


## createData

```TypeScript
function createData(data: Record<string, ValueType>): PasteData
```

构建一个包含多个类型数据的剪贴板内容对象，支持一次创建多个MIME类型的数据条目。 调用此方法后，系统将解析Record中的多个key-value对，创建多个PasteDataRecord条目，首个MIME类型作为默认类型。 非默认类型数据需通过[getData](arkts-basicservices-pasteboard-pastedatarecord-i.md#getData)接口读取。 应用需要将多种不同类型的数据(如文本、URI、HTML等)同时复制到剪贴板时，可使用此接口一次性构建包含多个MIME类型数据的剪贴板内容对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-pasteboard-function createData(data: Record<string, ValueType>): PasteData--><!--Device-pasteboard-function createData(data: Record<string, ValueType>): PasteData-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, ValueType&gt; | 是 | Record的key为剪贴板数据对应的MIME类型。 可以是[常量](arkts-pasteboard.md#常量)中已定义的类型， 包括HTML类型，Want类型，纯文本类型，URI类型，PixelMap类型。也可以是自定义的MIME类型，可自定义此参数值，mimeType长度不能超过1024字节。 Record的value为key中指定MIME类型对应的数据。 Record中的首个key-value指定的MIME类型，会作为剪贴板内容对象中首个PasteDataRecord的默认MIME类型， 非默认类型的数据在粘贴时只能使用[getData](arkts-basicservices-pasteboard-pastedatarecord-i.md#getData)接口读取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PasteData](arkts-basicservices-pasteboard-pastedata-i.md) | 剪贴板内容对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed. |

