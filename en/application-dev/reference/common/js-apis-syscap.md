# SysCap

<!--Kit: Basic Services Kit-->
<!--Subsystem: Startup-->
<!--Owner: @chenjinxiang3-->
<!--Designer: @chenjinxiang3-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=f4b612cc31aee9b84569bb08c2529a230ab54b6e translatedAt=2026-08-27T03:50:35.713Z pushedAt=2026-08-27T07:20:27.908Z -->

SystemCapability (SysCap) refers to a standalone feature in the operating system. Different devices support different SysCap sets. Each SysCap corresponds to one or more APIs. You can determine whether an API can be used by checking SysCap support.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## canIUse

canIUse(syscap: string): boolean

Checks whether a SysCap is supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

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