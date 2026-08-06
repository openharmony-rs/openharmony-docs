# concat

## concat

```TypeScript
function concat(list: Buffer[] | Uint8Array[], totalLength?: int): Buffer
```

将数组中的内容复制（默认复制全部内容，或复制指定字节长度）到新的Buffer对象中并返回。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function concat(list: Buffer[] | Uint8Array[], totalLength?: int): Buffer--><!--Device-buffer-function concat(list: Buffer[] | Uint8Array[], totalLength?: int): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| list | Buffer[] \| Uint8Array[] | 是 | Buffer或Uint8Array实例数组，用于拼接合并创建新的Buffer对象。 |
| totalLength | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 否 | 需要复制的总字节长度，默认值为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回新的Buffer对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "length" is out of range. It must be >= 0 and <= uint32 max.Received value is: [length] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from("1234");
let buf2 = buffer.from("abcd");
let buf = buffer.concat([buf1, buf2]);
console.info(buf.toString('hex'));
// 输出结果：3132333461626364
```

