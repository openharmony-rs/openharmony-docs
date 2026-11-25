# @system.brightness (Screen Brightness)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=6341d6494dfc8f40d09c0851f2587f01592d5b94 translatedAt=2026-11-06T01:41:07.229Z pushedAt=2026-11-09T03:46:08.512Z nl=1 -->

This module provides APIs for querying and adjusting the screen brightness and mode, as well as the API for setting the screen always on.

> **NOTE**
>
>- Module maintenance policy:
>
>    \- For lite wearables, this module is constantly maintained and available.
>
>    \- For other device types, this module is no longer maintained since API version 7.<!--Del--> You are advised to use APIs of [@ohos.brightness](js-apis-brightness-sys.md). <!--DelEnd-->The substitute APIs are available only for system applications.
>
>- The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>


## Modules to Import


```js
import brightness, { BrightnessModeResponse, BrightnessResponse } from '@system.brightness';
```

## Brightness

Provides APIs for querying and adjusting the screen brightness and mode, as well as the API for setting the screen always on.

### getValue<sup>(deprecated)</sup>

getValue(options?: GetBrightnessOptions): void

Obtains the current screen brightness.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [GetBrightnessOptions](#getbrightnessoptionsdeprecated) | No   | Options for obtaining the screen brightness. This parameter is optional and left empty by default. If this parameter is not passed, the brightness query result cannot be received through the callback. |

**Example**

ArkTS example:
  ```js
  brightness.getValue({
      success: (data: BrightnessResponse) => {
        console.info('success get brightness value:' + data.value);
      },
      fail: (data: string, code: number) => {
        console.error(`Failed to get brightness value. Code: ${code}, message: ${data}`);
      }
  });
  ```

JS example:
```xml
<!-- xxx.hml -->
<div class="container">
    <input type="button" value="Get Value" style="width: 240px; height: 50px; margin: 5px;" onclick="getValue"></input>
    <text class="title">getValue: {{ value }}</text>
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
import brightness from '@system.brightness';

export default {
    data: {
        value: ''
    },
    getValue() {
        const TAG = 'get_value_success_test';
        brightness.getValue({
            success: (brightnessResponse) => {
                this.value = brightnessResponse.value;
                console.info(`${TAG} brightnessResponse.value: ${brightnessResponse.value}`);
            },
            fail: (data, code) => {
                console.error(`Failed to get brightness value. Code: ${code}, message: ${data}`);
            },
            complete: () => {
                console.info(`${TAG} getValue complete`);
            }
        });
    },
}
```

### setValue<sup>(deprecated)</sup>

setValue(options?: SetBrightnessOptions): void

Sets the current screen brightness. The set brightness value is corrected by the system: values outside the range of 1 to 255 are automatically adjusted to the valid range, and decimals are truncated to integers. For details, see the description of the value parameter in [SetBrightnessOptions](#setbrightnessoptionsdeprecated).

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [SetBrightnessOptions](#setbrightnessoptionsdeprecated) | No | Options for setting the screen brightness. This parameter is optional and left empty by default. If you do not pass this parameter, the brightness value cannot be set, and the API call has no effect. |

**Example**

ArkTS example:
  ```js
  brightness.setValue({
      value: 100,
      success: () => {
        console.info('handling set brightness success.');
      },
      fail: (data: string, code: number) => {
        console.error(`Failed to set brightness value. Code: ${code}, message: ${data}`);
      }
  });
  ```

JS example:
```xml
<!-- xxx.hml -->
<div class="container">
    <input type="button" value="Set Value" style="width: 240px; height: 50px; margin: 5px;" onclick="setValue"></input>
    <text class="title">setValue: {{ value }}</text>
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
import brightness from '@system.brightness';

export default {
    data: {
        value: 100
    },
    setValue() {
        const TAG = 'set_value_success_test';
        brightness.setValue({
            value: this.value,
            success: () => {
                console.info(`${TAG} setValue success!`);
            },
            fail: (data, code) => {
                console.error(`Failed to set brightness value. Code: ${code}, message: ${data}`);
            },
            complete: () => {
                console.info(`${TAG} setValue complete`);
            }
        });
    },
}
```

### getMode<sup>(deprecated)</sup>

getMode(options?: GetBrightnessModeOptions): void

Obtains the current screen brightness mode.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [GetBrightnessModeOptions](#getbrightnessmodeoptionsdeprecated) | No | Options for obtaining the screen brightness mode. This parameter is optional and left empty by default. If this parameter is not passed, the mode query result cannot be received through the callback. |

**Example**

ArkTS example:
  ```js
  brightness.getMode({
      success: (data: BrightnessModeResponse) => {
        console.info('success get mode:' + data.mode);
      },
      fail: (data: string, code: number) => {
        console.error(`Failed to get brightness mode. Code: ${code}, message: ${data}`);
      }
  });
  ```

JS example:
```xml
<!-- xxx.hml -->
<div class="container">
    <input type="button" value="Get Mode" style="width: 240px; height: 50px; margin: 5px;" onclick="getMode"></input>
    <text class="title">getMode: {{ mode }}</text>
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
import brightness from '@system.brightness';

export default {
    data: {
        mode: ''
    },
    getMode() {
        const TAG = 'get_mode_success_test';
        brightness.getMode({
            success: (brightnessModeResponse) => {
                this.mode = brightnessModeResponse.mode;
                console.info(`${TAG} brightnessModeResponse mode: ${brightnessModeResponse.mode}`);
            },
            fail: (data, code) => {
                console.error(`Failed to get brightness mode. Code: ${code}, message: ${data}`);
            },
            complete: () => {
                console.info(`${TAG} getMode complete`);
            }
        });
    },
}
```

### setMode<sup>(deprecated)</sup>

setMode(options?: SetBrightnessModeOptions): void

Sets the current screen brightness mode. Both manual adjustment (**mode** = **0**) and automatic adjustment (**mode** = **1**) are supported. For details, see the description of the mode parameter in [SetBrightnessModeOptions](#setbrightnessmodeoptionsdeprecated).

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

**Parameters**
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [SetBrightnessModeOptions](#setbrightnessmodeoptionsdeprecated) | No | Options for setting the screen brightness mode. This parameter is optional and left empty by default. If this parameter is not passed, the brightness mode cannot be set, and the API call has no effect. |

**Example**

ArkTS example:
  ```js
  brightness.setMode({
      mode: 1,
      success: () => {
        console.info('handling set mode success.');
      },
      fail: (data: string, code: number) => {
        console.error(`Failed to set brightness mode. Code: ${code}, message: ${data}`);
      }
  });
  ```

JS example:
```xml
<!-- xxx.hml -->
<div class="container">
    <input type="button" value="Set Mode" style="width: 240px; height: 50px; margin: 5px;" onclick="setMode"></input>
    <text class="title">setMode: {{ mode }}</text>
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
import brightness from '@system.brightness';

export default {
    data: {
        mode: 1
    },
    setMode() {
        const TAG = 'set_mode_success_test';
        brightness.setMode({
            mode: this.mode,
            success: () => {
                console.info(`${TAG} setMode success`);
            },
            fail: (data, code) => {
                console.error(`Failed to set brightness mode. Code: ${code}, message: ${data}`);
            },
            complete: () => {
                console.info(`${TAG} setMode complete`);
            }
        });
    },
}
```

### setKeepScreenOn<sup>(deprecated)</sup>

setKeepScreenOn(options?: SetKeepScreenOnOptions): void

Sets whether to keep the screen always on. You are advised to call this API in the **onShow()** phase to enable the always-on mode.

> **NOTE**
>
> - Except for lite wearables, this API is no longer maintained since API version 7. You are advised to use [window.setWindowKeepScreenOn()](../apis-arkui/arkts-apis-window-Window.md#setwindowkeepscreenon9) instead.
> - On lite wearables, this API can only prevent the screen from turning off due to system inactivity timeout (automatic). It cannot prevent the screen from turning off due to user actions (such as covering the screen) or the end of the always-on period (the valid duration of screen always-on set by the system).

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [SetKeepScreenOnOptions](#setkeepscreenonoptionsdeprecated) | No | Options for setting the screen always on. This parameter is optional and left empty by default. If this parameter is not passed, the screen always-on state cannot be set, and the API call has no effect. |

**Example**

ArkTS example:
  ```js
  brightness.setKeepScreenOn({
      keepScreenOn: true,
      success: () => {
        console.info('handling set keep screen on success.');
      },
      fail: (data: string, code: number) => {
        console.error(`Failed to set keep screen on. Code: ${code}, message: ${data}`);
      }
  });
  ```

JS example:
```xml
<!-- xxx.hml -->
<div class="container">
    <input type="button" value="SetKeepScreenOn" style="width: 240px; height: 50px; margin: 5px;" onclick="setKeepScreenOn"></input>
    <text class="title">setKeepScreenOn: {{ keepScreenOn }}</text>
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
import brightness from '@system.brightness';

export default {
    data: {
        keepScreenOn: true
    },
    setKeepScreenOn() {
        const TAG = 'set_keep_screen_on_success_test';
        brightness.setKeepScreenOn({
            keepScreenOn: this.keepScreenOn,
            success: () => {
                console.info(`${TAG} setKeepScreenOn success`);
            },
            fail: (data, code) => {
                console.error(`Failed to set keep screen on. Code: ${code}, message: ${data}`);
            },
            complete: () => {
                console.info(`${TAG} setKeepScreenOn complete`);
            }
        });
    },
}
```

## GetBrightnessOptions<sup>(deprecated)</sup>

Options for obtaining the screen brightness.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

| Name    | Type                                                     | Mandatory| Description                                                        |
| -------- | --------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| success  | (data: [BrightnessResponse](#brightnessresponsedeprecated)) => void | No  | Called when an API call is successful. **data** is a return value of the [BrightnessResponse](#brightnessresponsedeprecated) type.|
| fail     | (data: string, code: number) => void                      | No  | Called when an API call has failed. **data** indicates the error information, and **code** indicates the error code.      |
| complete | () => void                                                | No   | Callback invoked when the API call ends, regardless of whether the API call succeeds or fails. Pass this callback when you need to execute cleanup or state update logic after the operation is complete. When no value is passed, the completion callback logic is not executed.                                     |

## SetBrightnessOptions<sup>(deprecated)</sup>

Options for setting the screen brightness.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

| Name    | Type                                | Mandatory| Description                                                        |
| -------- | ------------------------------------ | ---- | ------------------------------------------------------------ |
| value    | number                               | Yes   | Screen brightness. The value is an integer ranging from 1 to 255.<br>-&nbsp;If the value is less than or equal to 0, value **1** will be used.<br>-&nbsp;If the value is greater than 255, value **255** will be used.<br>-&nbsp;If the value contains decimals, the integral part of the value will be used. For example, if value **8.1** is set, value **8** will be used. |
| success  | () => void                           | No  | Called when an API call is successful.                                    |
| fail     | (data: string, code: number) => void | No  | Called when an API call has failed. **data** indicates the error information, and **code** indicates the error code.      |
| complete | () => void                           | No   | Callback invoked when the API call ends. It is executed regardless of whether the API call succeeds or fails. Pass this parameter when you need to execute cleanup or state update logic after the operation is complete. If this parameter is not passed, the completion callback logic is not executed.                                     |

## BrightnessResponse<sup>(deprecated)</sup>

Defines a response that returns the screen brightness.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

| Name| Type| Readable| Writable| Description|
| -------- | -------- | -------- | -------- | -------- |
| value | number | Yes | No | Screen brightness. The value must be an integer ranging from 1 to 255. |

## GetBrightnessModeOptions<sup>(deprecated)</sup>

Options for obtaining the screen brightness mode.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

| Name    | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| success  | (data: [BrightnessModeResponse](#brightnessmoderesponsedeprecated)) => void | No  | Called when an API call is successful. **data** is a return value of the [BrightnessModeResponse](#brightnessmoderesponsedeprecated) type.|
| fail     | (data: string, code: number) => void                         | No  | Called when an API call has failed. **data** indicates the error information, and **code** indicates the error code.      |
| complete | () => void                                                   | No   | Callback invoked when the API call is complete, which is executed regardless of API call success or failure. Pass this parameter when you need to execute cleanup or state update logic after the operation is complete. When this parameter is not passed, the completion callback logic is not executed.                                     |

## SetBrightnessModeOptions<sup>(deprecated)</sup>

Options for setting the screen brightness mode.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

| Name    | Type                                | Mandatory| Description                                                  |
| -------- | ------------------------------------ | ---- | ------------------------------------------------------ |
| mode     | number                               | Yes  | The value **0** indicates the manual adjustment mode, and the value **1** indicates the automatic adjustment mode.|
| success  | () => void                           | No  | Called when an API call is successful.                              |
| fail     | (data: string, code: number) => void | No  | Called when an API call has failed. **data** indicates the error information, and **code** indicates the error code.|
| complete | () => void                           | No   | Callback invoked when the API call is complete, which is executed regardless of API call success or failure. Pass it when you need to execute cleanup or state update logic after the operation is complete. When not passed, the completion callback logic is not executed.                               |

## BrightnessModeResponse<sup>(deprecated)</sup>

Defines a response that returns the screen brightness mode.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

| Name| Type| Readable| Writable| Description|
| -------- | -------- | -------- | -------- | -------- |
| mode | number | Yes| No| The value **0** indicates the manual adjustment mode, and the value **1** indicates the automatic adjustment mode.|

## SetKeepScreenOnOptions<sup>(deprecated)</sup>

Options for setting the screen to be steady on.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

| Name        | Type                                | Mandatory| Description                                                  |
| ------------ | ------------------------------------ | ---- | ------------------------------------------------------ |
| keepScreenOn | boolean                              | Yes   | The value **true** indicates keeping the screen always on (this setting can only prevent the screen from turning off due to system inactivity timeout, but cannot prevent the screen from turning off caused by user operations or the end of the always-on period), and **false** indicates canceling keeping the screen always on.          |
| success      | () => void                           | No  | Called when an API call is successful.                              |
| fail         | (data: string, code: number) => void | No  | Called when an API call has failed. **data** indicates the error information, and **code** indicates the error code.|
| complete     | () => void                           | No   | Callback invoked when the API call is complete,  which is executed regardless of API call success or failure. Pass this parameter when you need to execute cleanup or state update logic after the operation is complete; when not passed, the completion callback logic is not executed.                               |

