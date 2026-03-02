# @ohos.buffer (Buffer)

Buffer对象用于表示固定长度的字节序列，是专门存放二进制数据的缓存区。

**推荐使用场景：** 适用于处理大量二进制数据，如图片处理和文件接收上传等。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { buffer } from '@kit.ArkTS';
```
## BlobOptions<sup>20+</sup>

创建[Blob](#blob)的相关选项。

**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

| 名称      | 类型 | 只读 | 可选 | 说明               |
| --------- | -------- | ---- | ---- | ------------------ |
| type     | string  | 否 | 是 | Blob的内容类型。其目的是让类型传达数据的MIME媒体类型，但是不执行类型格式的验证。此参数非必填，默认参数为''。 |
| endings | string  | 否 | 是 | 含义为结束符'\n'的字符串如何被输出，为'transparent'或'native'。native代表行结束符会跟随系统。'transparent'代表会保持Blob中保存的结束符不变。此参数非必填，默认值为'transparent'。 |

## TypedArray<sup>20+</sup>

type TypedArray = Int8Array | Uint8Array | Uint8ClampedArray | Int16Array | Uint16Array | Int32Array | Uint32Array | Float32Array | Float64Array | BigInt64Array | BigUint64Array

表示Array类型。

取值类型为下表类型中的并集。

**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

| 类型    | 说明                 |
| ------- | -------------------- |
| Int8Array | 8位有符号整数数组。 |
| Uint8Array | 8位无符号整数数组。 |
| Uint8ClampedArray | 8位无符号整数固定数组。 |
| Int16Array | 16位有符号整数数组。 |
| Uint16Array | 16位无符号整数数组。 |
| Int32Array | 32位有符号整数数组。 |
| Uint32Array | 32位无符号整数数组。 |
| Float32Array | 32位浮点数数组。 |
| Float64Array | 64位浮点数数组。 |
| BigInt64Array | 64位有符号大整数数组。 |
| BigUint64Array | 64位无符号大整数数组。 | 

## ArrayUnionType<sup>20+</sup>

type ArrayUnionType = Array\<Int8Array\> | Array\<Uint8Array\> | Array\<Uint8ClampedArray\> | Array\<Int16Array\> | Array\<Uint16Array\> | Array\<Int32Array\> | Array\<Uint32Array\> | Array\<Float32Array\> | Array\<Float64Array\> | Array\<BigInt64Array\> | Array\<BigUint64Array\> | Array\<string\> | Array\<ArrayBuffer\> | Array\<DataView\> | Array\<Blob\>

[Blob](#blob)实例的数据源。

取值类型为下表类型中的并集。

**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

| 类型    | 说明                 |
| ------- | -------------------- |
| Array\<Int8Array\> | 表示Int8Array类型的数组。 |
| Array\<Uint8Array\> | 表示Uint8Array类型的数组。 |
| Array\<Uint8ClampedArray\> | 表示Uint8ClampedArray类型的数组。 |
| Array\<Int16Array\> | 表示Int16Array类型的数组。 |
| Array\<Uint16Array\> | 表示Uint16Array类型的数组。 |
| Array\<Int32Array\> | 表示Int32Array类型的数组。 |
| Array\<Uint32Array\> | 表示Uint32Array类型的数组。 |
| Array\<Float32Array\> | 表示Float32Array类型的数组。 |
| Array\<Float64Array\> | 表示Float64Array类型的数组。 |
| Array\<BigInt64Array\> | 表示BigInt64Array类型的数组。 |
| Array\<BigUint64Array\> | 表示BigUint64Array类型的数组。 |
| Array\<string\> | 表示string类型的数组。 |
| Array\<ArrayBuffer\> | 表示ArrayBuffer类型的数组。 |
| Array\<DataView\> | 表示DataView类型的数组。 |
| Array\<Blob\> | 表示Blob类型的数组。 |

## BufferEncoding

type BufferEncoding = | 'ascii' | 'utf8' | 'utf-8' | 'utf16le' | 'ucs2' | 'ucs-2' | 'base64' | 'base64url' | 'latin1' | 'binary' | 'hex'

表示支持的编码格式类型。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

| 类型    | 说明                 |
| ------- | -------------------- |
| 'ascii' | 表示ascii格式。 |
| 'utf8' | 表示utf8格式。 |
| 'utf-8' | 表示utf8格式。 |
| 'utf16le' | 表示utf16小端序格式。 |
| 'ucs2' | utf16le的别名。 |
| 'ucs-2' | utf16le的别名。 |
| 'base64' | 表示base64格式。 |
| 'base64url' | 表示base64url格式。 |
| 'latin1' | iso-8859-1的别名，向下兼容ascii格式。 |
| 'binary' | 表示二进制格式。 |
| 'hex' | 表示十六进制格式。 |

## buffer.alloc

ArkTS-Dyn: alloc(size: number, fill?: string | Buffer | number, encoding?: BufferEncoding): Buffer

ArkTS-Sta: alloc(size: int, fill?: string | Buffer | int | double | long, encoding?: BufferEncoding): Buffer

创建指定字节长度的Buffer对象并初始化。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| size | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 指定的Buffer对象长度，单位：字节。 |
| fill | ArkTS-Dyn：string \| [Buffer](#buffer) \| number <br> ArkTS-Sta：string \| [Buffer](#buffer) \| int \| double \| long | 否 | 填充至新缓存区的值，默认值：0。 |
| encoding | [BufferEncoding](#bufferencoding) | 否 | 编码格式（当`fill`为string时，才有意义）。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [Buffer](#buffer) | 返回一个Buffer对象。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

ArkTS-Sta错误码：

此接口在ArkTS-Sta无错误码。

**示例：**

ArkTS-Dyn示例：

```ts
import { buffer, JSON } from '@kit.ArkTS';

let buf1 = buffer.alloc(5);
console.info(JSON.stringify(buf1)); // {"type":"Buffer","data":[0,0,0,0,0]}

let buf2 = buffer.alloc(5, 'a');
console.info(JSON.stringify(buf2)); // {"type":"Buffer","data":[97,97,97,97,97]}

let buf3 = buffer.alloc(11, 'aGVsbG8gd29ybGQ=', 'base64');
console.info(JSON.stringify(buf3)); // {"type":"Buffer","data":[104,101,108,108,111,32,119,111,114,108,100]}
```

ArkTS-Sta示例：

```ts
import { buffer } from '@kit.ArkTS';	

let buf1 = buffer.alloc(5);	
console.info(JSON.stringify(buf1)); // {"type":"Buffer","data":[0,0,0,0,0]}

let buf2 = buffer.alloc(5, 'a');	
console.info(JSON.stringify(buf2)); // {"type":"Buffer","data":[97,97,97,97,97]}

let buf3 = buffer.alloc(11, 'aGVsbG8gd29ybGQ=', 'base64');	
console.info(JSON.stringify(buf3)); // {"type":"Buffer","data":[104,101,108,108,111,32,119,111,114,108,100]}
```

## buffer.allocUninitializedFromPool

ArkTS-Dyn：allocUninitializedFromPool(size: number): Buffer

ArkTS-Sta：allocUninitializedFromPool(size: int): Buffer

创建指定大小未初始化的Buffer对象。内存从缓冲池分配。
创建的Buffer内容未知，需要使用[fill](#fill)函数来初始化Buffer对象。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| size | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 指定的Buffer对象长度，单位：字节。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [Buffer](#buffer) | 未初始化的Buffer实例。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

ArkTS-Sta错误码：

此接口在ArkTS-Sta无错误码。

**示例：**

ArkTS-Dyn示例：

```ts
import { buffer, JSON } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(10);
buf.fill(0);
console.info(JSON.stringify(buf)); // {"type":"Buffer","data":[0,0,0,0,0,0,0,0,0,0]}
```

ArkTS-Sta示例：

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(10);
buf.fill(0);
console.info(JSON.stringify(buf)); // {"type":"Buffer","data":[0,0,0,0,0,0,0,0,0,0]}
```

## buffer.allocUninitialized

ArkTS-Dyn：allocUninitialized(size: number): Buffer

ArkTS-Sta：allocUninitialized(size: int): Buffer

创建指定大小未初始化的Buffer对象。内存不从缓冲池分配。
创建的Buffer的内容未知，需要使用[fill](#fill)函数来初始化Buffer对象。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| size | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 |指定的Buffer对象长度，单位：字节。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [Buffer](#buffer) | 未初始化的Buffer实例。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

ArkTS-Sta错误码：

此接口在ArkTS-Sta无错误码。

**示例：**

ArkTS-Dyn示例：

```ts
import { buffer, JSON } from '@kit.ArkTS';

let buf = buffer.allocUninitialized(10);
buf.fill(0);
console.info(JSON.stringify(buf)); // {"type":"Buffer","data":[0,0,0,0,0,0,0,0,0,0]}
```

ArkTS-Sta示例：

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitialized(10);
buf.fill(0);
console.info(JSON.stringify(buf)); // {"type":"Buffer","data":[0,0,0,0,0,0,0,0,0,0]}
```

## buffer.byteLength

byteLength(string: string | Buffer | TypedArray | DataView | ArrayBuffer | SharedArrayBuffer, encoding?: BufferEncoding): number

根据不同的编码格式，返回指定字符串的字节数。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| string | string \| [Buffer](#buffer) \| TypedArray \| DataView \| ArrayBuffer \| SharedArrayBuffer | 是 | 指定字符串。 |
| encoding | [BufferEncoding](#bufferencoding) | 否 | 编码格式。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| number | 返回指定字符串的字节数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let str = '\u00bd + \u00bc = \u00be';
console.info(`${str}: ${str.length} characters, ${buffer.byteLength(str, 'utf-8')} bytes`);
// 输出结果：½ + ¼ = ¾: 9 characters, 12 bytes
```

## buffer.byteLength<sup>20+</sup>

byteLength(doc: string | Buffer | TypedArray | DataView | ArrayBuffer, encoding?: BufferEncoding): int

根据不同的编码方法，返回指定字符串的字节数。

**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| doc | string&nbsp;\|&nbsp;Buffer&nbsp;\|&nbsp;[TypedArray](#typedarray20)&nbsp;\|&nbsp;DataView&nbsp;\|&nbsp;ArrayBuffer | 是 | 指定字符串。 |
| encoding | [BufferEncoding](#bufferencoding) | 否 | 编码格式。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| int | 返回指定字符串的字节数。 |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let str = '\u00bd + \u00bc = \u00be';
console.info(`${str}: ${str.length} characters, ${buffer.byteLength(str, 'utf-8')} bytes`);
// 输出结果：½ + ¼ = ¾: 9 characters, 12 bytes
```

## buffer.compare

compare(buf1: Buffer | Uint8Array, buf2: Buffer | Uint8Array): -1 | 0 | 1

返回两个Buffer对象的比较结果，通常用于对Buffer对象数组进行排序。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| buf1 | [Buffer](#buffer) \| Uint8Array | 是 | 待比较数组。 |
| buf2 | [Buffer](#buffer) \| Uint8Array | 是 | 待比较数组。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| -1&nbsp;\|&nbsp;0&nbsp;\|&nbsp;1 | 如果buf1与buf2相同，则返回0。<br/>如果排序时buf1位于buf2之后，则返回1。<br/>如果排序时buf1位于buf2之前，则返回-1。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from('1234');
let buf2 = buffer.from('0123');
let res = buffer.compare(buf1, buf2);

console.info(Number(res).toString());
// 输出结果：1
```

## buffer.compare<sup>20+</sup>

compare(buf1: Buffer | Uint8Array, buf2: Buffer | Uint8Array): int

返回两个数组的比较结果，通常用于对Buffer对象数组进行排序。

**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| buf1 | [Buffer](#buffer) \| Uint8Array | 是 | 待比较数组。 |
| buf2 | [Buffer](#buffer) \| Uint8Array | 是 | 待比较数组。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| int | 如果buf1与buf2相同，则返回0。<br/>如果排序时buf1位于buf2之后，则返回1。<br/>如果排序时buf1位于buf2之前，则返回-1。 |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from('1234');
let buf2 = buffer.from('0123');
let res = buffer.compare(buf1, buf2);

console.info(Number(res).toString());
// 输出结果：1
```

## buffer.concat

ArkTS-Dyn：concat(list: Buffer[] | Uint8Array[], totalLength?: number): Buffer

ArkTS-Sta：concat(list: Buffer[] | Uint8Array[], totalLength?: int): Buffer

将数组中的内容复制指定字节长度到新的Buffer对象中并返回。

**系统能力：** SystemCapability.Utils.Lang

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| list | Buffer[]&nbsp;\|&nbsp;Uint8Array[] | 是 | 实例数组。 |
| totalLength | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 需要复制的总字节长度，默认值为0。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [Buffer](#buffer) | 返回新的Buffer对象。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 10200001 | The value of "length" is out of range. It must be >= 0 and <= uint32 max. Received value is: [length] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "length" is out of range. It must be >= 0 and <= uint32 max. Received value is: [length] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from("1234");
let buf2 = buffer.from("abcd");
let buf = buffer.concat([buf1, buf2]);
console.info(buf.toString('hex'));
// 输出结果：3132333461626364
```

## buffer.from

ArkTS-Dyn：from(array: number[]): Buffer

ArkTS-Sta：from(array: double[]): Buffer

根据指定数组创建新的Buffer对象。

**系统能力：** SystemCapability.Utils.Lang

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| array | ArkTS-Dyn：number[] <br> ArkTS-Sta：double[] | 是 | 指定数组。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [Buffer](#buffer) | 新的Buffer对象。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

ArkTS-Sta错误码：

此接口在ArkTS-Sta无错误码。

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x62, 0x75, 0x66, 0x66, 0x65, 0x72]);
console.info(buf.toString('hex'));
// 输出结果：627566666572
```

## buffer.from

from(arrayBuffer: ArrayBuffer | SharedArrayBuffer, byteOffset?: number, length?: number): Buffer

创建与`arrayBuffer`共享内存的指定长度的Buffer对象。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| arrayBuffer | ArrayBuffer&nbsp;\|&nbsp;SharedArrayBuffer | 是 | 实例对象。 |
| byteOffset | number | 否 | 字节偏移量，默认值：0。 |
| length | number | 否 | 字节长度， 默认值:（arrayBuffer.byteLength - byteOffset）。在传入null时字节长度为0。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [Buffer](#buffer) | 返回一个Buffer对象，该对象与入参对象`arrayBuffer`共享相同的内存区域。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200001 | The value of "[byteOffset/length]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [byteOffset/length] |

**示例：**

```ts
import { buffer, JSON } from '@kit.ArkTS';

let ab = new ArrayBuffer(10);
let buf = buffer.from(ab, 0, 2);
console.info(JSON.stringify(buf)); // {"type":"Buffer","data":[0,0]}
```

## buffer.from<sup>20+</sup>

from(arrayBuffer: ArrayBuffer, byteOffset?: int, length?: int): Buffer

创建指定长度的与`arrayBuffer`共享内存的Buffer对象。

**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| arrayBuffer | ArrayBuffer | 是 | 实例对象。 |
| byteOffset | int | 否 | 字节偏移量，默认值：0。 |
| length | int | 否 | 字节长度， 默认值:（arrayBuffer.byteLength - byteOffset）。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Buffer | 返回一个Buffer对象，与入参对象保持内存共享。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[byteOffset/length]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [byteOffset/length] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let ab = new ArrayBuffer(10);
let buf = buffer.from(ab, 0, 2);
console.info(JSON.stringify(buf)); // {"type":"Buffer","data":[0,0]}
```

## buffer.from

from(buffer: Buffer | Uint8Array): Buffer

当入参为Buffer对象时，创建新的Buffer对象并复制入参Buffer对象的数据，然后返回新对象。
当入参为Uint8Array对象时，基于Uint8Array对象的内存创建新的Buffer对象并返回，保持数据的内存关联。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| buffer | [Buffer](#buffer) \| Uint8Array | 是 | 对象数据。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [Buffer](#buffer) | 新的Buffer对象。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

ArkTS-Sta错误码：

此接口在ArkTS-Sta无错误码。

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

// 以Buffer对象类型进行创建新的Buffer对象
let buf1 = buffer.from('buffer');
let buf2 = buffer.from(buf1);

// 以Uint8Array对象类型进行创建Buffer对象，保持对象间内存共享
let uint8Array = new Uint8Array(10);
let buf3 = buffer.from(uint8Array);
buf3.fill(1);
console.info("uint8Array:", uint8Array);
// 输出结果：1,1,1,1,1,1,1,1,1,1
```

## buffer.from

ArkTS-Dyn：from(object: Object, offsetOrEncoding: number | string, length: number): Buffer

ArkTS-Sta：from(object: Object, offsetOrEncoding: int | string, length: int): Buffer

根据指定的`object`类型数据，创建新的Buffer对象。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| object | Object | 是 | 支持Symbol.toPrimitive或valueOf()的对象。 |
| offsetOrEncoding | ArkTS-Dyn：number&nbsp;\|&nbsp;string <br> ArkTS-Sta：int&nbsp;\|&nbsp;string | 是 | 字节偏移量或编码格式。 |
| length | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | ArkTS-Dyn：字节长度（此入参仅在object的valueOf()返回值为ArrayBuffer时生效，取值范围：0 <= length <= ArrayBuffer.byteLength，超出范围时报错: 10200001）。其他情况下可填任意number类型值，该参数不会对结果产生影响。<br> ArkTS-Sta：字节长度（此入参仅在object的valueOf()返回值为ArrayBuffer时生效，取值范围：0 <= length <= ArrayBuffer.byteLength，超出范围时报错: 10200001）。其他情况下可填任意int类型值，该参数不会对结果产生影响。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [Buffer](#buffer) | 返回新的Buffer对象。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

ArkTS-Sta错误码：

此接口在ArkTS-Sta无错误码。

**示例：**

```ts
import { buffer, JSON } from '@kit.ArkTS';

let buf = buffer.from(new String('this is a test'), 'utf8', 14);
console.info(JSON.stringify(buf)); // {"type":"Buffer","data":[116,104,105,115,32,105,115,32,97,32,116,101,115,116]}
```

## buffer.from

from(string: String, encoding?: BufferEncoding): Buffer

根据指定编码格式的字符串，创建新的Buffer对象。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| string | String | 是 | 字符串。 |
| encoding | [BufferEncoding](#bufferencoding) | 否 | 编码格式。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [Buffer](#buffer) | 返回新的Buffer对象。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

ArkTS-Sta错误码：

此接口在ArkTS-Sta无错误码。

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from('this is a test');
let buf2 = buffer.from('7468697320697320612074c3a97374', 'hex');

console.info(buf1.toString());
// 输出结果：this is a test
console.info(buf2.toString());
// 输出结果：this is a tést
```


## buffer.isBuffer

isBuffer(obj: Object): boolean

判断`obj`是否为Buffer。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| obj | Object | 是 | 判断对象。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 如果obj是Buffer，则返回true，否则返回false。 |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let result = buffer.isBuffer(buffer.alloc(10)); // 10: buffer size
console.info("result = " + result);
// 输出结果：result = true
let result1 = buffer.isBuffer(buffer.from('foo'));
console.info("result1 = " + result1);
// 输出结果：result1 = true
let result2 = buffer.isBuffer('a string');
console.info("result2 = " + result2);
// 输出结果：result2 = false
let src: Array<string> = []
let result3 = buffer.isBuffer(src);
console.info("result3 = " + result3);
// 输出结果：result3 = false
let result4 = buffer.isBuffer(new Uint8Array(1024));
console.info("result4 = " + result4);
// 输出结果：result4 = false
```

## buffer.isEncoding

isEncoding(encoding: string): boolean

判断`encoding`是否为支持的编码格式。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| encoding | string | 是 | 编码格式。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 是支持的编码格式返回true，反之则返回false。 |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

console.info(buffer.isEncoding('utf-8').toString());
// 输出结果：true
console.info(buffer.isEncoding('hex').toString());
// 输出结果：true
console.info(buffer.isEncoding('utf/8').toString());
// 输出结果：false
console.info(buffer.isEncoding('').toString());
// 输出结果：false
```

## buffer.transcode

transcode(source: Buffer | Uint8Array, fromEnc: string, toEnc: string): Buffer

将Buffer或Uint8Array对象从一种字符编码重新编码为另一种。

**系统能力：** SystemCapability.Utils.Lang

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| source | [Buffer](#buffer) \| Uint8Array | 是 | 实例对象。 |
| fromEnc | string | 是 | 当前编码。 支持的格式范围为[BufferEncoding](#bufferencoding)。 |
| toEnc | string | 是 | 目标编码。 支持的格式范围为[BufferEncoding](#bufferencoding)。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [Buffer](#buffer) | 将当前编码转换成目标编码，并返回一个新的Buffer对象。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

ArkTS-Sta错误码：

此接口在ArkTS-Sta无错误码。

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let newBuf = buffer.transcode(buffer.from('€'), 'utf-8', 'ascii');
console.info("newBuf = " + newBuf.toString('ascii'));
// 输出结果：newBuf = ,
```

## Buffer

### 属性

**系统能力：** SystemCapability.Utils.Lang

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| length | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 否 | Buffer对象的字节长度。 |
| buffer | ArrayBuffer | 是 | 否 | ArrayBuffer对象。 |
| byteOffset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 否 | 当前Buffer所在内存池的偏移量。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200013 | ${propertyName} cannot be set for the buffer that has only a getter. |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from("1236");
console.info(JSON.stringify(buf.length));
// 输出结果：4
let arrayBuffer = buf.buffer;
console.info(JSON.stringify(new Uint8Array(arrayBuffer)));
// 输出结果：{"0":49,"1":50,"2":51,"3":54}
console.info(JSON.stringify(buf.byteOffset));
// 输出结果：0
```

### compare

compare(target: Buffer | Uint8Array, targetStart?: number, targetEnd?: number, sourceStart?: number, sourceEnd?: number): -1 | 0 | 1

比较当前Buffer对象与目标Buffer对象，并返回Buffer在排序中的结果。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| target | [Buffer](#buffer) \| Uint8Array | 是 | 要比较的实例对象。 |
| targetStart | number | 否 | `target`实例中开始的偏移量。默认值：0。 |
| targetEnd | number | 否 | `target`实例中结束的偏移量（不包含结束位置）。默认值：目标对象的字节长度。 |
| sourceStart | number | 否 | `this`实例中开始的偏移量。默认值：0。 |
| sourceEnd | number | 否 | `this`实例中结束的偏移量（不包含结束位置）。默认值：当前对象的字节长度。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| number | 返回比较结果。-1：当前排列在目标前，0：当前与目标相同，1：当前排列在目标后。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200001 | The value of "[targetStart/targetEnd/sourceStart/sourceEnd]" is out of range. |

**示例：**

```ts
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

### compare<sup>20+</sup>

compare(target: Buffer | Uint8Array, targetStart?: int, targetEnd?: int, sourceStart?: int, sourceEnd?: int): int

比较当前Buffer对象与目标Buffer对象，并返回Buffer在排序中的结果。

**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| target | [Buffer](#buffer) \| Uint8Array | 是 | 要比较的实例对象。 |
| targetStart | int | 否 | `target`实例中开始的偏移量。默认值：0。 |
| targetEnd | int | 否 | `target`实例中结束的偏移量（不包含结束位置）。默认值：目标对象的字节长度。 |
| sourceStart | int | 否 | `this`实例中开始的偏移量。默认值：0。 |
| sourceEnd | int | 否 | `this`实例中结束的偏移量（不包含结束位置）。默认值：当前对象的字节长度。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| int | 返回比较结果。-1：当前排列在目标前，0：当前与目标相同，1：当前排列在目标后。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[targetStart/targetEnd/sourceStart/sourceEnd]" is out of range. |

**示例：**

```ts
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

### copy

ArkTS-Dyn：copy(target: Buffer| Uint8Array, targetStart?: number, sourceStart?: number, sourceEnd?: number): number

ArkTS-Sta：copy(target: Buffer| Uint8Array, targetStart?: int, sourceStart?: int, sourceEnd?: int): int

将`this`实例中指定位置的数据复制到`target`的指定位置上，并返回复制的字节总长度。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| target | [Buffer](#buffer) \| Uint8Array | 是 | 要复制到的Buffer或Uint8Array实例。 |
| targetStart | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | `target`实例中开始写入的偏移量。默认值：0。 |
| sourceStart | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | `this`实例中开始复制的偏移量。默认值: 0。 |
| sourceEnd | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | `this`实例中结束复制的偏移量（不包含结束位置）。默认值：当前对象的字节长度。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int |  复制的字节总长度。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200001 | The value of "[targetStart/sourceStart/sourceEnd]" is out of range. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[targetStart/sourceStart/sourceEnd]" is out of range. |

**示例：**

```ts
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

### entries

ArkTS-Dyn：entries(): IterableIterator&lt;[number,&nbsp;number]&gt;

ArkTS-Sta：entries(): IterableIterator&lt;[int,&nbsp;long]&gt;

返回一个包含key和value的迭代器。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：IterableIterator&lt;[number,&nbsp;number]&gt; <br> ArkTS-Sta：IterableIterator&lt;[int,&nbsp;long]&gt; |  ArkTS-Dyn：包含key和value的迭代器，同时两者皆为number类型。<br> ArkTS-Sta：包含key和value的迭代器，key为int类型value为long类型。 |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from('buffer');
let pair = buf.entries();
for (let value of pair) {
  console.info("buffer: " + value);
  /*
  输出结果：buffer: 0,98
           buffer: 1,117
           buffer: 2,102
           buffer: 3,102
           buffer: 4,101
           buffer: 5,114
   */
}
```

### equals

equals(otherBuffer: Uint8Array | Buffer): boolean

比较`this`实例和otherBuffer实例是否相等。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| otherBuffer | Uint8Array \| [Buffer](#buffer) | 是 | 比较的目标对象。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 相等则返回true，否则返回false。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

ArkTS-Sta错误码：

此接口在ArkTS-Sta无错误码。

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from('ABC');
let buf2 = buffer.from('414243', 'hex');
let buf3 = buffer.from('ABCD');

console.info(buf1.equals(buf2).toString());
// 输出结果：true
console.info(buf1.equals(buf3).toString());
// 输出结果：false
```

### fill

ArkTS-Dyn：fill(value: string | Buffer | Uint8Array | number, offset?: number, end?: number, encoding?: BufferEncoding): Buffer

ArkTS-Sta：fill(value: string | Buffer | Uint8Array | int | double | long, offset?: int, end?: int, encoding?: BufferEncoding): Buffer

使用`value`填充当前对象指定位置的数据，默认为循环填充，并返回填充后的Buffer对象。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：string \| [Buffer](#buffer) \| Uint8Array \| number <br> ArkTS-Sta：string \| [Buffer](#buffer) \| Uint8Array \| int \| double \| long | 是 | 用于填充的值。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 起始偏移量。默认值：0。 |
| end | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 结束偏移量（不包含结束位置）。 默认值：当前对象的字节长度。 |
| encoding | [BufferEncoding](#bufferencoding) | 否 | 字符编码格式（`value`为string才有意义）。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [Buffer](#buffer) | 返回填充后的Buffer对象。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200001 | The value of "[offset/end]" is out of range. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[offset/end]" is out of range. |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let b = buffer.allocUninitializedFromPool(50).fill('h');
console.info(b.toString());
// 输出结果：hhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh
```


### includes

ArkTS-Dyn：includes(value: string | number | Buffer | Uint8Array, byteOffset?: number, encoding?: BufferEncoding): boolean

ArkTS-Sta：includes(value: string | int | double | long | Buffer | Uint8Array, byteOffset?: int, encoding?: BufferEncoding): boolean

检查Buffer对象是否包含`value`值。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：string \| number \| [Buffer](#buffer) \| Uint8Array <br> ArkTS-Sta：string \| int \| double \| long \| [Buffer](#buffer) \| Uint8Array | 是 | 要搜索的内容。 |
| byteOffset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 字节偏移量。如果为负数，则从末尾开始计算偏移量。默认值：0。 |
| encoding | [BufferEncoding](#bufferencoding) | 否 | 字符编码格式。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 存在为true，否则为false。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

ArkTS-Sta错误码：

此接口在ArkTS-Sta无错误码。

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from('this is a buffer');
console.info(buf.includes('this').toString());
// 输出结果：true
console.info(buf.includes('be').toString());
// 输出结果：false
```

### indexOf

ArkTS-Dyn：indexOf(value: string | number | Buffer | Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number

ArkTS-Sta：indexOf(value: string | int | double | long | Buffer | Uint8Array, byteOffset?: int, encoding?: BufferEncoding): int

返回当前对象中首次出现`value`的索引，如果不包含`value`，则返回-1。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | string \| ArkTS-Dyn：number <br> ArkTS-Sta：int \| double \| long \| [Buffer](#buffer) \| Uint8Array | 是 | 要查找的内容。 |
| byteOffset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 字节偏移量。如果为负数，则从末尾开始计算偏移量。默认值：0。 |
| encoding | [BufferEncoding](#bufferencoding) | 否 | 字符编码格式。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 第一次出现位置。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

ArkTS-Sta错误码：

此接口在ArkTS-Sta无错误码。

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from('this is a buffer');
console.info(buf.indexOf('this').toString());
// 输出结果：0
console.info(buf.indexOf('is').toString());
// 输出结果：2
```

### keys

ArkTS-Dyn：keys(): IterableIterator&lt;number&gt;

ArkTS-Sta：keys(): IterableIterator&lt;int&gt;

返回包含key值的迭代器。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
|  ArkTS-Dyn：IterableIterator&lt;number&gt; <br> ArkTS-Sta：IterableIterator&lt;int&gt; | 返回一个包含key值的迭代器。 |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from('buffer');
let numbers = Array.from(buf.keys());
for (const key of numbers) {
  console.info(key.toString());
  /*
  输出结果：0
           1
           2
           3
           4
           5
   */
}
```

### lastIndexOf

ArkTS-Dyn：lastIndexOf(value: string | number | Buffer | Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number

ArkTS-Sta：lastIndexOf(value: string | int | double | long | Buffer | Uint8Array, byteOffset?: int, encoding?: BufferEncoding): int

返回`this`实例中最后一次出现`value`的索引，如果对象不包含`value`，则返回-1。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：string \| number \| [Buffer](#buffer) \| Uint8Array <br> ArkTS-Sta：string \| int \| double \| long \| [Buffer](#buffer) \| Uint8Array | 是 | 要搜索的内容。 |
| byteOffset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 字节偏移量。如果为负数，则从末尾开始计算偏移量。默认值：Buffer.length。 |
| encoding | [BufferEncoding](#bufferencoding) | 否 | 字符编码格式。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 最后一次出现`value`值的索引。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

ArkTS-Sta错误码：

此接口在ArkTS-Sta无错误码。

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from('this buffer is a buffer');
console.info(buf.lastIndexOf('this').toString());
// 输出结果：0
console.info(buf.lastIndexOf('buffer').toString());
// 输出结果：17
```


### readBigInt64BE

ArkTS-Dyn：readBigInt64BE(offset?: number): bigint

ArkTS-Sta：readBigInt64BE(offset?: int): bigint

从指定的`offset`处读取有符号的大端序64位整数。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 8。|

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| bigint | 读取出的内容。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset]. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset]. |

**示例：**

```ts
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

### readBigInt64LE

ArkTS-Dyn：readBigInt64LE(offset?: number): bigint

ArkTS-Sta：readBigInt64LE(offset?: int): bigint

从指定的`offset`处读取有符号的小端序64位整数。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。取值范围：0 <= offset <= Buffer.length - 8，默认值：0。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| bigint | 读取出的内容。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset]. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset]. |

**示例：**

```ts
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

### readBigUInt64BE

ArkTS-Dyn：readBigUInt64BE(offset?: number): bigint

ArkTS-Sta：readBigUInt64BE(offset?: int): bigint

从指定的`offset`处读取无符号的大端序64位整数。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。取值范围：0 <= offset <= Buffer.length - 8，默认值：0。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| bigint | 读取出的内容。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset]. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset]. |

**示例：**

```ts
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

### readBigUInt64LE

ArkTS-Dyn：readBigUInt64LE(offset?: number): bigint

ArkTS-Sta：readBigUInt64LE(offset?: int): bigint

从指定的`offset`处读取无符号的小端序64位整数。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。取值范围：0 <= offset <= Buffer.length - 8，默认值：0。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| bigint | 读取出的内容。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset]. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset]. |

**示例：**

```ts
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

### readDoubleBE

ArkTS-Dyn：readDoubleBE(offset?: number): number

ArkTS-Sta：readDoubleBE(offset?: int): double

从指定的`offset`处读取64位大端序双精度值。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。取值范围：0 <= offset <= Buffer.length - 8，默认值：0。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：double | 读取出的内容。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset]. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset]. |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readDoubleBE(0).toString());
// 输出结果：8.20788039913184e-304
let buf1 = buffer.allocUninitializedFromPool(8);
let result = buf1.writeDoubleBE(123.456, 0);
console.info("result = " + result);
// 输出结果：result = 8
```

### readDoubleLE

ArkTS-Dyn：readDoubleLE(offset?: number): number

ArkTS-Sta：readDoubleLE(offset?: int): double

从指定的`offset`处读取64位小端序双精度值。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。取值范围：0 <= offset <= Buffer.length - 8，默认值：0。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：double | 读取出的内容。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset]. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset]. |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readDoubleLE(0).toString());
// 输出结果：5.447603722011605e-270
let buf1 = buffer.allocUninitializedFromPool(8);
let result = buf1.writeDoubleLE(123.456, 0);
console.info("result = " + result);
// 输出结果：result = 8
```

### readFloatBE

ArkTS-Dyn：readFloatBE(offset?: number): number

ArkTS-Sta：readFloatBE(offset?: int): double

从指定的`offset`处读取32位大端序浮点数。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。取值范围：0 <= offset <= Buffer.length - 4，默认值：0。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：double | 读取出的内容。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset]. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset]. |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readFloatBE(0).toString());
// 输出结果：2.387939260590663e-38
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeFloatBE(0xcabcbcbc, 0);
console.info("result = " + result);
// 输出结果：result = 4
```

### readFloatLE

ArkTS-Dyn：readFloatLE(offset?: number): number

ArkTS-Sta：readFloatLE(offset?: int): double

从指定的`offset`处读取32位小端序浮点数。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。取值范围：0 <= offset <= Buffer.length - 4，默认值：0。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：double | 读取出的内容。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset]. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset]. |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readFloatLE(0).toString());
// 输出结果：1.539989614439558e-36
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeFloatLE(0xcabcbcbc, 0);
console.info("result = " + result);
// 输出结果：result = 4
```

### readInt8

ArkTS-Dyn：readInt8(offset?: number): number

ArkTS-Sta：readInt8(offset?: int): long

从指定的`offset`处读取有符号的8位整数。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。取值范围：0 <= offset <= Buffer.length - 1，默认值：0。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：long | 读取出的内容。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 1. Received value is: [offset]. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 1. Received value is: [offset]. |

**示例：**

```ts
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

### readInt16BE

ArkTS-Dyn：readInt16BE(offset?: number): number

ArkTS-Sta：readInt16BE(offset?: int): long

从指定的`offset`处读取有符号的大端序16位整数。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。取值范围：0 <= offset <= Buffer.length - 2，默认值：0。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：long | 读取出的内容。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 2. Received value is: [offset]. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 2. Received value is: [offset]. |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0, 5]);
console.info(buf.readInt16BE(0).toString());
// 输出结果：5
let buf1 = buffer.alloc(2);
let result = buf1.writeInt16BE(0x1234, 0);
console.info("result = " + result);
// 输出结果：result = 2
```

### readInt16LE

ArkTS-Dyn：readInt16LE(offset?: number): number

ArkTS-Sta：readInt16LE(offset?: int): long

从指定的`offset`处读取有符号的小端序16位整数。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。取值范围：0 <= offset <= Buffer.length - 2，默认值：0。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：long | 读取出的内容。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 2. Received value is: [offset]. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 2. Received value is: [offset]. |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0, 5]);
console.info(buf.readInt16LE(0).toString());
// 输出结果：1280
let buf1 = buffer.alloc(2);
let result = buf1.writeInt16BE(0x1234, 0);
console.info("result = " + result);
// 输出结果：result = 2
```

### readInt32BE

ArkTS-Dyn：readInt32BE(offset?: number): number

ArkTS-Sta：readInt32BE(offset?: int): long

从指定的`offset`处读取有符号的大端序32位整数。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。取值范围：0 <= offset <= Buffer.length - 4，默认值：0。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：long | 读取出的内容。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset]. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset]. |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0, 0, 0, 5]);
console.info(buf.readInt32BE(0).toString());
// 输出结果：5
let buf1 = buffer.alloc(4);
let result = buf1.writeInt32BE(0x12345678, 0);
console.info("result = " + result);
// 输出结果：result = 4
```

### readInt32LE

ArkTS-Dyn：readInt32LE(offset?: number): number

ArkTS-Sta：readInt32LE(offset?: int): long

从指定的`offset`处读取有符号的小端序32位整数。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。取值范围：0 <= offset <= Buffer.length - 4，默认值：0。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：long | 读取出的内容。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 10200001 |  The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset]. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 |  The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset]. |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0, 0, 0, 5]);
console.info(buf.readInt32LE(0).toString());
// 输出结果：83886080
let buf1 = buffer.alloc(4);
let result = buf1.writeInt32BE(0x12345678, 0);
console.info("result = " + result);
// 输出结果：result = 4
```

### readIntBE

ArkTS-Dyn：readIntBE(offset: number, byteLength: number): number

ArkTS-Sta：readIntBE(offset: int, byteLength: int): long

从指定的`offset`处读取byteLength个字节，并将结果解释为支持最高48位精度的大端序、二进制补码有符号值。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 偏移量。取值范围：0 <= offset <= Buffer.length - byteLength。 |
| byteLength | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 读取的字节数。取值范围：1 <= byteLength <= 6。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：long | 读取的内容。当offset为小数时，返回undefined。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
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


### readIntLE

ArkTS-Dyn：readIntLE(offset: number, byteLength: number): number

ArkTS-Sta：readIntLE(offset: int, byteLength: int): long

从指定的`offset`处读取`byteLength`个字节，并将结果解释为支持最高48位精度的小端序、二进制补码有符号值。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 偏移量。取值范围：0 <= offset <= Buffer.length - byteLength。 |
| byteLength | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 读取的字节数。取值范围：1 <= byteLength <= 6。|


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：long | 读取出的内容。当offset为小数时，返回undefined。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x12, 0x34, 0x56, 0x78, 0x90, 0xab]);
console.info(buf.readIntLE(0, 6).toString(16));
// 输出结果：-546f87a9cbee
let buf1 = buffer.allocUninitializedFromPool(6);
let result = buf1.writeIntLE(0x123456789011, 0, 6);
console.info("result = " + result);
// 输出结果：result = 6
```

