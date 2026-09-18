# Policy

Defines the policy for sensitive content identification. In a single policy, keywords and regular expressions are combined in sequence, and two-level matching is performed. First, keyword matching is performed. If a keyword is matched, regular expression matching is performed within a scope of 100 bytes: from the position 50 bytes before the matched position of the keyword to that 50 bytes after the matched position. If only keywords are set, only keyword matching is performed. If only regular expressions are set, only regular expression matching is performed. Multiple policies are independent of each other, and each policy is applied separately during scanning. sensitiveLabel is used to mark the matching result to identify the specific policy matched.

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## Modules to Import

```TypeScript
import { identifySensitiveContent } from '@kit.DataProtectionKit';
```

## keywords

```TypeScript
keywords: Array<string>
```

Keyword set, which is used to match sensitive keywords in a file. The system searches for these keywords in the file content and returns the identification result if a keyword is matched. The keywords are case-sensitive. The array can contain a maximum of 50 elements, and each element can contain a maximum of 30 bytes.

**Type:** Array&lt;string&gt;

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## regex

```TypeScript
regex: string
```

Regular expression used to match sensitive content. The system performs pattern matching on the file content based on the regular expression. The matched content is returned. The value contains 0 to 512 characters. When entering a string, check whether some special characters (such as backslash (), double quotation marks ("), and newline characters) are automatically escaped to ensure the input effect of the string.

**Type:** string

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## sensitiveLabel

```TypeScript
sensitiveLabel: string
```

Label of an identification policy, which is used to identify and classify matching results. The value is a string of 1 to 30 bytes.

**Type:** string

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention
