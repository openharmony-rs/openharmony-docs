# compare

## 导入模块

```TypeScript
import { buffer } from '@kit.ArkTS';
```

## compare

```TypeScript
function compare(buf1: Buffer | Uint8Array, buf2: Buffer | Uint8Array): -1 | 0 | 1
```

返回两个Buffer对象的比较结果，通常用于对Buffer对象数组进行排序。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function compare(buf1: Buffer | Uint8Array, buf2: Buffer | Uint8Array): -1 | 0 | 1--><!--Device-buffer-function compare(buf1: Buffer | Uint8Array, buf2: Buffer | Uint8Array): -1 | 0 | 1-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf1 | Buffer \| Uint8Array | 是 | 待比较数组。 |
| buf2 | Buffer \| Uint8Array | 是 | 待比较数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| -1 | 如果buf1与buf2相同，则返回0。<br/>如果排序时buf1位于buf2之后，则返回1。<br/>如果排序时buf1位于buf2之前，则返回-1。 |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from('1234');
let buf2 = buffer.from('0123');
let res = buffer.compare(buf1, buf2);

console.info(Number(res).toString());
// 输出结果：1

```

