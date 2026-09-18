# HiAppEvent

## Overview

Provides application event logging functions.<br> Provides the event logging function for applications to log the fault, statistical, security, and user behavior events reported during running. Based on event information, you will be able to analyze the running status of applications.

**Since**: 8

## Files

| Name | Description |
| -- | -- |
| [hiappevent.h](capi-hiappevent-h.md) | The **HiAppEvent** module provides event subscription and event logging function definitions. Before performing application event logging, you must construct a parameter list object to store the input event parameters and specify the event domain, event name, and event type. <p>Event domain: domain associated with the application event. <p>Event name: name of the application event. <p>Event type: fault, statistics, security, or behavior. <p> Parameter list: a linked list used to store event parameters. Each parameter consists of a parameter name and a parameter value. |
| [hiappevent_cfg.h](capi-hiappevent-cfg-h.md) | Defines the names of all the configuration items of the event logging configuration function.<br> If you want to configure the event logging function, you can directly use the configuration item constants.<br> Sample code: <pre> bool res = OH_HiAppEvent_Configure(MAX_STORAGE, "100M"); </pre> |
| [hiappevent_event.h](capi-hiappevent-event-h.md) | Defines the event names of all predefined events.<br> In addition to custom events associated with specific apps, you can also use predefined events for logging.<br> Sample code: <pre> ParamList list = OH_HiAppEvent_CreateParamList(); OH_HiAppEvent_AddInt32Param(list, PARAM_USER_ID, 123); int res = OH_HiAppEvent_Write("user_domain", EVENT_USER_LOGIN, BEHAVIOR, list); OH_HiAppEvent_DestroyParamList(list); </pre> |
| [hiappevent_param.h](capi-hiappevent-param-h.md) | Defines the param names of all predefined events.<br> In addition to custom events associated with specific apps, you can also use predefined events for logging.<br> Sample code: <pre> ParamList list = OH_HiAppEvent_CreateParamList(); OH_HiAppEvent_AddInt32Param(list, PARAM_USER_ID, 123); int res = OH_HiAppEvent_Write("user_domain", EVENT_USER_LOGIN, BEHAVIOR, list); OH_HiAppEvent_DestroyParamList(list); </pre> |
