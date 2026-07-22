# Buffer

Buffer对象是处理二进制数据的缓存区。

**起始版本：** 9

<!--Device-buffer-class Buffer--><!--Device-buffer-class Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { buffer } from '@kit.ArkTS';
```

## compare

```TypeScript
compare(
      target: Buffer | Uint8Array,
      targetStart?: number,
      targetEnd?: number,
      sourceStart?: number,
      sourceEnd?: number
    ): -1 | 0 | 1
```

比较当前Buffer对象与目标Buffer对象，并返回Buffer在排序中的结果。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-compare(      target: Buffer | Uint8Array,      targetStart?: number,      targetEnd?: number,      sourceStart?: number,      sourceEnd?: number    ): -1 | 0 | 1--><!--Device-Buffer-compare(      target: Buffer | Uint8Array,      targetStart?: number,      targetEnd?: number,      sourceStart?: number,      sourceEnd?: number    ): -1 | 0 | 1-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | [Buffer](arkts-arkts-buffer-buffer-c.md) \| Uint8Array | 是 | 要比较的实例对象。 |
| targetStart | number | 否 | target实例中开始的偏移量。默认值：0。 |
| targetEnd | number | 否 | target实例中结束的偏移量（不包含结束位置）。默认值：目标对象的字节长度。 |
| sourceStart | number | 否 | this实例中开始的偏移量。默认值：0。 |
| sourceEnd | number | 否 | this实例中结束的偏移量（不包含结束位置）。默认值：当前对象的字节长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| -1 | 比较结果。如果两个Buffer对象相同，则返回0；如果当前对象在排序时位于目标对象之后，则返回1；如果当前对象在排序时位于目标对象之前，则返回-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[targetStart/targetEnd/sourceStart/sourceEnd]" is out of range.It must be >= 0 and <= [right range]. Received value is: [targetStart/targetEnd/sourceStart/sourceEnd] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from([1, 2, 3, 4, 5, 6, 7, 8, 9]);
let buf2 = buffer.from([5, 6, 7, 8, 9, 1, 2, 3, 4]);

console.info(buf1.compare(buf2, 5, 9, 0, 4).toString());
// 输出结果：0
console.info(buf1.compare(buf2, 0, 6, 4).toString());
// 输出结果：-1
console.info(buf1.compare(buf2, 5, 6, 5).toString());
// 输出结果：1

```

## copy

```TypeScript
copy(target: Buffer | Uint8Array, targetStart?: number, sourceStart?: number, sourceEnd?: number): number
```

