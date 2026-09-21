# setUserProperty

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## setUserProperty

```TypeScript
function setUserProperty(name: string, value: string): void
```

Sets a user property, which is used for association when a [Processor](arkts-performanceanalysis-hiappevent-processor-i.md) is configured.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Key of a user property. The value is string that contains a maximum of 256 characters, including digits (0 to 9), letters (a to z)(A to Z), underscore (_), and dollar sign ($). It must not start with a digit. |
| value | string | Yes | Value of a user property. It can contain a maximum of 1024 characters. If the value is **null** or left empty, the user property is cleared. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

**Examples**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  hiAppEvent.setUserProperty('key', 'value');
} catch (error) {
  hilog.error(0x0000, 'hiAppEvent', `failed to setUserProperty event, code=${error.code}`);
}
```