### readUInt8

ArkTS-Dyn：readUInt8(offset?: number): number

ArkTS-Sta：readUInt8(offset?: int): long

从`offset`处读取8位无符号整型数。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。取值范围：0 <= offset <= Buffer.length - 1，默认值：0。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：long | 读取出的内容。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 1. Received value is: [offset]. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 1. Received value is: [offset]. |

**示例：**

```ts
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

### readUInt16BE

ArkTS-Dyn：readUInt16BE(offset?: number): number

ArkTS-Sta：readUInt16BE(offset?: int): long

从指定的`offset`处读取无符号的大端序16位整数。

**系统能力：** SystemCapability.Utils.Lang

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。取值范围：0 <= offset <= Buffer.length - 2，默认值：0。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：long | 读取出的内容。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 2. Received value is: [offset]. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 2. Received value is: [offset]. |

**示例：**

```ts
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

### readUInt16LE

ArkTS-Dyn：readUInt16LE(offset?: number): number

ArkTS-Sta：readUInt16LE(offset?: int): long

从指定的`offset`处的buf读取无符号的小端序16位整数。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。取值范围：0 <= offset <= Buffer.length - 2，默认值：0。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：long | 读取出的内容。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 2. Received value is: [offset]. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 2. Received value is: [offset]. |

**示例：**

