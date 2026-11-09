# StringDecoder

```TypeScript
class StringDecoder
```

提供将二进制流解码为字符串的能力。支持以下编码类型：utf-8、iso-8859-2、koi8-r、macintosh、windows-1250、windows-1251、gbk、gb18030、big5、utf-16be 和 UTF-16le。

**起始版本：** 12

<!--Device-util-class StringDecoder--><!--Device-util-class StringDecoder-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor(encoding?: string)
```

StringDecoder的构造函数，创建一个默认编码为'utf-8'的StringDecoder实例。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-StringDecoder-constructor(encoding?: string)--><!--Device-StringDecoder-constructor(encoding?: string)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 否 | 输入数据的编码类型。默认值：'utf-8'。 |

**示例**

```TypeScript
let decoder = new util.StringDecoder();
```

## end

```TypeScript
end(chunk?: string | Uint8Array): string
```

结束解码过程，以字符串形式返回存储在内部缓冲区中的所有剩余输入。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-StringDecoder-end(chunk?: string | Uint8Array): string--><!--Device-StringDecoder-end(chunk?: string | Uint8Array): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chunk | string &#124; Uint8Array | 否 | 需要解码的最后一部分数据，默认为undefined。当还有剩余数据需要在结束解码时一并处理时传入此参数；不传入时默认为undefined，即仅返回内部缓冲区中存储的不完整字节序列的解码结果，不再处理新数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回存储在内部缓冲区中的所有剩余解码内容组成的字符串。 |

**示例**

```TypeScript
let decoder = new util.StringDecoder('utf-8');
let input = new Uint8Array([0xE4, 0xBD, 0xA0, 0xE5, 0xA5, 0xBD]);
const writeString = decoder.write(input.slice(0, 5));
const endString = decoder.end(input.slice(5));
console.info("writeString:", writeString);
// 输出结果：writeString: 你
console.info("endString:", endString);
// 输出结果：endString: 好
```

## write

```TypeScript
write(chunk: string | Uint8Array): string
```

返回一个解码后的字符串，确保Uint8Array末尾的任何不完整的多字节字符从返回的字符串中被过滤，并保存在一个内部的buffer中用于下次调用。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-StringDecoder-write(chunk: string | Uint8Array): string--><!--Device-StringDecoder-write(chunk: string | Uint8Array): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chunk | string &#124; Uint8Array | 是 | 需要解码的字符串。会根据输入的编码类型进行解码，参数为Uint8Array时正常解码，参数为string时会将参数直接返回。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回解码后的字符串，不完整的多字节字符已从返回值中过滤，并保存在内部缓冲区中供下次调用处理。 |

**示例**

```TypeScript
let decoder = new util.StringDecoder('utf-8');
let input =  new Uint8Array([0xE4, 0xBD, 0xA0, 0xE5, 0xA5, 0xBD]);
const decoded = decoder.write(input);
console.info("decoded:", decoded);
// 输出结果：decoded: 你好
```
