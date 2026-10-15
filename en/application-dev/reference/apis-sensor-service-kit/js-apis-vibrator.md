# @ohos.vibrator (Vibrator)
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @butterls-->
<!--Tester: @zhaofangyuan-->
<!--Adviser: @hu-zhiqiong-->

The **vibrator** module is a device vibration control module in Sensor Service Kit. This module provides precise control over device vibration. It allows you to trigger vibration based on the specified duration, preset effect, custom configuration file, or custom vibration pattern, and to stop vibration in a specified pattern or all patterns. In addition, this module provides capabilities such as querying vibration effects, querying vibration information, and listening for vibrator status changes.

The **vibrator** module is mainly used to enhance user interaction experience by providing intuitive physical feedback for apps through tactile perception. Typical use scenarios are as follows:
- Interaction feedback: short vibration feedback for haptic controls such as tapping, long press, swiping, and dragging. You are advised to use the preset effects in **VibratePreset** to ensure consistency with the overall vibration style of the system.
- Notification reminder: vibration reminders for notifications, incoming calls, alarms, and other scenarios.
- Games and multimedia: In complex scenarios such as game operation feedback and emoticon simulation effects, you are advised to use **VibrateFromFile** or **VibrateFromPattern** to customize vibration effects.
- Multi-device collaboration: In distributed scenarios, you can specify the device ID and vibrator ID to control the vibration of a remote device.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.

The core capabilities of the **vibrator** module focus on starting and stopping vibration. The overall usage process is as follows:

Process of starting vibration:

