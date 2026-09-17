# hiAppEvent(Application Event Logging)

This module provides application logging and event subscription capabilities, including event storage, event subscription, event clearance, and logging configuration. HiAppEvent records the events triggered during application running in [AppEventInfo](arkts-performanceanalysis-hiappevent-appeventinfo-i.md), and classifies the events into system events and application events.

System events are triggered in system services and are predefined in the system. The fields of the event parameter object **params** of such events are defined by each system event. For details, see overviews of user guides. For example, [Crash Event Overview](../../../dfx/hiappevent-watcher-crash-events.md).

Application events are defined by application developers and can be customized using the [Write](arkts-performanceanalysis-hiappevent-write-f.md) API as required.

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [domain](arkts-performanceanalysis-hiappevent-domain-n.md) | Provides domain name constants. |
| [event](arkts-performanceanalysis-hiappevent-event-n.md) | Provides event name constants, including system event name constants and application event name constants.<br>The application event name constants are optional custom event names reserved when you call Write for application event logging. |
| [param](arkts-performanceanalysis-hiappevent-param-n.md) | Provides parameter name constants. |

### Functions

| Name | Description |
| --- | --- |
| [configure](arkts-performanceanalysis-hiappevent-configure-f.md) | Configures the application event logging function, such as setting the logging switch and directory storage quota. |
| [write](arkts-performanceanalysis-hiappevent-write-f.md) | Writes events of the **AppEventInfo** type. This API uses a promise to return the result. The event object written by calling this API is a custom object. To avoid conflicts with system events, you are not advised to write it to system events (system event name constants defined in [Event](arkts-performanceanalysis-hiappevent-event-n.md)). The events written by this API can be subscribed to through ([addWatcher](arkts-performanceanalysis-hiappevent-addwatcher-f.md)). |
| [write](arkts-performanceanalysis-hiappevent-write-f.md) | Writes events of the **AppEventInfo** type. This API uses an asynchronous callback to return the result. The event object written by calling this API is a custom object. To avoid conflicts with system events, you are not advised to write it to system events (system event name constants defined in [Event](arkts-performanceanalysis-hiappevent-event-n.md)). The events written by this API can be subscribed to through ([addWatcher](arkts-performanceanalysis-hiappevent-addwatcher-f.md)). |
| [setEventParam](arkts-performanceanalysis-hiappevent-seteventparam-f.md) | Sets custom event parameters. This API uses a promise to return the result. During the same lifecycle, system events and application events can be associated through event domain and event name.System events only support crash, freeze and resource leak events. |
| [setEventConfig](arkts-performanceanalysis-hiappevent-seteventconfig-f.md) | Sets event configuration. This method uses a promise to return the result. In the same lifecycle, you can set event configuration by event name. |
| [addWatcher](arkts-performanceanalysis-hiappevent-addwatcher-f.md) | Adds an event watcher. You can use the callback of the event watcher to subscribe to events. |
| [removeWatcher](arkts-performanceanalysis-hiappevent-removewatcher-f.md) | Removes an event watcher. |
| [clearData](arkts-performanceanalysis-hiappevent-cleardata-f.md) | Clears local logging data of the application. |
| [setUserId](arkts-performanceanalysis-hiappevent-setuserid-f.md) | Sets a user ID, which is used for association when a [Processor](arkts-performanceanalysis-hiappevent-processor-i.md) is configured. |
| [getUserId](arkts-performanceanalysis-hiappevent-getuserid-f.md) | Obtains the value set through **setUserId**. |
| [setUserProperty](arkts-performanceanalysis-hiappevent-setuserproperty-f.md) | Sets a user property, which is used for association when a [Processor](arkts-performanceanalysis-hiappevent-processor-i.md) is configured. |
| [getUserProperty](arkts-performanceanalysis-hiappevent-getuserproperty-f.md) | Obtains the value set through **setUserProperty**. |
| [addProcessor](arkts-performanceanalysis-hiappevent-addprocessor-f.md) | Adds the configuration information of the data processor, such as the event name received by it. |
| [addProcessorFromConfig](arkts-performanceanalysis-hiappevent-addprocessorfromconfig-f.md) | Adds the configuration information of the data processor. The configuration file contains information such as the name of the event received by the data processor. This API uses a promise to return the result. |
| [removeProcessor](arkts-performanceanalysis-hiappevent-removeprocessor-f.md) | Removes the data processor of a reported event. |
| [configEventPolicy](arkts-performanceanalysis-hiappevent-configeventpolicy-f.md) | Sets a system event configuration policy. This API uses a promise to return the result. |
| [registerExternalLogManager](arkts-performanceanalysis-hiappevent-registerexternallogmanager-f.md) | Register external log manager |
| [isExternalLogManagerRegistered](arkts-performanceanalysis-hiappevent-isexternallogmanagerregistered-f.md) | Query if external log manager is already registered |

