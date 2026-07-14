# FastBuffer

FastBuffer对象是更高效的Buffer容器，用于表示固定长度的字节序列，是专门存放二进制数据的缓存区。

**起始版本：** 20

**系统能力：** SystemCapability.Utils.Lang

## compare

```TypeScript
compare(target: FastBuffer | Uint8Array, targetStart?: number, targetEnd?: number, sourceStart?: number, sourceEnd?: number): -1 | 0 | 1
```

比较当前对象this与目标对象target，并返回比较结果。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | FastBuffer \| Uint8Array | 是 | 要比较的实例对象。 |
| targetStart | number | 否 | `target`实例中开始的偏移量。默认值：0。取值范围：0 &lt;= targetStart &lt;= target.length。 |
| targetEnd | number | 否 | `target`实例中结束的偏移量（不包含结束位置）。默认值：目标对象的字节长度。取值范围：0 &lt;= targetEnd &lt;= target.length。 |
| sourceStart | number | 否 | `this`实例中开始的偏移量。默认值：0。取值范围：0 &lt;= sourceStart &lt;= this.length。 |
| sourceEnd | number | 否 | `this`实例中结束的偏移量（不包含结束位置）。默认值：当前对象的字节长度。取值范围：0 &lt;= sourceEnd &lt;= this.length。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| -1 | 返回比较结果。<br/>-1：当前排列在目标前；<br/>0：当前与目标相同；<br/>1：当前排列在目标后。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | Range error. Possible causes:The value of the parameter is not within the specified range. |
| [10200068](../errorcode-utils.md#10200068-引用已释放或分离的arraybuffer) | The underlying ArrayBuffer is null or detach. |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from([1, 2, 3, 4, 5, 6, 7, 8, 9]);
let buf2 = fastbuffer.from([5, 6, 7, 8, 9, 1, 2, 3, 4]);

console.info(buf1.compare(buf2, 5, 9, 0, 4).toString());
// 输出结果：0
console.info(buf1.compare(buf2, 0, 6, 4).toString());
// 输出结果：-1
console.info(buf1.compare(buf2, 5, 6, 5).toString());
// 输出结果：1

```

## copy

```TypeScript
copy(target: FastBuffer | Uint8Array, targetStart?: number, sourceStart?: number, sourceEnd?: number): number
```

将`this`实例中指定位置的数据复制到`target`的指定位置上，并返回复制的字节总长度。

如果sourceEnd大于target的长度，则以target的长度为准，超出部分不会被覆盖。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | FastBuffer \| Uint8Array | 是 | 要复制到的Buffer或Uint8Array实例。 |
| targetStart | number | 否 | `target`实例中开始写入的偏移量。默认值：0。取值范围：0 &lt;= targetStart &lt;= UINT32_MAX。 |
| sourceStart | number | 否 | `this`实例中开始复制的偏移量。默认值：0。取值范围：0 &lt;= sourceStart &lt;= UINT32_MAX。 |
| sourceEnd | number | 否 | `this`实例中结束复制的偏移量（不包含结束位置）。默认值：当前对象的字节长度。取值范围：0 &lt;= sourceEnd &lt;= this.length。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 复制的字节总长度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | Range error. Possible causes:The value of the parameter is not within the specified range. |
| [10200068](../errorcode-utils.md#10200068-引用已释放或分离的arraybuffer) | The underlying ArrayBuffer is null or detach. |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.allocUninitializedFromPool(26);
let buf2 = fastbuffer.allocUninitializedFromPool(26).fill('!');

for (let i = 0; i < 26; i++) {
  buf1.writeInt8(i + 97, i);
}

buf1.copy(buf2, 8, 16, 20);
console.info(buf2.toString('ascii', 0, 25));
// 输出结果：!!!!!!!!qrst!!!!!!!!!!!!!

```

## entries

```TypeScript
entries(): IterableIterator<[
            number,
            number
        ]>
```

返回一个包含key值和value值的迭代器。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[            number,            number        ]&gt; | @syscap SystemCapability.Utils.Lang@crossplatform@atomicservice |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from('buffer');
let pair = buf.entries();
let next: IteratorResult<Object[]> = pair.next();
while (!next.done) {
  console.info("fastbuffer: " + next.value);
  /*
  输出结果：buffer: 0,98
           fastbuffer: 1,117
           fastbuffer: 2,102
           fastbuffer: 3,102
           fastbuffer: 4,101
           fastbuffer: 5,114
   */
  next = pair.next();
}

```

## equals

```TypeScript
equals(otherBuffer: Uint8Array | FastBuffer): boolean
```

逐字节比较`this`和otherBuffer是否相等。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| otherBuffer | Uint8Array \| FastBuffer | 是 | 比较的目标对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 若`this`和otherBuffer逐字节相等则返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200068](../errorcode-utils.md#10200068-引用已释放或分离的arraybuffer) | The underlying ArrayBuffer is null or detach. |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from('ABC');
let buf2 = fastbuffer.from('414243', 'hex');
let buf3 = fastbuffer.from('ABCD');

console.info(buf1.equals(buf2).toString());
// 输出结果：true
console.info(buf1.equals(buf3).toString());
// 输出结果：false

```

## fill

```TypeScript
fill(value: string | FastBuffer | Uint8Array | number, offset?: number, end?: number, encoding?: BufferEncoding): FastBuffer
```

使用`value`填充当前对象指定位置的数据，默认为循环填充，并返回填充后的FastBuffer对象。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| FastBuffer \| Uint8Array \| number | 是 | 用于填充的值。 |
| offset | number | 否 | 起始偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length。 |
| end | number | 否 | 结束偏移量（不包含结束位置）。默认值：当前对象的字节长度。取值范围：0 &lt;= end &lt;= this.length。 |
| encoding | BufferEncoding | 否 | 字符编码格式（`value`为string才有意义）。默认值：'utf8'。传入无法识别的encoding会抛出TypeError。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FastBuffer | 返回填充后的FastBuffer对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | Range error. Possible causes:The value of the parameter is not within the specified range. |
| [10200068](../errorcode-utils.md#10200068-引用已释放或分离的arraybuffer) | The underlying ArrayBuffer is null or detach. |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let b = fastbuffer.allocUninitializedFromPool(50).fill('h');
console.info(b.toString());
// 输出结果：hhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh

```

## includes

```TypeScript
includes(value: string | number | FastBuffer | Uint8Array, byteOffset?: number, encoding?: BufferEncoding): boolean
```

检查FastBuffer对象是否包含`value`值。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| number \| FastBuffer \| Uint8Array | 是 | 要搜索的内容。 |
| byteOffset | number | 否 | 字节偏移量。若为正数，则从0开始计算偏移量；若为负数，则从末尾开始计算偏移量。默认值：0。 |
| encoding | BufferEncoding | 否 | 字符编码格式。默认值：'utf8'。传入无法识别的encoding会抛出TypeError。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 若FastBuffer对象包含`value`值时返回true，否则为false。 |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from('this is a buffer');
console.info(buf.includes('this').toString());
// 输出结果：true
console.info(buf.includes('be').toString());
// 输出结果：false

```

## indexOf

```TypeScript
indexOf(value: string | number | FastBuffer | Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number
```

返回当前对象中首次出现`value`的索引，如果不包含`value`，则返回-1。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| number \| FastBuffer \| Uint8Array | 是 | 要查找的内容。 |
| byteOffset | number | 否 | 字节偏移量。若byteOffset为正数，则从0开始计算偏移量；如果为负数，则从末尾开始计算偏移量。默认值：0。 |
| encoding | BufferEncoding | 否 | 字符编码格式。默认值：'utf8'。传入无法识别的encoding会抛出TypeError。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回第一次出现的位置。 |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from('this is a buffer');
console.info(buf.indexOf('this').toString());
// 输出结果：0
console.info(buf.indexOf('is').toString());
// 输出结果：2

```

## keys

```TypeScript
keys(): IterableIterator<number>
```

返回一个包含key值的迭代器。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;number&gt; | @syscap SystemCapability.Utils.Lang@crossplatform@atomicservice |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from('buffer');
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
lastIndexOf(value: string | number | FastBuffer | Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number
```

返回当前对象中最后一次出现`value`的索引，如果对象不包含`value`，则返回-1。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| number \| FastBuffer \| Uint8Array | 是 | 要搜索的内容。 |
| byteOffset | number | 否 | 字节偏移量。若byteOffset为正数，则从0开始计算偏移量；如果为负数，则从末尾开始计算偏移量。默认值：this.length - 1。 |
| encoding | BufferEncoding | 否 | 字符编码格式。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 最后一次出现`value`值的索引。 |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from('this buffer is a buffer');
console.info(buf.lastIndexOf('this').toString());
// 输出结果：0
console.info(buf.lastIndexOf('buffer').toString());
// 输出结果：17

```

## readBigInt64BE

```TypeScript
readBigInt64BE(offset?: number): bigint
```

从指定的`offset`处读取有符号的大端序64位整数。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigInt64BE(0).toString());
// 输出结果：7161960797921896816

```

## readBigInt64LE

```TypeScript
readBigInt64LE(offset?: number): bigint
```

从指定的`offset`处读取有符号的小端序64位整数。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigInt64LE(0).toString());
// 输出结果：8100120198111388771

```

## readBigUInt64BE

```TypeScript
readBigUInt64BE(offset?: number): bigint
```

从指定的`offset`处读取无符号的大端序64位整数。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigUInt64BE(0).toString());
// 输出结果：7161960797921896816

```

## readBigUInt64LE

```TypeScript
readBigUInt64LE(offset?: number): bigint
```

从指定的`offset`处读取无符号的小端序64位整数。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigUInt64LE(0).toString());
// 输出结果：8100120198111388771

