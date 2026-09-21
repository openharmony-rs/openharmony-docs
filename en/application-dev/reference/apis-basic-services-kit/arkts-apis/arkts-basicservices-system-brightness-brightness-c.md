# Brightness

```TypeScript
export default class Brightness
```

The module provides APIs for querying and adjusting the screen brightness and mode.

**Since:** 3

**Deprecated since:** 7

**System capability:** SystemCapability.PowerManager.DisplayPowerManager.Lite

## Modules to Import

```TypeScript
import { Brightness, BrightnessModeResponse, BrightnessResponse, GetBrightnessModeOptions, GetBrightnessOptions, SetBrightnessModeOptions, SetBrightnessOptions, SetKeepScreenOnOptions } from '@kit.BasicServicesKit';
```

## getMode

```TypeScript
static getMode(options?: GetBrightnessModeOptions): void
```

Obtains the screen brightness adjustment mode.

**Since:** 3

**Deprecated since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.PowerManager.DisplayPowerManager.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [GetBrightnessModeOptions](arkts-basicservices-system-brightness-getbrightnessmodeoptions-i.md) | No | Options for obtaining the screen brightness mode. This parameter is optional and is left blank by default. |

**Examples**

ArkTS example:

```TypeScript
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

```TypeScript
<!-- xxx.hml -->
<div class="container">
    <input type="button" value="Get Mode" style="width: 240px; height: 50px; margin: 5px;" onclick="getMode"></input>
    <text class="title">getMode: {{ mode }}</text>
</div>
```

```TypeScript
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

```TypeScript
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

## getValue

```TypeScript
static getValue(options?: GetBrightnessOptions): void
```

Obtains the current screen brightness.

**Since:** 3

**Deprecated since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.PowerManager.DisplayPowerManager.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [GetBrightnessOptions](arkts-basicservices-system-brightness-getbrightnessoptions-i.md) | No | Options for obtaining the screen brightness. This parameter is optional and is left blank by default. |

**Examples**

ArkTS example:

```TypeScript
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

```TypeScript
<!-- xxx.hml -->
<div class="container">
    <input type="button" value="Get Value" style="width: 240px; height: 50px; margin: 5px;" onclick="getValue"></input>
    <text class="title">getValue: {{ value }}</text>
</div>
```

```TypeScript
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

```TypeScript
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

## setKeepScreenOn

```TypeScript
static setKeepScreenOn(options?: SetKeepScreenOnOptions): void
```

Sets whether to always keep the screen on. Call this API in **onShow()**.

**NOTE:** 

- This API is no longer maintained since API version 7 except for lite wearables. You are advised to use [window.setWindowKeepScreenOn()](../../../reference/apis-arkui/arkts-apis-window-Window.md#setwindowkeepscreenon9) instead.

- On Lite Wearables, this API can only prevent the system from turning off the screen due to inactivity  
timeout (automatic). It cannot prevent screen-off caused by user actions (such as covering the screen) or the end of the keep-screen-on period.

**Since:** 3

**Deprecated since:** 7

**Substitutes:** setWindowKeepScreenOn

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.PowerManager.DisplayPowerManager.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SetKeepScreenOnOptions](arkts-basicservices-system-brightness-setkeepscreenonoptions-i.md) | No | Options for setting the screen to be steady on. This parameter is optional and is left blank by default. |

**Examples**

ArkTS example:

```TypeScript
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

```TypeScript
<!-- xxx.hml -->
<div class="container">
    <input type="button" value="SetKeepScreenOn" style="width: 240px; height: 50px; margin: 5px;" onclick="setKeepScreenOn"></input>
    <text class="title">setKeepScreenOn: {{ keepScreenOn }}</text>
</div>
```

```TypeScript
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

```TypeScript
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

## setMode

```TypeScript
static setMode(options?: SetBrightnessModeOptions): void
```

Sets the screen brightness adjustment mode.

**Since:** 3

**Deprecated since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.PowerManager.DisplayPowerManager.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SetBrightnessModeOptions](arkts-basicservices-system-brightness-setbrightnessmodeoptions-i.md) | No | Options for setting the screen brightness mode. This parameter is optional and is left blank by default. |

**Examples**

ArkTS example:

```TypeScript
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

```TypeScript
<!-- xxx.hml -->
<div class="container">
    <input type="button" value="Set Mode" style="width: 240px; height: 50px; margin: 5px;" onclick="setMode"></input>
    <text class="title">setMode: {{ mode }}</text>
</div>
```

```TypeScript
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

```TypeScript
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

## setValue

```TypeScript
static setValue(options?: SetBrightnessOptions): void
```

Sets the screen brightness.

**Since:** 3

**Deprecated since:** 7

**Substitutes:** [setValue](arkts-basicservices-brightness-setvalue-f-sys.md)

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.PowerManager.DisplayPowerManager.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SetBrightnessOptions](arkts-basicservices-system-brightness-setbrightnessoptions-i.md) | No | Options for setting the screen brightness. This parameter is optional and is left blank by default. |

**Examples**

ArkTS example:

```TypeScript
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

```TypeScript
<!-- xxx.hml -->
<div class="container">
    <input type="button" value="Set Value" style="width: 240px; height: 50px; margin: 5px;" onclick="setValue"></input>
    <text class="title">setValue: {{ value }}</text>
</div>
```

```TypeScript
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

```TypeScript
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
