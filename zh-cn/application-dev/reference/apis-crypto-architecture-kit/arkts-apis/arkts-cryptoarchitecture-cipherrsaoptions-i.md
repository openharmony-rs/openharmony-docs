# CipherRsaOptions

调用cipher rsa方法时，传入的参数。

**起始版本：** 3

**废弃版本：** 11

**替代接口：** Cipher

**系统能力：** SystemCapability.Security.Cipher

## action

```TypeScript
action: string
```

加解密操作类型，可选项有：

1. encrypt 加密；
2. decrypt 解密。

**类型：** string

**起始版本：** 3

**废弃版本：** 11

**替代接口：** Cipher

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

**系统能力：** SystemCapability.Security.Cipher

## key

```TypeScript
key: string
```

加解密使用的RSA密钥。加密时key为公钥，解密时key为私钥。

**类型：** string

**起始版本：** 3

**废弃版本：** 11

**替代接口：** Cipher

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

**系统能力：** SystemCapability.Security.Cipher

## text

```TypeScript
text: string
```

待加密或解密的文本内容。待加密的文本内容应该是一段普通文本，长度不能超过keySize / 8 - 66，其中keySize是密钥的长度
（例如密钥长度为1024时，text不能超过62个字节）。待解密的文本内容应该是经过base64编码的一段二进制值。base64编码使用
默认风格。

**类型：** string

**起始版本：** 3

**废弃版本：** 11

**替代接口：** Cipher

**系统能力：** SystemCapability.Security.Cipher

## transformation

```TypeScript
transformation?: string
```

RSA算法的填充项，默认为RSA/None/OAEPWithSHA256AndMGF1Padding。

**类型：** string

**起始版本：** 3

**废弃版本：** 11

**替代接口：** Cipher

**系统能力：** SystemCapability.Security.Cipher