将this实例中指定位置的数据复制到target的指定位置上，并返回复制的字节总长度。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-copy(target: Buffer | Uint8Array, targetStart?: int, sourceStart?: int, sourceEnd?: int): int--><!--Device-Buffer-copy(target: Buffer | Uint8Array, targetStart?: int, sourceStart?: int, sourceEnd?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | [Buffer](arkts-arkts-buffer-buffer-c.md) \| Uint8Array | 是 | 要复制到的Buffer或Uint8Array实例。 |
| targetStart | number | 否 | target实例中开始写入的偏移量。默认值：0。 |
| sourceStart | number | 否 | this实例中开始复制的偏移量。默认值：0。 |
| sourceEnd | number | 否 | this实例中结束复制的偏移量（不包含结束位置）。默认值：当前对象的字节长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 复制的字节总长度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[targetStart/sourceStart/sourceEnd]" is out of range. It must be >= 0.Received value is: [targetStart/sourceStart/sourceEnd] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.allocUninitializedFromPool(26);
let buf2 = buffer.allocUninitializedFromPool(26).fill('!');

for (let i = 0; i < 26; i++) {
  buf1.writeInt8(i + 97, i);
}

buf1.copy(buf2, 8, 16, 20);
console.info(buf2.toString('ascii', 0, 25));
// 输出结果：!!!!!!!!qrst!!!!!!!!!!!!!

```

## entries

```TypeScript
entries(): IterableIterator<[number, number]>
```

返回一个包含key和value的迭代器。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-entries(): IterableIterator<[int, long]>--><!--Device-Buffer-entries(): IterableIterator<[int, long]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[number, number]&gt; | 包含key和value的迭代器，同时两者皆为number类型。<br>**适用版本：** 9 - 10 |
| IterableIterator&lt;[number, number]&gt; | <br>**适用版本：** 11+ |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from('buffer');
let pair = buf.entries();
let next: IteratorResult<Object[]> = pair.next();
while (!next.done) {
  console.info("buffer: " + next.value);
  /*
  输出结果：buffer: 0,98
           buffer: 1,117
           buffer: 2,102
           buffer: 3,102
           buffer: 4,101
           buffer: 5,114
   */
  next = pair.next();
}

```

## equals

```TypeScript
equals(otherBuffer: Uint8Array | Buffer): boolean
```

比较this实例和otherBuffer实例是否相等。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-equals(otherBuffer: Uint8Array | Buffer): boolean--><!--Device-Buffer-equals(otherBuffer: Uint8Array | Buffer): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| otherBuffer | Uint8Array \| Buffer | 是 | 比较的目标对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 相等则返回true，否则返回false。 |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from('ABC');
let buf2 = buffer.from('414243', 'hex');
let buf3 = buffer.from('ABCD');

console.info(buf1.equals(buf2).toString());
// 输出结果：true
console.info(buf1.equals(buf3).toString());
// 输出结果：false

```

## fill

```TypeScript
fill(
      value: string | Buffer | Uint8Array | number | number | number,
      offset?: number,
      end?: number,
      encoding?: BufferEncoding
    ): Buffer
```

使用value填充当前对象指定位置的数据，默认为循环填充，并返回填充后的Buffer对象。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-fill(      value: string | Buffer | Uint8Array | int | double | long,      offset?: int,      end?: int,      encoding?: BufferEncoding    ): Buffer--><!--Device-Buffer-fill(      value: string | Buffer | Uint8Array | int | double | long,      offset?: int,      end?: int,      encoding?: BufferEncoding    ): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| Buffer \| Uint8Array \| number \| number \| number | 是 | 用于填充的值。<br>**起始版本：** 11 |
| offset | number | 否 | 起始偏移量。默认值：0。 |
| end | number | 否 | 结束偏移量（不包含结束位置）。默认值：当前对象的字节长度。 |
| encoding | [BufferEncoding](arkts-arkts-fastbuffer-bufferencoding-t.md) | 否 | 字符编码格式（value为string才有意义）。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 返回填充后的Buffer对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[offset/end]" is out of range. It must be >= 0 and <=[right range]. Received value is: [offset/end] |

## includes

```TypeScript
includes(value: string | number | number | number | Buffer | Uint8Array, byteOffset?: number, encoding?: BufferEncoding): boolean
```

检查Buffer对象是否包含value值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-includes(value: string | int | double | long | Buffer | Uint8Array, byteOffset?: int, encoding?: BufferEncoding): boolean--><!--Device-Buffer-includes(value: string | int | double | long | Buffer | Uint8Array, byteOffset?: int, encoding?: BufferEncoding): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| number \| number \| number \| Buffer \| Uint8Array | 是 | 要搜索的内容。<br>**起始版本：** 11 |
| byteOffset | number | 否 | 字节偏移量。如果为负数，则从末尾开始计算偏移量。默认值：0。 |
| encoding | [BufferEncoding](arkts-arkts-fastbuffer-bufferencoding-t.md) | 否 | 字符编码格式（value为string才有意义）。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 存在返回true，否则返回false。 |

## indexOf

```TypeScript
indexOf(value: string | number | number | number | Buffer | Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number
```

返回当前对象中首次出现value的索引，如果不包含value，则返回-1。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-indexOf(value: string | int | double | long | Buffer | Uint8Array, byteOffset?: int, encoding?: BufferEncoding): int--><!--Device-Buffer-indexOf(value: string | int | double | long | Buffer | Uint8Array, byteOffset?: int, encoding?: BufferEncoding): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| number \| number \| number \| Buffer \| Uint8Array | 是 | 要查找的内容。<br>**起始版本：** 11 |
| byteOffset | number | 否 | 字节偏移量。如果为负数，则从末尾开始计算偏移量。默认值：0。 |
| encoding | [BufferEncoding](arkts-arkts-fastbuffer-bufferencoding-t.md) | 否 | 字符编码格式（value为string才有意义）。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 第一次出现位置。 |

## keys

```TypeScript
keys(): IterableIterator<number>
```

返回包含key值的迭代器。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-keys(): IterableIterator<int>--><!--Device-Buffer-keys(): IterableIterator<int>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;number&gt; | 返回一个包含key值的迭代器。 |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from('buffer');
let keys = buf.keys();
for (const key of keys) {
  console.info(key.toString());
}
/*
输出结果：0
        1
        2
        3
        4
        5
 */

```

## lastIndexOf

```TypeScript
lastIndexOf(value: string | number | number | number | Buffer | Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number
```

返回this实例中最后一次出现value的索引，如果对象不包含value，则返回-1。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-lastIndexOf(value: string | int | double | long | Buffer | Uint8Array, byteOffset?: int, encoding?: BufferEncoding): int--><!--Device-Buffer-lastIndexOf(value: string | int | double | long | Buffer | Uint8Array, byteOffset?: int, encoding?: BufferEncoding): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| number \| number \| number \| Buffer \| Uint8Array | 是 | 要搜索的内容。<br>**起始版本：** 11 |
| byteOffset | number | 否 | 字节偏移量。如果为负数，则从末尾开始计算偏移量。默认值：Buffer.length。 |
| encoding | [BufferEncoding](arkts-arkts-fastbuffer-bufferencoding-t.md) | 否 | 字符编码格式（value为string才有意义）。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 最后一次出现value值的索引。 |

## readBigInt64BE

```TypeScript
readBigInt64BE(offset?: number): bigint
```

从指定的offset处读取有符号的大端序64位整数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readBigInt64BE(offset?: int): bigint--><!--Device-Buffer-readBigInt64BE(offset?: int): bigint-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigInt64BE(0).toString());
// 输出结果：7161960797921896816

let buf1 = buffer.allocUninitializedFromPool(8);
let result = buf1.writeBigInt64BE(BigInt(0x0102030405060708), 0);
console.info("result = " + result);
// 输出结果：result = 8

```

## readBigInt64LE

```TypeScript
readBigInt64LE(offset?: number): bigint
```

从指定的offset处读取有符号的小端序64位整数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readBigInt64LE(offset?: int): bigint--><!--Device-Buffer-readBigInt64LE(offset?: int): bigint-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigUInt64LE(0).toString());
// 输出结果：8100120198111388771

let buf1 = buffer.allocUninitializedFromPool(8);
let result = buf1.writeBigUInt64BE(BigInt(0xdecafafecacefade), 0);
console.info("result = " + result);
// 输出结果：result = 8

```

## readBigUInt64BE

```TypeScript
readBigUInt64BE(offset?: number): bigint
```

从指定的offset处读取无符号的大端序64位整数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readBigUInt64BE(offset?: int): bigint--><!--Device-Buffer-readBigUInt64BE(offset?: int): bigint-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigUInt64BE(0).toString());
// 输出结果：7161960797921896816
let buf1 = buffer.allocUninitializedFromPool(8);
let result = buf1.writeBigUInt64BE(BigInt(0xdecafafecacefade), 0);
console.info("result = " + result);
// 输出结果：result = 8

