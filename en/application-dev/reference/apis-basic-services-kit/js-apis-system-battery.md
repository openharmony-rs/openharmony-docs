# @system.battery (Battery Information)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=940093aa12ae353d9b623701a3a33e4e71d06ce9 translatedAt=2026-11-06T01:37:20.410Z pushedAt=2026-11-09T03:31:22.794Z nl=1 -->

This module provides APIs for querying the charging status and remaining battery level. It applies to scenarios where app behavior needs to be adjusted based on the device battery status, for example, reducing background activity frequency or reminding users to charge when the battery is low, helping you optimize the power consumption performance and user experience of apps.

>  **NOTE**
>
>- Module maintenance policy:
>
>    \- For lite wearables, this module is constantly maintained and available.
>
>    \- For other device types, this module is no longer maintained since API version 6. You are advised to use [@ohos.batteryInfo](js-apis-battery-info.md) instead.
>
>- The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>


## Modules to Import


```js
import {Battery, BatteryResponse } from '@kit.BasicServicesKit';
```


## Battery.getStatus<sup>(deprecated)</sup>

getStatus(options?: GetStatusOptions): void;

Obtains the current charging state and battery level.

**System capability**: SystemCapability.PowerManager.BatteryManager.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [GetStatusOptions](#getstatusoptionsdeprecated) | No | Object containing the API call result, which is used to obtain the device charging status and remaining battery level through a callback. If this parameter is not passed, the battery information cannot be obtained and no callback is executed. |

**Example**

ArkTS example:
```js
Battery.getStatus({
    success: (data: BatteryResponse) => {
        console.info('success get battery level:' + data.level);
    },
    fail: (data: string, code: number) => {
        console.error('fail to get battery level code:' + code + ', data: ' + data);
    }
});
```

JS example:
```xml
<!-- xxx.hml -->
<div class="container">
    <input type="button" value="Get Data" style="width: 240px; height: 50px; margin: 5px;" onclick="getBatteryInfo"></input>
    <text class="title">level: {{ capacity }}</text>
    <text class="title">charging: {{ charging }}</text>
</div>
```
```css
/* xxx.css */
.container {
  width: 100%;
  height: 100%;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.title {
  width: 200px;
  font-size: 30px;
  text-align: center;
}
```
```js
// xxx.js
import Battery from '@system.battery';

export default {
    data: {
        capacity: '',
        charging: ''
    },
    getBatteryInfo() {
        let TAG = 'get_status_success_test';
        Battery.getStatus({
            success: (batteryResponse) => {
                this.capacity = batteryResponse.level;
                this.charging = batteryResponse.charging;
                console.info(`${TAG} batteryResponse.level: ${batteryResponse.level}`);
                console.info(`${TAG} batteryResponse.charging: ${batteryResponse.charging}`);
            },
            fail: (data, code) => {
                console.error(`${TAG} fail data: ${data}, code: ${code}`);
            },
            complete: () => {
                console.info(`${TAG} getStatus complete`);
            }
        });
    },
}
```

## GetStatusOptions<sup>(deprecated)</sup>

Defines an object that contains the API call options, including success, failure, and completion.

**System capability**: SystemCapability.PowerManager.BatteryManager.Lite

| Name  | Type                                               | Mandatory| Description                                                        |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| success  | (data: [BatteryResponse](#batteryresponsedeprecated)) => void | No  | Called when an API call is successful. **data** is a return value of the [BatteryResponse](#batteryresponsedeprecated) type.|
| fail     | (data: string, code: number) => void                | No  | Called invoked when the API call fails. **data** indicates the error message, and **code** indicates the error code.      |
| complete | () => void | No | Callback invoked when the API call ends, regardless of whether the API call succeeds or fails. Pass this callback when cleanup or notification operations need to be performed after the API call is complete. If this callback is not passed, no end notification is provided. |

## BatteryResponse<sup>(deprecated)</sup>

Defines a response that returns the charging status and remaining power of the device.

**System capability**: SystemCapability.PowerManager.BatteryManager.Lite

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| charging | boolean | No| No| Whether the battery is being charged. The value **true** indicates that the battery is being changed; **false** indicates the opposite. The default value is **false**.<br>Note: This API is no longer maintained since API version 6 except for lite wearables. You are advised to use batteryInfo.[chargingStatus](js-apis-battery-info.md#constants) instead.|
| level | number | No| No| Battery level, in percentage. The value ranges from 0.00 to 1.00.<br>Note: This API is no longer maintained since API version 6 except for lite wearables. You are advised to use batteryInfo.[batterySOC](js-apis-battery-info.md#constants) instead.|