1. To use a preset vibration effect (**VibratePreset**), you are advised to call [vibrator.isSupportEffect](#vibratorissupporteffect10) or [vibrator.isSupportEffectSync](#vibratorissupporteffectsync12) to check whether the device supports the effect. To use a custom vibration configuration file (**VibrateFromFile**), you are advised to check whether the device supports the custom vibration mode. You can call [vibrator.isHdHapticSupported](#vibratorishdhapticsupported12) to check whether high-definition vibration is supported. To use a custom vibration pattern (**VibrateFromPattern**), you need to use [VibratorPatternBuilder](#vibratorpatternbuilder18) to build a vibration sequence first.
2. To start vibration by calling [vibrator.startVibration](#vibratorstartvibration9), you need to specify both **VibrateEffect** and **VibrateAttribute**. The **usage** parameter determines the vibration scenario type. Different scenario types are controlled by different system vibration switch rules.

Process of stopping vibration:

- Stop vibration for a specified duration or preset effect. Call [vibrator.stopVibration](#vibratorstopvibration9) (API version 9) and pass the corresponding **VibratorStopMode**.
- Stop custom vibration (**VibrateFromFile** or **VibrateFromPattern**). Call [vibrator.stopVibration](#vibratorstopvibration10-1) (version with no parameters since API version 10+) to stop vibration in all modes.
- Stop vibration in all modes. Call [vibrator.stopVibration](#vibratorstopvibration10-1) (version with no parameters) or [vibrator.stopVibrationSync](#vibratorstopvibrationsync12) (synchronous version).
- Stop vibrator vibration on a specified device. Call [vibrator.stopVibration](#vibratorstopvibration19). Since API version 19+, pass **VibratorInfoParam**.

Multi-vibrator device scenarios:

Since API version 19, multi-device and multi-vibrator scenarios are supported. You can call [vibrator.getVibratorInfoSync](#vibratorgetvibratorinfosync19) to query vibrator information and call [vibrator.on](#vibratoron19) to listen for vibrator status changes. Based on the information, you can dynamically select a vibrator to trigger vibration.

Vibration effect types:

| Vibration Effect Type| Scenario| Personalization Degree| Recommended Priority|
| --- | --- | --- | --- |
| VibratePreset | Short vibration scenarios in interactive feedback (such as tapping, long-pressing, sliding, and dragging).| Low. Use the preset effect.| Recommended. The effect is consistent with the overall vibration feedback experience of the system.|
| VibrateFromFile | Complex effect scenarios (such as realistic effects of emoji packs, or feedback for in-game actions/mechanics).| High. The vibration configuration file can be customized.| Applicable to scenarios that require fine vibration.|
| VibrateFromPattern | Same as **VibrateFromFile**, but more flexible.| High. The combination of vibration event arrays is supported.| Applicable to scenarios that require dynamic combination of vibration events.|
| VibrateTime | Vibration of the basic duration. Only the start and stop need to be controlled in this scenario.| Low. The intensity and frequency cannot be adjusted.| Only basic function requirements are met.|

## Modules to Import

```ts
import { vibrator } from '@kit.SensorServiceKit';
```

## vibrator.startVibration<sup>9+</sup>

startVibration(effect: VibrateEffect, attribute: VibrateAttribute, callback: AsyncCallback&lt;void&gt;): void

Starts vibration with the specified effect and attribute. This API uses an asynchronous callback to return the result.

This function is applicable to scenarios where tactile feedback is required for user interaction, vibration reminders are needed for events such as notifications and alarms, or immersive vibration experience is desired in games and multimedia. After the API is successfully called, the vibrator will start to vibrate based on the specified effect and attribute. If the same vibrator is already vibrating, the new request will be processed based on the system priority rules. The **vibrator.startVibration** (**#vibratorstartvibration9-1**) is also provided when the API uses a promise to return the result. You can choose either version based on your preference for the callback style.

**Required permissions**: ohos.permission.VIBRATE

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name   | Type                                  | Mandatory| Description                                                        |
| --------- | -------------------------------------- | ---- | :----------------------------------------------------------- |
| effect    | [VibrateEffect](#vibrateeffect9)       | Yes  | Vibration effect. The following options are supported:<br>1. [VibratePreset](#vibratepreset9): triggers vibration according to preset vibration effects. This mode is suitable for short vibration scenarios in interactive feedback (such as tapping, long-pressing, sliding, dragging, etc.). This API is recommended to maintain consistency with the system's overall vibration feedback experience.<br>2. [VibrateFromFile](#vibratefromfile10): triggers vibration according to custom vibration configuration file. This mode is suitable for interactive feedback in complex scenarios requiring precise vibration patterns (such as realistic effects triggered by emoji packs, or feedback for in-game actions/mechanics).<br>3. [VibrateTime](#vibratetime9): triggers vibration of the specified duration, providing basic control over the start and stop of vibration. This mode does not support customization of vibration intensity, frequency, or other parameters. As a result, the vibration adjustment is relatively coarse and not suitable for delivering a refined experience.<br>4. [VibrateFromPattern<sup>18+</sup>](#vibratefrompattern18): starts vibration according to a custom vibration pattern. The usage scenario is the same as **VibrateFromFile**. **VibrateFromFile** utilizes predefined effects in a custom configuration file, passing specific vibration events to the API via file descriptors. By contrast, **VibrateFromPattern** enables more flexible vibration event combinations, delivering them to the API as a vibration event array.<br>|
| attribute | [VibrateAttribute](#vibrateattribute9) | Yes  | Vibration attribute, which specifies the vibrator ID, device ID, and vibration usage scenario. The **usage** parameter in **attribute** determines the vibration scenario type. Different scenario types are controlled by different system vibration switch rules. You need to select a proper value for **usage** based on the actual service scenario.|
| callback  | AsyncCallback&lt;void&gt;              | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object, which contains the error code and error information. The callback result can be used to check whether the vibration is started successfully. If the vibration fails to be started, you can rectify the fault based on the error code.|

**Error codes**

For details about the error codes, see [Vibrator Error Codes](errorcode-vibrator.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 801      | Capability not supported.                                    |
| 14600101 | Device operation failed.                                     |

**Example**

1. Trigger vibration based on a preset effect.

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   // Use try catch to capture possible exceptions.
   try {
     // Check whether 'haptic.notice.success' is supported.
     vibrator.isSupportEffect('haptic.notice.success', (err: BusinessError, state: boolean) => {
       if (err) {
         console.error(`Failed to query effect. Code: ${err.code}, message: ${err.message}`);
         return;
       }
       console.info('Succeed in querying effect');
       if (state) {
         try {
           vibrator.startVibration({
             type: 'preset',
             effectId: 'haptic.notice.success',
             count: 1,
           }, {
             usage: 'notification' // The switch control is subject to the selected type.
           }, (error: BusinessError) => {
             if (error) {
               console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
          return;
             }
             console.info('Succeed in starting vibration');
          
           });
         } catch (err) {
           let e: BusinessError = err as BusinessError;
       console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
         }
       }
     })
   } catch (error) {
     let e: BusinessError = error as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```

2. Trigger vibration based on a custom vibration configuration file.

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { resourceManager } from '@kit.LocalizationKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   const fileName: string = 'xxx.json';

   @Entry
   @Component
   struct Index {
     uiContext = this.getUIContext();

     build() {
       Row() {
         Column() {
           Button('alarm-file')
             .onClick(() => {
               let rawFd: resourceManager.RawFileDescriptor | undefined = this.uiContext.getHostContext()?.resourceManager.getRawFdSync(fileName);
               if (rawFd != undefined) {
                 try {
                   vibrator.startVibration({
                     type: 'file',
                     hapticFd: { fd: rawFd.fd, offset: rawFd.offset, length: rawFd.length }
                   }, {
                     id: 0,
                     usage: 'alarm' // The switch control is subject to the selected type.
                   }, (error: BusinessError) => {
                     if (error) {
                       console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
                       return;
                     }
                     console.info('Succeed in starting vibration');
                   });
                 } catch (err) {
                   let e: BusinessError = err as BusinessError;
                   console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
                 } finally {
                   vibrator.stopVibration();
                   this.uiContext.getHostContext()?.resourceManager.closeRawFdSync(fileName);
                 }
               }
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```

3. Trigger vibration based on a specified duration.

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   try {
     vibrator.startVibration({
       type: 'time',
       duration: 1000,
     }, {
       id: 0,
       usage: 'alarm' // The switch control is subject to the selected type.
     }, (error: BusinessError) => {
       if (error) {
         console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
         return;
       }
       console.info('Succeed in starting vibration');
     });
   } catch (err) {
     let e: BusinessError = err as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```

## vibrator.startVibration<sup>9+</sup>

startVibration(effect: VibrateEffect, attribute: VibrateAttribute): Promise&lt;void&gt;

Starts vibration with the specified effect and attribute. This API uses a promise to return the result.

This method is applicable to interactive tactile feedback, event vibration notifications, and immersive vibration scenarios such as games and multimedia. If this API is called successfully, the promise returns no value through **resolve**. If the call fails, the promise returns an error object through **reject**. If the same vibrator is already vibrating, the new request will be processed based on the system priority rules. The **vibrator.startVibration** (**#vibratorstartvibration9**) is also provided when the API uses a callback to return the result. You can choose either version based on your preference for the callback style.

**Required permissions**: ohos.permission.VIBRATE

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name   | Type                                  | Mandatory| Description                                                        |
| --------- | -------------------------------------- | ---- | ------------------------------------------------------------ |
| effect    | [VibrateEffect](#vibrateeffect9)       | Yes  | Vibration effect. The following options are supported:<br>1. [VibratePreset](#vibratepreset9): triggers vibration according to preset vibration effects. This mode is suitable for short vibration scenarios in interactive feedback (such as tapping, long-pressing, sliding, dragging, etc.). This API is recommended to maintain consistency with the system's overall vibration feedback experience.<br>2. [VibrateFromFile](#vibratefromfile10): triggers vibration according to custom vibration configuration file. This mode is suitable for interactive feedback in complex scenarios requiring precise vibration patterns (such as realistic effects triggered by emoji packs, or feedback for in-game actions/mechanics).<br>3. [VibrateTime](#vibratetime9): triggers vibration of the specified duration, providing basic control over the start and stop of vibration. This mode does not support customization of vibration intensity, frequency, or other parameters. As a result, the vibration adjustment is relatively coarse and not suitable for delivering a refined experience.<br>4. [VibrateFromPattern<sup>18+</sup>](#vibratefrompattern18): starts vibration according to a custom vibration pattern. The usage scenario is the same as **VibrateFromFile**. **VibrateFromFile** utilizes predefined effects in a custom configuration file, passing specific vibration events to the API via file descriptors. By contrast, **VibrateFromPattern** enables more flexible vibration event combinations, delivering them to the API as a vibration event array.|
| attribute | [VibrateAttribute](#vibrateattribute9) | Yes  | Vibration attribute, which specifies the vibrator ID, device ID, and vibration usage scenario. The **usage** parameter in **attribute** determines the vibration scenario type. Different scenario types are controlled by different system vibration switch rules. You need to select a proper value for **usage** based on the actual service scenario.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. If the API is called successfully, the promise returns a value through **resolve**, indicating that the vibration is started successfully. If the call fails, the promise returns an error object through **reject**. The error object contains the error code and error message, which can be used to locate the cause of the vibration startup failure.|

**Error codes**

For details about the error codes, see [Vibrator Error Codes](errorcode-vibrator.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 801      | Capability not supported.                                    |
| 14600101 | Device operation failed.                                     |

**Example**

1. Trigger vibration based on a preset effect.

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   
   // Use try catch to capture possible exceptions.
   try {
     // Check whether 'haptic.notice.success' is supported.
     vibrator.isSupportEffect('haptic.notice.success').then((state: boolean) => {
       console.info('Succeed in querying effect');
       if (state) {
         try {
           vibrator.startVibration({
             type: 'preset',
             effectId: 'haptic.notice.success',
             count: 1,
           }, {
             usage: 'notification' // The switch control is subject to the selected type.
           }).then(() => {
             console.info('Succeed in starting vibration');
           }).catch((error: BusinessError) => {
             console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
           });
         } catch (err) {
           let e: BusinessError = err as BusinessError;
           console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
         }
       }
     }, (error: BusinessError) => {
       console.error(`Failed to query effect. Code: ${error.code}, message: ${error.message}`);
     })
   } catch (error) {
     let e: BusinessError = error as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```

2. Trigger vibration based on a custom vibration configuration file.

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { resourceManager } from '@kit.LocalizationKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   const fileName: string = 'xxx.json';

   @Entry
   @Component
   struct Index {
     uiContext = this.getUIContext();

     build() {
       Row() {
         Column() {
           Button('alarm-file')
             .onClick(() => {
               let rawFd: resourceManager.RawFileDescriptor | undefined = this.uiContext.getHostContext()?.resourceManager.getRawFdSync(fileName);
               if (rawFd != undefined) {
                 try {
                   vibrator.startVibration({
                     type: 'file',
                     hapticFd: { fd: rawFd.fd, offset: rawFd.offset, length: rawFd.length }
                   }, {
                     id: 0,
                     usage: 'alarm' // The switch control is subject to the selected type.
                   }).then(() => {
                     console.info('Succeed in starting vibration');
                   }).catch((error: BusinessError) => {
                     console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
                   });
                 } catch (err) {
                   let e: BusinessError = err as BusinessError;
                   console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
                 } finally {
                   vibrator.stopVibration();
                   this.uiContext.getHostContext()?.resourceManager.closeRawFdSync(fileName);
                 }
               }
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```

3. Trigger vibration based on a specified duration.

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   try {
     vibrator.startVibration({
       type: 'time',
       duration: 1000
     }, {
       id: 0,
       usage: 'alarm' // The switch control is subject to the selected type.
     }).then(() => {
       console.info('Succeed in starting vibration');
     }, (error: BusinessError) => {
       console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
     });
   } catch (err) {
     let e: BusinessError = err as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```

## vibrator.stopVibration<sup>9+</sup>

stopVibration(stopMode: VibratorStopMode, callback: AsyncCallback&lt;void&gt;): void

Stops vibration in the specified mode. If the API is called successfully, the vibrator stops vibrating in the specified mode. This API uses an asynchronous callback to return the result.

The value of **stopMode** must match the **VibrateEffect** type used to start vibration. **VIBRATOR_STOP_MODE_TIME** is used to stop vibration of the **VibrateTime** type, and **VIBRATOR_STOP_MODE_PRESET** is used to stop vibration of the **VibratePreset** type. Otherwise, the stop operation may be invalid. If the API is called successfully, the vibration in the specified mode stops. If no vibration is in progress, a success message is returned. This API cannot stop custom vibration (**VibrateFromFile** and **VibrateFromPattern**). To stop custom vibration or vibration in all modes, use **vibrator.stopVibration** (**#vibratorstopvibration10**).

**Required permissions**: ohos.permission.VIBRATE

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name  | Type                                 | Mandatory| Description                                                        |
| -------- | ------------------------------------- | ---- | ------------------------------------------------------------ |
| stopMode | [VibratorStopMode](#vibratorstopmode) | Yes  | Specified vibration stop mode, which is used to stop vibration in the specified mode. The following modes are supported:<br>- **VIBRATOR_STOP_MODE_TIME**: used to stop vibration of the [VibrateTime](#vibratetime9) type with the specified duration.<br>- **VIBRATOR_STOP_MODE_PRESET**: used to stop vibration of the [VibratePreset](#vibratepreset9) type with the preset effect.<br>To stop custom vibration ([VibrateFromFile](#vibratefromfile10) and [VibrateFromPattern](#vibratefrompattern18)), use [vibrator.stopVibration<sup>10+</sup>](#vibratorstopvibration10). The value of **stopMode** must match the **VibrateEffect** type used to start vibration. Otherwise, the stop operation may fail.|
| callback | AsyncCallback&lt;void&gt;             | Yes  | Callback used to return the result. If the vibration stops, **err** is **undefined**; otherwise, **err** is an error object. The callback result can be used to check whether the vibration is stopped successfully.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

1. Stop vibration of the specified duration.

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   // Use try catch to capture possible exceptions.
   try {
     // Start vibration of the specified duration.
     vibrator.startVibration({
       type: 'time',
       duration: 1000,
     }, {
       id: 0,
       usage: 'alarm' // The switch control is subject to the selected type.
     }, (error: BusinessError) => {
       if (error) {
         console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
         return;
       }
       console.info('Succeed in starting vibration');
     });
   } catch (err) {
     let e: BusinessError = err as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }

   try {
     // Stop vibration in VIBRATOR_STOP_MODE_TIME mode.
     vibrator.stopVibration(vibrator.VibratorStopMode.VIBRATOR_STOP_MODE_TIME, (error: BusinessError) => {
       if (error) {
         console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
         return;
       }
       console.info('Succeed in stopping vibration');
     })
   } catch (err) {
     let e: BusinessError = err as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```

2. Stop preset vibration.

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   try {
     // Start vibration based on a preset effect.
     vibrator.startVibration({
       type: 'preset',
       effectId: 'haptic.notice.success',
       count: 1,
     }, {
       id: 0,
       usage: 'notification' // The switch control is subject to the selected type.
     }, (error: BusinessError) => {
       if (error) {
         console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
         return;
       }
       console.info('Succeed in starting vibration');
     });
   } catch (err) {
     let e: BusinessError = err as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }

   try {
     // Stop vibration in VIBRATOR_STOP_MODE_PRESET mode.
     vibrator.stopVibration(vibrator.VibratorStopMode.VIBRATOR_STOP_MODE_PRESET, (error: BusinessError) => {
       if (error) {
         console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
         return;
       }
       console.info('Succeed in stopping vibration');
     })
   } catch (err) {
     let e: BusinessError = err as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```

## vibrator.stopVibration<sup>9+</sup>

stopVibration(stopMode: VibratorStopMode): Promise&lt;void&gt;

Stops vibration in the specified mode. If the API is called successfully, the vibrator stops vibrating in the specified mode. This API uses a promise to return the result.

Stops the vibration of the specified duration triggered by **VibrateTime** or the preset vibration triggered by **VibratePreset**. If the API is called successfully, the promise returns a value through **resolve**. If the API fails to be called, an error object is returned. If no vibration is in progress, a success message is returned. To stop custom vibration (**VibrateFromFile** and **VibrateFromPattern**), use **vibrator.stopVibration** (**#vibratorstopvibration10-1**). The value of **stopMode** must match the type of **VibrateEffect** used to start the vibration. Otherwise, the vibration cannot be stopped. **VibrateTime** corresponds to **VIBRATOR_STOP_MODE_TIME**, and **VibratePreset** corresponds to **VIBRATOR_STOP_MODE_PRESET**.

**Required permissions**: ohos.permission.VIBRATE

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name  | Type                                 | Mandatory| Description                                                        |
| -------- | ------------------------------------- | ---- | ------------------------------------------------------------ |
| stopMode | [VibratorStopMode](#vibratorstopmode) | Yes  | Specified vibration stop mode, which is used to stop vibration in the specified mode. The following modes are supported:<br>- **VIBRATOR_STOP_MODE_TIME**: used to stop vibration of the [VibrateTime](#vibratetime9) type with the specified duration.<br>- **VIBRATOR_STOP_MODE_PRESET**: used to stop vibration of the [VibratePreset](#vibratepreset9) type with the preset effect.<br>To stop custom vibration ([VibrateFromFile](#vibratefromfile10) and [VibrateFromPattern](#vibratefrompattern18)), use [vibrator.stopVibration<sup>10+</sup>](#vibratorstopvibration10-1). The value of **stopMode** must match the **VibrateEffect** type used to start vibration. Otherwise, the stop operation may fail.|

**Return value**

| Type               | Description         |
| ------------------- | ------------- |
| Promise&lt;void&gt; | Promise that returns the result. If the API is called successfully, the promise returns a value through **resolve**, indicating that the vibration is stopped successfully. If the call fails, the promise returns an error object through **reject**. The error object contains the error code and error message, which can be used to locate the cause of the vibration stop failure.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

1. Stop vibration of the specified duration.

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   // Use try catch to capture possible exceptions.
   try {
     // Start vibration of the specified duration.
     vibrator.startVibration({
       type: 'time',
       duration: 1000,
     }, {
       id: 0,
       usage: 'alarm' // The switch control is subject to the selected type.
     }).then(() => {
       console.info('Succeed in starting vibration');
     }, (error: BusinessError) => {
       console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
     });
   } catch (err) {
     let e: BusinessError = err as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }

   try {
     // Stop vibration in VIBRATOR_STOP_MODE_TIME mode.
     vibrator.stopVibration(vibrator.VibratorStopMode.VIBRATOR_STOP_MODE_TIME).then(() => {
       console.info('Succeed in stopping vibration');
     }, (error: BusinessError) => {
       console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
     });
   } catch (err) {
     let e: BusinessError = err as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```

2. Stop preset vibration.

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   
   try {
     // Start vibration based on a preset effect.
     vibrator.startVibration({
       type: 'preset',
       effectId: 'haptic.notice.success',
       count: 1,
     }, {
       id: 0,
       usage: 'notification' // The switch control is subject to the selected type.
     }).then(() => {
       console.info('Succeed in starting vibration');
     }, (error: BusinessError) => {
       console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
     });
   } catch (err) {
     let e: BusinessError = err as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }

   try {
     // Stop vibration in VIBRATOR_STOP_MODE_PRESET mode.
     vibrator.stopVibration(vibrator.VibratorStopMode.VIBRATOR_STOP_MODE_PRESET).then(() => {
       console.info('Succeed in stopping vibration');
     }, (error: BusinessError) => {
       console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
     });
   } catch (err) {
     let e: BusinessError = err as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```

## vibrator.stopVibration<sup>10+</sup>

stopVibration(callback: AsyncCallback&lt;void&gt;): void

Stops vibration in all modes. If the API is called successfully, the vibrator stops vibrating. This API uses an asynchronous callback to return the result.

This method is used to stop all types of vibration on the device (including **VibrateTime**, **VibratePreset**, **VibrateFromFile**, and **VibrateFromPattern**). This API is applicable to scenarios where all types of vibration need to be stopped immediately, such as when an app exits or a page is switched. Unlike **vibrator.stopVibration** (**#vibratorstopvibration9**) which requires the stop mode to be specified, this method does not require the stop mode to be specified and can stop all types of vibration, including custom vibration.

**Required permissions**: ohos.permission.VIBRATE

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name  | Type                     | Mandatory| Description                                                        |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the vibrator stops vibration successfully, **err** is **undefined**; otherwise, **err** is an error object, which contains the error code and error information. The callback result can be used to check whether all types of vibration are stopped successfully.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |

**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   // Use try catch to capture possible exceptions.
   try {
     // Stop vibration in all modes.
     vibrator.stopVibration((error: BusinessError) => {
       if (error) {
         console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
         return;
       }
       console.info('Succeed in stopping vibration');
     })
   } catch (error) {
     let e: BusinessError = error as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```

## vibrator.stopVibration<sup>10+</sup>

stopVibration(): Promise&lt;void&gt;

Stops vibration in all modes. If the API is called successfully, the vibrator stops vibrating. This API uses a promise to return the result.

This method is used to stop all types of vibration on the device (including **VibrateTime**, **VibratePreset**, **VibrateFromFile**, and **VibrateFromPattern**). This API is applicable to scenarios where all types of vibration need to be stopped immediately, such as when an app exits or a page is switched. If the API is called successfully, the promise returns a value through **resolve**. If the operation fails, an error object is returned. Unlike **vibrator.stopVibration** (**#vibratorstopvibration9-1**) which requires the stop mode to be specified, this method does not require the stop mode to be specified and can stop all types of vibration, including custom vibration.

**Required permissions**: ohos.permission.VIBRATE

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.MiscDevice

**Return value**

| Type               | Description         |
| ------------------- | ------------- |
| Promise&lt;void&gt; | Promise that returns the result. If the API is called successfully, the promise returns a value through **resolve**, indicating that all types of vibration are stopped successfully. If the call fails, the promise returns an error object through **reject**. The error object contains the error code and error message, which can be used to locate the cause of the vibration stop failure.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |

**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   // Use try catch to capture possible exceptions.
   try {
     // Stop vibration in all modes.
     vibrator.stopVibration().then(() => {
       console.info('Succeed in stopping vibration');
     }, (error: BusinessError) => {
       console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
     });
   } catch (error) {
     let e: BusinessError = error as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```

## vibrator.stopVibration<sup>19+</sup>

stopVibration(param?: VibratorInfoParam): Promise&lt;void&gt;

Stops vibration of a specified device. If no parameters are passed, this API stops all vibrators of the local device by default. This API uses a promise to return the result.

This method is used to stop vibration of a specified device or vibrator in a multi-device and multi-vibrator scenario. If no parameter is passed, this API stops all vibrators of the local device by default. If **VibratorInfoParam** is passed, a specific vibrator of a remote device can be specified. If the API is called successfully, the promise returns a value through **resolve**. If the operation fails, an error object is returned. Compared with **vibrator.stopVibration** (**#vibratorstopvibration10-1**) with no parameters passed, this API adds the optional parameter **VibratorInfoParam** to specify the vibrator to stop. **vibrator.stopVibration** stops all vibrators of the local device.

**Required permissions**: ohos.permission.VIBRATE

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name  | Type                                                        | Mandatory| Description                               |
| -------- | ------------------------------------------------------------ | ---- |-----------------------------------|
| param     | [VibratorInfoParam](#vibratorinfoparam19)                       | No  | Information about the device and vibrator whose vibration needs to be stopped. If no parameter is passed, all types of vibration on the local device is stopped by default. The default value of **deviceId** is **-1** (local device), and the default value of **vibratorId** is **0** (all vibrators on the device). You can obtain the values of **deviceId** and **vibratorId** by calling [vibrator.getVibratorInfoSync](#vibratorgetvibratorinfosync19) or [vibrator.on](#vibratoron19).|

**Return value**

| Type               | Description         |
| ------------------- | ------------- |
| Promise&lt;void&gt; | Promise that returns the result. If the API is called successfully, the promise returns a value through **resolve**, indicating that the vibration of a specified device is stopped successfully. If the call fails, the promise returns an error object through **reject**. The error object contains the error code and error message, which can be used to locate the cause of the vibration stop failure.|

**Error codes**

For details about the error codes, see [Vibrator Error Codes](errorcode-vibrator.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 14600101 | Device operation failed. |

**Example**

  ```ts
  import { vibrator } from '@kit.SensorServiceKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  function vibratorDemo() {
    // Query information about all vibrators.
    const vibratorInfoList: vibrator.VibratorInfo[] = vibrator.getVibratorInfoSync();
    // Obtain the target vibrator based on the actual service logic. The following example shows how to obtain the local vibrator. You need to adjust the filtering logic as required.
    const targetVibrator = vibratorInfoList.find((vibrator: vibrator.VibratorInfo) => {
      return vibrator.isLocalVibrator;
    });
    if (!targetVibrator) {
      return;
    }
    // Call vibrator.startVibration to start vibration.
    // ...

    // Use try catch to capture possible exceptions.
    try {
      // Stop the vibration based on the actual service scenario.
      vibrator.stopVibration({ deviceId: targetVibrator.deviceId, vibratorId: targetVibrator.vibratorId }).then(() => {
        console.info('Succeed in stopping vibration');
      }, (error: BusinessError) => {
        console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
      });
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
    }
  }
  ```

## vibrator.stopVibrationSync<sup>12+</sup>

stopVibrationSync(): void

Stops any form of vibrator vibration. If the API is called successfully, the vibrator stops vibrating. This API is a synchronous API. It blocks the main thread until the vibration stops, which may affect UI interaction. Exercise caution when using this API.

Use this API when you need to stop all types of vibration immediately and do not care about the asynchronous callback result. This API is suitable for scenarios that require high real-time performance (for example, emergency vibration interruption). After the API is called successfully, all ongoing vibrator vibration on the device stops immediately. If the call fails, an exception will be thrown. You need to use **try catch** to catch the exception. Compared with the asynchronous version [vibrator.stopVibration](#vibratorstopvibration10-1), this API is a synchronous API that directly returns the result without a callback, but it will block the main thread. You are advised to use this API in a non-UI thread or preferentially use the asynchronous version in the UI thread to avoid affecting interaction response.

**Required permissions**: ohos.permission.VIBRATE

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Sensors.MiscDevice

**Error codes**

For details about the error codes, see [Vibrator Error Codes](errorcode-vibrator.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                |
| -------- | ------------------------ |
| 201      | Permission denied.       |
| 14600101 | Device operation failed. |

**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   // Use try catch to capture possible exceptions.
   try {
     // Stop any form of vibrator vibration.
     vibrator.stopVibrationSync();
     console.info('Succeed in stopping vibration');
   } catch (error) {
     let e: BusinessError = error as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```

## vibrator.isSupportEffect<sup>10+</sup>

isSupportEffect(effectId: string, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether the current device supports the preset vibration effect specified by the effect ID. This API uses an asynchronous callback to return the result.

This API is used when you need to check whether the current device supports the specified preset vibration effect before triggering the effect. Different devices may have different preset vibration effects. Therefore, you are advised to call this API to query the preset vibration effect before using the **VibratePreset** type of [vibrator.startVibration](#vibratorstartvibration9) to avoid poor vibration effect on unsupported devices. After the API is successfully called, a boolean value is returned through the callback. If **true** is returned, the device supports the effect ID and can directly use it in **startVibration**. If **false** is returned, the device does not support the effect ID. In this case, using the effect ID to trigger vibration may result in poor effect or no vibration.

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name  | Type                        | Mandatory| Description                                                       |
| -------- | ---------------------------- | ---- | ----------------------------------------------------------- |
| effectId | string                       | Yes  | ID of the preset vibration effect to be confirmed. The value can contain a maximum of 64 characters. If the length exceeds 64 characters, the first 64 characters are used. Use scenarios: The preset vibration effects may vary depending on the device. You need to pass the specific effect ID to check whether the effect is supported. For details about the values, see [EffectId](#effectid) and [HapticFeedback](#hapticfeedback12).|
| callback | AsyncCallback&lt;boolean&gt; | Yes  | Callback used to return the result. If **true** is returned, the device supports the effect ID and the effect ID can be used in [startVibration](#vibratorstartvibration9). If **false** is returned, the device does not support the effect ID, and using the effect ID to trigger vibration may result in poor effect.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   // Use try catch to capture possible exceptions.
   try {
     // Check whether 'haptic.notice.success' is supported.
     vibrator.isSupportEffect('haptic.notice.success', (err: BusinessError, state: boolean) => {
       if (err) {
         console.error(`Failed to query effect. Code: ${err.code}, message: ${err.message}`);
         return;
       }
       console.info('Succeed in querying effect');
       if (state) {
         try {
           // To use startVibration, you must configure the ohos.permission.VIBRATE permission.
           vibrator.startVibration({
             type: 'preset',
             effectId: 'haptic.notice.success',
             count: 1,
           }, {
             usage: 'unknown' // The switch control is subject to the selected type.
           }, (error: BusinessError) => {
             if (error) {
               console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
             } else {
               console.info('Succeed in starting vibration');
             }
           });
         } catch (error) {
           let e: BusinessError = error as BusinessError;
           console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
         }
       }
     })
   } catch (error) {
     let e: BusinessError = error as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```

## vibrator.isSupportEffect<sup>10+</sup>

isSupportEffect(effectId: string): Promise&lt;boolean&gt;

Checks whether the current device supports the preset vibration effect specified by the effect ID. This API uses a promise to return the result.

This API is used when you need to check whether the current device supports the specified preset vibration effect before triggering the effect. The functionality is the same as the callback version. You can choose either based on your preference for the asynchronous callback style. If the API is called successfully, the promise returns a boolean value through **resolve**. The **value** true indicates that the device supports the specified effect ID, while the value **false** indicates the opposite. In this case, using the effect ID to trigger vibration may result in poor effect or no vibration.

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name  | Type  | Mandatory| Description                  |
| -------- | ------ | ---- | ---------------------- |
| effectId | string | Yes  | ID of the preset vibration effect to be confirmed. The value can contain a maximum of 64 characters. If the length exceeds 64 characters, the first 64 characters are used. Use scenarios: The preset vibration effects may vary depending on the device. You need to pass the specific effect ID to check whether the effect is supported. For details about the values, see [EffectId](#effectid) and [HapticFeedback](#hapticfeedback12).|

**Return value**

| Type                  | Description                                                        |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise that returns the result. If **true** is returned, the device supports the effect ID and the effect ID can be used in [startVibration](#vibratorstartvibration9-1). If **false** is returned, the device does not support the effect ID, and using the effect ID to trigger vibration may result in poor effect.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   // Use try catch to capture possible exceptions.
   try {
     // Check whether 'haptic.notice.success' is supported.
     vibrator.isSupportEffect('haptic.notice.success').then((state: boolean) => {
       console.info(`The query result is ${state}`);
       if (state) {
         try {
           vibrator.startVibration({
             type: 'preset',
             effectId: 'haptic.notice.success',
             count: 1,
           }, {
             usage: 'unknown' // The switch control is subject to the selected type.
           }).then(() => {
             console.info('Succeed in starting vibration');
           }).catch((error: BusinessError) => {
             console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
           });
         } catch (error) {
           let e: BusinessError = error as BusinessError;
           console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
         }
       }
     }, (error: BusinessError) => {
       console.error(`Failed to query effect. Code: ${error.code}, message: ${error.message}`);
     })
   } catch (error) {
     let e: BusinessError = error as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```

## vibrator.isSupportEffectSync<sup>12+</sup>

isSupportEffectSync(effectId: string): boolean

Checks whether the current device supports the preset vibration effect. This API is a synchronous API. It blocks the main thread until the query is complete, which may affect UI interaction. Exercise caution when using this API.

This API is used when you need to check whether the current device supports the specified preset vibration effect immediately before triggering the effect. This API is applicable to scenarios that have high requirements for real-time performance and simple query logic. The boolean result is returned. If **true** is returned, the device supports the effect ID and the effect ID can be used in [startVibration](#vibratorstartvibration9). If **false** is returned, the device does not support the effect ID, and using the effect ID to trigger vibration may result in poor effect or no vibration. Compared with the asynchronous version [vibrator.isSupportEffect](#vibratorissupporteffect10), this API is a synchronous API that directly returns the result without a callback, but it will block the main thread. You are advised to use this API in a non-UI thread or preferentially use the asynchronous version in the UI thread to avoid affecting interaction response.

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name  | Type  | Mandatory| Description                  |
| -------- | ------ | ---- | ---------------------- |
| effectId | string | Yes  | ID of the preset vibration effect to be confirmed. The value can contain a maximum of 64 characters. If the length exceeds 64 characters, the first 64 characters are used. Use scenarios: The preset vibration effects may vary depending on the device. You need to pass the specific effect ID to check whether the effect is supported. For details about the values, see [EffectId](#effectid) and [HapticFeedback](#hapticfeedback12).|

**Return value**

| Type   | Description                                                       |
| ------- | ----------------------------------------------------------- |
| boolean | Returned object. If **true** is returned, the device supports the effect ID and the effect ID can be used in [startVibration](#vibratorstartvibration9). If **false** is returned, the device does not support the effect ID, and using the effect ID to trigger vibration may result in poor effect or no vibration.|

**Error codes**

For details about the error codes, see [Vibrator Error Codes](errorcode-vibrator.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14600101 | Device operation failed.                                     |

**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   // Use try catch to capture possible exceptions.
   try {
     // Check whether the preset 'haptic.notice.success' is supported.
     let ret = vibrator.isSupportEffectSync('haptic.notice.success');
     console.info(`The query result is ${ret}`);
   } catch (error) {
     let e: BusinessError = error as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```

## vibrator.getEffectInfoSync<sup>19+</sup>

getEffectInfoSync(effectId: string, param?: VibratorInfoParam): EffectInfo

Obtains the preset vibration effect based on the device ID and vibrator ID to determine whether the preset vibration effect is supported by the specified vibrator of the specified device.

This method is used to check whether a specified vibrator of a specified device supports a preset vibration effect in a multi-device and multi-vibrator scenario. If **param** is not passed, the local device is queried by default. This method is used to check the availability of the effect before triggering vibration, preventing poor vibration effects on devices or vibrators that do not support the effect. The **EffectInfo** object is returned. The **isEffectSupported** field indicates whether the preset vibration effect is supported. If **true** is returned, the effect can be directly used in **startVibration** (**#vibratorstartvibration9**). If **false** is returned, using the effect ID to trigger vibration may result in poor effect. To query whether a preset vibration effect is supported across devices, use **getEffectInfoSync**. To query whether a preset vibration effect is supported on the local device, use **isSupportEffect**.

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name  | Type                                                        | Mandatory| Description                         |
| -------- | ------------------------------------------------------------ | ---- |-----------------------------|
| effectId | string | Yes  | ID of the preset vibration effect to be confirmed. The value can contain a maximum of 64 characters. If the length exceeds 64 characters, the first 64 characters are used. Use scenarios: The preset vibration effects may vary depending on the device. You need to pass the specific effect ID to check whether the effect is supported. For details about the values, see [EffectId](#effectid) and [HapticFeedback](#hapticfeedback12).|
| param     | [VibratorInfoParam](#vibratorinfoparam19)                       | No  | Information about the device and vibrator to be queried. If **param** is not specified, the local device is queried by default. The default value of **deviceId** is **-1** (local device), and the default value of **vibratorId** is **0** (all vibrators on the device). You can obtain the values of **deviceId** and **vibratorId** by calling [vibrator.getVibratorInfoSync](#vibratorgetvibratorinfosync19) or [vibrator.on](#vibratoron19).|

**Error codes**

For details about the error codes, see [Vibrator Error Codes](errorcode-vibrator.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                |
| -------- | ------------------------ |
| 14600101 | Device operation failed. |

**Return value**

| Type   | Description                                                     |
| ------- | --------------------------------------------------------- |
| [EffectInfo](#effectinfo19) | Preset vibration effect information. If the value of **isEffectSupported** is **true**, the effect is supported and can be used in [startVibration](#vibratorstartvibration9). If the value is **false**, the effect is not supported and using the effect ID to trigger vibration may result in poor effect.|


**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   // Use try catch to capture possible exceptions.
   try {
     const effectInfo: vibrator.EffectInfo = vibrator.getEffectInfoSync('haptic.clock.timer', { deviceId: 1, vibratorId: 3});
     console.info(`isEffectSupported: ${effectInfo.isEffectSupported}`);
   } catch (error) {
     let e: BusinessError = error as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```


## vibrator.getVibratorInfoSync<sup>19+</sup>

getVibratorInfoSync(param?: VibratorInfoParam): Array&lt;VibratorInfo&gt;;

Queries the vibrator list of one or all devices. This method is used to query the vibrator capabilities of a device and the vibrator IDs of a multi-vibrator device before triggering vibration, so that a proper vibrator can be selected to trigger vibration.

If **param** is not specified, the vibrator information of all devices is queried. If **VibratorInfoParam** is passed, the vibrator information of a specified device or vibrator is queried. A **VibratorInfo** array is returned, which contains attributes such as **deviceId**, **vibratorId**, **deviceName**, **isHdHapticSupported**, and **isLocalVibrator**. This array can be used to specify the vibrator and device in **startVibration** (**#vibratorstartvibration9**) and **stopVibration** (**#vibratorstopvibration19**).

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name  | Type                                     | Mandatory| Description                               |
| -------- |-----------------------------------------| ---- |-----------------------------------|
| param     | [VibratorInfoParam](#vibratorinfoparam19) | No  | Information about the device and vibrator to be queried. If **param** is not specified, information about all vibrators of all devices is queried by default. The default value of **deviceId** is **-1**, indicating all devices are queried. The default value of **vibratorId** is **0**, indicating all vibrators of the device are queried.|

**Return value**

| Type                           | Description                                                     |
|-------------------------------| --------------------------------------------------------- |
| Array&lt;[VibratorInfo](#vibratorinfo19)&gt; | Array of vibrator information. Each element contains attributes such as **deviceId**, **vibratorId**, **deviceName**, **isHdHapticSupported**, and **isLocalVibrator**, which can be used to select a proper vibrator to trigger vibration or determine the vibration capability of the device.|


**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   try {
     const vibratorInfoList: vibrator.VibratorInfo[] = vibrator.getVibratorInfoSync({ deviceId: 1, vibratorId: 3 });
     console.info(`vibratorInfoList: ${JSON.stringify(vibratorInfoList)}`);
   } catch (error) {
     let e: BusinessError = error as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```


## vibrator.on<sup>19+</sup>

on(type: 'vibratorStateChange', callback: Callback&lt;VibratorStatusEvent&gt;): void

Enables listening for vibrator status changes. The callback is triggered when a vibrator goes online or offline.

Use this API when you need to detect vibrator status changes in real time. This API is used to dynamically obtain vibrator information in distributed multi-device scenarios, so that vibration can be triggered in a timely manner when a vibrator goes online or stopped when it goes offline. After the registration is successful, when a vibrator goes online or offline, the system calls back the **VibratorStatusEvent** object, which contains information such as the device ID, number of vibrators, and online/offline status. The device ID obtained in the callback can be used in APIs such as [startVibration](#vibratorstartvibration9) and [stopVibration](#vibratorstopvibration19) to specify the target device.

After the callback is registered, call [vibrator.off](#vibratoroff19) at a proper time to unregister the callback to avoid memory leaks. If the same callback is repeatedly registered for the same type, the callback will not be overwritten. You need to call **vibrator.off** first, and then **vibrator.on**.

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                       |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | string                       | Yes  | Event type. The value is fixed at **vibratorStateChange**, indicating the vibrator status change event.             |
| callback | Callback&lt;[VibratorStatusEvent](#vibratorstatusevent19)&gt; | Yes  | Callback used to return the result. This callback is triggered when a vibrator goes online or offline. The callback parameter is a **VibratorStatusEvent** object, which contains information such as **timestamp**, **deviceId**, **vibratorCount**, and **isVibratorOnline**. The device ID obtained in the callback can be used in APIs such as [startVibration](#vibratorstartvibration9) and [stopVibration](#vibratorstopvibration19) to specify the target device.|

**Error codes**

For details about the error codes, see [Vibrator Error Codes](errorcode-vibrator.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                |
| -------- | ------------------------ |
| 14600101 | Device operation failed. |


**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   // Callback
   const vibratorStateChangeCallback = (data: vibrator.VibratorStatusEvent) => {
     console.info('vibrator state callback info:', JSON.stringify(data));
   }

   // Use try catch to capture possible exceptions.
   try {
     // Subscribe to vibratorStateChange events.
     vibrator.on('vibratorStateChange', vibratorStateChangeCallback);
   } catch (error) {
     let e: BusinessError = error as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```


## vibrator.off<sup>19+</sup>

off(type: 'vibratorStateChange', callback?: Callback&lt;VibratorStatusEvent&gt;): void

Disables listening for vibrator status changes.

Use this API to unregister the callback when you no longer need to listen for vibrator status changes. If a **callback** value is passed, the specified callback is unregistered. If no **callback** value is passed, all registered callbacks of the specified type are unregistered. After the callback is unregistered, the corresponding callback function will not be triggered. If the passed **callback** has not been registered, the unregistration operation is invalid but no error is reported. The callback can be unregistered only after being registered using [vibrator.on](#vibratoron19). If the same callback is repeatedly registered for the same type, the callback will not be overwritten. You need to call **vibrator.off** first, and then **vibrator.on**.

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                       |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | string                       | Yes  | Event type. The value is fixed at **vibratorStateChange**, indicating the vibrator status change event.             |
| callback | Callback&lt;[VibratorStatusEvent](#vibratorstatusevent19)&gt; | No  | Callback to be unregistered. If this parameter is not passed, all callbacks of the **vibratorStateChange** type are unregistered. Use scenarios: If only a specific callback needs to be unregistered, pass the corresponding **callback**. If all callbacks need to be unregistered, do not pass this parameter.|

**Error codes**

For details about the error codes, see [Vibrator Error Codes](errorcode-vibrator.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                |
| -------- | ------------------------ |
| 14600101 | Device operation failed. |


**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   // Callback
   const vibratorStateChangeCallback = (data: vibrator.VibratorStatusEvent) => {
     console.info('vibrator state callback info:', JSON.stringify(data));
   }
   // Use try catch to capture possible exceptions.
   try {
     // Unsubscribe from specified vibratorStateChange events.
     vibrator.off('vibratorStateChange', vibratorStateChangeCallback);
     // Unsubscribe from all vibratorStateChange events.
     // vibrator.off('vibratorStateChange');
   } catch (error) {
     let e: BusinessError = error as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```


## VibratorStatusEvent<sup>19+</sup>

Defines the vibrator status change event. This object is passed through the [vibrator.on](#vibratoron19) callback when a vibrator goes online or offline.

**System capability**: SystemCapability.Sensors.MiscDevice


| Name              | Type     | Read-Only| Optional| Description                              |
|------------------|---------|----|----|----------------------------------|
| timestamp        | number  | No | No | Event timestamp, in ms.                       |
| deviceId         | number  | No | No | Device ID. It can be used in APIs such as [startVibration](#vibratorstartvibration9) and [stopVibration](#vibratorstopvibration19) to specify the target device.                          |
| vibratorCount    | number  | No | No | Number of vibrators on the device.                      |
| isVibratorOnline | boolean | No | No | Whether a vibrator is online. The value **true** indicates that the vibrator is online and can be used to trigger vibration. The value **false** indicates that the vibrator is offline and cannot be used.|


## VibratorInfoParam<sup>19+</sup>

Defines the vibrator parameters. This API defines information about the device and vibrator to be queried or controlled. If **VibratorInfoParam** is left unspecified, an API applies to all vibrators of the local device by default.

**System capability**: SystemCapability.Sensors.MiscDevice


| Name| Type  | Read-Only| Optional| Description                                                        |
| ---- | ------ | ---- | ---- |------------------------------------------------------------|
| deviceId    | number | No  | Yes  | Device ID. The default value is **-1**, which indicates the local device. Use scenarios: This parameter is used when a remote device needs to be specified in a multi-device scenario. If this parameter is not set, the local device is controlled by default. Since API version 19, the device ID can be obtained by calling [getVibratorInfoSync](#vibratorgetvibratorinfosync19) or [on](#vibratoron19).|
| vibratorId    | number | No  | Yes  | Vibrator ID. The default value is **0**, indicating all vibrators on the device. Use scenarios: This parameter is used when a vibrator needs to be specified on a device with multiple vibrators. If this parameter is not specified, all vibrators on the device are controlled by default. Since API version 19, the vibrator ID can be obtained by calling [getVibratorInfoSync](#vibratorgetvibratorinfosync19) or [on](#vibratoron19).    |



## EffectInfo<sup>19+</sup>

Defines the preset effect. This object is returned through [vibrator.getEffectInfoSync](#vibratorgeteffectinfosync19), which is used to determine whether the preset vibration effect is supported by the specified vibrator of the specified device.

**System capability**: SystemCapability.Sensors.MiscDevice


| Name               | Type     | Read-Only| Optional| Description                           |
|-------------------|---------|----|----|-------------------------------|
| isEffectSupported | boolean | No | No | Whether a preset effect is supported. If the value is **true**, the preset effect is supported and can be used in [startVibration](#vibratorstartvibration9). If the value is **false**, the effect is not supported and using the effect ID to trigger vibration may result in poor effect.|


## VibratorInfo<sup>19+</sup>

Defines the vibrator information. This object is returned through[vibrator.getVibratorInfoSync](#vibratorgetvibratorinfosync19), which is to obtain the vibrator capabilities of the device and select a proper vibrator to trigger vibration.

**System capability**: SystemCapability.Sensors.MiscDevice

| Name                 | Type     | Read-Only| Optional| Description       |
|---------------------|---------|----|----|-----------|
| deviceId            | number  | No | No | Device ID. It can be used in APIs such as [startVibration](#vibratorstartvibration9) and [stopVibration](#vibratorstopvibration19) to specify the target device.    |
| vibratorId          | number  | No | No | Vibrator ID. It can be used in APIs such as [startVibration](#vibratorstartvibration9) and [stopVibration](#vibratorstopvibration19) to specify the target vibrator.    |
| deviceName          | string  | No | No | Device name.    |
| isHdHapticSupported | boolean | No | No | Whether HD vibration is supported. The value **true** indicates that HD vibration is supported and can be triggered by **VibrateFromFile** and **VibrateFromPattern**. The value **false** indicates that HD vibration is not supported, and using a custom vibration type may result in poor effect.|
| isLocalVibrator     | boolean | No | No | Whether the device is a local device. The value **true** indicates that the device is a local device, which can directly trigger vibration. The value **false** indicates that the device a remote device, which needs to be used in distributed scenarios.|


## vibrator.isHdHapticSupported<sup>12+</sup>

isHdHapticSupported(): boolean

Checks whether the device supports HD vibration.

This method is used to check whether the device supports HD vibration before triggering it, preventing poor vibration effects or error code 801 when **VibrateFromFile** or **VibrateFromPattern** is called on a device that does not support HD vibration. If **true** is returned, the device supports HD vibration, and you can use **VibrateFromFile** or **VibrateFromPattern** to trigger vibration. If **false** is returned, the device does not support HD vibration, and using a custom vibration type will return error code 801 or result in poor vibration effects.

**System capability**: SystemCapability.Sensors.MiscDevice

**Return value**

| Type   | Description                                                     |
| ------- | --------------------------------------------------------- |
| boolean | Whether HD vibration is supported. The value **true** indicates that HD vibration is supported, and the **VibrateFromFile** and **VibrateFromPattern** types can be used. **false** indicates that HD vibration is not supported. If a custom vibration type is used, error code 801 may be returned or the effect may be poor.|

**Error codes**

For details about the error codes, see [Vibrator Error Codes](errorcode-vibrator.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                |
| -------- | ------------------------ |
| 14600101 | Device operation failed. |

**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   // Use try catch to capture possible exceptions.
   try {
     // Check whether HD vibration is supported.
     let ret = vibrator.isHdHapticSupported();
     console.info(`The query result is ${ret}`);
   } catch (error) {
     let e: BusinessError = error as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```

## VibratorPatternBuilder<sup>18+</sup>

Provides methods for adding continuous and transient vibration events and generating a **VibratorPattern** object. Use process: Call [addContinuousEvent](#addcontinuousevent18) or [addTransientEvent](#addtransientevent18) to add vibration events, call [build](#build18) to generate a **VibratorPattern** object, and then pass the object as the **pattern** parameter of [VibrateFromPattern](#vibratefrompattern18) to [vibrator.startVibration](#vibratorstartvibration9) to trigger vibration.

This API is used when you need to flexibly combine vibration events (long vibration and short vibration) to create a custom vibration pattern. This API is applicable to interactive feedback scenarios that require dynamic arrangement of vibration events (such as realistic effects of emoji packs, or feedback for in-game actions). Compared with **VibrateFromFile**, which transfers vibration events using file descriptors, **VibratorPatternBuilder** transfers vibration events using vibration event arrays, supporting more flexible arrangement and combination of vibration events.

**System capability**: SystemCapability.Sensors.MiscDevice

### addContinuousEvent<sup>18+</sup>

addContinuousEvent(time: number, duration: number, options?: ContinuousParam): VibratorPatternBuilder;

Adds a long vibration event. After adding the event, use the build (#build18) method to generate a **VibratorPattern** (**#vibratorpattern18**) object.

Adds a continuous vibration event to a custom vibration pattern. This method is applicable to scenarios where continuous vibration feedback is required, such as engine vibration and haptic vibration. This API returns a **VibratorPatternBuilder** object, which allows you to call **addContinuousEvent** or **addTransientEvent** to add more vibration events.

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name  | Type                                 | Mandatory| Description                                                        |
| -------- | ------------------------------------- | ---- | ------------------------------------------------------------ |
| time     | number                                | Yes  | Start time of the long vibration event, in ms. The value must be an integer within the range of (0,1800000]. Use scenarios: Specify the start time of a long vibration event in the vibration sequence. The time values of multiple events cannot overlap.|
| duration | number                                | Yes  | Duration of the long vibration event, in ms. The value must be an integer within the range of (0,5000].|
| options  | [ContinuousParam](#continuousparam18) | No  | Optional parameters used to specify the vibration intensity, frequency, vibration adjustment curve, and channel ID of a long vibration event. If this parameter is left empty, the default values of the parameters are used (**100** for **intensity**, **50** for **frequency**, and **0** for **index**).                                    |

**Return value**

| Type                  | Description                                                |
| ---------------------- | ---------------------------------------------------- |
| VibratorPatternBuilder | **VibratorPatternBuilder** object representing a long vibration event. You can continue to chain call **addContinuousEvent** or **addTransientEvent** to add more vibration events, and then call [build](#build18) to generate a **VibratorPattern** object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message        |
| -------- | ---------------- |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   let builder = new vibrator.VibratorPatternBuilder();
   // Use try catch to capture possible exceptions.
   try {
     let pointsMe: vibrator.VibratorCurvePoint[] = [
       { time: 0, intensity: 0, frequency: -7 },
       { time: 42, intensity: 1, frequency: -6 },
       { time: 128, intensity: 0.94, frequency: -4 },
       { time: 217, intensity: 0.63, frequency: -14 },
       { time: 763, intensity: 0.48, frequency: -14 },
       { time: 1125, intensity: 0.53, frequency: -10 },
       { time: 1503, intensity: 0.42, frequency: -14 },
       { time: 1858, intensity: 0.39, frequency: -14 },
       { time: 2295, intensity: 0.34, frequency: -17 },
       { time: 2448, intensity: 0.21, frequency: -14 },
       { time: 2468, intensity: 0, frequency: -21 }
     ] // No less than four VibratorCurvePoint objects must be set. The maximum value is 16.
     let param: vibrator.ContinuousParam = {
       intensity: 97,
       frequency: 34,
       points:pointsMe,
       index: 0
     }
     builder.addContinuousEvent(0, 2468, param);
     console.info(`addContinuousEvent builder is ${builder.build()}`);
   } catch(error) {
     let e: BusinessError = error as BusinessError;
     console.error(`Failed to add continuous event. Code: ${e.code}, message: ${e.message}`);
   }
   ```

### addTransientEvent<sup>18+</sup>

addTransientEvent(time: number, options?: TransientParam): VibratorPatternBuilder;

Adds a transient vibration event. After the event is added, use the [build](#build18) method to generate a [VibratorPattern](#vibratorpattern18) object. This method is applicable to scenarios where short vibration feedback is required, such as clicks and key presses. It returns a **VibratorPatternBuilder** object, which supports chain calls to add more vibration events.

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name | Type                               | Mandatory| Description                                                        |
| ------- | ----------------------------------- | ---- | ------------------------------------------------------------ |
| time    | number                              | Yes  | Start time of the short vibration event, in ms. The value must be an integer within the range of (0,1800000]. Use scenarios: Specify the start time of a short vibration event in the vibration sequence. The time values of multiple events cannot overlap.|
| options | [TransientParam](#transientparam18) | No  | Optional parameters used to specify the vibration intensity, frequency, and channel ID of a short vibration event. If this parameter is left empty, the default values of the parameters are used (**100** for **intensity**, **50** for **frequency**, and **0** for **index**).                                    |

**Return value**

| Type                  | Description                                            |
| ---------------------- | ------------------------------------------------ |
| VibratorPatternBuilder | **VibratorPatternBuilder** object representing a short vibration event. You can continue to chain call **addContinuousEvent** or **addTransientEvent** to add more vibration events, and then call [build](#build18) to generate a **VibratorPattern** object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message        |
| -------- | ---------------- |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   let builder = new vibrator.VibratorPatternBuilder();
   // Use try catch to capture possible exceptions.
   try {
     let param: vibrator.TransientParam = {
       intensity: 80,
       frequency: 70,
       index: 0
     }
     builder.addTransientEvent(0, param);
     console.info(`addTransientEvent builder is ${builder.build()}`);
   } catch(error) {
     let e: BusinessError = error as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```

### build<sup>18+</sup>

build(): VibratorPattern;

Constructor used to create a **VibratorPattern** object, which determines the vibration sequence of short or long events.

This method is applicable to scenarios where custom vibration events need to be combined into a vibration sequence and then vibration is triggered by calling [VibrateFromPattern](#vibratefrompattern18). You need to add vibration events by calling [addContinuousEvent](#addcontinuousevent18) or [addTransientEvent](#addtransientevent18) before calling this method to generate a **VibratorPattern** object. A **VibratorPattern** object is returned, which contains the start time of the vibration sequence and the array of vibration events. This object can be passed as the **pattern** parameter of the [startVibration](#vibratorstartvibration9) method to trigger vibration. You need to add at least one vibration event by calling [addContinuousEvent](#addcontinuousevent18) or [addTransientEvent](#addtransientevent18) before calling this method. Otherwise, the generated **VibratorPattern** object is an empty sequence.

**System capability**: SystemCapability.Sensors.MiscDevice

**Return value**

| Type                                 | Description                              |
| ------------------------------------- | ---------------------------------- |
| [VibratorPattern](#vibratorpattern18) | Vibration pattern object. It contains the start time of the vibration pattern and the vibration event array. It can be passed as the **pattern** parameter of [VibrateFromPattern](#vibratefrompattern18) to the [startVibration](#vibratorstartvibration9) API to trigger vibration.|

**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   let builder = new vibrator.VibratorPatternBuilder();
   try {
     let param: vibrator.TransientParam = {
       intensity: 80,
       frequency: 70,
       index: 0
     }
     builder.addTransientEvent(0, param);
     console.info(`addTransientEvent builder is ${builder.build()}`);
   } catch(error) {
     let e: BusinessError = error as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   try {
     vibrator.startVibration({
       type: 'pattern',
       pattern: builder.build()
     }, {
     usage: 'alarm', // The switch control is subject to the selected type.
     }, (error) => {
     if (error) {
       let e: BusinessError = error as BusinessError;
       console.error(`Vibrate fail. Code: ${e.code}, message: ${e.message}`);
     } else {
       console.info(`vibrate success`);
     }
     });
   } catch(error) {
     let e: BusinessError = error as BusinessError;
     console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
   }
   ```

## EffectId

Enumerates the preset vibration effect IDs. This type is used when the [vibrator.startVibration<sup>9+</sup>](#vibratorstartvibration9) or [vibrator.stopVibration<sup>9+</sup>](#vibratorstopvibration9-1) API is called to deliver the [VibratePreset](#vibratepreset9) vibration. This parameter supports a variety of values, such as **haptic.clock.timer**. [HapticFeedback<sup>12+</sup>](#hapticfeedback12) provides several frequently used **EffectId** values.

> **NOTE**
> 
> Preset effects vary according to devices. You are advised to call [vibrator.isSupportEffect](#vibratorissupporteffect10)<sup>10+</sup> or [vibrator.isSupportEffectSync](#vibratorissupporteffectsync12) to check whether the device supports the preset effect before use.

**System capability**: SystemCapability.Sensors.MiscDevice

| Name       | Value                  | Description                        |
| ----------- | -------------------- | ---------------------------- |
| EFFECT_CLOCK_TIMER | 'haptic.clock.timer' | Vibration effect when a user adjusts the timer.|

## HapticFeedback<sup>12+</sup>

Defines the vibration effect. The frequency of the same vibration effect may vary depending on the vibrator, but the frequency trend remains consistent. These vibration effects are specific values of the **EffectId** parameter. For details about how to use them, see the sample code for delivering the [VibratePreset](#vibratepreset9) vibration effect using the [vibrator.startVibration<sup>9+</sup>](#vibratorstartvibration9) or [vibrator.stopVibration<sup>9+</sup>](#vibratorstopvibration9-1) API.

> **NOTE**
>
> The effects vary according to devices. You are advised to call [vibrator.isSupportEffect](#vibratorissupporteffect10)<sup>10+</sup> or [vibrator.isSupportEffectSync](#vibratorissupporteffectsync12) to check whether the device supports the preset effect before use.

**System capability**: SystemCapability.Sensors.MiscDevice

| Name                               | Value                     | Description                        |
| ----------------------------------- | ----------------------- | ---------------------------- |
| EFFECT_SOFT                         | 'haptic.effect.soft'    | Soft vibration, low frequency. This effect is applicable to soft haptic feedback scenarios.|
| EFFECT_HARD                         | 'haptic.effect.hard'    | Hard vibration, medium frequency. This effect is applicable to firm haptic feedback scenarios.|
| EFFECT_SHARP                        | 'haptic.effect.sharp'   | Sharp vibration, high frequency. This effect is applicable to warning haptic feedback scenarios.|
| EFFECT_NOTICE_SUCCESS<sup>18+</sup> | 'haptic.notice.success' | Vibration for a success notification. This effect is applicable to operation success notification scenarios.    |
| EFFECT_NOTICE_FAILURE<sup>18+</sup> | 'haptic.notice.fail'    | Vibration for a failure notification. This effect is applicable to operation failure notification scenarios.    |
| EFFECT_NOTICE_WARNING<sup>18+</sup> | 'haptic.notice.warning' | Vibration for an alert. This effect is applicable to risk warning notification scenarios.    |

## VibratorStopMode

Enumerates vibration stop modes. This type is used to specify the vibration stop mode when the [vibrator.stopVibration<sup>9+</sup>](#vibratorstopvibration9) or [vibrator.stopVibration<sup>9+</sup>](#vibratorstopvibration9-1) API is called. The stop mode must correspond to the mode delivered in [VibrateEffect<sup>9+</sup>](#vibrateeffect9). **VIBRATOR_STOP_MODE_TIME** corresponds to the **VibrateTime** type, and **VIBRATOR_STOP_MODE_PRESET** corresponds to the **VibratePreset** type.

**System capability**: SystemCapability.Sensors.MiscDevice

| Name                     | Value      | Description                    |
| ------------------------- | -------- | ------------------------ |
| VIBRATOR_STOP_MODE_TIME   | 'time'   | Vibration of the [VibrateTime](#vibratetime9) type (duration mode). The value must correspond to the **VibrateTime** type used in **startVibration**.|
| VIBRATOR_STOP_MODE_PRESET | 'preset' | Vibration of the [VibratePreset](#vibratepreset9) type (preset **EffectId** mode). The value must correspond to the **VibratePreset** type used in **startVibration**.|

## VibrateEffect<sup>9+</sup>

type VibrateEffect = VibrateTime | VibratePreset | VibrateFromFile | VibrateFromPattern

Defines the vibration effect. This parameter is required for [vibrator.startVibration<sup>9+</sup>](#vibratorstartvibration9) or [vibrator.startVibration<sup>9+</sup>](#vibratorstartvibration9-1).

**System capability**: SystemCapability.Sensors.MiscDevice

| Type                                 | Description                                                        |
| ------------------------------------- | ------------------------------------------------------------ |
| [VibrateTime](#vibratetime9)          | Triggers vibration based on a specified duration. This effect is applicable to basic scenarios where only the vibration duration needs to be controlled.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| [VibratePreset](#vibratepreset9)      | Triggers vibration based on a preset effect. This effect is applicable to short vibration scenarios in interactive feedback. You are advised to use this effect to maintain consistent style with the overall vibration feedback experience of the system.                              |
| [VibrateFromFile](#vibratefromfile10) | Triggers vibration based on a custom vibration configuration file. This effect is applicable to complex scenarios that require fine-grained vibration control.                        |
| [VibrateFromPattern<sup>18+</sup>](#vibratefrompattern18)      | Triggers vibration based on a custom effect. This effect is applicable to scenarios that require flexible combination of vibration events.                            |

## VibrateTime<sup>9+</sup>

Represents vibration of the specified duration. This API provides basic control over the start and stop of vibration, but does not support customization of vibration intensity, frequency, or other parameters.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.MiscDevice

| Name    | Type  | Read-Only| Optional| Description                                                       |
| -------- | ------ | ---- | ---- | ----------------------------------------------------------- |
| type     | 'time' | No  | No  | The value is **time**, indicating vibration of the specified duration. The value is fixed and cannot be changed.                     |
| duration | number | No  | No  | Continuous vibration duration of the vibrator, in ms. The value must be an integer within the range of (0,1800000]. The maximum vibration duration varies with devices due to different component protection design specifications of drivers provided by different vendors. It is recommended that a single vibration duration be less than or equal to 10,000 ms (10s) to maximize user experience.|

## VibratePreset<sup>9+</sup>

Represents the preset vibration effect. When [vibrator.startVibration<sup>9+</sup>](#vibratorstartvibration9) or [vibrator.startVibration<sup>9+</sup>](#vibratorstartvibration9-1) is called, the value of [VibrateEffect<sup>9+</sup>](#vibrateeffect9) can be **VibratePreset**, indicating that the preset vibration effect is triggered. This mode is suitable for short vibration scenarios in interactive feedback (such as tapping, long-pressing, sliding, and dragging). You are advised to use this vibration type to maintain consistency with the system's overall vibration feedback experience.

**System capability**: SystemCapability.Sensors.MiscDevice

| Name                   | Type    | Read-Only| Optional| Description                                                        |
| ----------------------- | -------- | ---- | ---- | ------------------------------------------------------------ |
| type                    | 'preset' | No  | No  | The value **preset** means that vibration is triggered based on the specified effect. The value is fixed and cannot be changed.                |
| effectId                | string   | No  | No  | Preset vibration effect ID. The value can contain a maximum of 64 characters. If the length exceeds 64 characters, the first 64 characters are used. Use scenarios: The preset vibration effects may vary depending on the device. You are advised to use [vibrator.isSupportEffect](#vibratorissupporteffect10) or [vibrator.isSupportEffectSync](#vibratorissupporteffectsync12) to check whether the effect is supported. For details about the values, see [EffectId](#effectid) and [HapticFeedback](#hapticfeedback12).                            |
| count                   | number   | No  | Yes  | Number of repeated vibrations. This parameter is optional. The default value is **1**, The value must be a positive integer. Use scenarios: This parameter is applicable to interaction feedback scenarios where the same vibration effect needs to be repeated for multiple times, for example, reminders for continuous tapping. If this parameter is not specified, the vibration is repeated once by default.                       |
| intensity<sup>12+</sup> | number   | No  | Yes  | Vibration adjustment strength. This is an optional parameter. The value must be an integer within the range of (0,100]. The default value is **100**. Use scenarios: This parameter is applicable to interactive feedback scenarios where the vibration intensity needs to be adjusted. If this parameter is not specified, the maximum intensity is used by default. If vibration intensity adjustment is not supported, the default vibration intensity will be used.|

## VibrateFromFile<sup>10+</sup>

Represents a custom vibration pattern. Only some devices support HD vibration. If a device does not support this vibration type, error code 801 will be returned. When [vibrator.startVibration<sup>9+</sup>](#vibratorstartvibration9) or [vibrator.startVibration<sup>9+</sup>](#vibratorstartvibration9-1) is called, the value of [VibrateEffect<sup>9+</sup>](#vibrateeffect9) can be **VibrateFromFile**, indicating that a custom vibration pattern is triggered. This mode is suitable for interactive feedback in complex scenarios requiring precise vibration patterns (such as realistic effects triggered by emoji packs, or feedback for in-game actions/mechanics).

This mode is suitable for interactive feedback scenarios where precise vibration effects need to be customized based on vibration configuration files. You are advised to use [vibrator.isHdHapticSupported](#vibratorishdhapticsupported12) to check whether the device supports HD vibration.

**System capability**: SystemCapability.Sensors.MiscDevice

| Name    | Type                                                        | Read-Only| Optional| Description                                      |
| -------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------ |
| type     | 'file'                                                       | No  | No  | The value **file** means vibration according to a vibration configuration file. The value is fixed and cannot be changed.|
| hapticFd | [HapticFileDescriptor](#hapticfiledescriptor10)<sup>10+</sup> | No  | No  | File descriptor (FD) of the vibration configuration file. Ensure that the file is available and in the correct format. For details about the storage format of the vibration sequence, see [Vibration Effect Description](../../device/sensor/vibrator-guidelines.md#vibration-effect-description).                    |

## HapticFileDescriptor<sup>10+</sup>

Describes the FD of a custom vibration configuration file. Ensure that the file is available, and the parameters in it can be obtained from the sandbox path through the [fileIo.open](../apis-core-file-kit/js-apis-file-fs.md#fileioopen) API or from the HAP resource through the [getRawFd](../apis-localization-kit/js-apis-resource-manager.md#getrawfd9) API. The application scenario is as follows: The vibration sequence is stored in a file and vibration needs to be triggered based on the offset and length. For details about the storage format of the vibration sequence, see [Vibration Effect Description](../../device/sensor/vibrator-guidelines.md#vibration-effect-description).

Pay attention to the following when using this method:
- After the vibration ends, you are advised to close the file descriptor in a timely manner to prevent resource leaks. The file descriptor obtained using **getRawFd** must be closed using **closeRawFd**, and the file descriptor obtained using **fileIo.open** must be closed using **fileIo.close**.

**System capability**: SystemCapability.Sensors.MiscDevice

| Name  | Type  | Read-Only| Optional| Description                                                        |
| ------ | ------ | ---- | ---- | ------------------------------------------------------------ |
| fd     | number | No  | No  | FD of the custom vibration configuration file. It can be obtained from the sandbox path through the [fileIo.open](../apis-core-file-kit/js-apis-file-fs.md#fileioopen) API or from the HAP resource through the [getRawFd](../apis-localization-kit/js-apis-resource-manager.md#getrawfd9) API.                                            |
| offset | number | No  | Yes  | Offset from the start position of the file, in bytes. The default value is **0**, indicating the start position of the file. The value cannot exceed the valid range of the file. Use scenarios: This parameter is applicable when the vibration configuration file contains multiple vibration effects and you need to specify the start position of the vibration. If this parameter is not specified, the vibration starts from the start position of the file by default.|
| length | number | No  | Yes  | Resource length, in bytes. The default value is the length from the offset position to the end of the file. The value cannot exceed the valid range of the file. Use scenarios: This parameter is applicable when the vibration configuration file contains multiple vibration effects and you need to specify vibration of the specific duration. If this parameter is not specified, all content from the offset position to the end of the file is read by default.|

## VibratorEventType<sup>18+</sup>

Enumerates vibration event types. This parameter is used to specify the type of a vibration event in the **eventType** field of [VibratorEvent](#vibratorevent18).

**System capability**: SystemCapability.Sensors.MiscDevice

| Name      | Value  | Description             |
| --------- | ------ | ----------------- |
| CONTINUOUS | 0 | Long vibration. This method is applicable to scenarios where continuous vibration feedback is required, such as engine vibration and haptic vibration.|
| TRANSIENT  | 1 | Short vibration. This method is applicable to scenarios where short vibration feedback is required, such as tapping and key feedback.|

## VibratorCurvePoint<sup>18+</sup>

Defines the gain relative to the vibration intensity. This parameter is used in the **points** field of [ContinuousParam](#continuousparam18) and [VibratorEvent](#vibratorevent18) to precisely control the change trend of vibration intensity and frequency.

**System capability**: SystemCapability.Sensors.MiscDevice

| Name     | Type  | Read-Only| Optional| Description                                                        |
| --------- | ------ | ---- | ---- | ------------------------------------------------------------ |
| time      | number | No  | No  | Start time offset, in ms. Time position of the adjustment point in the vibration adjustment curve.                                              |
| intensity | number | No  | Yes  | Gain relative to the vibration intensity. This is an optional parameter. The value range is [0,1]. The default value is **1**, Use scenarios: This parameter is used for fine-tuning the vibration intensity in interactive feedback scenarios. A larger value indicates stronger vibration. If this parameter is not set, the maximum gain is used by default.|
| frequency | number | No  | Yes  | Change relative to the vibration frequency. This is an optional parameter. The value must be an integer within the range of [-100,100]. The default value is **0**. Use scenarios: This parameter is used for fine-tuning the vibration frequency in interactive feedback scenarios. A positive value indicates an increase in frequency, while a negative value indicates a decrease. If this parameter is not specified, the frequency remains unchanged by default.|

## VibratorEvent<sup>18+</sup>

Enumerates vibration events. This API defines specific vibration events in the **events** array of [VibratorPattern](#vibratorpattern18).

**System capability**: SystemCapability.Sensors.MiscDevice

| Name     | Type                           | Read-Only| Optional| Description                                                        |
| --------- | ------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| eventType | VibratorEventType               | No  | No  | Enumerates vibration event types. **CONTINUOUS (0)** indicates long vibration, and **TRANSIENT (1)** indicates short vibration.                                              |
| time      | number                          | No  | No  | Vibration start time, in ms. The value must be an integer within the range of (0,1800000]. This parameter is used to specify the start time of a vibration event in the sequence. The time values of multiple events cannot overlap.   |
| duration  | number                          | No  | Yes  | Vibration duration, in ms. This is an optional parameter.  The value must be an integer within the range of (0,5000]. The default value is **48** for short vibration and **1000** for long vibration. Use scenarios: This parameter is used for interactive feedback of long and short vibration. If this parameter is not specified, the default duration of the corresponding type is used.|
| intensity | number                          | No  | Yes  | Vibration intensity. This is an optional parameter. The value must be an integer within the range of [0,100]. The default value is **100**. If this parameter is not specified, the maximum intensity is used by default.|
| frequency | number                          | No  | Yes  | Vibration frequency. This is an optional parameter. The value must be an integer within the range of [0,100]. The default value is **50**. If this parameter is not specified, the medium frequency is used by default.|
| index     | number                          | No  | Yes  | Vibrator channel ID. This is an optional parameter. The value must be an integer within the range of [0,2]. The default value is **0**. Use scenarios: Different channels correspond to different vibrator components. This parameter is applicable to fine-grained control of multi-vibrator devices. If this parameter is not specified, channel 0 is used by default.       |
| points    | Array&lt;[VibratorCurvePoint](#vibratorcurvepoint18)&gt; | No  | Yes  | Adjustment points of the vibration curve. Use scenarios: This method is applicable to interaction feedback scenarios where fine-grained control over the vibration intensity and frequency change trend is required. The array must contain four to 16 elements.                            |

## VibratorPattern<sup>18+</sup>

Defines the vibration sequence. The sequence is generated by [VibratorPatternBuilder.build](#build18) and passed to [startVibration](#vibratorstartvibration9) as the **pattern** parameter of [VibrateFromPattern](#vibratefrompattern18) to trigger vibration.

**System capability**: SystemCapability.Sensors.MiscDevice

| Name  | Type                      | Read-Only| Optional| Description                                                |
| ------ | -------------------------- | ---- | ---- | ---------------------------------------------------- |
| time   | number                     | No  | No  | Absolute vibration start time, in ms.                                  |
| events | Array&lt;[VibratorEvent](#vibratorevent18)&gt; | No  | No  | Array of vibration events. It is generated by the **build** method after the **addContinuousEvent** and **addTransientEvent** methods of [VibratorPatternBuilder](#vibratorpatternbuilder18) are called. The time values of multiple **VibratorEvent** objects in the same **VibratorPattern** cannot overlap.|

## ContinuousParam<sup>18+</sup>

Defines the parameters for continuous vibration. This API defines the **options** parameter used in [VibratorPatternBuilder.addContinuousEvent](#addcontinuousevent18), which specifies the vibration intensity, frequency, vibration adjustment curve, and channel ID of a long vibration event.

**System capability**: SystemCapability.Sensors.MiscDevice

| Name     | Type                | Read-Only| Optional| Description                                                        |
| --------- | -------------------- | ---- | ---- | ------------------------------------------------------------ |
| intensity | number               | No  | Yes  | Vibration intensity. This is an optional parameter. The value must be an integer within the range of [0,100]. The default value is **100**. If this parameter is not specified, the maximum intensity is used by default.|
| frequency | number               | No  | Yes  | Vibration frequency. This is an optional parameter. The value must be an integer within the range of [0,100]. The default value is **50**. If this parameter is not specified, the medium frequency is used by default.|
| points    | [VibratorCurvePoint](#vibratorcurvepoint18)[] | No  | Yes  | Adjustment points of the vibration curve. Use scenarios: This method is applicable to interaction feedback scenarios where fine-grained control over the vibration intensity and frequency change trend is required. The array must contain four to 16 elements.                            |
| index     | number               | No  | Yes  | Channel ID. This is an optional parameter. The value must be an integer within the range of [0,2]. The default value is **0**. Use scenarios: Different channels correspond to different vibrator components. This parameter is applicable to fine-grained control of multi-vibrator devices. If this parameter is not specified, channel 0 is used by default.                   |

## TransientParam<sup>18+</sup>

Defines the parameters for transient vibration. This API defines the **options** parameter in [VibratorPatternBuilder.addTransientEvent](#addtransientevent18), which specifies the vibration intensity, frequency, and channel ID of a short vibration event.

**System capability**: SystemCapability.Sensors.MiscDevice

| Name     | Type  | Read-Only| Optional| Description                                                        |
| --------- | ------ | ---- | ---- | ------------------------------------------------------------ |
| intensity | number | No  | Yes  | Vibration intensity. This is an optional parameter. The value must be an integer within the range of [0,100]. The default value is **100**. If this parameter is not specified, the maximum intensity is used by default.|
| frequency | number | No  | Yes  | Vibration frequency. This is an optional parameter. The value must be an integer within the range of [0,100]. The default value is **50**. If this parameter is not specified, the medium frequency is used by default.|
| index     | number | No  | Yes  | Channel ID. This is an optional parameter. The value must be an integer within the range of [0,2]. The default value is **0**. Use scenarios: Different channels correspond to different vibrator components. This parameter is applicable to fine-grained control of multi-vibrator devices. If this parameter is not specified, channel 0 is used by default.                   |

## VibrateFromPattern<sup>18+</sup>

Defines the custom vibration effect. This mode is suitable for interactive feedback scenarios that require flexible combination of vibration events (such as realistic effects triggered by emoji packs, or feedback for in-game actions/mechanics). Compared with **VibrateFromFile**, which is designed for effects pre-defined in files and transfers vibration events as file descriptors, **VibrateFromPattern** offers more flexible arrangement and combination of vibration events, transferring them as an array of vibration events.

**System capability**: SystemCapability.Sensors.MiscDevice

| Name   | Type           | Read-Only| Optional| Description                                                |
| ------- | --------------- | ---- | ---- | ---------------------------------------------------- |
| type    | 'pattern'       | No  | No  | If the value is **'pattern'**, the vibrator vibrates based on the specified pattern. The value is fixed and cannot be changed.           |
| pattern | VibratorPattern | No  | No  | A [VibratorPattern](#vibratorpattern18) object returned by the [build](#build18) method. You need to add vibration events using [VibratorPatternBuilder](#vibratorpatternbuilder18) before calling the **build** method to generate a [VibratorPattern](#vibratorpattern18) object.|

## VibrateAttribute<sup>9+</sup>

Vibration attribute. This parameter is used as the **attribute** parameter in the [startVibration](#vibratorstartvibration9) API to specify the vibrator ID, device ID, and vibration use scenario.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.MiscDevice

| Name                  | Type            | Read-Only| Optional| Description                                                        |
| ---------------------- | ---------------- | ---- | ---- | ------------------------------------------------------------ |
| id                     | number           | No  | Yes  | Vibrator ID. The default value is **0**. Use scenarios: When there are multiple vibrators on the device, you can select a specific vibrator by specifying the vibrator ID to trigger vibration. You can query the vibrator ID by calling [getVibratorInfoSync](#vibratorgetvibratorinfosync19). If this parameter is not specified, the vibrator whose ID is **0** is used by default.                                        |
| deviceId<sup>19+</sup> | number           | No  | Yes  | Device ID. The default value is **-1**, which indicates the local device. Use scenarios: This parameter is used when a remote device needs to be specified in a multi-device scenario. If this parameter is not set, the local device is controlled by default. Since API version 19, the device ID can be obtained by calling [getVibratorInfoSync](#vibratorgetvibratorinfosync19) or [on](#vibratoron19).<br>**Atomic service API**: This API can be used in atomic services since API version 19.|
| usage                  | [Usage](#usage9) | No  | No  | Vibration scenario. The default value is **'unknown'**. The value must be an enum defined in [Usage](#usage9). Different **usage** values correspond to different system vibration control rules. You need to select a proper **usage** value based on the actual service scenario.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|

## Usage<sup>9+</sup>

type Usage = 'unknown' | 'alarm' | 'ring' | 'notification' | 'communication' | 'touch' | 'media' | 'physicalFeedback' | 'simulateReality'

Enumerates the vibration scenarios. Different **usage** values correspond to different system vibration control rules. You need to select a proper **usage** value based on the actual service scenario.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.MiscDevice
<!--RP1-->

| Type              | Description                                                   |
| ------------------ | ------------------------------------------------------- |
| 'unknown'          | Unknown scenario, with the lowest priority. This parameter has a fixed value of **unknown**. It is not controlled by any specific vibration switch.|
| 'alarm'            | Vibration for alarms. This parameter has a fixed value of **alarm**. It is controlled by the alarm vibration switch.                  |
| 'ring'             | Vibration for ringing. This parameter has a fixed value of **ring**. It is controlled by the ring vibration switch.                   |
| 'notification'     | Vibration for notification. This parameter has a fixed value of **notification**. It is controlled by the notification vibration switch.           |
| 'communication'    | Vibration for communication. This parameter has a fixed value of **communication**. It is controlled by the communication vibration switch.          |
| 'touch'            | Vibration for touch. This parameter has a fixed value of **touch**. It is controlled by the haptic vibration switch.                  |
| 'media'            | Vibration for media. This parameter has a fixed value of **media**. It is controlled by the media vibration switch.                |
| 'physicalFeedback' | Vibration for physical feedback. This parameter has a fixed value of **physicalFeedback**. It is controlled by the physical feedback vibration switch.   |
| 'simulateReality'  | Vibration for simulated reality. This parameter has a fixed value of **simulateReality**. It is controlled by the simulated reality vibration switch.    |

<!--RP1End-->

## vibrator.vibrate<sup>(deprecated)</sup>

vibrate(duration: number): Promise&lt;void&gt;

Triggers vibration based on a specified duration. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [vibrator.startVibration](#vibratorstartvibration9-1) instead.

**Required permissions**: ohos.permission.VIBRATE

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name  | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| duration | number | Yes  | Vibrator vibration duration, in ms. The value must be an integer within the range of (0,1800000]. The maximum vibration duration varies with devices due to different component protection design specifications of drivers provided by different vendors. It is recommended that a single vibration duration be less than or equal to 10,000 ms (10s) to maximize user experience.|

**Return value**

| Type               | Description         |
| ------------------- | ------------- |
| Promise&lt;void&gt; | Promise that returns the result. If the API is called successfully, the promise returns a value through **resolve**, indicating that the vibration is started successfully. If the call fails, the promise returns an error object through **reject**. The error object contains the error code and error message.|

**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   vibrator.vibrate(1000).then(() => {
     console.info('Succeed in vibrating');
   }, (error: BusinessError) => {
     console.error(`Failed to vibrate. Code: ${error.code}, message: ${error.message}`);
   });
   ```

## vibrator.vibrate<sup>(deprecated)</sup>

vibrate(duration: number, callback?: AsyncCallback&lt;void&gt;): void

Triggers vibration based on a specified duration. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [vibrator.startVibration](#vibratorstartvibration9) instead.

**Required permissions**: ohos.permission.VIBRATE

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name  | Type                     | Mandatory| Description                                                        |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| duration | number                    | Yes  | Vibrator vibration duration, in ms. The value must be an integer within the range of (0,1800000]. The maximum vibration duration varies with devices due to different component protection design specifications of drivers provided by different vendors. It is recommended that a single vibration duration be less than or equal to 10,000 ms (10s) to maximize user experience.|
| callback | AsyncCallback&lt;void&gt; | No  | Callback used to return the result. If the vibration starts, **err** is **undefined**; otherwise, **err** is an error object. Use scenarios: If this parameter is not specified, only the vibration is triggered and the callback result is not obtained.  |

**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   vibrator.vibrate(1000, (error: BusinessError) => {
     if (error) {
       console.error(`Failed to vibrate. Code: ${error.code}, message: ${error.message}`);
     } else {
       console.info('Succeed in vibrating');
     }
   })
   ```


## vibrator.vibrate<sup>(deprecated)</sup>

vibrate(effectId: EffectId): Promise&lt;void&gt;

Triggers vibration based on a specified effect. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [vibrator.startVibration](#vibratorstartvibration9-1) instead.

**Required permissions**: ohos.permission.VIBRATE

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name  | Type                 | Mandatory| Description              |
| -------- | --------------------- | ---- | ------------------ |
| effectId | [EffectId](#effectid) | Yes  | Preset vibration effect ID. The value can contain a maximum of 64 characters. If the length exceeds 64 characters, the first 64 characters are used. You are advised to use [vibrator.isSupportEffect](#vibratorissupporteffect10) or [vibrator.isSupportEffectSync](#vibratorissupporteffectsync12) to check whether the effect is supported.|

**Return value**

| Type               | Description         |
| ------------------- | ------------- |
| Promise&lt;void&gt; | Promise that returns the result. If the API is called successfully, the promise returns a value through **resolve**, indicating that the vibration is started successfully. If the call fails, the promise returns an error object through **reject**. The error object contains the error code and error message.|

**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   vibrator.vibrate(vibrator.EffectId.EFFECT_CLOCK_TIMER).then(() => {
     console.info('Succeed in vibrating');
   }, (error: BusinessError) => {
     console.error(`Failed to vibrate. Code: ${error.code}, message: ${error.message}`);
   });
   ```


## vibrator.vibrate<sup>(deprecated)</sup>

vibrate(effectId: EffectId, callback?: AsyncCallback&lt;void&gt;): void

Triggers vibration based on a specified effect. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [vibrator.startVibration](#vibratorstartvibration9) instead.

**Required permissions**: ohos.permission.VIBRATE

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name  | Type                     | Mandatory| Description                                                      |
| -------- | ------------------------- | ---- | ---------------------------------------------------------- |
| effectId | [EffectId](#effectid)     | Yes  | Preset vibration effect ID. The value can contain a maximum of 64 characters. If the length exceeds 64 characters, the first 64 characters are used. You are advised to use [vibrator.isSupportEffect](#vibratorissupporteffect10) or [vibrator.isSupportEffectSync](#vibratorissupporteffectsync12) to check whether the effect is supported.                                        |
| callback | AsyncCallback&lt;void&gt; | No  | Callback used to return the result. If the vibration starts, **err** is **undefined**; otherwise, **err** is an error object. Use scenarios: If this parameter is not specified, only the vibration is triggered and the callback result is not obtained.|

**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   vibrator.vibrate(vibrator.EffectId.EFFECT_CLOCK_TIMER, (error: BusinessError) => {
     if (error) {
       console.error(`Failed to vibrate. Code: ${error.code}, message: ${error.message}`);
     } else {
       console.info('Succeed in vibrating');
     }
   })
   ```

## vibrator.stop<sup>(deprecated)</sup>

stop(stopMode: VibratorStopMode): Promise&lt;void&gt;

Stops vibration in the specified mode.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [vibrator.stopVibration](#vibratorstopvibration9-1) instead.

**Required permissions**: ohos.permission.VIBRATE

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name  | Type                                 | Mandatory| Description                    |
| -------- | ------------------------------------- | ---- | ------------------------ |
| stopMode | [VibratorStopMode](#vibratorstopmode) | Yes  | Mode to stop the vibration. The mode must correspond to the mode used to start the vibration. **VIBRATOR_STOP_MODE_TIME** is used to stop duration-based vibration, and **VIBRATOR_STOP_MODE_PRESET** is used to stop preset vibration.|

**Return value**

| Type               | Description         |
| ------------------- | ------------- |
| Promise&lt;void&gt; | Promise that returns the result. If the API is called successfully, the promise returns a value through **resolve**, indicating that the vibration is stopped successfully. If the call fails, the promise returns an error object through **reject**. The error object contains the error code and error message.|

**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   // Start vibration based on the specified effect ID.
   vibrator.vibrate(vibrator.EffectId.EFFECT_CLOCK_TIMER, (error: BusinessError) => {
     if (error) {
       console.error(`Failed to vibrate. Code: ${error.code}, message: ${error.message}`);
     } else {
       console.info('Succeed in vibrating');
     }
   })
   // Stop vibration in VIBRATOR_STOP_MODE_PRESET mode.
   vibrator.stop(vibrator.VibratorStopMode.VIBRATOR_STOP_MODE_PRESET).then(() => {
     console.info('Succeed in stopping');
   }, (error: BusinessError) => {
     console.error(`Failed to stop. Code: ${error.code}, message: ${error.message}`);
   });
   ```


## vibrator.stop<sup>(deprecated)</sup>

stop(stopMode: VibratorStopMode, callback?: AsyncCallback&lt;void&gt;): void

Stops vibration in the specified mode.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [vibrator.stopVibration](#vibratorstopvibration9) instead.

**Required permissions**: ohos.permission.VIBRATE

**System capability**: SystemCapability.Sensors.MiscDevice

**Parameters**

| Name  | Type                                 | Mandatory| Description                                                        |
| -------- | ------------------------------------- | ---- | ------------------------------------------------------------ |
| stopMode | [VibratorStopMode](#vibratorstopmode) | Yes  | Mode to stop the vibration. The mode must correspond to the mode used to start the vibration. **VIBRATOR_STOP_MODE_TIME** is used to stop duration-based vibration, and **VIBRATOR_STOP_MODE_PRESET** is used to stop preset vibration.                                    |
| callback | AsyncCallback&lt;void&gt;             | No  | Callback used to return the result. If the vibration stops, **err** is **undefined**; otherwise, **err** is an error object. Use scenarios: If this parameter is not specified, only the vibration is stopped and the callback result is not obtained.|

**Example**

   ```ts
   import { vibrator } from '@kit.SensorServiceKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   // Start vibration based on the specified effect ID.
   vibrator.vibrate(vibrator.EffectId.EFFECT_CLOCK_TIMER, (error: BusinessError) => {
     if (error) {
       console.error(`Failed to vibrate. Code: ${error.code}, message: ${error.message}`);
     } else {
       console.info('Succeed in vibrating');
     }
   })
   // Stop vibration in VIBRATOR_STOP_MODE_PRESET mode.
   vibrator.stop(vibrator.VibratorStopMode.VIBRATOR_STOP_MODE_PRESET, (error: BusinessError) => {
     if (error) {
       console.error(`Failed to stop. Code: ${error.code}, message: ${error.message}`);
     } else {
       console.info('Succeed in stopping');
     }
   })
   ```
