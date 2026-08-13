# parseUUID

## parseUUID

```TypeScript
function parseUUID(uuid: string): Uint8Array
```

将generateRandomUUID生成的string类型UUID转换为[generateRandomBinaryUUID](arkts-arkts-util-generaterandombinaryuuid-f.md#generateRandomBinaryUUID)生成的UUID， 符合RFC 4122版本规范。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-util-function parseUUID(uuid: string): Uint8Array--><!--Device-util-function parseUUID(uuid: string): Uint8Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uuid | string | 是 | UUID字符串，必须符合RFC 4122版本规范。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 返回表示此UUID的Uint8Array，如果解析失败，则抛出异常，错误码为10200002。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200002](../errorcode-utils.md#10200002-参数解析错误) | Invalid uuid string. |

## 示例

```TypeScript
let uuid = util.parseUUID("84bdf796-66cc-4655-9b89-d6218d100f9c");
console.info("uuid = " + uuid);
// 输出结果：uuid = 132,189,247,150,102,204,70,85,155,137,214,33,141,16,15,156
```