```ts
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

### readUInt32BE

ArkTS-Dyn：readUInt32BE(offset?: number): number

ArkTS-Sta：readUInt32BE(offset?: int): long

从指定的`offset`处的buf读取无符号的大端序32位整数。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。取值范围：0 <= offset <= Buffer.length - 4，默认值：0。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：long | 读取出的内容。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset]. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset]. |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x12, 0x34, 0x56, 0x78]);
console.info(buf.readUInt32BE(0).toString(16));
// 输出结果：12345678
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeUInt32BE(0x12345678, 0);
console.info("result = " + result);
// 输出结果：result = 4
```

### readUInt32LE

ArkTS-Dyn：readUInt32LE(offset?: number): number

ArkTS-Sta：readUInt32LE(offset?: int): long

从指定的`offset`处的buf读取无符号的小端序32位整数。

**系统能力：** SystemCapability.Utils.Lang

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。取值范围：0 <= offset <= Buffer.length - 4，默认值：0。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：long | 读取出的内容。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset]. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset]. |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x12, 0x34, 0x56, 0x78]);
console.info(buf.readUInt32LE(0).toString(16));
// 输出结果：78563412
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeUInt32LE(0x12345678, 0);
console.info("result = " + result);
// 输出结果：result = 4
```

### readUIntBE

ArkTS-Dyn：readUIntBE(offset: number, byteLength: number): number

ArkTS-Sta：readUIntBE(offset: int, byteLength: int): long

从指定的`offset`处的buf读取`byteLength`个字节，并将结果解释为支持最高48位精度的无符号大端序整数。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 偏移量。取值范围：0 <= offset <= Buffer.length - byteLength。 |
| byteLength | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 要读取的字节数。读取的字节数。取值范围：1 <= byteLength <= 6。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：long | 读取出的内容。当offset为小数时，返回undefined。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x12, 0x34, 0x56, 0x78, 0x90, 0xab]);
console.info(buf.readUIntBE(0, 6).toString(16));
// 输出结果：1234567890ab
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeUIntBE(0x13141516, 0, 4);
console.info("result = " + result);
// 输出结果：result = 4
```

