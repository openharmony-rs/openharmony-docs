# HashStream

HashStream 类是用于创建数据的哈希摘要的实用工具。由 [createHash](arkts-corefile-hash-createhash-f.md#createhash-1) 接口获得。

**继承/实现关系：** HashStream extends [stream.Transform](../../apis-arkts/arkts-apis/arkts-arkts-stream-transform-c.md)

**起始版本：** 12

<!--Device-hash-class HashStream extends stream.Transform--><!--Device-hash-class HashStream extends stream.Transform-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { hash } from '@kit.CoreFileKit';
```

## digest

```TypeScript
digest(): string
```

计算传递给哈希处理的所有数据的摘要。

**起始版本：** 12

<!--Device-HashStream-digest(): string--><!--Device-HashStream-digest(): string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回数据的哈希值。该哈希值表示为十六进制数字串，所有字母均大写。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error |
| 13900042 | Unknown error |

**示例：**

```TypeScript
// 创建哈希流
const hs = hash.createHash('sha256');
hs.update(new Uint8Array('1234567890'?.split('').map((x: string) => x.charCodeAt(0))).buffer);
hs.update(new Uint8Array('abcdefg'?.split('').map((x: string) => x.charCodeAt(0))).buffer);
const hashResult = hs.digest();
// 88A00F46836CD629D0B79DE98532AFDE3AEAD79A5C53E4848102F433046D0106
console.info(`Succeeded in calculating file hash. hashResult: ${hashResult}`);

```

## update

```TypeScript
update(data: ArrayBuffer): void
```

使用给定的 data 更新哈希内容，可多次调用。

**起始版本：** 12

<!--Device-HashStream-update(data: ArrayBuffer): void--><!--Device-HashStream-update(data: ArrayBuffer): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | updated data. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error |
| 13900042 | Unknown error |

**示例：**

```TypeScript
// 创建哈希流
const hs = hash.createHash('sha256');
hs.update(new Uint8Array('1234567890'?.split('').map((x: string) => x.charCodeAt(0))).buffer);
hs.update(new Uint8Array('abcdefg'?.split('').map((x: string) => x.charCodeAt(0))).buffer);
const hashResult = hs.digest();
// 88A00F46836CD629D0B79DE98532AFDE3AEAD79A5C53E4848102F433046D0106
console.info(`Succeeded in calculating file hash. hashResult: ${hashResult}`);

```

