# hiAppEvent(Application Event Logging)

```TypeScript
declare namespace hiAppEvent
```

The **hiAppEvent** module provides the application event logging functions, such as writing application events to the event file and managing the event logging configuration.

> **NOTE:** 
> 
> - The APIs provided by this module are deprecated since API version 9. You are advised to use [@ohos.hiviewdfx.hiAppEvent](arkts-performanceanalysis-hiappevent-n.md).

**Since:** 7

**Deprecated since:** 9

**Substitutes:** hiAppEvent

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## Modules to Import

```TypeScript
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [Event](arkts-performanceanalysis-hiappevent-event-depr-n.md) | Provides constants that define the names of all predefined events. |
| [Param](arkts-performanceanalysis-hiappevent-param-depr-n.md) | Provides constants that define the names of all predefined event parameters. |

### Functions

| Name | Description |
| --- | --- |
| [write](arkts-performanceanalysis-hiappevent-write-depr-f.md#write) | Writes event information to the event file of the current day. This API uses a promise to return the result. |
| [write](arkts-performanceanalysis-hiappevent-write-depr-f.md#write-1) | Writes event information to the event file of the current day. This API uses an asynchronous callback to return the result. |
| [configure](arkts-performanceanalysis-hiappevent-configure-depr-f.md#configure) | Configures the application event logging function, such as setting the event logging switch and maximum size of the directory that stores the event logging files. |

### Interfaces

| Name | Description |
| --- | --- |
| [ConfigOption](arkts-performanceanalysis-hiappevent-configoption-depr-i.md) | Provides the configuration items for application event logging. |

### Enums

| Name | Description |
| --- | --- |
| [EventType](arkts-performanceanalysis-hiappevent-eventtype-depr-e.md) | Enumerates the event types. |