### readUIntLE

ArkTS-Dyn：readUIntLE(offset: number, byteLength: number): number

ArkTS-Sta：readUIntLE(offset: int, byteLength: int): long

从指定的`offset`处的buf读取`byteLength`个字节，并将结果解释为支持最高48位精度的无符号小端序整数。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 偏移量。取值范围：0 <= offset <= Buffer.length - byteLength。 |
| byteLength | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 读取的字节数。取值范围：1 <= byteLength <= 6。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：long | 读取出的内容。当offset为小数时，返回undefined。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x12, 0x34, 0x56, 0x78, 0x90, 0xab]);
console.info(buf.readUIntLE(0, 6).toString(16));
// 输出结果：ab9078563412
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeUIntLE(0x13141516, 0, 4);
console.info("result = " + result);
// 输出结果：result = 4
```

### subarray

ArkTS-Dyn：subarray(start?: number, end?: number): Buffer

ArkTS-Sta：subarray(start?: int, end?: int): Buffer

截取当前对象指定位置的数据并返回。

**系统能力：** SystemCapability.Utils.Lang

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| start | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 截取开始位置。默认值：0。 |
| end | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 |  截取结束位置（不包含结束位置）。默认值：当前对象的字节长度。 ArkTS-Dyn：在传入null时返回空Buffer。|

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [Buffer](#buffer) | 返回新的Buffer对象。当start < 0或end < 0时返回空Buffer。 |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.allocUninitializedFromPool(26);

for (let i = 0; i < 26; i++) {
  buf1.writeInt8(i + 97, i);
}
const buf2 = buf1.subarray(0, 3);
console.info(buf2.toString('ascii', 0, buf2.length));
// 输出结果: abc
```