```

## readBigUInt64LE

```TypeScript
readBigUInt64LE(offset?: number): bigint
```

从指定的offset处读取无符号的小端序64位整数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readBigUInt64LE(offset?: int): bigint--><!--Device-Buffer-readBigUInt64LE(offset?: int): bigint-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigUInt64LE(0).toString());
// 输出结果：8100120198111388771

let buf1 = buffer.allocUninitializedFromPool(8);
let result = buf1.writeBigUInt64BE(BigInt(0xdecafafecacefade), 0);
console.info("result = " + result);
// 输出结果：result = 8

```

## readDoubleBE

```TypeScript
readDoubleBE(offset?: number): number
```

从指定的offset处读取64位大端序双精度值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readDoubleBE(offset?: int): double--><!--Device-Buffer-readDoubleBE(offset?: int): double-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readDoubleBE(0).toString());
// 输出结果：8.20788039913184e-304
let buf1 = buffer.allocUninitializedFromPool(8);
let result = buf1.writeDoubleBE(123.456, 0);
console.info("result = " + result);
// 输出结果：result = 8

```

## readDoubleLE

```TypeScript
readDoubleLE(offset?: number): number
```

从指定的offset处读取64位小端序双精度值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readDoubleLE(offset?: int): double--><!--Device-Buffer-readDoubleLE(offset?: int): double-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readDoubleLE(0).toString());
// 输出结果：5.447603722011605e-270
let buf1 = buffer.allocUninitializedFromPool(8);
let result = buf1.writeDoubleLE(123.456, 0);
console.info("result = " + result);
// 输出结果：result = 8

```

## readFloatBE

```TypeScript
readFloatBE(offset?: number): number
```

从指定的offset处读取32位大端序浮点数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readFloatBE(offset?: int): double--><!--Device-Buffer-readFloatBE(offset?: int): double-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readFloatBE(0).toString());
// 输出结果：2.387939260590663e-38
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeFloatBE(0xcabcbcbc, 0);
console.info("result = " + result);
// 输出结果：result = 4

```

## readFloatLE

```TypeScript
readFloatLE(offset?: number): number
```

从指定的offset处读取32位小端序浮点数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readFloatLE(offset?: int): double--><!--Device-Buffer-readFloatLE(offset?: int): double-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readFloatLE(0).toString());
// 输出结果：1.539989614439558e-36
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeFloatLE(0xcabcbcbc, 0);
console.info("result = " + result);
// 输出结果：result = 4

```

## readInt16BE

```TypeScript
readInt16BE(offset?: number): number
```

从指定的offset处读取有符号的大端序16位整数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readInt16BE(offset?: int): long--><!--Device-Buffer-readInt16BE(offset?: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 2. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0, 5]);
console.info(buf.readInt16BE(0).toString());
// 输出结果：5
let buf1 = buffer.alloc(2);
let result = buf1.writeInt16BE(0x1234, 0);
console.info("result = " + result);
// 输出结果：result = 2

```

## readInt16LE

```TypeScript
readInt16LE(offset?: number): number
```

从指定的offset处读取有符号的小端序16位整数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readInt16LE(offset?: int): long--><!--Device-Buffer-readInt16LE(offset?: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 2. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0, 5]);
console.info(buf.readInt16LE(0).toString());
// 输出结果：1280
let buf1 = buffer.alloc(2);
let result = buf1.writeInt16BE(0x1234, 0);
console.info("result = " + result);
// 输出结果：result = 2

```

