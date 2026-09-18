# hiappevent_cfg.h

## Overview

Defines the names of all the configuration items of the event logging configuration function.<br> If you want to configure the event logging function, you can directly use the configuration item constants.<br> Sample code: <pre> bool res = OH_HiAppEvent_Configure(MAX_STORAGE, "100M"); </pre>

**Library**: libhiappevent_ndk.z.so

**System capability**: SystemCapability.HiviewDFX.HiAppEvent

**Since**: 8

**Related module**: [HiAppEvent](capi-hiappevent.md)

## Summary

### Macro

| Name | Description |
| -- | -- |
| HIVIEWDFX_HIAPPEVENT_CONFIG_H | Defines the names of all the configuration items of the event logging configuration function.<br> If you want to configure the event logging function, you can directly use the configuration item constants.<br> Sample code: <pre> bool res = OH_HiAppEvent_Configure(MAX_STORAGE, "100M"); </pre><br>**Since**: 8<br>**System capability**: SystemCapability.HiviewDFX.HiAppEvent |
| DISABLE "disable" | Whether to disable event logging. The default value is false. The value true means to disable the event logging function, and the value false means the opposite.<br>**Since**: 8 |
| MAX_STORAGE "max_storage" | Event file directory storage quota size. The default value is 10MB.<br>**Since**: 8 |

