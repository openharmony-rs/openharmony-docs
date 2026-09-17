# @ohos.hiSysEvent(System Event Logging)

The **hiSysEvent** module provides the system event logging functions, such as configuring trace points, subscribing to system events, and querying system events written to the event file.

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addWatcher](arkts-performanceanalysis-hisysevent-addwatcher-f-sys.md) | Adds a watcher for event subscription. |
| [exportSysEvents](arkts-performanceanalysis-hisysevent-exportsysevents-f-sys.md) | Exports system events in batches and writes them as a file to the fixed directory of the application sandbox (that is, /data/storage/el2/base/cache/hiview/event/). |
| [query](arkts-performanceanalysis-hisysevent-query-f-sys.md) | Queries system events. |
| [removeWatcher](arkts-performanceanalysis-hisysevent-removewatcher-f-sys.md) | Removes a watcher used for event subscription. |
| [subscribe](arkts-performanceanalysis-hisysevent-subscribe-f-sys.md) | Subscribes to real-time system events that occur occasionally or occur in a low frequency. These events are written as a file to the fixed directory of the application sandbox (that is, /data/storage/el2/base/cache/hiview/event/). |
| [unsubscribe](arkts-performanceanalysis-hisysevent-unsubscribe-f-sys.md) | Unsubscribes from system events. |
| [write](arkts-performanceanalysis-hisysevent-write-f-sys.md) | Writes event information to the event file. This API uses a promise to return the result. |
| [write](arkts-performanceanalysis-hisysevent-write-f-sys.md) | Writes event information to the event file. This API uses an asynchronous callback to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [Querier](arkts-performanceanalysis-hisysevent-querier-i-sys.md) | Defines an event query instance. |
| [QueryArg](arkts-performanceanalysis-hisysevent-queryarg-i-sys.md) | Defines arguments for an event query. |
| [QueryRule](arkts-performanceanalysis-hisysevent-queryrule-i-sys.md) | Defines event query rules. |
| [SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md) | Defines a system event. |
| [Watcher](arkts-performanceanalysis-hisysevent-watcher-i-sys.md) | Defines a watcher for event subscription. |
| [WatchRule](arkts-performanceanalysis-hisysevent-watchrule-i-sys.md) | Defines event subscription rules. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [EventType](arkts-performanceanalysis-hisysevent-eventtype-e-sys.md) | Enumerate system event types. |
| [RuleType](arkts-performanceanalysis-hisysevent-ruletype-e-sys.md) | Enumerates matching rule types. |
<!--DelEnd-->
