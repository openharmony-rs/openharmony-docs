# @system.brightness (屏幕亮度)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->

该模块提供屏幕亮度、模式的查询、调节接口，以及屏幕常亮的设置接口。

> **说明：**
>
>- 模块维护策略：
>
>    \- 对于Lite Wearable设备类型，该模块长期维护，正常使用。
>
>    \- 对于支持该模块的其他设备类型，该模块从API Version 7 开始不再维护<!--Del-->。建议使用[@ohos.brightness](js-apis-brightness-sys.md)替代<!--DelEnd-->，替代接口能力仅对系统应用开放。
>
>- 本模块首批接口从API version 3开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>


## 导入模块


```js
import brightness, { BrightnessModeResponse, BrightnessResponse } from '@system.brightness';
```

## Brightness

提供屏幕亮度、模式的查询、调节接口，以及屏幕常亮的设置接口。

### getValue<sup>(deprecated)</sup>

getValue(options?: GetBrightnessOptions): void

获取设备当前的屏幕亮度值。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| options | [GetBrightnessOptions](#getbrightnessoptionsdeprecated) | 否   | 获取屏幕亮度的参数对象。可选，默认为空。不传入此参数时，将无法通过回调接收亮度查询结果。 |

**示例：**

ArkTS示例：
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

JS示例：
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

设置设备当前的屏幕亮度值。设置的亮度值会被系统校正：超出1-255范围的值自动调整至有效范围，小数截断为整数。详见[SetBrightnessOptions](#setbrightnessoptionsdeprecated)中value参数说明。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| options | [SetBrightnessOptions](#setbrightnessoptionsdeprecated) | 否   | 设置屏幕亮度的参数对象。可选，默认为空。不传入此参数时，无法设置亮度值，接口调用无实际效果。 |

**示例：**

ArkTS示例：
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

JS示例：
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

获取设备当前的屏幕亮度模式。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| options | [GetBrightnessModeOptions](#getbrightnessmodeoptionsdeprecated) | 否 | 获取屏幕亮度模式的参数对象。可选，默认为空。不传入此参数时，将无法通过回调接收模式查询结果。 |

**示例：**

ArkTS示例：
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

JS示例：
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

设置设备当前的屏幕亮度模式。支持手动调节（mode=0）和自动调节（mode=1）两种模式。详见[SetBrightnessModeOptions](#setbrightnessmodeoptionsdeprecated)中mode参数说明。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| options | [SetBrightnessModeOptions](#setbrightnessmodeoptionsdeprecated) | 否   | 设置屏幕亮度模式的参数对象。可选，默认为空。不传入此参数时，无法设置亮度模式，接口调用无实际效果。 |

**示例：**

ArkTS示例：
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

JS示例：
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

设置屏幕是否保持常亮状态，开启常亮模式推荐在`onShow()`阶段调用。

> **注意：**
>
> - 除Lite Wearable外，从API version 7开始不再维护，建议使用[window.setWindowKeepScreenOn()](../apis-arkui/arkts-apis-window-Window.md#setwindowkeepscreenon9)替代。
> - 在Lite Wearable上，该接口仅能阻止系统无活动超时灭屏（自动），无法阻止用户主动操作（如盖屏）、常亮时刻（系统设定的屏幕常亮有效时长）结束等导致的灭屏。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| options | [SetKeepScreenOnOptions](#setkeepscreenonoptionsdeprecated) | 否 | 设置屏幕常亮的参数对象。可选，默认为空。不传入此参数时，无法设置屏幕常亮状态，接口调用无实际效果。 |

**示例：**

ArkTS示例：
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

JS示例：
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

获取屏幕亮度的参数对象。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

| 名称     | 类型                                                      | 必填 | 说明                                                         |
| -------- | --------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| success  | (data: [BrightnessResponse](#brightnessresponsedeprecated)) => void | 否   | 接口调用成功的回调函数。data为[BrightnessResponse](#brightnessresponsedeprecated)类型的返回值。 |
| fail     | (data: string, code: number) => void                      | 否   | 接口调用失败的回调函数。data为错误信息，code为错误码。       |
| complete | () => void                                                | 否   | 接口调用结束的回调函数，无论接口调用成功或失败都会执行。当需要在操作完成后执行清理或状态更新等逻辑时传入，不传入时不执行结束回调逻辑。                                     |

## SetBrightnessOptions<sup>(deprecated)</sup>

设置屏幕亮度的参数对象。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

| 名称     | 类型                                 | 必填 | 说明                                                         |
| -------- | ------------------------------------ | ---- | ------------------------------------------------------------ |
| value    | number                               | 是   | 屏幕亮度，值为1-255之间的整数。<br>-&nbsp;如果值小于等于0，系统按1处理。<br>-&nbsp;如果值大于255，系统按255处理。<br>-&nbsp;如果值为小数，系统将处理为整数。例如设置为8.1，系统按8处理。 |
| success  | () => void                           | 否   | 接口调用成功的回调函数。                                     |
| fail     | (data: string, code: number) => void | 否   | 接口调用失败的回调函数。data为错误信息，code为错误码。       |
| complete | () => void                           | 否   | 接口调用结束的回调函数，无论接口调用成功或失败都会执行。当需要在操作完成后执行清理或状态更新等逻辑时传入，不传入时不执行结束回调逻辑。                                     |

## BrightnessResponse<sup>(deprecated)</sup>

包含屏幕亮度的对象。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

| 名称 | 类型 | 可读 | 可写 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| value | number | 是 | 否 | 屏幕亮度，范围为1到255的整数。 |

## GetBrightnessModeOptions<sup>(deprecated)</sup>

获取屏幕亮度模式的参数对象。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

| 名称     | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| success  | (data: [BrightnessModeResponse](#brightnessmoderesponsedeprecated)) => void | 否   | 接口调用成功的回调函数。data为[BrightnessModeResponse](#brightnessmoderesponsedeprecated)类型的返回值。 |
| fail     | (data: string, code: number) => void                         | 否   | 接口调用失败的回调函数。data为错误信息，code为错误码。       |
| complete | () => void                                                   | 否   | 接口调用结束的回调函数，无论接口调用成功或失败都会执行。当需要在操作完成后执行清理或状态更新等逻辑时传入，不传入时不执行结束回调逻辑。                                     |

## SetBrightnessModeOptions<sup>(deprecated)</sup>

设置屏幕亮度模式的参数对象。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

| 名称     | 类型                                 | 必填 | 说明                                                   |
| -------- | ------------------------------------ | ---- | ------------------------------------------------------ |
| mode     | number                               | 是   | 0表示手动调节屏幕亮度模式，1表示自动调节屏幕亮度模式。 |
| success  | () => void                           | 否   | 接口调用成功的回调函数。                               |
| fail     | (data: string, code: number) => void | 否   | 接口调用失败的回调函数。data为错误信息，code为错误码。 |
| complete | () => void                           | 否   | 接口调用结束的回调函数，无论接口调用成功或失败都会执行。当需要在操作完成后执行清理或状态更新等逻辑时传入，不传入时不执行结束回调逻辑。                               |

## BrightnessModeResponse<sup>(deprecated)</sup>

包含屏幕亮度模式的对象。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

| 名称 | 类型 | 可读 | 可写 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| mode | number | 是 | 否 | 0表示手动调节屏幕亮度模式，1表示自动调节屏幕亮度模式。 |

## SetKeepScreenOnOptions<sup>(deprecated)</sup>

设置屏幕常亮的参数对象。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

| 名称         | 类型                                 | 必填 | 说明                                                   |
| ------------ | ------------------------------------ | ---- | ------------------------------------------------------ |
| keepScreenOn | boolean                              | 是   | true表示保持屏幕常亮（仅阻止系统无活动超时灭屏，无法阻止用户主动操作或常亮时刻结束等导致的灭屏），false表示取消屏幕常亮。          |
| success      | () => void                           | 否   | 接口调用成功的回调函数。                               |
| fail         | (data: string, code: number) => void | 否   | 接口调用失败的回调函数。data为错误信息，code为错误码。 |
| complete     | () => void                           | 否   | 接口调用结束的回调函数，无论接口调用成功或失败都会执行。当需要在操作完成后执行清理或状态更新等逻辑时传入，不传入时不执行结束回调逻辑。                               |

