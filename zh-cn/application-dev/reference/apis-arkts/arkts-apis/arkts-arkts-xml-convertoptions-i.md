# ConvertOptions

转换选项，用于自定义XML到JavaScript对象的转换行为，如控制是否修剪空白字符、是否忽略特定组件（声明、指令、属性、注释、CDATA、Doctype和文本等）， 以及指定输出对象中各类型组件的属性键名称。 > **说明：** > > 各键属性（declarationKey、instructionKey等）的取值应唯一，不可与其他键属性值重复，否则输出对象可能出现键名冲突。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

<!--Device-xml-interface ConvertOptions--><!--Device-xml-interface ConvertOptions-End-->

**系统能力：** SystemCapability.Utils.Lang

## attributesKey

```TypeScript
attributesKey: string
```

用于输出对象中attributes的属性键的名称，仅在ignoreAttributes为false时生效。

**类型：** string

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertOptions-attributesKey: string--><!--Device-ConvertOptions-attributesKey: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## cdataKey

```TypeScript
cdataKey: string
```

用于输出对象中cdata的属性键的名称，仅在ignoreCDATA为false时生效。

**类型：** string

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertOptions-cdataKey: string--><!--Device-ConvertOptions-cdataKey: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## commentKey

```TypeScript
commentKey: string
```

用于输出对象中comment的属性键的名称，仅在ignoreComment为false时生效。

**类型：** string

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertOptions-commentKey: string--><!--Device-ConvertOptions-commentKey: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## declarationKey

```TypeScript
declarationKey: string
```

用于输出对象中declaration的属性键的名称，仅在ignoreDeclaration为false时生效。

**类型：** string

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertOptions-declarationKey: string--><!--Device-ConvertOptions-declarationKey: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## doctypeKey

```TypeScript
doctypeKey: string
```

用于输出对象中doctype的属性键的名称，仅在ignoreDoctype为false时生效。

**类型：** string

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertOptions-doctypeKey: string--><!--Device-ConvertOptions-doctypeKey: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## elementsKey

```TypeScript
elementsKey: string
```

用于输出对象中elements的属性键的名称。

**类型：** string

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertOptions-elementsKey: string--><!--Device-ConvertOptions-elementsKey: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## ignoreAttributes

```TypeScript
ignoreAttributes?: boolean
```

是否忽略元素的属性信息，true表示忽略元素的属性信息，false表示保留元素的属性信息，默认false。

**类型：** boolean

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertOptions-ignoreAttributes?: boolean--><!--Device-ConvertOptions-ignoreAttributes?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## ignoreCDATA

```TypeScript
ignoreCDATA?: boolean
```

是否忽略元素的CDATA（Character Data）信息，true表示忽略元素的CDATA信息，false表示保留元素的CDATA信息，默认false。

**类型：** boolean

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertOptions-ignoreCDATA?: boolean--><!--Device-ConvertOptions-ignoreCDATA?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## ignoreComment

```TypeScript
ignoreComment?: boolean
```

是否忽略元素的注释信息，true表示忽略元素的注释信息，false表示保留元素的注释信息，默认false。

**类型：** boolean

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertOptions-ignoreComment?: boolean--><!--Device-ConvertOptions-ignoreComment?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## ignoreDeclaration

```TypeScript
ignoreDeclaration?: boolean
```

是否忽略XML声明，true表示忽略XML声明，false表示保留XML声明，默认false。

**类型：** boolean

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertOptions-ignoreDeclaration?: boolean--><!--Device-ConvertOptions-ignoreDeclaration?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## ignoreDoctype

```TypeScript
ignoreDoctype?: boolean
```

是否忽略Doctype（Document Type Declaration）信息，true表示忽略元素的Doctype信息，false表示保留元素的Doctype信息，默认false。

**类型：** boolean

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertOptions-ignoreDoctype?: boolean--><!--Device-ConvertOptions-ignoreDoctype?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## ignoreInstruction

```TypeScript
ignoreInstruction?: boolean
```

是否忽略XML处理指令，true表示忽略XML处理指令，false表示保留XML处理指令，默认false。

**类型：** boolean

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertOptions-ignoreInstruction?: boolean--><!--Device-ConvertOptions-ignoreInstruction?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## ignoreText

```TypeScript
ignoreText?: boolean
```

是否忽略元素的文本信息，true表示忽略元素的文本信息，false表示保留元素的文本信息，默认false。

**类型：** boolean

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertOptions-ignoreText?: boolean--><!--Device-ConvertOptions-ignoreText?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## instructionKey

```TypeScript
instructionKey: string
```

用于输出对象中instruction的属性键的名称，仅在ignoreInstruction为false时生效。

**类型：** string

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertOptions-instructionKey: string--><!--Device-ConvertOptions-instructionKey: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## nameKey

```TypeScript
nameKey: string
```

用于输出对象中name的属性键的名称。

**类型：** string

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertOptions-nameKey: string--><!--Device-ConvertOptions-nameKey: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## parentKey

```TypeScript
parentKey: string
```

用于输出对象中parent的属性键的名称，parent表示当前元素所属的父元素名称。

**类型：** string

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertOptions-parentKey: string--><!--Device-ConvertOptions-parentKey: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## textKey

```TypeScript
textKey: string
```

用于输出对象中text的属性键的名称，仅在ignoreText为false时生效。

**类型：** string

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertOptions-textKey: string--><!--Device-ConvertOptions-textKey: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## trim

```TypeScript
trim: boolean
```

是否修剪位于文本内容前后的空白字符，true表示元素内文本内容前后的空白字符将会被修剪，false则表示空白字符会被保留，默认false。

**类型：** boolean

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertOptions-trim: boolean--><!--Device-ConvertOptions-trim: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## typeKey

```TypeScript
typeKey: string
```

用于输出对象中type的属性键的名称，type标识XML组件的类型（如element、text、cdata、comment、instruction等）。

**类型：** string

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConvertOptions-typeKey: string--><!--Device-ConvertOptions-typeKey: string-End-->

**系统能力：** SystemCapability.Utils.Lang

