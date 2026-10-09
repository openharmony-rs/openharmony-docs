# @system.vibrator (Vibrator)
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @andeszhang-->
<!--Tester: @zhaofangyuan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=2974411111293c1b9305b6df370742288c188888 translatedAt=2026-09-02T07:39:48.417Z pushedAt=2026-09-06T07:09:29.659Z -->

The **@system.vibrator** module provides the capability of controlling the vibration of a device. You can use this module to trigger the device to perform long or short vibration effects, providing tactile feedback for users. It is mainly used in interaction scenarios that require tactile feedback, such as alarm clock, power-off vibration, and incoming call vibration. It helps apps attract users' attention through vibration when key events occur.

This module is applicable to lite wearables. For other device types, this module is not maintained since API version 8.

Compared with the [@ohos.vibrator](js-apis-vibrator.md) module, this module provides simpler functions and does not support advanced functions such as querying vibration effects, querying the vibrator list, and customizing vibration files. For lite wearable devices, this module is continuously maintained. For other device types, this module is no longer maintained since API version 8. You are advised to use the [vibrator.startVibration()](js-apis-vibrator.md#vibratorstartvibration9) API of the [@ohos.vibrator](js-apis-vibrator.md) module. This API supports more vibration effects (including [VibrateTime](js-apis-vibrator.md#vibratetime9), [VibratePreset](js-apis-vibrator.md#vibratepreset9), and [VibrateFromFile](js-apis-vibrator.md#vibratefromfile10)) and is applicable to more device types.

> **NOTE**
>
> - Module maintenance policy:
 >   - For lite wearables, this module is constantly maintained and available.
 >   - For other device types, this module is no longer maintained since API version 8, and you are advised to use the new [@ohos.vibrator (Vibrator)](js-apis-vibrator.md) module.
> - The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This module requires hardware support and can only be debugged on real devices. You can check whether the device supports the vibration function by querying the system device information or using related APIs.

## Modules to Import

```ts
import { Vibrator } from '@kit.SensorServiceKit';
```

## Vibrator

Provides static methods for triggering device vibration.

### Vibrator.vibrate

static vibrate(options?: VibrateOptions): void

Triggers the device to vibrate in short or long mode based on the specified vibration mode. This API uses an asynchronous callback to return the result.

Use this API to trigger device vibration such as alarm clock vibration, incoming call vibration, power-off vibration, and button touch feedback on lite wearable devices. After this API is called, the device vibrates in the specified mode (short or long vibration). If the **mode** parameter is not specified, the device will perform long vibration (the default value of **mode** is **'long'**).

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [vibrator.startVibration()](js-apis-vibrator.md#vibratorstartvibration9) since API version 8.

**Required permissions**: ohos.permission.VIBRATE

**System capability**: SystemCapability.Sensors.MiscDevice.Lite

**Parameters**

| Name | Type                             | Mandatory| Description      |
| ------- | --------------------------------- | ---- | ---------- |
| options | [VibrateOptions](#vibrateoptions) | No | Vibration configuration parameters, which are used to specify the vibration mode and callback function. If this parameter is not specified, the default configuration is used. The default value of **mode** is **'long'**. In this case, only the **success** and **complete** callbacks are triggered, while the **fail** callback will not be triggered. |

**ArkTS example**

```ts
import { Vibrator, VibrateOptions } from '@kit.SensorServiceKit';

// Create a VibrateOptions object.
let vibrateOptions: VibrateOptions = {
  mode: 'short',  // Set the vibration mode to short vibration.
  success: () => {
    console.info('Succeed in vibrating');
  },
  fail: (data: string, code: number) => {
    console.error(`Failed to vibrate. Data: ${data}, code: ${code}`);
  },
  complete: () => {
    console.info('vibration completed');
  }
};
// Trigger device vibration.
Vibrator.vibrate(vibrateOptions);
```

**JS example**

```js
import vibrator from '@system.vibrator';

export default {
  data: {
    TAG: 'WearLiteSample:',
    result: ''
  },
  vibrate() {
    try {
      // Create a VibrateOptions object.
      let vibrateOptions = {
        mode: 'short',  // Set the vibration mode to short vibration.
        success: () => {
          console.info('Succeeded in vibrating');
          this.result = 'Succeeded in vibrating';
        },
        fail: (data, code) => {
          console.error(`Failed to vibrate. Data: ${data}, code: ${code}`);
          this.result = `Failed to vibrate. Data: ${data}, code: ${code}`;
        },
        complete: () => {
          console.info('vibration completed');
        }
      };
      // Trigger device vibration.
      vibrator.vibrate(vibrateOptions);
    } catch (e) {
      console.error(this.TAG + 'vibrate exception occurred, message:' + JSON.stringify(e));
    }
  }
};
```

```xml
<!-- xxx.hml -->
<div class="container">
  <text class="title">
    {{ result }}
  </text>
  <input class="buttonText" type="button" onclick="vibrate">Tap to vibrate</input>
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
  justify-content: center;
}
.title {
  width: 200px;
  font-size: 30px;
  text-align: center;
}
.buttonText {
  background-color: blue;
  radius: 30px;
  text-color: white;
  font-size: 25px;
  width: 150px;
  height:50px;
  margin-top: 20px;
  font-weight: bolder;
  align-items: center;
}
```

## VibrateOptions

Defines the configuration parameters for triggering device vibration, including the vibration mode and callback function. When calling [Vibrator.vibrate()](#vibratorvibrate), you can use **VibrateOptions** to specify the vibration mode (short or long vibration) and the callback function for listening for the vibration triggering success, failure, and completion events. After **VibrateOptions** is passed, the device vibrates in the specified mode. When the vibration is successfully triggered, the **success** function is called back. If the vibration fails to be triggered, the **fail** function is called back. When the API call is complete, the **complete** function is called back.

> **NOTE**
>
> This API is supported since API version 3 and deprecated since API version 8. You are advised to use [VibrateTime](js-apis-vibrator.md#vibratetime9) instead.

**Required permissions**: ohos.permission.VIBRATE

**System capability**: SystemCapability.Sensors.MiscDevice.Lite

| Name    | Type    | Read-Only| Optional| Description                                                        |
| -------- | -------- | ---- | ---- | ------------------------------------------------------------ |
| mode     | string   | No   | Yes   | Vibration mode, which specifies the duration type of device vibration. The options include **'long'** (long vibration) and **'short'** (short vibration). The default value is **'long'**. Use scenarios: You can select the vibration mode based on your requirements. For example, use **'long'** for incoming call notifications to continuously remind users, and use **'short'** for button touch feedback to provide instant feedback. If this parameter is not specified, long vibration is performed by default. Restrictions: This parameter applies only to lite wearables. |
| success  | Function | No   | No   | Callback invoked when the vibration is successfully triggered. Use scenarios: This callback is used to send notices upon successful vibration triggering. Effect: After the vibration is successfully triggered, the system calls this callback function. No parameter is returned. |
| fail     | Function | No   | Yes   | Callback invoked when the vibration fails to be triggered. Use scenarios: This callback is used to obtain error information upon failure to trigger vibration. For example, the permission is not granted or the device does not support vibration. If this parameter is not specified, no callback notification will be sent when the vibration fails to be triggered. Effect: When the vibration fails to be triggered, the system calls this callback function and passes the error information data and error code. The callback function signature is **(data: string, code: number) => void**, where **data** is the error information string and **code** is the error code number, indicating the specific error type. |
| complete | Function | No   | Yes   | Callback function invoked when the vibration API call is complete. Usage scenarios: Use this callback when you need to perform clearance or status update operations after the vibration API call is complete (regardless of whether the call is successful or fails). If this parameter is not specified, no callback notification will be sent when the API call is complete. Effect: The system calls this callback function regardless of whether the vibration is successfully triggered. No parameter is returned. |