## readInt32BE

```TypeScript
readInt32BE(offset?: number): number
```

从指定的offset处读取有符号的大端序32位整数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readInt32BE(offset?: int): long--><!--Device-Buffer-readInt32BE(offset?: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0, 0, 0, 5]);
console.info(buf.readInt32BE(0).toString());
// 输出结果：5
let buf1 = buffer.alloc(4);
let result = buf1.writeInt32BE(0x12345678, 0);
console.info("result = " + result);
// 输出结果：result = 4

```

## readInt32LE

```TypeScript
readInt32LE(offset?: number): number
```

从指定的offset处读取有符号的小端序32位整数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readInt32LE(offset?: int): long--><!--Device-Buffer-readInt32LE(offset?: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0, 0, 0, 5]);
console.info(buf.readInt32LE(0).toString());
// 输出结果：83886080
let buf1 = buffer.alloc(4);
let result = buf1.writeInt32BE(0x12345678, 0);
console.info("result = " + result);
// 输出结果：result = 4

```

## readInt8

```TypeScript
readInt8(offset?: number): number
```

从指定的offset处读取有符号的8位整数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readInt8(offset?: int): long--><!--Device-Buffer-readInt8(offset?: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 1. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([-1, 5]);
console.info(buf.readInt8(0).toString());
// 输出结果：0
console.info(buf.readInt8(1).toString());
// 输出结果：5
let buf1 = buffer.allocUninitializedFromPool(2);
let result = buf1.writeInt8(0x12);
console.info("result = " + result);
// 输出结果：result = 1

```

## readIntBE

```TypeScript
readIntBE(offset: number, byteLength: number): number
```

从指定的offset处读取byteLength个字节，并将结果解释为支持最高48位精度的大端序、二进制补码有符号值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readIntBE(offset: int, byteLength: int): long--><!--Device-Buffer-readIntBE(offset: int, byteLength: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - byteLength。 |
| byteLength | number | 是 | 读取的字节数。取值范围：1 <= byteLength <= 6。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取的内容。当offset为小数时，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from("ab");
let num = buf.readIntBE(0, 1);
console.info(num.toString());
// 输出结果：97
let buf1 = buffer.allocUninitializedFromPool(6);
let result = buf1.writeIntBE(0x123456789011, 0, 6);
console.info("result = " + result);
// 输出结果：result = 6

```

## readIntLE

```TypeScript
readIntLE(offset: number, byteLength: number): number
```

从指定的offset处读取byteLength个字节，并将结果解释为支持最高48位精度的小端序、二进制补码有符号值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readIntLE(offset: int, byteLength: int): long--><!--Device-Buffer-readIntLE(offset: int, byteLength: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - byteLength。 |
| byteLength | number | 是 | 读取的字节数。取值范围：1 <= byteLength <= 6。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。当offset为小数时，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x12, 0x34, 0x56, 0x78, 0x90, 0xab]);
console.info(buf.readIntLE(0, 6).toString(16));
// 输出结果：-546f87a9cbee
let buf1 = buffer.allocUninitializedFromPool(6);
let result = buf1.writeIntLE(0x123456789011, 0, 6);
console.info("result = " + result);
// 输出结果：result = 6

```

## readUInt16BE

```TypeScript
readUInt16BE(offset?: number): number
```

从指定的offset处读取无符号的大端序16位整数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readUInt16BE(offset?: int): long--><!--Device-Buffer-readUInt16BE(offset?: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 2. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x12, 0x34, 0x56]);
console.info(buf.readUInt16BE(0).toString(16));
// 输出结果：1234
console.info(buf.readUInt16BE(1).toString(16));
// 输出结果：3456
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeUInt16BE(0x1234, 0);
console.info("result = " + result);
// 输出结果：result = 2

```

## readUInt16LE

```TypeScript
readUInt16LE(offset?: number): number
```

从指定的offset处的buf读取无符号的小端序16位整数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readUInt16LE(offset?: int): long--><!--Device-Buffer-readUInt16LE(offset?: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 2. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x12, 0x34, 0x56]);
console.info(buf.readUInt16LE(0).toString(16));
// 输出结果：3412
console.info(buf.readUInt16LE(1).toString(16));
// 输出结果：5634
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeUInt16LE(0x1234, 0);
console.info("result = " + result);
// 输出结果：result = 2

```

## readUInt32BE

```TypeScript
readUInt32BE(offset?: number): number
```

从指定的offset处的buf读取无符号的大端序32位整数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readUInt32BE(offset?: int): long--><!--Device-Buffer-readUInt32BE(offset?: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x12, 0x34, 0x56, 0x78]);
console.info(buf.readUInt32BE(0).toString(16));
// 输出结果：12345678
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeUInt32BE(0x12345678, 0);
console.info("result = " + result);
// 输出结果：result = 4

```

## readUInt32LE

```TypeScript
readUInt32LE(offset?: number): number
```

