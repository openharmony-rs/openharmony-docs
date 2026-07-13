# compare

## compare

```TypeScript
function compare(buf1: FastBuffer | Uint8Array, buf2: FastBuffer | Uint8Array): -1 | 0 | 1
```

返回两个FastBuffer对象的比较结果，通常用于对FastBuffer对象数组进行排序。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf1 | FastBuffer \| Uint8Array | 是 | 待比较的第一个对象。 |
| buf2 | FastBuffer \| Uint8Array | 是 | 待比较的第二个对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| -1 | 如果buf1与buf2相同，则返回0。<br/>如果排序时buf1位于buf2之后，则返回1。<br/>如果排序时buf1位于buf2之前，则返回-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200068](../errorcode-utils.md#10200068-引用已释放或分离的arraybuffer) | The underlying ArrayBuffer is null or detach. |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from('1234');
let buf2 = fastbuffer.from('0123');
let res = fastbuffer.compare(buf1, buf2);

console.info(Number(res).toString());
// 输出结果：1

```