### Classes

| Name | Description |
| --- | --- |
| [AppEventPackageHolder](arkts-performanceanalysis-hiappevent-appeventpackageholder-c.md) | Defines a subscription data holder for processing event information. |
| [ExternalLogManager](arkts-performanceanalysis-hiappevent-externallogmanager-c.md) | Defines an external log manager for external log management. |
| [ExternalLogContainer](arkts-performanceanalysis-hiappevent-externallogcontainer-c.md) | An external log container including all external log files. |
| [ExternalLogWrapper](arkts-performanceanalysis-hiappevent-externallogwrapper-c.md) | The wrapper of external log, providing various information. |

### Interfaces

| Name | Description |
| --- | --- |
| [ConfigOption](arkts-performanceanalysis-hiappevent-configoption-i.md) | Provides configuration options for application event logging. |
| [AppEventInfo](arkts-performanceanalysis-hiappevent-appeventinfo-i.md) | Defines parameters of the event information. |
| [AppEventPackage](arkts-performanceanalysis-hiappevent-appeventpackage-i.md) | Defines parameters of an **AppEventPackage** object. This API is used to obtain detail information about an event package, which is obtained using the [takeNext](arkts-performanceanalysis-hiappevent-appeventpackageholder-c.md#takenext) API. |
| [TriggerCondition](arkts-performanceanalysis-hiappevent-triggercondition-i.md) | Defines the triggering condition parameters of the **onTrigger** callback of a [Watcher](arkts-performanceanalysis-hiappevent-watcher-i.md). |
| [AppEventFilter](arkts-performanceanalysis-hiappevent-appeventfilter-i.md) | Defines parameters of subscription filtering conditions of a [Watcher](arkts-performanceanalysis-hiappevent-watcher-i.md). This API is used to set event filtering conditions in the event watcher to ensure that only the events that meet the filtering conditions are subscribed to. |
| [AppEventGroup](arkts-performanceanalysis-hiappevent-appeventgroup-i.md) | Defines parameters of the event group returned by the subscription. This API can be used to obtain detail information about an event group, which is often used in the **onReceive** callback of [Watcher](arkts-performanceanalysis-hiappevent-watcher-i.md). |
| [Watcher](arkts-performanceanalysis-hiappevent-watcher-i.md) | Defines parameters for a **Watcher** object. This API is used to configure and manage event watchers to subscribe to and process specified events. |
| [AppEventReportConfig](arkts-performanceanalysis-hiappevent-appeventreportconfig-i.md) | Defines the event configuration for the data processor to report. |
| [Processor](arkts-performanceanalysis-hiappevent-processor-i.md) | Defines a data processor for reporting and managing events. You can customize processor configurations as required. |
| [MainThreadJankPolicy](arkts-performanceanalysis-hiappevent-mainthreadjankpolicy-i.md) | Defines the configuration policy for the main thread jank event. |
| [CpuUsageHighPolicy](arkts-performanceanalysis-hiappevent-cpuusagehighpolicy-i.md) | Defines the configuration policy for the high CPU usage event. |
| [AppCrashPolicy](arkts-performanceanalysis-hiappevent-appcrashpolicy-i.md) | Defines the application crash event configuration policy. |
| [AppFreezePolicy](arkts-performanceanalysis-hiappevent-appfreezepolicy-i.md) | Defines the application freeze event configuration policy. |
| [ResourceOverlimitPolicy](arkts-performanceanalysis-hiappevent-resourceoverlimitpolicy-i.md) | Defines the resource leak event configuration policy. |
| [AddressSanitizerPolicy](arkts-performanceanalysis-hiappevent-addresssanitizerpolicy-i.md) | Defines the address sanitizer event configuration policy. |
| [EventPolicy](arkts-performanceanalysis-hiappevent-eventpolicy-i.md) | Defines the system event configuration policy, which is set by calling [configEventPolicy](arkts-performanceanalysis-hiappevent-configeventpolicy-f.md). |

### Types

| Name | Description |
| --- | --- |
| [ParamType](arkts-performanceanalysis-hiappevent-paramtype-t.md) | Enumerates the types of custom event parameter values. |

### Enums

| Name | Description |
| --- | --- |
| [EventType](arkts-performanceanalysis-hiappevent-eventtype-e.md) | Enumerates event types. |