从指定的offset处的buf读取无符号的小端序32位整数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readUInt32LE(offset?: int): long--><!--Device-Buffer-readUInt32LE(offset?: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x12, 0x34, 0x56, 0x78]);
console.info(buf.readUInt32LE(0).toString(16));
// 输出结果：78563412
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeUInt32LE(0x12345678, 0);
console.info("result = " + result);
// 输出结果：result = 4

```

## readUInt8

```TypeScript
readUInt8(offset?: number): number
```

从offset处读取8位无符号整型数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readUInt8(offset?: int): long--><!--Device-Buffer-readUInt8(offset?: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 1. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([1, -2]);
console.info(buf.readUInt8(0).toString());
// 输出结果：1
console.info(buf.readUInt8(1).toString());
// 输出结果：0
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeUInt8(0x42);
console.info("result = " + result);
// 输出结果：result = 1

```

## readUIntBE

```TypeScript
readUIntBE(offset: number, byteLength: number): number
```

从指定的offset处的buf读取byteLength个字节，并将结果解释为支持最高48位精度的无符号大端序整数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readUIntBE(offset: int, byteLength: int): long--><!--Device-Buffer-readUIntBE(offset: int, byteLength: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - byteLength。 |
| byteLength | number | 是 | 要读取的字节数。取值范围：1 <= byteLength <= 6。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。当offset为小数时，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x12, 0x34, 0x56, 0x78, 0x90, 0xab]);
console.info(buf.readUIntBE(0, 6).toString(16));
// 输出结果：1234567890ab
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeUIntBE(0x13141516, 0, 4);
console.info("result = " + result);
// 输出结果：result = 4

```

## readUIntLE

```TypeScript
readUIntLE(offset: number, byteLength: number): number
```

从指定的offset处的buf读取byteLength个字节，并将结果解释为支持最高48位精度的无符号小端序整数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-readUIntLE(offset: int, byteLength: int): long--><!--Device-Buffer-readUIntLE(offset: int, byteLength: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - byteLength。 |
| byteLength | number | 是 | 读取的字节数。取值范围：1 <= byteLength <= 6。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。当offset为小数时，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x12, 0x34, 0x56, 0x78, 0x90, 0xab]);
console.info(buf.readUIntLE(0, 6).toString(16));
// 输出结果：ab9078563412
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeUIntLE(0x13141516, 0, 4);
console.info("result = " + result);
// 输出结果：result = 4

```

## subarray

```TypeScript
subarray(start?: number, end?: number): Buffer
```

截取当前对象指定位置的数据并返回。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-subarray(start?: int, end?: int): Buffer--><!--Device-Buffer-subarray(start?: int, end?: int): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 否 | 截取开始位置。默认值：0。 |
| end | number | 否 | 截取结束位置（不包含结束位置）。默认值：当前对象的字节长度。在传入null时返回空Buffer。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 返回新的Buffer对象。当start < 0或end < 0时返回空Buffer。 |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.allocUninitializedFromPool(26);

for (let i = 0; i < 26; i++) {
  buf1.writeInt8(i + 97, i);
}
const buf2 = buf1.subarray(0, 3);
console.info(buf2.toString('ascii', 0, buf2.length));
// 输出结果: abc

```

## swap16

```TypeScript
swap16(): Buffer
```

将当前对象转换为无符号的16位整数数组，并交换字节顺序。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-swap16(): Buffer--><!--Device-Buffer-swap16(): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 交换之后的Buffer对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200009](../errorcode-utils.md#10200009-buffer的长度错误) | The buffer size must be a multiple of 16-bits |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from([0x1, 0x2, 0x3, 0x4, 0x5, 0x6, 0x7, 0x8]);
console.info(buf1.toString('hex'));
// 输出结果：0102030405060708
buf1.swap16();
console.info(buf1.toString('hex'));
// 输出结果：0201040306050807

```

## swap32

```TypeScript
swap32(): Buffer
```

