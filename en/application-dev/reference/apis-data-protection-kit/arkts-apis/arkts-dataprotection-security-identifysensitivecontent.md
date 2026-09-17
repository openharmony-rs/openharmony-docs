# @ohos.security.identifySensitiveContent(Identify sensitive file)

This module identifies sensitive information in a specified file based on the input Policy. The system matches the file content against the provided Policy (including sensitive labels, keyword sets, and regular expressions) and returns the matched sensitive content.

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## Modules to Import

```TypeScript
import { identifySensitiveContent } from '@kit.DataProtectionKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [scanFile](arkts-dataprotection-identifysensitivecontent-scanfile-f.md) | Identifies sensitive content in a specified file based on the configured policy and returns the identified result array, including the matched sensitivity labels, matched content, and number of matched items. This API uses a promise to return the result. |

### Interfaces

| Name | Description |
| --- | --- |
| [MatchResult](arkts-dataprotection-identifysensitivecontent-matchresult-i.md) | Displays the identification result of sensitive content. |
| [Policy](arkts-dataprotection-identifysensitivecontent-policy-i.md) | Defines the policy for sensitive content identification. In a single policy, keywords and regular expressions are combined in sequence, and two-level matching is performed. First, keyword matching is performed. If a keyword is matched, regular expression matching is performed within a scope of 100 bytes: from the position 50 bytes before the matched position of the keyword to that 50 bytes after the matched position. If only keywords are set, only keyword matching is performed. If only regular expressions are set, only regular expression matching is performed. Multiple policies are independent of each other, and each policy is applied separately during scanning. sensitiveLabel is used to mark the matching result to identify the specific policy matched. |