```

## readDoubleBE

```TypeScript
readDoubleBE(offset?: number): number
```

从指定的`offset`处读取64位大端序双精度值。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readDoubleBE(0).toString());
// 输出结果：8.20788039913184e-304

```

## readDoubleLE

```TypeScript
readDoubleLE(offset?: number): number
```

从指定的`offset`处读取64位小端序双精度值。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readDoubleLE(0).toString());
// 输出结果：5.447603722011605e-270

```

## readFloatBE

```TypeScript
readFloatBE(offset?: number): number
```

从指定的`offset`处读取32位大端序浮点数。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readFloatBE(0).toString());
// 输出结果：2.387939260590663e-38

```

## readFloatLE

```TypeScript
readFloatLE(offset?: number): number
```

从指定的`offset`处读取32位小端序浮点数。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readFloatLE(0).toString());
// 输出结果：1.539989614439558e-36

```

## readInt16BE

```TypeScript
readInt16BE(offset?: number): number
```

从指定的`offset`处读取有符号的大端序16位整数。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 2. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0, 5]);
console.info(buf.readInt16BE(0).toString());
// 输出结果：5

```

## readInt16LE

```TypeScript
readInt16LE(offset?: number): number
```

从指定的`offset`处读取有符号的小端序16位整数。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 2. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0, 5]);
console.info(buf.readInt16LE(0).toString());
// 输出结果：1280