将当前对象转换为无符号的32位整数数组，并交换字节顺序。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-swap32(): Buffer--><!--Device-Buffer-swap32(): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 交换之后的Buffer对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200009](../errorcode-utils.md#10200009-buffer的长度错误) | The buffer size must be a multiple of 32-bits |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from([0x1, 0x2, 0x3, 0x4, 0x5, 0x6, 0x7, 0x8]);
console.info(buf1.toString('hex'));
// 输出结果：0102030405060708
buf1.swap32();
console.info(buf1.toString('hex'));
// 输出结果：0403020108070605

```

## swap64

```TypeScript
swap64(): Buffer
```

将当前对象转换为无符号的64位整数数组，并交换字节顺序。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-swap64(): Buffer--><!--Device-Buffer-swap64(): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 交换之后的Buffer对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200009](../errorcode-utils.md#10200009-buffer的长度错误) | The buffer size must be a multiple of 64-bits |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from([0x1, 0x2, 0x3, 0x4, 0x5, 0x6, 0x7, 0x8]);
console.info(buf1.toString('hex'));
// 输出结果：0102030405060708
buf1.swap64();
console.info(buf1.toString('hex'));
// 输出结果：0807060504030201

```

## toJSON

```TypeScript
toJSON(): Object
```

将Buffer转为JSON并返回。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-toJSON(): Object--><!--Device-Buffer-toJSON(): Object-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | JSON对象。 |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from([0x1, 0x2, 0x3, 0x4, 0x5]);
let obj = buf1.toJSON();
console.info(JSON.stringify(obj));
// 输出结果: {"type":"Buffer","data":[1,2,3,4,5]}

```

## toString

```TypeScript
toString(encoding?: string, start?: number, end?: number): string
```

将当前对象中指定位置的数据转成指定编码格式的字符串并返回。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-toString(encoding?: string, start?: number, end?: number): string--><!--Device-Buffer-toString(encoding?: string, start?: number, end?: number): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 否 | 字符编码格式（value为string才有意义）。默认值：'utf8'。 |
| start | number | 否 | 开始位置。默认值：0。 |
| end | number | 否 | 结束位置。默认值：Buffer.length。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 字符串。当start >= Buffer.length或start > end时返回空字符串。 |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.allocUninitializedFromPool(26);
for (let i = 0; i < 26; i++) {
  buf1.writeInt8(i + 97, i);
}
console.info(buf1.toString('utf-8'));
// 输出结果: abcdefghijklmnopqrstuvwxyz

```

## values

```TypeScript
values(): IterableIterator<number>
```

返回一个包含value的迭代器。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-values(): IterableIterator<long>--><!--Device-Buffer-values(): IterableIterator<long>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;number&gt; | 迭代器。 |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from('buffer');
let pair = buf1.values();
let next:IteratorResult<number> = pair.next();
while (!next.done) {
  console.info(next.value.toString());
  /*
  输出结果：98
           117
           102
           102
           101
           114
   */
  next = pair.next();
}

```

## write

```TypeScript
write(str: string, offset?: number, length?: number, encoding?: string): number
```

在Buffer对象的offset偏移处写入指定编码的字符串，写入的字节长度为length。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-write(str: string, offset?: int, length?: int, encoding?: string): int--><!--Device-Buffer-write(str: string, offset?: int, length?: int, encoding?: string): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| str | string | 是 | 要写入Buffer的字符串。 |
| offset | number | 否 | 偏移量。默认值：0。 |
| length | number | 否 | 最大字节长度。默认值：（Buffer.length - offset）。 |
| encoding | string | 否 | 字符编码。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[offset/length]" is out of range. It must be >= 0 and <=buf.length. Received value is: [offset/length] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.alloc(256);
let len = buf.write('\u00bd + \u00bc = \u00be', 0);
console.info(`${len} bytes: ${buf.toString('utf-8', 0, len)}`);
// 输出结果: 12 bytes: ½ + ¼ = ¾

let buffer1 = buffer.alloc(10);
let length = buffer1.write('abcd', 8);
console.info("length = " + length);
// 输出结果：length = 2

```

## writeBigInt64BE

```TypeScript
writeBigInt64BE(value: bigint, offset?: number): number
```

在Buffer对象的offset偏移处写入有符号的大端序64位BigInt型数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeBigInt64BE(value: bigint, offset?: int): int--><!--Device-Buffer-writeBigInt64BE(value: bigint, offset?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | bigint | 是 | 写入Buffer的数据。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeBigInt64BE(BigInt(0x0102030405060708), 0);
console.info("result = " + result);
// 输出结果：result = 8

```

## writeBigInt64LE

```TypeScript
writeBigInt64LE(value: bigint, offset?: number): number
```

在Buffer对象的offset偏移处写入有符号的小端序64位BigInt型数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeBigInt64LE(value: bigint, offset?: int): int--><!--Device-Buffer-writeBigInt64LE(value: bigint, offset?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | bigint | 是 | 写入Buffer的数据。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeBigInt64LE(BigInt(0x0102030405060708), 0);
console.info("result = " + result);
// 输出结果：result = 8

```

## writeBigUInt64BE

```TypeScript
writeBigUInt64BE(value: bigint, offset?: number): number
```

在Buffer对象的offset偏移处写入无符号的大端序64位BigUInt型数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeBigUInt64BE(value: bigint, offset?: int): int--><!--Device-Buffer-writeBigUInt64BE(value: bigint, offset?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | bigint | 是 | 写入Buffer的数据。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeBigUInt64BE(BigInt(0xdecafafecacefade), 0);
console.info("result = " + result);
// 输出结果：result = 8

```

## writeBigUInt64LE

```TypeScript
writeBigUInt64LE(value: bigint, offset?: number): number
```

在Buffer对象的offset偏移处写入无符号的小端序64位BigUInt型数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeBigUInt64LE(value: bigint, offset?: int): int--><!--Device-Buffer-writeBigUInt64LE(value: bigint, offset?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | bigint | 是 | 写入Buffer的数据。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeBigUInt64LE(BigInt(0xdecafafecacefade), 0);
console.info("result = " + result);
// 输出结果：result = 8

```

## writeDoubleBE

```TypeScript
writeDoubleBE(value: number, offset?: number): number
```

在Buffer对象的offset偏移处写入大端序的64位双浮点型数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeDoubleBE(value: double, offset?: int): int--><!--Device-Buffer-writeDoubleBE(value: double, offset?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeDoubleBE(123.456, 0);
console.info("result = " + result);
// 输出结果：result = 8

```

## writeDoubleLE

```TypeScript
writeDoubleLE(value: number, offset?: number): number
```

在Buffer对象的offset偏移处写入小端序的64位双浮点型数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeDoubleLE(value: double, offset?: int): int--><!--Device-Buffer-writeDoubleLE(value: double, offset?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeDoubleLE(123.456, 0);
console.info("result = " + result);
// 输出结果：result = 8

```

## writeFloatBE

```TypeScript
writeFloatBE(value: number, offset?: number): number
```

在Buffer对象的offset偏移处写入大端序的32位浮点型数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeFloatBE(value: double, offset?: int): int--><!--Device-Buffer-writeFloatBE(value: double, offset?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeFloatBE(0xcafebabe, 0);
console.info("result = " + result);
// 输出结果：result = 4

```

## writeFloatLE

```TypeScript
writeFloatLE(value: number, offset?: number): number
```

在Buffer对象的offset偏移处写入小端序的32位浮点型数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeFloatLE(value: double, offset?: int): int--><!--Device-Buffer-writeFloatLE(value: double, offset?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeFloatLE(0xcafebabe, 0);
console.info("result = " + result);
// 输出结果：result = 4

```

## writeInt16BE

```TypeScript
writeInt16BE(value: number, offset?: number): number
```

在Buffer对象的offset偏移处写入大端序的16位有符号整型数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeInt16BE(value: long, offset?: int): int--><!--Device-Buffer-writeInt16BE(value: long, offset?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(2);
let result = buf.writeInt16BE(0x0102, 0);
console.info("result = " + result);
// 输出结果：result = 2

```

## writeInt16LE

```TypeScript
writeInt16LE(value: number, offset?: number): number
```

在Buffer对象的offset偏移处写入小端序的16位有符号整型数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeInt16LE(value: long, offset?: int): int--><!--Device-Buffer-writeInt16LE(value: long, offset?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(2);
let result = buf.writeInt16LE(0x0304, 0);
console.info("result = " + result);
// 输出结果：result = 2

```

## writeInt32BE

```TypeScript
writeInt32BE(value: number, offset?: number): number
```

在Buffer对象的offset偏移处写入大端序的32位有符号整型数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeInt32BE(value: long, offset?: int): int--><!--Device-Buffer-writeInt32BE(value: long, offset?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
let result = buf.writeInt32BE(0x01020304, 0);
console.info("result = " + result);
// 输出结果：result = 4

```

## writeInt32LE

```TypeScript
writeInt32LE(value: number, offset?: number): number
```

在Buffer对象的offset偏移处写入小端序的32位有符号整型数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeInt32LE(value: long, offset?: int): int--><!--Device-Buffer-writeInt32LE(value: long, offset?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
let result = buf.writeInt32LE(0x05060708, 0);
console.info("result = " + result);
// 输出结果：result = 4

```

## writeInt8

```TypeScript
writeInt8(value: number, offset?: number): number
```

在Buffer对象的offset偏移处写入8位有符号整型数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeInt8(value: long, offset?: int): int--><!--Device-Buffer-writeInt8(value: long, offset?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(2);
let result = buf.writeInt8(2, 0);
console.info("result = " + result);
// 输出结果：result = 1
let result1 = buf.writeInt8(-2, 1);
console.info("result1 = " + result1);
// 输出结果：result1 = 2

```

## writeIntBE

```TypeScript
writeIntBE(value: number, offset: number, byteLength: number): number
```

在Buffer对象的offset偏移处写入大端序的有符号数据，字节长度为byteLength。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeIntBE(value: long, offset: int, byteLength: int): int--><!--Device-Buffer-writeIntBE(value: long, offset: int, byteLength: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。 |
| offset | number | 是 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - byteLength。 |
| byteLength | number | 是 | 要写入的字节数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(6);
let result = buf.writeIntBE(0x1234567890ab, 0, 6);
console.info("result = " + result);
// 输出结果：result = 6

```

## writeIntLE

```TypeScript
writeIntLE(value: number, offset: number, byteLength: number): number
```

在Buffer对象的offset偏移处写入小端序的有符号数据，字节长度为byteLength。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeIntLE(value: long, offset: int, byteLength: int): int--><!--Device-Buffer-writeIntLE(value: long, offset: int, byteLength: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。 |
| offset | number | 是 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - byteLength。 |
| byteLength | number | 是 | 要写入的字节数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(6);
let result = buf.writeIntLE(0x1234567890ab, 0, 6);
console.info("result = " + result);
// 输出结果：result = 6

```

## writeUInt16BE

```TypeScript
writeUInt16BE(value: number, offset?: number): number
```

在Buffer对象的offset偏移处写入大端序的16位无符号整型数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeUInt16BE(value: long, offset?: int): int--><!--Device-Buffer-writeUInt16BE(value: long, offset?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
let result = buf.writeUInt16BE(0xdead, 0);
console.info("result = " + result);
// 输出结果：result = 2
let result1 = buf.writeUInt16BE(0xbeef, 2);
console.info("result1 = " + result1);
// 输出结果：result1 = 4

```

## writeUInt16LE

```TypeScript
writeUInt16LE(value: number, offset?: number): number
```

在Buffer对象的offset偏移处写入小端序的16位无符号整型数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeUInt16LE(value: long, offset?: int): int--><!--Device-Buffer-writeUInt16LE(value: long, offset?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
let result = buf.writeUInt16LE(0xdead, 0);
console.info("result = " + result);
// 输出结果：result = 2
let result1 = buf.writeUInt16LE(0xbeef, 2);
console.info("result1 = " + result1);
// 输出结果：result1 = 4

```

## writeUInt32BE

```TypeScript
writeUInt32BE(value: number, offset?: number): number
```

在Buffer对象的offset偏移处写入大端序的32位无符号整型数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeUInt32BE(value: long, offset?: int): int--><!--Device-Buffer-writeUInt32BE(value: long, offset?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
let result = buf.writeUInt32BE(0xfeedface, 0);
console.info("result = " + result);
// 输出结果：result = 4

```

## writeUInt32LE

```TypeScript
writeUInt32LE(value: number, offset?: number): number
```

在Buffer对象的offset偏移处写入小端序的32位无符号整型数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeUInt32LE(value: long, offset?: int): int--><!--Device-Buffer-writeUInt32LE(value: long, offset?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
let result = buf.writeUInt32LE(0xfeedface, 0);
console.info("result = " + result);
// 输出结果：result = 4

```

## writeUInt8

```TypeScript
writeUInt8(value: number, offset?: number): number
```

在Buffer对象的offset偏移处写入8位无符号整型数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeUInt8(value: long, offset?: int): int--><!--Device-Buffer-writeUInt8(value: long, offset?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
let result = buf.writeUInt8(0x3, 0);
console.info("result = " + result);
// 输出结果：result = 1
let result1 = buf.writeUInt8(0x4, 1);
console.info("result1 = " + result1);
// 输出结果：result1 = 2
let result2 = buf.writeUInt8(0x23, 2);
console.info("result2 = " + result2);
// 输出结果：result2 = 3
let result3 = buf.writeUInt8(0x42, 3);
console.info("result3 = " + result3);
// 输出结果：result3 = 4

```

## writeUIntBE

```TypeScript
writeUIntBE(value: number, offset: number, byteLength: number): number
```

在Buffer对象的offset偏移处写入大端序的无符号数据，字节长度为byteLength。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeUIntBE(value: long, offset: int, byteLength: int): int--><!--Device-Buffer-writeUIntBE(value: long, offset: int, byteLength: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。 |
| offset | number | 是 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - byteLength。 |
| byteLength | number | 是 | 要写入的字节数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(6);
let result = buf.writeUIntBE(0x1234567890ab, 0, 6);
console.info("result = " + result);
// 输出结果：result = 6

```

## writeUIntLE

```TypeScript
writeUIntLE(value: number, offset: number, byteLength: number): number
```

在Buffer对象的offset偏移处写入小端序的无符号数据，字节长度为byteLength。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-writeUIntLE(value: long, offset: int, byteLength: int): int--><!--Device-Buffer-writeUIntLE(value: long, offset: int, byteLength: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。 |
| offset | number | 是 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - byteLength。 |
| byteLength | number | 是 | 要写入的字节数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be >= [left range] and <=[right range]. Received value is: [param] |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(6);
let result = buf.writeUIntLE(0x1234567890ab, 0, 6);
console.info("result = " + result);
// 输出结果：result = 6

```

## buffer

```TypeScript
buffer: ArrayBuffer
```

ArrayBuffer对象。

**类型：** ArrayBuffer

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-buffer: ArrayBuffer--><!--Device-Buffer-buffer: ArrayBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

## byteOffset

```TypeScript
byteOffset: number
```

当前Buffer所在内存池的偏移量。当Buffer通过内存池创建时（如使用[allocUninitializedFromPool](arkts-arkts-buffer-allocuninitializedfrompool-f.md#allocuninitializedfrompool)创建Buffer，或使用buffer.from()传入字符串，且字符串长度加当前内存池偏移量小于4kb），返回相对于内存池的偏移量。当Buffer直接分配内存时（如使用[alloc](arkts-arkts-buffer-alloc-f.md#alloc)），返回值为0。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-byteOffset: number--><!--Device-Buffer-byteOffset: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## length

```TypeScript
length: number
```

Buffer对象的字节长度。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Buffer-length: number--><!--Device-Buffer-length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

