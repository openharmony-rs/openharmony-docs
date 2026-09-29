# ConvertOptions

```TypeScript
interface ConvertOptions
```

Options for conversion.

**Since:** 8

<!--Device-xml-interface ConvertOptions--><!--Device-xml-interface ConvertOptions-End-->

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { convertxml } from '@kit.ArkTS';
```

## attributesKey

```TypeScript
attributesKey: string
```

Name of the attribute key for **attributes** in the output object.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConvertOptions-attributesKey: string--><!--Device-ConvertOptions-attributesKey: string-End-->

**System capability:** SystemCapability.Utils.Lang

## cdataKey

```TypeScript
cdataKey: string
```

Name of the attribute key for **cdata** in the output object.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConvertOptions-cdataKey: string--><!--Device-ConvertOptions-cdataKey: string-End-->

**System capability:** SystemCapability.Utils.Lang

## commentKey

```TypeScript
commentKey: string
```

Name of the attribute key for **comment** in the output object.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConvertOptions-commentKey: string--><!--Device-ConvertOptions-commentKey: string-End-->

**System capability:** SystemCapability.Utils.Lang

## declarationKey

```TypeScript
declarationKey: string
```

Name of the attribute key for **declaration** in the output object.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConvertOptions-declarationKey: string--><!--Device-ConvertOptions-declarationKey: string-End-->

**System capability:** SystemCapability.Utils.Lang

## doctypeKey

```TypeScript
doctypeKey: string
```

Name of the attribute key for **doctype** in the output object.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConvertOptions-doctypeKey: string--><!--Device-ConvertOptions-doctypeKey: string-End-->

**System capability:** SystemCapability.Utils.Lang

## elementsKey

```TypeScript
elementsKey: string
```

Name of the attribute key for **elements** in the output object.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConvertOptions-elementsKey: string--><!--Device-ConvertOptions-elementsKey: string-End-->

**System capability:** SystemCapability.Utils.Lang

## ignoreAttributes

```TypeScript
ignoreAttributes?: boolean
```

Whether to ignore the element's attribute information. The value **true** means to ignore the element's attribute information, and **false** means the opposite. The default value is **false**.

**Type:** boolean

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConvertOptions-ignoreAttributes?: boolean--><!--Device-ConvertOptions-ignoreAttributes?: boolean-End-->

**System capability:** SystemCapability.Utils.Lang

## ignoreCDATA

```TypeScript
ignoreCDATA?: boolean
```

Whether to ignore the element's CDATA information. The value **true** means to ignore the element's CDATA information, and **false** means the opposite. The default value is **false**.

**Type:** boolean

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConvertOptions-ignoreCDATA?: boolean--><!--Device-ConvertOptions-ignoreCDATA?: boolean-End-->

**System capability:** SystemCapability.Utils.Lang

## ignoreComment

```TypeScript
ignoreComment?: boolean
```

Whether to ignore element comments. The value **true** means to ignore element comments, and **false** means the opposite. The default value is **false**.

**Type:** boolean

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConvertOptions-ignoreComment?: boolean--><!--Device-ConvertOptions-ignoreComment?: boolean-End-->

**System capability:** SystemCapability.Utils.Lang

## ignoreDeclaration

```TypeScript
ignoreDeclaration?: boolean
```

Whether to ignore the XML declaration. The value **true** means to ignore the XML declaration, and **false** means the opposite. The default value is **false**.

**Type:** boolean

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConvertOptions-ignoreDeclaration?: boolean--><!--Device-ConvertOptions-ignoreDeclaration?: boolean-End-->

**System capability:** SystemCapability.Utils.Lang

## ignoreDoctype

```TypeScript
ignoreDoctype?: boolean
```

Whether to ignore the element's Doctype information. The value **true** means to ignore the element's Doctype information, and **false** means the opposite. The default value is **false**.

**Type:** boolean

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConvertOptions-ignoreDoctype?: boolean--><!--Device-ConvertOptions-ignoreDoctype?: boolean-End-->

**System capability:** SystemCapability.Utils.Lang

## ignoreInstruction

```TypeScript
ignoreInstruction?: boolean
```

Whether to ignore the XML processing instruction. The value **true** means to ignore the XML processing instruction, and **false** means the opposite. The default value is **false**.

**Type:** boolean

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConvertOptions-ignoreInstruction?: boolean--><!--Device-ConvertOptions-ignoreInstruction?: boolean-End-->

**System capability:** SystemCapability.Utils.Lang

## ignoreText

```TypeScript
ignoreText?: boolean
```

Whether to ignore the element's text information. The value **true** means to ignore the element's text information, and **false** means the opposite. The default value is **false**.

**Type:** boolean

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConvertOptions-ignoreText?: boolean--><!--Device-ConvertOptions-ignoreText?: boolean-End-->

**System capability:** SystemCapability.Utils.Lang

## instructionKey

```TypeScript
instructionKey: string
```

Name of the attribute key for **instruction** in the output object.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConvertOptions-instructionKey: string--><!--Device-ConvertOptions-instructionKey: string-End-->

**System capability:** SystemCapability.Utils.Lang

## nameKey

```TypeScript
nameKey: string
```

Name of the attribute key for **name** in the output object.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConvertOptions-nameKey: string--><!--Device-ConvertOptions-nameKey: string-End-->

**System capability:** SystemCapability.Utils.Lang

## parentKey

```TypeScript
parentKey: string
```

Name of the attribute key for **parent** in the output object.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConvertOptions-parentKey: string--><!--Device-ConvertOptions-parentKey: string-End-->

**System capability:** SystemCapability.Utils.Lang

## textKey

```TypeScript
textKey: string
```

Name of the attribute key for **text** in the output object.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConvertOptions-textKey: string--><!--Device-ConvertOptions-textKey: string-End-->

**System capability:** SystemCapability.Utils.Lang

## trim

```TypeScript
trim: boolean
```

Whether to trim the whitespace characters before and after the text. The value **true** means to trim the whitespace characters before and after the text, and **false** means to keep them.

**Type:** boolean

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConvertOptions-trim: boolean--><!--Device-ConvertOptions-trim: boolean-End-->

**System capability:** SystemCapability.Utils.Lang

## typeKey

```TypeScript
typeKey: string
```

Name of the attribute key for **type** in the output object.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConvertOptions-typeKey: string--><!--Device-ConvertOptions-typeKey: string-End-->

**System capability:** SystemCapability.Utils.Lang
