# StringDecoder

提供将二进制流解码为字符串的能力。支持以下编码类型：utf-8、iso-8859-2、koi8-r、macintosh、windows-1250、windows-1251、gbk、gb18030、big5、utf-16be 和 UTF-16le。

**起始版本：** 12

<!--Device-util-class StringDecoder--><!--Device-util-class StringDecoder-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor(encoding?: string)
```

用于创建 **StringDecoder** 实例的构造函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-StringDecoder-constructor(encoding?: string)--><!--Device-StringDecoder-constructor(encoding?: string)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 否 | 输入数据的编码类型。默认值为 **utf-8**。 |

**示例：**

```TypeScript
let decoder = new util.StringDecoder();

```

<a id="end"></a>
## end

```TypeScript
end(chunk?: string | Uint8Array): string
```

结束解码过程，并将内部缓存中存储的任何剩余输入作为字符串返回。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-StringDecoder-end(chunk?: string | Uint8Array): string--><!--Device-StringDecoder-end(chunk?: string | Uint8Array): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chunk | string \| Uint8Array | 否 | 要解码的字符串。默认值为 **undefined**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 解码后的字符串。 |

**示例：**

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

<a id="write"></a>
## write

```TypeScript
write(chunk: string | Uint8Array): string
```

解码字符串。Uint8Array 末尾的任何不完整多字节字符都会从返回的字符串中过滤掉，并存储在内部缓存中以供下次调用使用。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-StringDecoder-write(chunk: string | Uint8Array): string--><!--Device-StringDecoder-write(chunk: string | Uint8Array): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chunk | string \| Uint8Array | 是 | 要解码的字符串。基于输入的编码类型进行解码。如果输入为 Uint8Array 类型，则正常解码。如果输入为字符串类型，则直接返回该参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 解码后的字符串。 |

**示例：**

```TypeScript
let decoder = new util.StringDecoder('utf-8');
let input =  new Uint8Array([0xE4, 0xBD, 0xA0, 0xE5, 0xA5, 0xBD]);
const decoded = decoder.write(input);
console.info("decoded:", decoded);
// 输出结果：decoded: 你好

```

