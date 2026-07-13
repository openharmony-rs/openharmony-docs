# Brightness

该模块提供屏幕亮度和模式的查询、调节接口。

**起始版本：** 3

**废弃版本：** 7

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## getMode

```TypeScript
static getMode(options?: GetBrightnessModeOptions): void
```

获得当前屏幕亮度模式。

**起始版本：** 3

**废弃版本：** 7

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | GetBrightnessModeOptions | 否 | 获取屏幕亮度模式的参数对象。可选，默认为空。 |

**示例：**

ArkTS示例：

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

JS示例：

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

获得设备当前的屏幕亮度值。

**起始版本：** 3

**废弃版本：** 7

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | GetBrightnessOptions | 否 | 获取屏幕亮度的参数对象。可选，默认为空。 |

**示例：**

ArkTS示例：

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

JS示例：

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

设置屏幕是否保持常亮状态，开启常亮模式推荐在onShow()阶段调用。

注意：

- 除Lite Wearable外，从API version 7开始不再维护，建议使用[window.setWindowKeepScreenOn()](../../../../reference/apis-arkui/arkts-apis-window-Window.md#setwindowkeepscreenon9)替代。

- 在Lite Wearable上，该接口仅能阻止系统无活动超时灭屏（自动），无法阻止用户主动操作（如盖屏）、常亮时刻结束等导致的灭屏。

**起始版本：** 3

**废弃版本：** 7

**替代接口：** setWindowKeepScreenOn

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | SetKeepScreenOnOptions | 否 | 设置屏幕常亮的参数对象。可选，默认为空。 |

**示例：**

ArkTS示例：

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

JS示例：

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

设置设备当前的屏幕亮度模式。

**起始版本：** 3

**废弃版本：** 7

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | SetBrightnessModeOptions | 否 | 设置屏幕亮度模式的参数对象。可选，默认为空。 |

**示例：**

ArkTS示例：

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

JS示例：

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

设置设备当前的屏幕亮度值。

**起始版本：** 3

**废弃版本：** 7

**替代接口：** [setValue](arkts-basicservices-setvalue-f-sys.md#setvalue-1)

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | SetBrightnessOptions | 否 | 设置屏幕亮度的参数对象。可选，默认为空。 |

**示例：**

ArkTS示例：

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

JS示例：

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

