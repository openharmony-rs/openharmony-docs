# HiAppEvent_AppEventGroup

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @liujiaxing2024-->
<!--Designer: @junjie_shi-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## Overview

Defines the information of an event group, including its name, the array of event information grouped by name, and the length of the event array.

**Since**: 12

**Related module**: [HiAppEvent](capi-hiappevent.md)

**Header file**: [hiappevent.h](capi-hiappevent-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char* name | Pointer to the event name.|
| const struct HiAppEvent_AppEventInfo* appEventInfos | Pointer to the array of events with the same event name.|
| uint32_t infoLen | Length of the event array.|
