# Policy

定义敏感内容识别策略。单个策略内，关键字与正则表达式为顺序组合关系，实行两级匹配：首先进行关键字匹配，若命中，则仅在该关键字匹配位置的前后50字节窗口内，进行正则表达式匹配。多个Policy策略之间独立，扫描时会分别应用每个策略。sensitiveLabel用于标记匹配结果，便于识别具体匹配的策略。

**起始版本：** 21

<!--Device-identifySensitiveContent-export interface Policy--><!--Device-identifySensitiveContent-export interface Policy-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## 导入模块

```TypeScript
import { identifySensitiveContent } from '@kit.DataProtectionKit';
```

## keywords

```TypeScript
keywords: Array<string>
```

表示关键字集合，用于匹配文件中的敏感关键字。系统会在文件内容中搜索这些关键字，匹配时区分大小写，匹配成功则返回识别结果。Array最大50，每个元素最大30字节。

**类型：** Array<string>

**起始版本：** 21

<!--Device-Policy-keywords: Array<string>--><!--Device-Policy-keywords: Array<string>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## regex

```TypeScript
regex: string
```

表示匹配敏感内容的正则表达式。系统将在文件内容中按此正则表达式进行模式匹配，匹配成功的内容将返回在结果中。长度范围0-512字节。在输入字符串时，需检查某些特殊字符（如反斜杠 \、双引号 "、换行符等），不会被自动转义，确保字符串的输入效果。

**类型：** string

**起始版本：** 21

<!--Device-Policy-regex: string--><!--Device-Policy-regex: string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## sensitiveLabel

```TypeScript
sensitiveLabel: string
```

表示识别策略的标签，用于标识和分类匹配结果。长度范围1-30字节。

**类型：** string

**起始版本：** 21

<!--Device-Policy-sensitiveLabel: string--><!--Device-Policy-sensitiveLabel: string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

