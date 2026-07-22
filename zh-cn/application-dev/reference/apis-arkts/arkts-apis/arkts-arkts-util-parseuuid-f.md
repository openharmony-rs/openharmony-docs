# parseUUID

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## parseUUID

```TypeScript
function parseUUID(uuid: string): Uint8Array
```

将 **generateRandomUUID** 生成的字符串类型的 UUID 转换为 **generateRandomBinaryUUID** 生成的 UUID，如 RFC 4122所述。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-util-function parseUUID(uuid: string): Uint8Array--><!--Device-util-function parseUUID(uuid: string): Uint8Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uuid | string | 是 | 表示 UUID 的字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 表示解析后 UUID 的 Uint8Array 值。如果解析失败，则抛出 **SyntaxError**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200002](../errorcode-utils.md#10200002-参数解析错误) | Invalid uuid string. |

**示例：**

```TypeScript
let uuid = util.parseUUID("84bdf796-66cc-4655-9b89-d6218d100f9c");
console.info("uuid = " + uuid);
// 输出结果：uuid = 132,189,247,150,102,204,70,85,155,137,214,33,141,16,15,156

```

