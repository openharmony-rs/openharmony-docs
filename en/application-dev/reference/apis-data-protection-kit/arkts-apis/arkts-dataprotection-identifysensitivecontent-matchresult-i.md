# MatchResult

Displays the identification result of sensitive content.

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## Modules to Import

```TypeScript
import { identifySensitiveContent } from '@kit.DataProtectionKit';
```

## matchContent

```TypeScript
readonly matchContent: string
```

Matched sensitive content segment, that is, the text content matched by keyword or regular expression.

**Type:** string

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## matchNumber

```TypeScript
readonly matchNumber: number
```

Total number of matched items.

**Type:** number

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## sensitiveLabel

```TypeScript
readonly sensitiveLabel: string
```

Label of an identification policy, which corresponds to sensitiveLabel in the input policy and is used to label the policy used to identify the matching result.

**Type:** string

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention
