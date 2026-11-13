# @ohos.charger (Charger) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=b6e13138f92c3dbb8b70b3fd5db1178bdab496cf translatedAt=2026-11-06T01:37:27.854Z pushedAt=2026-11-09T02:09:14.510Z nl=1 -->

The **charger** module enumerates charging types.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.


## Modules to Import

```js
import { charger } from '@kit.BasicServicesKit';
```

## ChargeType

Enumerates charging types.

**System API**: This is a system API.

**System capability**: SystemCapability.PowerManager.BatteryManager.Core

| Name      | Value | Description             |
| -------- | ---- | ----------------- |
| NONE                 | 0    | Unknown charging type.     |
| WIRED_NORMAL         | 1    | Wired normal charging.|
| WIRED_QUICK          | 2    | Wired fast charging.  |
| WIRED_SUPER_QUICK    | 3    | Wired super fast charging.|
| WIRELESS_NORMAL      | 4    | Wireless normal charging.|
| WIRELESS_QUICK       | 5    | Wireless fast charging.|
| WIRELESS_SUPER_QUICK | 6    | Wireless super fast charging.|
