# parseUUID

## parseUUID

```TypeScript
function parseUUID(uuid: string): Uint8Array
```

Parse a UUID from the string standard representation as described in the RFC 4122 version 4.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-util-function parseUUID(uuid: string): Uint8Array--><!--Device-util-function parseUUID(uuid: string): Uint8Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uuid | string | 是 | String that specifies a UUID |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | Return a Uint8Array representing this UUID. Throw SyntaxError if parsing fails. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200002](../errorcode-utils.md#10200002-参数解析错误) | Invalid uuid string. |

