# addWatcher

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## addWatcher

```TypeScript
function addWatcher(watcher: Watcher): AppEventPackageHolder
```

Adds an event watcher. You can use the callback of the event watcher to subscribe to events.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| watcher | [Watcher](arkts-performanceanalysis-hiappevent-watcher-i.md) | Yes | Event watcher. |

**Return value:**

| Type | Description |
| --- | --- |
| [AppEventPackageHolder](arkts-performanceanalysis-hiappevent-appeventpackageholder-c.md) | Subscription data holder. If the subscription fails, **null** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |
| [11102001](../errorcode-hiappevent.md#11102001-invalid-watcher-name) | Invalid watcher name. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11102002](../errorcode-hiappevent.md#11102002-invalid-filtering-event-domain-name) | Invalid filtering event domain. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11102003](../errorcode-hiappevent.md#11102003-invalid-event-number) | Invalid row value. Possibly caused by the row value is less than zero. |
| [11102004](../errorcode-hiappevent.md#11102004-invalid-event-size) | Invalid size value. Possibly caused by the size value is less than zero. |
| [11102005](../errorcode-hiappevent.md#11102005-invalid-timeout-value) | Invalid timeout value. Possibly caused by the timeout value is less than zero. |

**Examples**

```TypeScript
Based on the type of the event watcher, the following methods are available:

Method 1: Set triggerCondition to implement the onTrigger() callback. When the callback conditions are met, the system automatically triggers the callback.
```

```TypeScript
Method 2: If the triggerCondition parameter is not set, use the holder object returned by the event subscription to obtain the subscribed event.

For crash events (hiAppEvent.event.APP_CRASH) and freeze events (hiAppEvent.event.APP_FREEZE) generated during abnormal exits, the system needs time to capture debug logs. Typically, capture completes within 30 seconds; in extreme cases, it may take up to about 2 minutes.

When the subscription data holder is used to manually process subscription events, the events may not be generated or the log capture is not complete. Therefore, you are advised to call takeNext() to obtain such events again after the process is started.
```

```TypeScript
Method 3: Implement the onReceive() callback, which is triggered in real time when the subscribed event occurs.
```