### swap16

swap16(): Buffer

将当前对象转换为无符号的16位整数数组，并交换字节顺序。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [Buffer](#buffer) | 交换之后的Buffer对象。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200009 | The buffer size must be a multiple of 16-bits. |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from([0x1, 0x2, 0x3, 0x4, 0x5, 0x6, 0x7, 0x8]);
console.info(buf1.toString('hex'));
// 输出结果：0102030405060708
buf1.swap16();
console.info(buf1.toString('hex'));
// 输出结果：0201040306050807
```

### swap32

swap32(): Buffer

将当前对象转换为无符号的32位整数数组，并交换字节顺序。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [Buffer](#buffer) | 交换之后的Buffer对象。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200009 | The buffer size must be a multiple of 32-bits. |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from([0x1, 0x2, 0x3, 0x4, 0x5, 0x6, 0x7, 0x8]);
console.info(buf1.toString('hex'));
// 输出结果：0102030405060708
buf1.swap32();
console.info(buf1.toString('hex'));
// 输出结果：0403020108070605
```

### swap64

swap64(): Buffer

将当前对象转换为无符号的64位整数数组，并交换字节顺序。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [Buffer](#buffer) | 交换之后的Buffer对象。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200009 | The buffer size must be a multiple of 64-bits. |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from([0x1, 0x2, 0x3, 0x4, 0x5, 0x6, 0x7, 0x8]);
console.info(buf1.toString('hex'));
// 输出结果：0102030405060708
buf1.swap64();
console.info(buf1.toString('hex'));
// 输出结果：0807060504030201
```

### toJSON

toJSON(): Object

将Buffer转为JSON并返回。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Object | JSON对象。 |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from([0x1, 0x2, 0x3, 0x4, 0x5]);
let obj = buf1.toJSON();
console.info(JSON.stringify(obj));
// 输出结果: {"type":"Buffer","data":[1,2,3,4,5]}
```

### toJSON<sup>20+</sup>

toJSON(): jsonx.JsonElement

将Buffer转为JSON并返回。

**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 20

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [jsonx.JsonElement](../native-lib/arkts1.2-jsonx.md#jsonelement) | 返回一个包含buffer的JsonElement |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from([0x1, 0x2, 0x3, 0x4, 0x5]);
let obj = buf1.toJSON();
console.info(JSON.stringify(obj));
// 输出结果: {"type":"Buffer","data":[1,2,3,4,5]}
```

### toString

toString(encoding?: string, start?: number, end?: number): string

将当前对象中指定位置的数据转成指定编码格式的字符串并返回。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| encoding | string | 否 | 字符编码格式。默认值：'utf8'。 |
| start  | number | 否 |  开始位置。默认值：0。 |
| end  | number | 否 |  结束位置。默认值：Buffer.length。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| string | 字符串。当start >= Buffer.length或start > end时返回空字符串。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types. |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.allocUninitializedFromPool(26);
for (let i = 0; i < 26; i++) {
  buf1.writeInt8(i + 97, i);
}
console.info(buf1.toString('utf-8'));
// 输出结果: abcdefghijklmnopqrstuvwxyz
```

### toString<sup>20+</sup>

toString(encoding?: BufferEncoding, start?: int, end?: int): string

将当前对象中指定位置数据转成指定编码格式字符串并返回。

**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| encoding | [BufferEncoding](#bufferencoding) | 否 | 字符编码格式。默认值：'utf8'。 |
| start  | int | 否 |  开始位置。默认值：0。 |
| end  | int | 否 |  结束位置。默认值：Buffer.length。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| string | 字符串。当start >= Buffer.length或start > end时返回空字符串。 |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.allocUninitializedFromPool(26);
for (let i = 0; i < 26; i++) {
  buf1.writeInt8(i + 97, i);
}
console.info(buf1.toString('utf-8'));
// 输出结果: abcdefghijklmnopqrstuvwxyz
```

### values

ArkTS-Dyn：values(): IterableIterator&lt;number&gt;

ArkTS-Sta：values(): IterableIterator&lt;long&gt;

返回一个包含value的迭代器。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：IterableIterator&lt;number&gt; <br> ArkTS-Sta：IterableIterator&lt;long&gt; | 迭代器。 |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.from('buffer');
let pair = buf.values();
for (let value of pair) {
  console.info("buffer: " + value);
  /*
  输出结果：buffer: 98
           buffer: 117
           buffer: 102
           buffer: 102
           buffer: 101
           buffer: 114
   */
}
```

### write

ArkTS-Dyn：write(str: string, offset?: number, length?: number, encoding?: string): number

ArkTS-Sta：write(str: string, offset?: int, length?: int, encoding?: string): int

在Buffer对象的offset偏移处写入指定编码的字符串，写入的字节长度为length。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| str | string | 是 | 要写入Buffer的字符串。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值：0。 |
| length | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 最大字节长度。默认值：(Buffer.length - offset)。|
| encoding | string | 否 | 字符编码。默认值：'utf8'。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200001 | The value of "[offset/length]" is out of range. It must be >= 0 and <= buf.length. Received value is: [offset/length]. |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[offset/length]" is out of range. It must be >= 0 and <= buf.length. Received value is: [offset/length]. |

**示例：**

```ts
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

### writeBigInt64BE

ArkTS-Dyn：writeBigInt64BE(value: bigint, offset?: number): number

ArkTS-Sta：writeBigInt64BE(value: bigint, offset?: int): int

在Buffer对象的offset偏移处写入有符号的大端序64位BigInt型数据。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | bigint | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 8。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeBigInt64BE(BigInt(0x0102030405060708), 0);
console.info("result = " + result);
// 输出结果：result = 8
```

### writeBigInt64LE

ArkTS-Dyn：writeBigInt64LE(value: bigint, offset?: number): number

ArkTS-Sta：writeBigInt64LE(value: bigint, offset?: int): int

在Buffer对象的offset偏移处写入有符号的小端序64位BigInt型数据。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | bigint | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 8。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeBigInt64LE(BigInt(0x0102030405060708), 0);
console.info("result = " + result);
// 输出结果：result = 8
```

### writeBigUInt64BE

ArkTS-Dyn：writeBigUInt64BE(value: bigint, offset?: number): number

ArkTS-Sta：writeBigUInt64BE(value: bigint, offset?: int): int

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

在Buffer对象的offset偏移处写入无符号的大端序64位BigUInt型数据。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | bigint | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 8。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeBigUInt64BE(BigInt(0xdecafafecacefade), 0);
console.info("result = " + result);
// 输出结果：result = 8
```

### writeBigUInt64LE

ArkTS-Dyn：writeBigUInt64LE(value: bigint, offset?: number): number

ArkTS-Sta：writeBigUInt64LE(value: bigint, offset?: int): int

在Buffer对象的offset偏移处写入无符号的小端序64位BigUInt型数据。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | bigint | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 8。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeBigUInt64LE(BigInt(0xdecafafecacefade), 0);
console.info("result = " + result);
// 输出结果：result = 8
```

### writeDoubleBE

ArkTS-Dyn：writeDoubleBE(value: number, offset?: number): number

ArkTS-Sta：writeDoubleBE(value: double, offset?: int): int

在Buffer对象的offset偏移处写入大端序的64位双浮点型数据。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：number <br> ArkTS-Sta：double | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 8。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeDoubleBE(123.456, 0);
console.info("result = " + result);
// 输出结果：result = 8
```

### writeDoubleLE

ArkTS-Dyn：writeDoubleLE(value: number, offset?: number): number

ArkTS-Sta：writeDoubleLE(value: double, offset?: int): int

在Buffer对象的offset偏移处写入小端序的64位双浮点型数据。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：number <br> ArkTS-Sta：double | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 8。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeDoubleLE(123.456, 0);
console.info("result = " + result);
// 输出结果：result = 8
```

### writeFloatBE

ArkTS-Dyn：writeFloatBE(value: number, offset?: number): number

ArkTS-Sta：writeFloatBE(value: double, offset?: int): int

在Buffer对象的offset偏移处写入大端序的32位浮点型数据。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：number <br> ArkTS-Sta：double | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 4。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn: number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeFloatBE(0xcafebabe, 0);
console.info("result = " + result);
// 输出结果：result = 4
```


### writeFloatLE

ArkTS-Dyn：writeFloatLE(value: number, offset?: number): number

ArkTS-Sta：writeFloatLE(value: double, offset?: int): int

在Buffer对象的offset偏移处写入小端序的32位浮点型数据。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：number <br> ArkTS-Sta：double | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 4。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeFloatLE(0xcafebabe, 0);
console.info("result = " + result);
// 输出结果：result = 4
```

### writeInt8

ArkTS-Dyn：writeInt8(value: number, offset?: number): number

ArkTS-Sta：writeInt8(value: long, offset?: int): int

在Buffer对象的offset偏移处写入8位有符号整型数据。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：number <br> ArkTS-Sta：long | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 1。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(2);
let result = buf.writeInt8(2, 0);
console.info("result = " + result);
// 输出结果：result = 1
let result1 = buf.writeInt8(-2, 1);
console.info("result1 = " + result1);
// 输出结果：result1 = 2
```


### writeInt16BE

ArkTS-Dyn：writeInt16BE(value: number, offset?: number): number

ArkTS-Sta：writeInt16BE(value: long, offset?: int): int

在Buffer对象的offset偏移处写入大端序的16位有符号整型数据。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：number <br> ArkTS-Sta：long | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 2。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(2);
let result = buf.writeInt16BE(0x0102, 0);
console.info("result = " + result);
// 输出结果：result = 2
```


### writeInt16LE

ArkTS-Dyn：writeInt16LE(value: number, offset?: number): number

ArkTS-Sta：writeInt16LE(value: long, offset?: int): int

在Buffer对象的offset偏移处写入小端序的16位有符号整型数据。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：number <br> ArkTS-Sta：long | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 2。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(2);
let result = buf.writeInt16LE(0x0304, 0);
console.info("result = " + result);
// 输出结果：result = 2
```

### writeInt32BE

ArkTS-Dyn：writeInt32BE(value: number, offset?: number): number

ArkTS-Sta：writeInt32BE(value: long, offset?: int): int

在Buffer对象的offset偏移处写入大端序的32位有符号整型数据。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：number <br> ArkTS-Sta：long | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 4。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
let result = buf.writeInt32BE(0x01020304, 0);
console.info("result = " + result);
// 输出结果：result = 4
```


### writeInt32LE

ArkTS-Dyn：writeInt32LE(value: number, offset?: number): number

ArkTS-Sta：writeInt32LE(value: long, offset?: int): int

在Buffer对象的offset偏移处写入小端序的32位有符号整型数据。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：number <br> ArkTS-Sta：long | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 4。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
let result = buf.writeInt32LE(0x05060708, 0);
console.info("result = " + result);
// 输出结果：result = 4
```

### writeIntBE

ArkTS-Dyn：writeIntBE(value: number, offset: number, byteLength: number): number

ArkTS-Sta：writeIntBE(value: long, offset: int, byteLength: int): int

在Buffer对象的offset偏移处写入大端序的有符号数据，字节长度为byteLength。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：number <br> ArkTS-Sta：long | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 偏移量。取值范围：0 <= offset <= Buffer.length - byteLength。 |
| byteLength | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 要写入的字节数。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(6);
let result = buf.writeIntBE(0x1234567890ab, 0, 6);
console.info("result = " + result);
// 输出结果：result = 6
```


### writeIntLE

ArkTS-Dyn：writeIntLE(value: number, offset: number, byteLength: number): number

ArkTS-Sta：writeIntLE(value: long, offset: int, byteLength: int): int

在Buffer对象的offset偏移处写入小端序的有符号数据，字节长度为byteLength。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：number <br> ArkTS-Sta：long | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 偏移量。取值范围：0 <= offset <= Buffer.length - byteLength。 |
| byteLength | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 要写入的字节数。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(6);
let result = buf.writeIntLE(0x1234567890ab, 0, 6);
console.info("result = " + result);
// 输出结果：result = 6
```

### writeUInt8

ArkTS-Dyn：writeUInt8(value: number, offset?: number): number

ArkTS-Sta：writeUInt8(value: long, offset?: int): int

在Buffer对象的offset偏移处写入8位无符号整型数据。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：number <br> ArkTS-Sta：long | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 1。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
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

### writeUInt16BE

ArkTS-Dyn：writeUInt16BE(value: number, offset?: number): number

ArkTS-Sta：writeUInt16BE(value: long, offset?: int): int

在Buffer对象的offset偏移处写入大端序的16位无符号整型数据。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：number <br> ArkTS-Sta：long | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值为0。取值范围：0 <= offset <= Buffer.length - 2。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
let result = buf.writeUInt16BE(0xdead, 0);
console.info("result = " + result);
// 输出结果：result = 2
let result1 = buf.writeUInt16BE(0xbeef, 2);
console.info("result1 = " + result1);
// 输出结果：result1 = 4
```

### writeUInt16LE

ArkTS-Dyn：writeUInt16LE(value: number, offset?: number): number

ArkTS-Sta：writeUInt16LE(value: long, offset?: int): int

在Buffer对象的offset偏移处写入小端序的16位无符号整型数据。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：number <br> ArkTS-Sta：long | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 2。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
let result = buf.writeUInt16LE(0xdead, 0);
console.info("result = " + result);
// 输出结果：result = 2
let result1 = buf.writeUInt16LE(0xbeef, 2);
console.info("result1 = " + result1);
// 输出结果：result1 = 4
```

### writeUInt32BE

ArkTS-Dyn：writeUInt32BE(value: number, offset?: number): number

ArkTS-Sta：writeUInt32BE(value: long, offset?: int): int

在Buffer对象的offset偏移处写入大端序的32位无符号整型数据。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：number <br> ArkTS-Sta：long | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 4。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
let result = buf.writeUInt32BE(0xfeedface, 0);
console.info("result = " + result);
// 输出结果：result = 4
```

### writeUInt32LE

ArkTS-Dyn：writeUInt32LE(value: number, offset?: number): number

ArkTS-Sta：writeUInt32LE(value: long, offset?: int): int

在Buffer对象的offset偏移处写入小端序的32位无符号整型数据。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：number <br> ArkTS-Sta：long | 是 | 写入Buffer对象的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 偏移量。默认值：0。取值范围：0 <= offset <= Buffer.length - 4。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
let result = buf.writeUInt32LE(0xfeedface, 0);
console.info("result = " + result);
// 输出结果：result = 4
```

### writeUIntBE

ArkTS-Dyn：writeUIntBE(value: number, offset: number, byteLength: number): number

ArkTS-Sta：writeUIntBE(value: long, offset: int, byteLength: int): int

在Buffer对象的offset偏移处写入大端序的无符号数据，字节长度为byteLength。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：number <br> ArkTS-Sta：long | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 偏移量。取值范围：0 <= offset <= Buffer.length - byteLength。 |
| byteLength | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 要写入的字节数。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(6);
let result = buf.writeUIntBE(0x1234567890ab, 0, 6);
console.info("result = " + result);
// 输出结果：result = 6
```

### writeUIntLE

ArkTS-Dyn：writeUIntLE(value: number, offset: number, byteLength: number): number

ArkTS-Sta：writeUIntLE(value: long, offset: int, byteLength: int): int

在Buffer对象的offset偏移处写入小端序的无符号数据，字节长度为byteLength。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | ArkTS-Dyn：number <br> ArkTS-Sta：long | 是 | 写入Buffer的数据。 |
| offset | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 偏移量。取值范围：0 <= offset <= Buffer.length - byteLength。 |
| byteLength | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 要写入的字节数。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn：number <br> ArkTS-Sta：int | 偏移量offset加上写入的字节数。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

ArkTS-Sta错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(6);
let result = buf.writeUIntLE(0x1234567890ab, 0, 6);
console.info("result = " + result);
// 输出结果：result = 6
```

### \[index\]<sup>20+</sup>

\[index: int\]: long

将数据设置在指定索引处或返回指定索引处的数据。

**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| index | int | 是 | 要写入的字节索引。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| long | 返回指定索引处的数据。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of index is out of range. |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let buf = buffer.alloc(4);
buf[1] = 100;
buf[3] = 255 ;
let result1 = buf[1];
console.info("result1 = " + result1);
// 输出结果：result1 = 100

let result2 = buf[3];
console.info("result2 = " + result2);
// 输出结果：result2 = 255
```

## Blob

### 属性

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| size | ArkTS-Dyn：number <br> ArkTS-Sta：int | 是 | 否 | Blob实例的总字节大小。 |
| type | string | 是 | 否 | Blob实例的内容类型。 |

### constructor

constructor(sources: string[] | ArrayBuffer[] | TypedArray[] | DataView[] | Blob[] , options?: Object)

Blob的构造函数。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| sources | string[]&nbsp;\|&nbsp;ArrayBuffer[]&nbsp;\|&nbsp;TypedArray[]&nbsp;\|&nbsp;DataView[]&nbsp;\|&nbsp;Blob[] | 是 | Blob实例的数据源。 |
| options | Object | 否 | options:<br/>- endings：含义为结束符'\n'的字符串如何被输出，为'transparent'或'native'。native代表行结束符会跟随系统。'transparent'代表会保持Blob中保存的结束符不变。此参数非必填，默认值为'transparent'。<br/>- type：Blob内容类型。其目的是让类型传达数据的MIME媒体类型，但是不执行类型格式的验证。此参数非必填，默认参数为''。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**
```ts
import { buffer } from '@kit.ArkTS';

let blob: buffer.Blob  = new buffer.Blob(['a', 'b', 'c']);

class option {
  endings: string = "";
  type: string = "";
}
let o1: option = {endings:'native', type: 'MIME'}
let blob1: buffer.Blob = new buffer.Blob(['a', 'b', 'c'], o1);
```

### constructor<sup>20+</sup>

constructor(sources: ArrayUnionType, options?: BlobOptions)

Blob的构造函数。

**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| sources | [ArrayUnionType](#arrayuniontype20) | 是 | Blob实例的数据源。 |
| options | [BlobOptions](#bloboptions20) | 否 | options:<br/>- endings：含义为结束符'\n'的字符串如何被输出，为'transparent'或'native'。native代表行结束符会跟随系统。'transparent'代表会保持Blob中保存的结束符不变。此参数非必填，默认值为'transparent'。<br/>- type：Blob内容类型。其目的是让类型传达数据的MIME媒体类型，但是不执行类型格式的验证。此参数非必填，默认参数为''。 |

**示例：**

```ts
import { buffer } from '@kit.ArkTS';

let blob: buffer.Blob  = new buffer.Blob(['a', 'b', 'c']);

let blob1: buffer.Blob = new buffer.Blob(['a', 'b', 'c'], {endings:'native', type: 'MIME'} as buffer.BlobOptions);
```

### arrayBuffer

arrayBuffer(): Promise&lt;ArrayBuffer&gt;

将Blob数据放入ArrayBuffer中，并返回一个Promise。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;ArrayBuffer&gt; | Promise对象，返回包含Blob数据的ArrayBuffer。 |

**示例：**
```ts
import { buffer } from '@kit.ArkTS';

let blob: buffer.Blob = new buffer.Blob(['a', 'b', 'c']);
let pro = blob.arrayBuffer();
pro.then((val: ArrayBuffer) => {
  let uint8Array: Uint8Array = new Uint8Array(val);
  console.info(uint8Array.toString());
  // 输出结果：97,98,99
});
```
### slice

ArkTS-Dyn：slice(start?: number, end?: number, type?: string): Blob

ArkTS-Sta：slice(start?: int, end?: int, type?: string): Blob

创建并返回一个包含原Blob对象中指定长度数据的新Blob对象。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| start | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 起始位置。默认值为0。 |
| end | ArkTS-Dyn：number <br> ArkTS-Sta：int | 否 | 结束位置。默认值为原Blob对象中的数据长度。 |
| type | string | 否 | 内容类型。默认值为''。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Blob | 新的Blob实例对象。 |

**示例：**
```ts
import { buffer } from '@kit.ArkTS';

let blob: buffer.Blob = new buffer.Blob(['a', 'b', 'c']);
let blob2 = blob.slice(0, 2);
let blob3 = blob.slice(0, 2, "MIME");
console.info("type:", blob3.type); // type: MIME
```

### text

text(): Promise&lt;string&gt;

使用UTF8解码并返回文本。使用Promise进行异步回调。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;string&gt; | Promise对象，返回包含以UTF8解码的文本。 |

**示例：**
```ts
import { buffer } from '@kit.ArkTS';

let blob: buffer.Blob = new buffer.Blob(['a', 'b', 'c']);
let pro = blob.text();
pro.then((val: string) => {
  console.info(val);
  // 输出结果：abc
});
```