# @system.brightness (Screen Brightness)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->

The **brightness** module provides APIs for querying and adjusting the screen brightness and mode.

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

The **brightness** module provides APIs for querying and adjusting the screen brightness and mode.

### getValue<sup>(deprecated)</sup>

getValue(options?: GetBrightnessOptions): void

Obtains the current screen brightness.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [GetBrightnessOptions](#getbrightnessoptionsdeprecated) | No  | Options for obtaining the screen brightness. This parameter is optional and is left blank by default.|

**Example**

ArkTS example:
  ```js
  brightness.getValue({
      success: (data: BrightnessResponse) => {
        console.info('success get brightness value:' + data.value);
      },
      fail: (data: string, code: number) => {
        console.error('get brightness fail, code: ' + code + ', data: ' + data);
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
        let TAG = 'get_value_success_test';
        brightness.getValue({
            success: (brightnessResponse) => {
                this.value = brightnessResponse.value;
                console.info(`${TAG} brightnessResponse.value: ${brightnessResponse.value}`);
            },
            fail: (data, code) => {
                console.error(`${TAG} fail data: ${data}, code: ${code}`);
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

Sets the screen brightness.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [SetBrightnessOptions](#setbrightnessoptionsdeprecated) | No  | Options for setting the screen brightness. This parameter is optional and is left blank by default.|

**Example**

ArkTS example:
  ```js
  brightness.setValue({
      value: 100,
      success: () => {
        console.info('handling set brightness success.');
      },
      fail: (data: string, code: number) => {
        console.error('handling set brightness value fail, code:' + code + ', data: ' + data);
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
        let TAG = 'set_value_success_test';
        brightness.setValue({
            value: this.value,
            success: () => {
                console.info(`${TAG} setValue success!`);
            },
            fail: (data, code) => {
                console.error(`${TAG} fail data: ${data}, code: ${code}`);
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

Obtains the screen brightness adjustment mode.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [GetBrightnessModeOptions](#getbrightnessmodeoptionsdeprecated) | No| Options for obtaining the screen brightness mode. This parameter is optional and is left blank by default.|

**Example**

ArkTS example:
  ```js
  brightness.getMode({
      success: (data: BrightnessModeResponse) => {
        console.info('success get mode:' + data.mode);
      },
      fail: (data: string, code: number) => {
        console.error('handling get mode fail, code:' + code + ', data: ' + data);
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
        let TAG = 'get_mode_success_test';
        brightness.getMode({
            success: (brightnessModeResponse) => {
                this.mode = brightnessModeResponse.mode;
                console.info(`${TAG} brightnessModeResponse mode: ${brightnessModeResponse.mode}`);
            },
            fail: (data, code) => {
                console.error(`${TAG} fail data: ${data}, code: ${code}`);
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

Sets the screen brightness mode.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

**Parameters**
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [SetBrightnessModeOptions](#setbrightnessmodeoptionsdeprecated) | No  | Options for setting the screen brightness mode. This parameter is optional and is left blank by default.|

**Example**

ArkTS example:
  ```js
  brightness.setMode({
      mode: 1,
      success: () => {
        console.info('handling set mode success.');
      },
      fail: (data: string, code: number) => {
        console.error('handling set mode fail, code:' + code + ', data: ' + data);
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
        let TAG = 'set_mode_success_test';
        brightness.setMode({
            mode: this.mode,
            success: () => {
                console.info(`${TAG} setMode success`);
            },
            fail: (data, code) => {
                console.error(`${TAG} fail data: ${data}, code: ${code}`);
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

Sets whether to always keep the screen on. Call this API in **onShow()**.

> **NOTE**
>
> - This API is no longer maintained since API version 7 except for lite wearables. You are advised to use [window.setWindowKeepScreenOn()](../apis-arkui/arkts-apis-window-Window.md#setwindowkeepscreenon9) instead.
> - On lite wearables, this API can only prevent the screen from turning off (automatically) due to inactivity. It cannot prevent the screen from turning off due to user actions (such as covering the screen) or the end of screen-on time.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [SetKeepScreenOnOptions](#setkeepscreenonoptionsdeprecated) | No| Options for setting the screen to be steady on. This parameter is optional and is left blank by default.|

**Example**

ArkTS example:
  ```js
  brightness.setKeepScreenOn({
      keepScreenOn: true,
      success: () => {
        console.info('handling set keep screen on success.');
      },
      fail: (data: string, code: number) => {
        console.error('handling set keep screen on fail, code:' + code + ', data: ' + data);
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
        let TAG = 'set_keep_screen_on_success_test';
        brightness.setKeepScreenOn({
            keepScreenOn: this.keepScreenOn,
            success: () => {
                console.info(`${TAG} setKeepScreenOn success`);
            },
            fail: (data, code) => {
                console.error(`${TAG} fail data: ${data}, code: ${code}`);
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
| complete | () => void                                                | No  | Called when an API call is complete.                                    |

## SetBrightnessOptions<sup>(deprecated)</sup>

Options for setting the screen brightness.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

| Name    | Type                                | Mandatory| Description                                                        |
| -------- | ------------------------------------ | ---- | ------------------------------------------------------------ |
| value    | number                               | Yes  | Screen brightness. The value is an integer ranging from **1** to **255**.<br>- If the value is less than or equal to **0**, value **1** will be used.<br>- If the value is greater than **255**, value **255** will be used.<br>- If the value contains decimals, the integral part of the value will be used. For example, if value **8.1** is set, value **8** will be used.|
| success  | () => void                           | No  | Called when an API call is successful.                                    |
| fail     | (data: string, code: number) => void | No  | Called when an API call has failed. **data** indicates the error information, and **code** indicates the error code.      |
| complete | () => void                           | No  | Called when an API call is complete.                                    |

## BrightnessResponse<sup>(deprecated)</sup>

Defines a response that returns the screen brightness.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

| Name| Type| Readable| Writable| Description|
| -------- | -------- | -------- | -------- | -------- |
| value | number | Yes| No| Screen brightness. The value ranges from **1** to **255**.|

## GetBrightnessModeOptions<sup>(deprecated)</sup>

Options for obtaining the screen brightness mode.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

| Name    | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| success  | (data: [BrightnessModeResponse](#brightnessmoderesponsedeprecated)) => void | No  | Called when an API call is successful. **data** is a return value of the [BrightnessModeResponse](#brightnessmoderesponsedeprecated) type.|
| fail     | (data: string, code: number) => void                         | No  | Called when an API call has failed. **data** indicates the error information, and **code** indicates the error code.      |
| complete | () => void                                                   | No  | Called when an API call is complete.                                    |

## SetBrightnessModeOptions<sup>(deprecated)</sup>

Options for setting the screen brightness mode.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager.Lite

| Name    | Type                                | Mandatory| Description                                                  |
| -------- | ------------------------------------ | ---- | ------------------------------------------------------ |
| mode     | number                               | Yes  | The value **0** indicates the manual adjustment mode, and the value **1** indicates the automatic adjustment mode.|
| success  | () => void                           | No  | Called when an API call is successful.                              |
| fail     | (data: string, code: number) => void | No  | Called when an API call has failed. **data** indicates the error information, and **code** indicates the error code.|
| complete | () => void                           | No  | Called when an API call is complete.                              |

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
| keepScreenOn | boolean                              | Yes  | The value **true** means to keep the screen steady on, and the value **false** indicates the opposite.         |
| success      | () => void                           | No  | Called when an API call is successful.                              |
| fail         | (data: string, code: number) => void | No  | Called when an API call has failed. **data** indicates the error information, and **code** indicates the error code.|
| complete     | () => void                           | No  | Called when an API call is complete.                              |
