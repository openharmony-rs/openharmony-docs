# SysCap

<!--Kit: Basic Services Kit-->
<!--Subsystem: Startup-->
<!--Owner: @chenjinxiang3-->
<!--Designer: @chenjinxiang3-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:22:48.206Z pushedAt=2026-06-22T03:21:12.893Z -->

SystemCapability (SysCap) refers to a standalone feature in the operating system. Different devices support different SysCap sets. Each SysCap corresponds to one or more APIs. You can determine whether an API can be used by checking SysCap support.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## canIUse

canIUse(syscap: string): boolean

Checks whether a SysCap is supported.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11. This API applies only to ArkTS-Dyn.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| syscap | string | Yes| Name of the SysCap to check. **null** and **undefined** are not supported.|

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Check result. The value **true** means that the SysCap is supported, and **false** means the opposite.|

**Example**

```js
import { geoLocationManager } from '@kit.LocationKit'
import { BusinessError } from '@kit.BasicServicesKit';

const isLocationAvailable = canIUse('SystemCapability.Location.Location.Core');
if (isLocationAvailable) {
    geoLocationManager.getCurrentLocation((err: BusinessError, location: geoLocationManager.Location) => {
        if (err) {
            console.error('err=' + JSON.stringify(err));
        }
        if (location) {
            console.info('location=' + JSON.stringify(location));
        }
    });
} else {
    console.info('Location not by this device.');
}
```