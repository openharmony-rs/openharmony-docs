# generateRandomBinaryUUID

## generateRandomBinaryUUID

```TypeScript
function generateRandomBinaryUUID(entropyCache?: boolean): Uint8Array | undefined
```

Generate a random RFC 4122 version 4 binary UUID using a cryptographically secure random number generator.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-util-function generateRandomBinaryUUID(entropyCache?: boolean): Uint8Array | undefined--><!--Device-util-function generateRandomBinaryUUID(entropyCache?: boolean): Uint8Array | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| entropyCache | boolean | 否 | Whether to generate the UUID with using the cache. Default: true. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | Return a Uint8Array representing this UUID, or undefined on failure. |

