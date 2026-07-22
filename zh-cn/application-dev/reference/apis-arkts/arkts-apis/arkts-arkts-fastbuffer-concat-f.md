# concat

## 导入模块

```TypeScript
import { fastbuffer } from '@kit.ArkTS';
```

## concat

```TypeScript
function concat(list: FastBuffer[] | Uint8Array[], totalLength?: number): FastBuffer
```

将数组中指定字节长度的内容复制到新的FastBuffer对象中并返回拼接后的FastBuffer对象。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-fastbuffer-function concat(list: FastBuffer[] | Uint8Array[], totalLength?: number): FastBuffer--><!--Device-fastbuffer-function concat(list: FastBuffer[] | Uint8Array[], totalLength?: number): FastBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| list | FastBuffer[] \| Uint8Array[] | 是 | 实例数组。 |
| totalLength | number | 否 | 需要复制的总字节长度，默认值为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | 返回新的FastBuffer对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | Range error. Possible causes:The value of the parameter is not within the specified range. |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from('1234');
let buf2 = fastbuffer.from('abcd');
let buf = fastbuffer.concat([buf1, buf2]);
console.info(buf.toString('hex'));
// 输出结果：3132333461626364

```