```

## readInt32BE

```TypeScript
readInt32BE(offset?: number): number
```

从指定的`offset`处读取有符号的大端序32位整数。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0, 0, 0, 5]);
console.info(buf.readInt32BE(0).toString());
// 输出结果：5

```

## readInt32LE

```TypeScript
readInt32LE(offset?: number): number
```

从指定的`offset`处读取有符号的小端序32位整数。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0, 0, 0, 5]);
console.info(buf.readInt32LE(0).toString());
// 输出结果：83886080

```

## readInt8

```TypeScript
readInt8(offset?: number): number
```

从指定的`offset`处读取有符号的8位整数。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 1. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([-1, 5]);
console.info(buf.readInt8(0).toString());
// 输出结果：-1
console.info(buf.readInt8(1).toString());
// 输出结果：5

```

## readIntBE

```TypeScript
readIntBE(offset: number, byteLength: number): number
```

从指定的`offset`处读取byteLength个字节，并将结果解释为支持最高48位精度的大端序、二进制补码有符号值。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 偏移量。取值范围：0 &lt;= offset &lt;= this.length - byteLength，默认值：0。 |
| byteLength | number | 是 | 读取的字节数。取值范围：1 &lt;= byteLength &lt;= 6。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from("ab");
let num = buf.readIntBE(0, 1);
console.info(num.toString());
// 输出结果：97

