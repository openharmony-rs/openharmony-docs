# @ohos.hiviewdfx.hiAppEvent(Application Event Logging)

This module provides application logging and event subscription capabilities, including event storage, event subscription, event clearance, and logging configuration. HiAppEvent records the events triggered during application running in [AppEventInfo](arkts-performanceanalysis-hiappevent-appeventinfo-i.md), and classifies the events into system events and application events.

System events are triggered in system services and are predefined in the system. The fields of the event parameter object **params** of such events are defined by each system event. For details, see overviews of user guides. For example, [Crash Event Overview](../../../dfx/hiappevent-watcher-crash-events.md).

Application events are defined by application developers and can be customized using the [Write](arkts-performanceanalysis-hiappevent-write-f.md) API as required.

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [hiAppEvent](arkts-performanceanalysis-hiappevent-n.md) | This module provides application logging and event subscription capabilities, including event storage, event subscription, event clearance, and logging configuration. HiAppEvent records the events triggered during application running in [AppEventInfo](arkts-performanceanalysis-hiappevent-appeventinfo-i.md), and classifies the events into system events and application events. |
