# @ohos.security.identifySensitiveContent (Identifying Sensitive Content)
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @Yuan_bys-->
<!--Designer: @zhengdu_628-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

This module identifies sensitive information in a specified file based on the input [Policy](#policy). The system matches the file content against the provided [Policy](#policy) (including sensitive labels, keyword sets, and regular expressions) and returns the matched sensitive content.

> **NOTE**
>
> The initial APIs of this module are supported since API version 21. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { identifySensitiveContent } from '@kit.DataProtectionKit';
```

## identifySensitiveContent.scanFile
scanFile(filePath: string, identifyPolicies:Array&lt;Policy&gt;): Promise&lt;Array&lt;MatchResult&gt;&gt;

Identifies sensitive content in a specified file based on the configured policy and returns the identified result array, including the matched sensitivity labels, matched content, and number of matched items. This API uses a promise to return the result.

**Required permissions:** ohos.permission.ENTERPRISE_DATA_IDENTIFY_FILE

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters**

| Parameter| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| filePath | string | Yes| File path identified. The path must be a physical path. The file to which the path points must exist and can be accessed.|
| identifyPolicies | Array&lt;[Policy](#policy)&gt; | Yes| An array of policies used to identify sensitive content. Each policy defines an identification rule (tags, keywords, and regular expressions). The system scans file content based on these rules and returns the matching result.|

**Return value**
| Type| Description|
| -------- | -------- |
| Promise&lt;Array&lt;[MatchResult](#matchresult)&gt;&gt; | Promise used to return the identification result of sensitive content. If the operation is successful, the matching result array is returned. If the operation fails, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Service Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 201 | permission denied. |
| 801 | Capability not supported. |
| 19110001 | Parameter error.Possible causes:1. Incorrect policy format. 2. Invalid parameter range. |
| 19110002 | Sensitive file content identification timed out. |
| 19110003 | The file is not supported. Possible causes:1. The file path does not exist. 2. The file type is not supported. 3. The file permission is not supported. |
| 19110004 | A system error has occurred. |

**Example**

```ts
// Import the sensitive content identification module.
import { identifySensitiveContent } from '@kit.DataProtectionKit';

// Define the physical file path to be scanned.
let filepath = "/data/app/el1/bundle/public/bundleName/test.txt";

// Configures the policy for sensitive content identification.
let policies: Array<identifySensitiveContent.Policy> = [
  {"sensitiveLabel":"1", "keywords":[], "regex":""}
];
try {
  // Call the scanFile API to identify sensitive content in the file.
  identifySensitiveContent.scanFile(filepath, policies).then(records => {
    // Identification result
    console.info('scanFile finish');
  }).catch((err:Error) => {
    // Failed to identify.
    console.error('error message', err.message);
  })
} catch (err) {
  // Capture exceptions.
  console.error('error message', err.message);
}
```

## Policy

Defines the policy for sensitive content identification.

- In a single policy, keywords and regular expressions are combined in sequence, and two-level matching is performed. First, keyword matching is performed. If a keyword is matched, regular expression matching is performed within a scope of 100 bytes: from the position 50 bytes before the matched position of the keyword to that 50 bytes after the matched position.
- Multiple policies are independent of each other, and each policy is applied separately during scanning.
- **sensitiveLabel** is used to mark the matching result to identify the specific policy matched.

**System capability:** SystemCapability.Security.DataLossPrevention

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| sensitiveLabel | string | No| No| Label of an identification policy, which is used to identify and classify matching results. The value is a string of 1 to 30 bytes.|
| keywords | Array&lt;string&gt; | No| No| Keyword set, which is used to match sensitive keywords in a file.<br>The system searches for these keywords in the file content and returns the identification result if a keyword is matched. The keywords are case-sensitive. The array can contain a maximum of 50 elements, and each element can contain a maximum of 30 bytes.|
| regex | string | No| No| Regular expression used to match sensitive content. The system performs pattern matching on the file content based on the regular expression. The matched content is returned. The value contains 0 to 512 characters.<br>When entering a string, check whether some special characters (such as backslash (\), double quotation marks ("), and newline characters) are automatically escaped to ensure the input effect of the string.|

## MatchResult

Displays the identification result of sensitive content.

**System capability**: SystemCapability.Security.DataLossPrevention

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| sensitiveLabel | string | Yes| No| Label of an identification policy, which corresponds to **sensitiveLabel** in the input policy and is used to label the policy used to identify the matching result.|
| matchContent | string | Yes| No| Matched sensitive content segment, that is, the text content matched by keyword or regular expression.|
| matchNumber | number | Yes| No| Total number of matched items.|
