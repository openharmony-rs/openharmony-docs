# compare

## compare

```TypeScript
function compare(buf1: Buffer | Uint8Array, buf2: Buffer | Uint8Array): -1 | 0 | 1
```

返回两个Buffer或Uint8Array对象的比较结果，通常用于对Buffer或Uint8Array对象数组进行排序。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function compare(buf1: Buffer | Uint8Array, buf2: Buffer | Uint8Array): -1 | 0 | 1--><!--Device-buffer-function compare(buf1: Buffer | Uint8Array, buf2: Buffer | Uint8Array): -1 | 0 | 1-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf1 | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| Uint8Array | 是 | 待比较的第一个Buffer或Uint8Array实例。 |
| buf2 | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| Uint8Array | 是 | 待比较的第二个Buffer或Uint8Array实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| -1 | 如果buf1与buf2相同，则返回0。 |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from('1234');
let buf2 = buffer.from('0123');
let res = buffer.compare(buf1, buf2);

console.info(Number(res).toString());
// 输出结果：1
```


## compare

```TypeScript
function compare(buf1: Buffer | Uint8Array, buf2: Buffer | Uint8Array): int
```

返回两个Buffer或Uint8Array对象的比较结果，通常用于对Buffer或Uint8Array对象数组进行排序。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function compare(buf1: Buffer | Uint8Array, buf2: Buffer | Uint8Array): int--><!--Device-buffer-function compare(buf1: Buffer | Uint8Array, buf2: Buffer | Uint8Array): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf1 | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| Uint8Array | 是 | 待比较的第一个Buffer或Uint8Array实例。 |
| buf2 | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| Uint8Array | 是 | 待比较的第二个Buffer或Uint8Array实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 如果buf1与buf2相同，则返回0。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_如果排序时buf1位于buf2之后，则返回1。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_如果排序时buf1位于buf2之前，则返回-1。 |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from('1234');
let buf2 = buffer.from('0123');
let res = buffer.compare(buf1, buf2);

console.info(Number(res).toString());
// 输出结果：1
```