```

## readIntLE

```TypeScript
readIntLE(offset: number, byteLength: number): number
```

从指定的`offset`处读取`byteLength`个字节，并将结果解释为支持最高48位精度的小端序、二进制补码有符号值。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 偏移量。取值范围：0 &lt;= offset &lt;= this.length - byteLength，默认值：0。 |
| byteLength | number | 是 | 读取的字节数。取值范围：1 &lt;= byteLength &lt;= 6。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56, 0x78, 0x90, 0xab]);
console.info(buf.readIntLE(0, 6).toString(16));
// 输出结果：-546f87a9cbee

```

## readUInt16BE

```TypeScript
readUInt16BE(offset?: number): number
```

从指定的`offset`处读取无符号的大端序16位整数。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 2. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56]);
console.info(buf.readUInt16BE(0).toString(16));
// 输出结果：1234
console.info(buf.readUInt16BE(1).toString(16));
// 输出结果：3456

```

## readUInt16LE

```TypeScript
readUInt16LE(offset?: number): number
```

从指定的`offset`处的buf读取无符号的小端序16位整数。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 2. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56]);
console.info(buf.readUInt16LE(0).toString(16));
// 输出结果：3412
console.info(buf.readUInt16LE(1).toString(16));
// 输出结果：5634

```

## readUInt32BE

```TypeScript
readUInt32BE(offset?: number): number
```

从指定的`offset`处的buf读取无符号的大端序32位整数。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56, 0x78]);
console.info(buf.readUInt32BE(0).toString(16));
// 输出结果：12345678

```

## readUInt32LE

```TypeScript
readUInt32LE(offset?: number): number
```

从指定的`offset`处的buf读取无符号的小端序32位整数。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56, 0x78]);
console.info(buf.readUInt32LE(0).toString(16));
// 输出结果：78563412

```

## readUInt8

```TypeScript
readUInt8(offset?: number): number
```

从`offset`处读取8位无符号整型数。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 1. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([1, -2]);
console.info(buf.readUInt8(0).toString());
// 输出结果：1
console.info(buf.readUInt8(1).toString());
// 输出结果：254

```

## readUIntBE

```TypeScript
readUIntBE(offset: number, byteLength: number): number
```

从指定的`offset`处的buf读取`byteLength`个字节，并将结果解释为支持最高48位精度的无符号大端序整数。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 偏移量。取值范围：0 &lt;= offset &lt;= this.length - byteLength，默认值：0。 |
| byteLength | number | 是 | 要读取的字节数。取值范围：1 &lt;= byteLength &lt;= 6。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。当offset为小数时，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56, 0x78, 0x90, 0xab]);
console.info(buf.readUIntBE(0, 6).toString(16));
// 输出结果：1234567890ab

```

## readUIntLE

```TypeScript
readUIntLE(offset: number, byteLength: number): number
```

从指定的`offset`处的buf读取`byteLength`个字节，并将结果解释为支持最高48位精度的无符号小端序整数。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 偏移量。取值范围：0 &lt;= offset &lt;= this.length - byteLength，默认值：0。 |
| byteLength | number | 是 | 读取的字节数。取值范围：1 &lt;= byteLength &lt;= 6。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 读取出的内容。当offset为小数时，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56, 0x78, 0x90, 0xab]);
console.info(buf.readUIntLE(0, 6).toString(16));
// 输出结果：ab9078563412

```

## subarray

```TypeScript
subarray(start?: number, end?: number): FastBuffer
```

截取当前对象指定位置的数据并返回。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 否 | 截取开始位置。默认值：0。 |
| end | number | 否 | 截取结束位置（不包含结束位置）。默认值：当前对象的字节长度。取值范围：start &lt;= end &lt;= this.length。传入null时返回空FastBuffer。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FastBuffer | 返回新的FastBuffer对象。 |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.allocUninitializedFromPool(26);

for (let i = 0; i < 26; i++) {
  buf1.writeInt8(i + 97, i);
}
const buf2 = buf1.subarray(0, 3);
console.info(buf2.toString('ascii', 0, buf2.length));
// 输出结果: abc

```

