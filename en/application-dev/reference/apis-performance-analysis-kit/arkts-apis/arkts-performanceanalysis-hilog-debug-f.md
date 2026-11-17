# debug

## Modules to Import

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
```

## debug

```TypeScript
function debug(domain: number, tag: string, format: string, ...args: any[]): void
```

Prints a DEBUG-level log.

DEBUG-level logs are not printed by default in release versions. They are only printed in debug versions or when the debug switch is enabled.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-hilog-function debug(domain: number, tag: string, format: string, ...args: any[]): void--><!--Device-hilog-function debug(domain: number, tag: string, format: string, ...args: any[]): void-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| domain | number | Yes | Domain identifier for the log, ranging from 0x0 to 0xFFFF. Logs outside this range cannot be printed.<br>It is recommended that developers define and divide domains as needed within the application. |
| tag | string | Yes | Specifies the log tag, which can be any string. It is recommended to identify the calling class or business behavior. The recommended tag length should not exceed 31 bytes. Chinese characters are not recommended as they may cause garbled text or alignment issues. |
| format | string | Yes | Format string for formatted log output. The format string can contain multiple parameters, each requiring a parameter type and privacy flag.<br>Privacy flags are divided into {public} and {private}, defaulting to {private}. Content marked with {public} is output in plaintext, while content marked with {private} is displayed as <private>. The privacy flag mechanism helps developers protect privacy-sensitive data. |
| args | any[] | Yes | Variable-length parameter list corresponding to the format string. The number and types of parameters must match the placeholders in the format string one-to-one. When the format string does not contain placeholders, this parameter can be omitted, and only the format string itself is output. |

**Examples**

This example is used to output a DEBUG log with the format string being "%{public}s World %{private}d". The variable  is a plaintext string, and the variable  is a private integer.

```TypeScript
hilog.debug(0x0001, "testTag", "%{public}s World %{private}d", "hello", 3);
```

If "hello" is filled in %{public}s and 3 in %{private}d, the output log is as follows:

```TypeScript
08-05 12:21:47.579  2695-2703  A00001/testTag  com.example.hilogDemo  D     hello World <private>
```
