# MatchResult

表示敏感内容的识别结果。

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

## matchContent

```TypeScript
readonly matchContent: string
```

表示匹配到的敏感内容片段，即文件中实际匹配到关键字或正则表达式的文本内容。

**类型：** string

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

## matchNumber

```TypeScript
readonly matchNumber: number
```

表示匹配内容的总数。

**类型：** number

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

## sensitiveLabel

```TypeScript
readonly sensitiveLabel: string
```

表示识别策略的标签，与输入策略中的sensitiveLabel对应，用于标识匹配结果对应的识别策略。

**类型：** string

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