## swap16

```TypeScript
swap16(): FastBuffer
```

将当前对象转换为无符号的16位整数数组，并交换字节顺序。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FastBuffer | 交换之后的FastBuffer对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200009](../errorcode-utils.md#10200009-buffer的长度错误) | The fastbuffer size must be a multiple of 16-bits |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from([0x1, 0x2, 0x3, 0x4, 0x5, 0x6, 0x7, 0x8]);
console.info(buf1.toString('hex'));
// 输出结果：0102030405060708
buf1.swap16();
console.info(buf1.toString('hex'));
// 输出结果：0201040306050807

```

## swap32

```TypeScript
swap32(): FastBuffer
```

将当前对象转换为无符号的32位整数数组，并交换字节顺序。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FastBuffer | 交换之后的FastBuffer对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200009](../errorcode-utils.md#10200009-buffer的长度错误) | The fastbuffer size must be a multiple of 32-bits |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from([0x1, 0x2, 0x3, 0x4, 0x5, 0x6, 0x7, 0x8]);
console.info(buf1.toString('hex'));
// 输出结果：0102030405060708
buf1.swap32();
console.info(buf1.toString('hex'));
// 输出结果：0403020108070605

```

## swap64

```TypeScript
swap64(): FastBuffer
```

将当前对象转换为无符号的64位整数数组，并交换字节顺序。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FastBuffer | 交换之后的FastBuffer对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200009](../errorcode-utils.md#10200009-buffer的长度错误) | The fastbuffer size must be a multiple of 64-bits |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from([0x1, 0x2, 0x3, 0x4, 0x5, 0x6, 0x7, 0x8]);
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

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | JSON对象。 |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from([0x1, 0x2, 0x3, 0x4, 0x5]);
let obj = buf1.toJSON();
console.info(JSON.stringify(obj));
// 输出结果: {"type":"FastBuffer","data":[1,2,3,4,5]}

```

## toString

```TypeScript
toString(encoding?: string, start?: number, end?: number): string
```

将当前对象中指定位置的数据转成指定编码格式的字符串并返回。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 否 | 字符编码格式。默认值：'utf8'。 |
| start | number | 否 | 开始位置。默认值：0。 |
| end | number | 否 | 结束位置。默认值：Buffer.length。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 字符串。当start &gt;= this.length或start &gt; end时返回空字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200068](../errorcode-utils.md#10200068-引用已释放或分离的arraybuffer) | The underlying ArrayBuffer is null or detach. |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.allocUninitializedFromPool(26);
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

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;number&gt; | @syscap SystemCapability.Utils.Lang@crossplatform@atomicservice |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from('buffer');
let pair = buf1.values()
let next:IteratorResult<number> = pair.next()
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

在FastBuffer对象的offset偏移处写入指定编码的字符串，写入的字节长度为length。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| str | string | 是 | 要写入Buffer的字符串。 |
| offset | number | 否 | 偏移量。默认值：0。 |
| length | number | 否 | 最大字节长度。默认值：（this.length - offset）。 |
| encoding | string | 否 | 字符编码。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | Range error. Possible causes:The value of the parameter is not within the specified range. |
| [10200068](../errorcode-utils.md#10200068-引用已释放或分离的arraybuffer) | The underlying ArrayBuffer is null or detach. |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.alloc(256);
let len = buf.write('\u00bd + \u00bc = \u00be', 0);
console.info(`${len} bytes: ${buf.toString('utf-8', 0, len)}`);
// 输出结果: 12 bytes: ½ + ¼ = ¾

let buffer1 = fastbuffer.alloc(10);
let length = buffer1.write('abcd', 8);
console.info("length = " + length);
// 输出结果：length = 2

```

## writeBigInt64BE

```TypeScript
writeBigInt64BE(value: bigint, offset?: number): number
```

在FastBuffer对象的offset偏移处写入有符号的大端序64位BigInt型数据。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | bigint | 是 | 写入Buffer的数据。取值范围：-INT64_MAX &lt;= value &lt;= INT64_MAX。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeBigInt64BE(BigInt(0x0102030405060708), 0);
console.info("result = " + result);
// 输出结果：result = 8

```

## writeBigInt64LE

```TypeScript
writeBigInt64LE(value: bigint, offset?: number): number
```

在FastBuffer对象的offset偏移处写入有符号的小端序64位BigInt型数据。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | bigint | 是 | 写入Buffer的数据。取值范围：-INT64_MAX &lt;= value &lt;= INT64_MAX。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeBigInt64LE(BigInt(0x0102030405060708), 0);
console.info("result = " + result);
// 输出结果：result = 8

```

## writeBigUInt64BE

```TypeScript
writeBigUInt64BE(value: bigint, offset?: number): number
```

在FastBuffer对象的offset偏移处写入无符号的大端序64位BigUInt型数据。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | bigint | 是 | 写入Buffer的数据。取值范围：0 &lt;= value &lt;= UINT64_MAX。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeBigUInt64BE(BigInt(0xdecafafecacefade), 0);
console.info("result = " + result);
// 输出结果：result = 8

```

## writeBigUInt64LE

```TypeScript
writeBigUInt64LE(value: bigint, offset?: number): number
```

在FastBuffer对象的offset偏移处写入无符号的小端序64位BigUInt型数据。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | bigint | 是 | 写入Buffer的数据。取值范围：0 &lt;= value &lt;= UINT64_MAX。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeBigUInt64LE(BigInt(0xdecafafecacefade), 0);
console.info("result = " + result);
// 输出结果：result = 8

```

## writeDoubleBE

```TypeScript
writeDoubleBE(value: number, offset?: number): number
```

在FastBuffer对象的offset偏移处写入大端序的64位双浮点型数据。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。取值范围：-DOUBLE_MAX &lt;= value &lt;= DOUBLE_MAX。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeDoubleBE(123.456, 0);
console.info("result = " + result);
// 输出结果：result = 8

```

## writeDoubleLE

```TypeScript
writeDoubleLE(value: number, offset?: number): number
```

在FastBuffer对象的offset偏移处写入小端序的64位双浮点型数据。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。取值范围：-DOUBLE_MAX &lt;= value &lt;= DOUBLE_MAX。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeDoubleLE(123.456, 0);
console.info("result = " + result);
// 输出结果：result = 8

```

## writeFloatBE

```TypeScript
writeFloatBE(value: number, offset?: number): number
```

在FastBuffer对象的offset偏移处写入大端序的32位浮点型数据。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。取值范围：-FLOAT_MAX &lt;= value &lt;= FLOAT_MAX。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeFloatBE(3.1415, 0);
console.info("result = " + result);
// 输出结果：result = 4

```

## writeFloatLE

```TypeScript
writeFloatLE(value: number, offset?: number): number
```

在FastBuffer对象的offset偏移处写入小端序的32位浮点型数据。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。取值范围：-FLOAT_MAX &lt;= value &lt;= FLOAT_MAX。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeFloatLE(3.1415, 0);
console.info("result = " + result);
// 输出结果：result = 4

```

## writeInt16BE

```TypeScript
writeInt16BE(value: number, offset?: number): number
```

在FastBuffer对象的offset偏移处写入大端序的16位有符号整型数据。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。取值范围：-INT16_MAX &lt;= value &lt;= INT16_MAX。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(2);
let result = buf.writeInt16BE(0x0102, 0);
console.info("result = " + result);
// 输出结果：result = 2

```

## writeInt16LE

```TypeScript
writeInt16LE(value: number, offset?: number): number
```

在FastBuffer对象的offset偏移处写入小端序的16位有符号整型数据。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。取值范围：-INT16_MAX &lt;= value &lt;= INT16_MAX。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(2);
let result = buf.writeInt16LE(0x0304, 0);
console.info("result = " + result);
// 输出结果：result = 2

```

## writeInt32BE

```TypeScript
writeInt32BE(value: number, offset?: number): number
```

在FastBuffer对象的offset偏移处写入大端序的32位有符号整型数据。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。取值范围：-INT32_MAX &lt;= value &lt;= INT32_MAX。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
let result = buf.writeInt32BE(0x01020304, 0);
console.info("result = " + result);
// 输出结果：result = 4

```

## writeInt32LE

```TypeScript
writeInt32LE(value: number, offset?: number): number
```

在FastBuffer对象的offset偏移处写入小端序的32位有符号整型数据。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。取值范围：-INT32_MAX &lt;= value &lt;= INT32_MAX。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
let result = buf.writeInt32LE(0x05060708, 0);
console.info("result = " + result);
// 输出结果：result = 4

```

## writeInt8

```TypeScript
writeInt8(value: number, offset?: number): number
```

在FastBuffer对象的offset偏移处写入8位有符号整型数据。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。取值范围：-INT8_MAX &lt;= value &lt;= INT8_MAX。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(2);
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

在FastBuffer对象的offset偏移处写入大端序的有符号数据，字节长度为byteLength。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。取值范围取决于byteLength。 |
| offset | number | 是 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - byteLength。传入null或undefined时偏移量为0。 |
| byteLength | number | 是 | 要写入的字节数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(6);
let result = buf.writeIntBE(0x1234567890ab, 0, 6);
console.info("result = " + result);
// 输出结果：result = 6

```

## writeIntLE

```TypeScript
writeIntLE(value: number, offset: number, byteLength: number): number
```

在FastBuffer对象的offset偏移处写入小端序的有符号数据，字节长度为byteLength。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。取值范围取决于byteLength。 |
| offset | number | 是 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - byteLength。传入null或undefined时偏移量为0。 |
| byteLength | number | 是 | 要写入的字节数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(6);
let result = buf.writeIntLE(0x1234567890ab, 0, 6);
console.info("result = " + result);
// 输出结果：result = 6

```

## writeUInt16BE

```TypeScript
writeUInt16BE(value: number, offset?: number): number
```

在FastBuffer对象的offset偏移处写入大端序的16位无符号整型数据。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。取值范围：0 &lt;= value &lt;= UINT16_MAX。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
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

在FastBuffer对象的offset偏移处写入小端序的16位无符号整型数据。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。取值范围：0 &lt;= value &lt;= UINT16_MAX。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
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

在FastBuffer对象的offset偏移处写入大端序的32位无符号整型数据。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。取值范围：0 &lt;= value &lt;= UINT32_MAX。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
let result = buf.writeUInt32BE(0xfeedface, 0);
console.info("result = " + result);
// 输出结果：result = 4

```

## writeUInt32LE

```TypeScript
writeUInt32LE(value: number, offset?: number): number
```

在FastBuffer对象的offset偏移处写入小端序的32位无符号整型数据。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入FastBuffer对象的数据。取值范围：0 &lt;= value &lt;= UINT32_MAX。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 4。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
let result = buf.writeUInt32LE(0xfeedface, 0);
console.info("result = " + result);
// 输出结果：result = 4

```

## writeUInt8

```TypeScript
writeUInt8(value: number, offset?: number): number
```

在FastBuffer对象的offset偏移处写入8位无符号整型数据。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。取值范围：0 &lt;= value &lt;= UINT8_MAX。 |
| offset | number | 否 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - 1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
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

在FastBuffer对象的offset偏移处写入大端序的无符号数据，字节长度为byteLength。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。取值范围取决于byteLength。 |
| offset | number | 是 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - byteLength。传入null或undefined时偏移量为0。 |
| byteLength | number | 是 | 要写入的字节数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(6);
let result = buf.writeUIntBE(0x1234567890ab, 0, 6);
console.info("result = " + result);
// 输出结果：result = 6

```

## writeUIntLE

```TypeScript
writeUIntLE(value: number, offset: number, byteLength: number): number
```

在FastBuffer对象的offset偏移处写入小端序的无符号数据，字节长度为byteLength。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 写入Buffer的数据。取值范围取决于byteLength。 |
| offset | number | 是 | 偏移量。默认值：0。取值范围：0 &lt;= offset &lt;= this.length - byteLength。传入null或undefined时偏移量为0。 |
| byteLength | number | 是 | 要写入的字节数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 偏移量offset加上写入的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(6);
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

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## byteOffset

```TypeScript
byteOffset: number
```

当前Buffer所在内存池的偏移量。

**类型：** number

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## length

```TypeScript
length: number
```

FastBuffer对象的字节长度。

**类型：** number

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

