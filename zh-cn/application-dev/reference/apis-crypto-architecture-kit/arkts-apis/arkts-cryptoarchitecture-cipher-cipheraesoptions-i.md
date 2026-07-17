# CipherAesOptions

调用cipher aes方法时，传入的参数。

**起始版本：** 3

**废弃版本：** 11

**替代接口：** Cipher

<!--Device-unnamed-export interface CipherAesOptions--><!--Device-unnamed-export interface CipherAesOptions-End-->

**系统能力：** SystemCapability.Security.Cipher

## 导入模块

```TypeScript
import { CipherAesOptions, CipherResponse, CipherRsaOptions } from '@kit.CryptoArchitectureKit';
```

## action

```TypeScript
action: string
```

加解密操作类型，可选项有：

1. encrypt 加密；2. decrypt 解密。

**类型：** string

**起始版本：** 3

**废弃版本：** 11

**替代接口：** Cipher

<!--Device-CipherAesOptions-action: string--><!--Device-CipherAesOptions-action: string-End-->

**系统能力：** SystemCapability.Security.Cipher

## complete

```TypeScript
complete: () => void
```

接口调用结束的回调函数。

**类型：** () => void

**起始版本：** 3

**废弃版本：** 11

**替代接口：** Cipher

<!--Device-CipherAesOptions-complete: () => void--><!--Device-CipherAesOptions-complete: () => void-End-->

**系统能力：** SystemCapability.Security.Cipher

## fail

```TypeScript
fail: (data: string, code: number) => void
```

接口调用失败的回调函数。

**类型：** (data: string, code: number) => void

**起始版本：** 3

**废弃版本：** 11

**替代接口：** Cipher

<!--Device-CipherAesOptions-fail: (data: string, code: number) => void--><!--Device-CipherAesOptions-fail: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.Security.Cipher

## iv

```TypeScript
iv?: string
```

AES加解密的初始向量，经过base64编码后的字符串，默认值为key值。

**类型：** string

**起始版本：** 3

**废弃版本：** 11

**替代接口：** Cipher

<!--Device-CipherAesOptions-iv?: string--><!--Device-CipherAesOptions-iv?: string-End-->

**系统能力：** SystemCapability.Security.Cipher

## ivLen

```TypeScript
ivLen?: string
```

AES加解密的初始向量字节长度，当前为预留字段，默认值16，仅支持16。

**类型：** string

**起始版本：** 3

**废弃版本：** 11

**替代接口：** Cipher

<!--Device-CipherAesOptions-ivLen?: string--><!--Device-CipherAesOptions-ivLen?: string-End-->

**系统能力：** SystemCapability.Security.Cipher

## ivOffset

```TypeScript
ivOffset?: string
```

AES加解密的初始向量偏移，默认值0，仅支持0。

**类型：** string

**起始版本：** 3

**废弃版本：** 11

**替代接口：** Cipher

<!--Device-CipherAesOptions-ivOffset?: string--><!--Device-CipherAesOptions-ivOffset?: string-End-->

**系统能力：** SystemCapability.Security.Cipher

## key

```TypeScript
key: string
```

加密或解密使用到的密钥，经过 base64 编码后生成的字符串。

**类型：** string

**起始版本：** 3

**废弃版本：** 11

**替代接口：** Cipher

<!--Device-CipherAesOptions-key: string--><!--Device-CipherAesOptions-key: string-End-->

**系统能力：** SystemCapability.Security.Cipher

## success

```TypeScript
success: (data: CipherResponse) => void
```

接口调用成功的回调函数。

**类型：** (data: CipherResponse) => void

**起始版本：** 3

**废弃版本：** 11

**替代接口：** Cipher

<!--Device-CipherAesOptions-success: (data: CipherResponse) => void--><!--Device-CipherAesOptions-success: (data: CipherResponse) => void-End-->

**系统能力：** SystemCapability.Security.Cipher

## text

```TypeScript
text: string
```

待加密或解密的文本内容。待加密的文本内容应该是一段普通文本。待解密的文本内容应该是经过 base64 编码的一段二进制值。base64 编码使用默认风格。

**类型：** string

**起始版本：** 3

**废弃版本：** 11

**替代接口：** Cipher

<!--Device-CipherAesOptions-text: string--><!--Device-CipherAesOptions-text: string-End-->

**系统能力：** SystemCapability.Security.Cipher

## transformation

```TypeScript
transformation?: string
```

AES算法的加密模式和填充项，默认AES/CBC/PKCS5Padding。

**类型：** string

**起始版本：** 3

**废弃版本：** 11

**替代接口：** Cipher

<!--Device-CipherAesOptions-transformation?: string--><!--Device-CipherAesOptions-transformation?: string-End-->

**系统能力：** SystemCapability.Security.Cipher

