# setEventConfig

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## setEventConfig

```TypeScript
function setEventConfig(name: string, config: Record<string, ParamType>): Promise<void>
```

Sets event configuration. This method uses a promise to return the result. In the same lifecycle, you can set event configuration by event name.

Configuration items vary depending on events. Currently, only the following events are supported:

- **MAIN_THREAD_JANK** (For details about the parameter configuration, see [Main Thread Jank Event Overview](../../../dfx/hiappevent-watcher-mainthreadjank-events.md#parameters-of-seteventconfig).)  
- **APP_CRASH** (For details about the parameter configuration, see [Crash Log Configuration Parameters](../../../dfx/hiappevent-watcher-crash-events.md#customizing-crash-log-specifications).)  
- **RESOURCE_OVERLIMIT** (For details about the parameter configuration, see [Resource Leak Event Overview](../../../dfx/hiappevent-watcher-resourceleak-events.md#customizing-specifications).)

> **NOTE:** 
> 
> Since API version 26.0.0, all settings of this API are supported by
> [configEventPolicy](arkts-performanceanalysis-hiappevent-configeventpolicy-f.md). You are advised to use
> [configEventPolicy](arkts-performanceanalysis-hiappevent-configeventpolicy-f.md).

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Event name. |
| config | Record&lt;string, [ParamType](arkts-performanceanalysis-hiappevent-paramtype-t.md)&gt; | Yes | Custom parameter object. The parameter name and value are defined as follows:<br>- The parameter name contains a maximum of 1024 characters, which is of the string type and cannot be empty.<br>- The parameter value is of the ParamType and contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3.Parameter verification failed. |

**Examples**

```TypeScript
The following example sets the collection stack parameters of the MAIN_THREAD_JANK event:
```
