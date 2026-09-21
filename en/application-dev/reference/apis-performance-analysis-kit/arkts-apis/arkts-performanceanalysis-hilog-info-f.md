# info

## Modules to Import

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
```

## info

```TypeScript
function info(domain: number, tag: string, format: string, ...args: any[]): void
```

Prints INFO logs.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiLog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| domain | number | Yes | Service domain of logs. The value ranges from **0x0** to **0xFFFF**. If the value exceeds the range, logs cannot be printed.<br>You can define the value as required. |
| tag | string | Yes | Log tag in the string format. You are advised to use this parameter to identify a particular service behavior or the class holding the ongoing method. A tag can contain a maximum of 31 bytes. If a tag exceeds this limit, it will be truncated. Chinese characters are not recommended because garbled characters or alignment problems may occur. |
| format | string | Yes | Format string used to output logs in a specified format. It can contain several elements, where the parameter type and privacy identifier are mandatory.<br>Parameters labeled **{public}** are public data and are displayed in plaintext; parameters labeled **{private}** (default value) are private data and are filtered by **&lt;private&gt;**. |
| args | any[] | Yes | Variable-length parameter list corresponding to the format string. The number and type of parameters must map to the identifier in the format string. |

**Examples**

This example is used to output an INFO log with the format string being "%{public}s World %{private}d". The variable  is a plaintext string, and the variable  is a private integer.

```TypeScript
hilog.info(0x0001, "testTag", "%{public}s World %{private}d", "hello", 3);
```

If "hello" is filled in %{public}s and 3 in %{private}d, the output log is as follows:

```TypeScript
08-05 12:21:47.579  2695-2703  A00001/testTag  com.example.hilogDemo  I     hello World <private>
```
