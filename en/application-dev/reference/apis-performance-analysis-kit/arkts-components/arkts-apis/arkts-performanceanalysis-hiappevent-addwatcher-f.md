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

Based on the type of the event watcher, the following methods are available:

Method 1: Set triggerCondition to implement the onTrigger() callback. When the callback conditions are met, the system automatically triggers the callback.

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

hiAppEvent.addWatcher({
  name: "watcher1",
  // Subscription filters. The application crash event in the system event domain is subscribed.
  appEventFilters: [
    {
      domain: hiAppEvent.domain.OS,
      names: [hiAppEvent.event.APP_CRASH]
    }
  ],
  // Set the condition for triggering the onTrigger callback. The callback is triggered when the total number of events reaches 10, the total event size reaches 1000 bytes, or the event lasts for more than 30s.
  triggerCondition: {
    row: 10,
    size: 1000,
    timeOut: 1
  },
  // Implement the onTrigger callback with triggerCondition. When the callback condition is met, the callback is triggered. After the callback notification is received, use takeNext() to query the subscribed event.
  onTrigger: (curRow: number, curSize: number, holder: hiAppEvent.AppEventPackageHolder) => {
    if (holder == null) {
      hilog.error(0x0000, 'hiAppEvent', "holder is null");
      return;
    }
    hilog.info(0x0000, 'hiAppEvent', `curRow=${curRow}, curSize=${curSize}`);
    let eventPkg: hiAppEvent.AppEventPackage | null = null;
    while ((eventPkg = holder.takeNext()) != null) {
      hilog.info(0x0000, 'hiAppEvent', `eventPkg.packageId=${eventPkg.packageId}`);
      hilog.info(0x0000, 'hiAppEvent', `eventPkg.row=${eventPkg.row}`);
      hilog.info(0x0000, 'hiAppEvent', `eventPkg.size=${eventPkg.size}`);
      for (const eventInfo of eventPkg.data) {
        hilog.info(0x0000, 'hiAppEvent', `eventPkg.data=${eventInfo}`);
      }
    }
  }
});
```

Method 2: If the triggerCondition parameter is not set, use the holder object returned by the event subscription to obtain the subscribed event.

For crash events (hiAppEvent.event.APP_CRASH) and freeze events (hiAppEvent.event.APP_FREEZE) generated during abnormal exits, the system needs time to capture debug logs. Typically, capture completes within 30 seconds; in extreme cases, it may take up to about 2 minutes.

When the subscription data holder is used to manually process subscription events, the events may not be generated or the log capture is not complete. Therefore, you are advised to call takeNext() to obtain such events again after the process is started.

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

let holder: hiAppEvent.AppEventPackageHolder = hiAppEvent.addWatcher({
  name: "watcher2",
  // Subscription filters. The application crash event in the system event domain is subscribed.
  appEventFilters: [
    {
      domain: hiAppEvent.domain.OS,
      names: [hiAppEvent.event.APP_CRASH]
    }
  ],
});
// Obtain crash events through the subscription data holder.
if (holder != null) {
  let eventPkg: hiAppEvent.AppEventPackage | null = null;
  while ((eventPkg = holder.takeNext()) != null) {
    hilog.info(0x0000, 'hiAppEvent', `eventPkg.packageId=${eventPkg.packageId}`);
    hilog.info(0x0000, 'hiAppEvent', `eventPkg.row=${eventPkg.row}`);
    hilog.info(0x0000, 'hiAppEvent', `eventPkg.size=${eventPkg.size}`);
    for (const eventInfo of eventPkg.data) {
      hilog.info(0x0000, 'hiAppEvent', `eventPkg.data=${eventInfo}`);
    }
  }
}
```

Method 3: Implement the onReceive() callback, which is triggered in real time when the subscribed event occurs.

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

hiAppEvent.addWatcher({
  name: "watcher3",
  // Subscription filters. The application crash event in the system event domain is subscribed.
  appEventFilters: [
    {
      domain: hiAppEvent.domain.OS,
      names: [hiAppEvent.event.APP_CRASH]
    }
  ],
  // Implement the onReceive callback, which is called in real time after an event is detected.
  onReceive: (domain: string, appEventGroups: Array<hiAppEvent.AppEventGroup>) => {
    hilog.info(0x0000, 'hiAppEvent', `domain=${domain}`);
    for (const eventGroup of appEventGroups) {
      hilog.info(0x0000, 'hiAppEvent', `eventName=${eventGroup.name}`);
      for (const eventInfo of eventGroup.appEventInfos) {
        hilog.info(0x0000, 'hiAppEvent', `event=${JSON.stringify(eventInfo)}`);
      }
    }
  }
});
```
