# @ohos.multimodalInput.inputMonitor (输入监听)(系统接口)

输入监听模块，提供了监听输入设备事件的能力。输入设备事件当前包括触屏事件、鼠标输入事件和触控板输入事件。

>**说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
>- 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
>- 文档中“全局”表示整个触控屏或触控板。如监听全局触屏事件，表示触摸触控板任何位置时，整个触控板的触屏事件均被监听。
>
>- 本模块接口均为系统接口。

## 导入模块

```js
import { inputMonitor } from '@kit.InputKit';
```

## <span id = "on_touch_dyn">inputMonitor.on('touch')</span>

on(type: 'touch', receiver: TouchEventReceiver): void

监听全局触屏事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[onTouch](#on_touch_sta)

**ArkTS-Dyn起始版本**：7

**参数：**

| 参数名       | 类型                                       | 必填   | 说明                  |
| -------- | ---------------------------------------- | ---- | ------------------- |
| type     | string                                   | 是    | 输入设备事件类型，取值'touch'。 |
| receiver | [TouchEventReceiver](#toucheventreceiver) | 是    | 回调函数，异步上报触摸屏输入事件。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputMonitor.on('touch', (touchEvent: TouchEvent) => {
              console.log(`Monitor on success ${JSON.stringify(touchEvent)}`);
              return false;
            });
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_touch_sta">inputMonitor.onTouch<sup>22+</sup></span>

onTouch(type: 'touch', receiver: TouchEventReceiver): void

监听全局触屏事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[on](#on_touch_dyn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名       | 类型                                       | 必填   | 说明                  |
| -------- | ---------------------------------------- | ---- | ------------------- |
| receiver | [TouchEventReceiver](#toucheventreceiver) | 是    | 回调函数，异步上报触摸屏输入事件。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputMonitor.onTouch('touch', (touchEvent: TouchEvent) => {
              console.log(`Monitor on success ${JSON.stringify(touchEvent)}`);
              return false;
            });
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_mouse_dyn">inputMonitor.on('mouse')<sup>9+</sup></span>

on(type: 'mouse', receiver: Callback&lt;MouseEvent&gt;): void

监听全局鼠标事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[onMouse](#on_mouse_sta)

**ArkTS-Dyn起始版本**：9

**参数：** 

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | 是    | 输入设备事件类型，取值'mouse'。 |
| receiver | Callback&lt;[MouseEvent](js-apis-mouseevent.md#mouseevent)&gt; | 是    | 回调函数，异步上报鼠标输入事件。  |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';
import { MouseEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputMonitor.on('mouse', (mouseEvent: MouseEvent) => {
              console.log(`Monitor on success ${JSON.stringify(mouseEvent)}`);
              return false;
            });
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_mouse_sta">inputMonitor.onMouse<sup>22+</sup></span>

onMouse(receiver: Callback&lt;MouseEvent&gt;): void

监听全局鼠标事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[onMouse](#on_mouse_dyn)

**ArkTS-Sta起始版本**：22

**参数：** 

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| receiver | Callback&lt;[MouseEvent](js-apis-mouseevent.md#mouseevent)&gt; | 是    | 回调函数，异步上报鼠标输入事件。  |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';
import { MouseEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputMonitor.onMouse((mouseEvent: MouseEvent) => {
              console.log(`Monitor on success ${JSON.stringify(mouseEvent)}`);
              return false;
            });
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_mouse_rect_dyn">inputMonitor.on('mouse')<sup>11+</sup></span>

on(type: 'mouse', rect: display.Rect[], receiver: Callback&lt;MouseEvent&gt;): void

监听鼠标事件，当鼠标移动至指定矩形区域内时，触发回调任务。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[onMouse](#on_mouse_rect_sta)

**ArkTS-Dyn起始版本**：11

**参数：** 

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | 是    | 输入设备事件类型，取值'mouse'。 |
| rect     | display.Rect[]             | 是    | 可以触发回调任务的矩形区域，可传入1至2个。 |
| receiver | Callback&lt;[MouseEvent](js-apis-mouseevent.md#mouseevent)&gt; | 是    | 回调函数，异步上报鼠标输入事件。  |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';
import { MouseEvent } from '@kit.InputKit';
import { display } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          /**
           * 鼠标在矩形区域内时，触发的回调任务。
           */
          let callback = (mouseEvent : MouseEvent) => {
            this.getUIContext().getPromptAction().showToast({
              message: `监听成功：${JSON.stringify(mouseEvent)}`
            })
            console.log(`Monitor on success ${JSON.stringify(mouseEvent)}`);
            return false;
          };

          /**
           * 触发回调事件矩形区域。
           */
          let rect: display.Rect[] = [{
            left: 100,
            top: 100,
            width: 100,
            height: 100
          }, {
            left: 600,
            top: 100,
            width: 100,
            height: 100
          }];

          try {
            inputMonitor.on('mouse', rect, callback);
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_mouse_rect_sta">inputMonitor.onMouse<sup>22+</sup></span>

onMouse(rect: display.Rect[], receiver: Callback&lt;MouseEvent&gt;): void

监听鼠标事件，当鼠标移动至指定矩形区域内时，触发回调任务。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[on](#on_mouse_rect_dyn)

**ArkTS-Sta起始版本**：22

**参数：** 

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| rect     | display.Rect[]             | 是    | 可以触发回调任务的矩形区域，可传入1至2个。 |
| receiver | Callback&lt;[MouseEvent](js-apis-mouseevent.md#mouseevent)&gt; | 是    | 回调函数，异步上报鼠标输入事件。  |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';
import { MouseEvent } from '@kit.InputKit';
import { display } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          /**
           * 鼠标在矩形区域内时，触发的回调任务。
           */
          let callback = (mouseEvent : MouseEvent) => {
            this.getUIContext().getPromptAction().showToast({
              message: `监听成功：${JSON.stringify(mouseEvent)}`
            })
            console.log(`Monitor on success ${JSON.stringify(mouseEvent)}`);
            return false;
          };

          /**
           * 触发回调事件矩形区域。
           */
          let rect: display.Rect[] = [{
            left: 100,
            top: 100,
            width: 100,
            height: 100
          }, {
            left: 600,
            top: 100,
            width: 100,
            height: 100
          }];

          try {
            inputMonitor.onMouse(rect, callback);
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_touch_dyn">inputMonitor.off('touch')</span>

off(type: 'touch', receiver?: TouchEventReceiver): void

取消监听全局触屏事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[offTouch](#off_touch_sta)

**ArkTS-Dyn起始版本**：7

**参数：**

| 参数名       | 类型                                       | 必填   | 说明                  |
| -------- | ---------------------------------------- | ---- | ------------------- |
| type     | string                                   | 是    | 输入设备事件类型，取值'touch'。 |
| receiver | [TouchEventReceiver](#toucheventreceiver) | 否    | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。  |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (touchEvent: TouchEvent) => {
            console.log(`Monitor on success ${JSON.stringify(touchEvent)}`);
            return false;
          };
          try {
            inputMonitor.on('touch', callback);
            inputMonitor.off('touch', callback);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (touchEvent: TouchEvent) => {
            console.log(`Monitor on success ${JSON.stringify(touchEvent)}`);
            return false;
          };
          try {
            inputMonitor.on('touch', callback);
            inputMonitor.off('touch');
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_touch_sta">inputMonitor.offTouch</span>

offTouch(receiver?: TouchEventReceiver): void

取消监听全局触屏事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[off](#off_touch_dyn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名       | 类型                                       | 必填   | 说明                  |
| -------- | ---------------------------------------- | ---- | ------------------- |
| receiver | [TouchEventReceiver](#toucheventreceiver) | 否    | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。  |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (touchEvent: TouchEvent) => {
            console.log(`Monitor on success ${JSON.stringify(touchEvent)}`);
            return false;
          };
          try {
            inputMonitor.onTouch(callback);
            inputMonitor.offTouch(callback);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (touchEvent: TouchEvent) => {
            console.log(`Monitor on success ${JSON.stringify(touchEvent)}`);
            return false;
          };
          try {
            inputMonitor.onTouch(callback);
            inputMonitor.offTouch();
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_mouse_dyn">inputMonitor.off('mouse')<sup>9+</sup></span>

off(type: 'mouse', receiver?: Callback&lt;MouseEvent&gt;): void

取消监听全局鼠标事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[offMouse](#off_mouse_sta)

**ArkTS-Dyn起始版本**：9

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | 是    | 输入设备事件类型，取值'mouse'。 |
| receiver | Callback&lt;MouseEvent&gt; | 否    | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';
import { MouseEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (mouseEvent: MouseEvent) => {
            console.log(`Monitor on success ${JSON.stringify(mouseEvent)}`);
            return false;
          };
          try {
            inputMonitor.on('mouse', callback);
            inputMonitor.off('mouse', callback);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { MouseEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (mouseEvent: MouseEvent) => {
            console.log(`Monitor on success ${JSON.stringify(mouseEvent)}`);
            return false;
          };
          try {
            inputMonitor.on('mouse', callback);
            inputMonitor.off('mouse');
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_mouse_sta">inputMonitor.offMouse<sup>22+</sup></span>

offMouse(receiver?: Callback&lt;MouseEvent&gt;): void

取消监听全局鼠标事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[off](#off_mouse_syn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| receiver | Callback&lt;MouseEvent&gt; | 否    | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';
import { MouseEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (mouseEvent: MouseEvent) => {
            console.log(`Monitor on success ${JSON.stringify(mouseEvent)}`);
            return false;
          };
          try {
            inputMonitor.onMouse(callback);
            inputMonitor.offMouse(callback);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { MouseEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (mouseEvent: MouseEvent) => {
            console.log(`Monitor on success ${JSON.stringify(mouseEvent)}`);
            return false;
          };
          try {
            inputMonitor.onMouse(callback);
            inputMonitor.offMouse();
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## TouchEventReceiver

type TouchEventReceiver = (touchEvent: TouchEvent) => boolean;

触屏输入事件的回调函数。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS-Dyn起始版本**：7

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名         | 类型                                       | 必填   | 说明                                       |
| ---------- | ---------------------------------------- | ---- | ---------------------------------------- |
| touchEvent | [TouchEvent](js-apis-touchevent.md#touchevent) | 是    | 触屏输入事件。 |

**返回值：**

| 类型      | 说明                                       |
| ------- | ---------------------------------------- |
| Boolean | 若返回true，本次触屏后续产生的事件不再分发到窗口；若返回false，本次触屏后续产生的事件还会分发到窗口。 |

ArkTS-Dyn示例：

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputMonitor.on('touch', touchEvent => {
              if (touchEvent.touches.length == 3) { // 当前有三个手指按下
                return true;
              }
              return false;
            });
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputMonitor.onTouch(touchEvent => {
              if (touchEvent.touches.length == 3) { // 当前有三个手指按下
                return true;
              }
              return false;
            });
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_pinch_dyn">inputMonitor.on('pinch')<sup>10+</sup></span>

on(type: 'pinch', receiver: Callback&lt;[Pinch](js-apis-multimodalinput-gestureevent.md#pinch)&gt;): void

监听全局触控板的捏合事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[onPinch](#on_pinch_sta)

**ArkTS-Dyn起始版本**：10

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | 是    | 输入设备事件类型，取值'pinch'。 |
| receiver | Callback&lt;[Pinch](js-apis-multimodalinput-gestureevent.md#pinch)&gt; | 是    | 回调函数，异步上报捏合输入事件。  |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';
import { Pinch } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputMonitor.on('pinch', (pinchEvent) => {
              console.log(`Monitor on success ${JSON.stringify(pinchEvent)}`);
              return false;
            });
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_pinch_sta">inputMonitor.onPinch<sup>22+</sup></span>

onPinch(receiver: Callback&lt;[Pinch](js-apis-multimodalinput-gestureevent.md#pinch)&gt;): void

监听全局触控板的捏合事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Sta接口是[on](#on_pinch_dyn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| receiver | Callback&lt;[Pinch](js-apis-multimodalinput-gestureevent.md#pinch)&gt; | 是    | 回调函数，异步上报捏合输入事件。  |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';
import { Pinch } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputMonitor.onPinch((pinchEvent) => {
              console.log(`Monitor on success ${JSON.stringify(pinchEvent)}`);
              return false;
            });
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_pinch_dyn">inputMonitor.off('pinch')<sup>10+</sup></span>

off(type: 'pinch', receiver?: Callback&lt;[Pinch](js-apis-multimodalinput-gestureevent.md#pinch)&gt;): void

取消监听全局触控板的捏合事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[offPinch](#off_pinch_sta)

**ArkTS-Dyn起始版本**：10


**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | 是    | 输入设备事件类型，取值'pinch'。 |
| receiver | Callback&lt;[Pinch](js-apis-multimodalinput-gestureevent.md#pinch)&gt; | 否    | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';
import { Pinch } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (pinchEvent: Pinch) => {
            console.log(`Monitor on success ${JSON.stringify(pinchEvent)}`);
            return false;
          };
          try {
            inputMonitor.on('pinch', callback);
            inputMonitor.off('pinch', callback);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { Pinch } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (pinchEvent: Pinch) => {
            console.log(`Monitor on success ${JSON.stringify(pinchEvent)}`);
            return false;
          };
          try {
            inputMonitor.on('pinch', callback);
            inputMonitor.off('pinch');
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_pinch_sta">inputMonitor.offPinch'<sup>22+</sup></span>

offPinch(receiver?: Callback&lt;[Pinch](js-apis-multimodalinput-gestureevent.md#pinch)&gt;): void

取消监听全局触控板的捏合事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[off](#off_pinch_dyn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| receiver | Callback&lt;[Pinch](js-apis-multimodalinput-gestureevent.md#pinch)&gt; | 否    | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';
import { Pinch } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (pinchEvent: Pinch) => {
            console.log(`Monitor on success ${JSON.stringify(pinchEvent)}`);
            return false;
          };
          try {
            inputMonitor.onPinch(callback);
            inputMonitor.offPinch(callback);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { Pinch } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (pinchEvent: Pinch) => {
            console.log(`Monitor on success ${JSON.stringify(pinchEvent)}`);
            return false;
          };
          try {
            inputMonitor.onPinch(callback);
            inputMonitor.offPinch();
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_threeFingersSwipe_dyn">inputMonitor.on('threeFingersSwipe')<sup>10+</sup></span>

on(type: 'threeFingersSwipe', receiver: Callback&lt;[ThreeFingersSwipe](js-apis-multimodalinput-gestureevent.md#threefingersswipe)&gt;): void

监听全局触控板的三指滑动事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[onThreeFingersSwipe](#on_threeFingersSwipe_sta)

**ArkTS-Dyn起始版本**：10

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | 是    | 输入设备事件类型，取值'threeFingersSwipe'。 |
| receiver | Callback&lt;[ThreeFingersSwipe](js-apis-multimodalinput-gestureevent.md#threefingersswipe)&gt; | 是    | 回调函数，异步上报三指滑动输入事件。  |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputMonitor.on('threeFingersSwipe', (threeFingersSwipe) => {
              console.log(`Monitor on success ${JSON.stringify(threeFingersSwipe)}`);
              return false;
            });
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_threeFingersSwipe_sta">inputMonitor.onThreeFingersSwipe<sup>22+</sup></span>

onThreeFingersSwipe(receiver: Callback&lt;[ThreeFingersSwipe](js-apis-multimodalinput-gestureevent.md#threefingersswipe)&gt;): void

监听全局触控板的三指滑动事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[onThreeFingersSwipe](#on_threeFingersSwipe_dyn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| receiver | Callback&lt;[ThreeFingersSwipe](js-apis-multimodalinput-gestureevent.md#threefingersswipe)&gt; | 是    | 回调函数，异步上报三指滑动输入事件。  |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputMonitor.onThreeFingersSwipe((threeFingersSwipe) => {
              console.log(`Monitor on success ${JSON.stringify(threeFingersSwipe)}`);
              return false;
            });
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_threeFingersSwipe_dyn">inputMonitor.off('threeFingersSwipe')<sup>10+</sup></span>

off(type: 'threeFingersSwipe', receiver?: Callback&lt;[ThreeFingersSwipe](js-apis-multimodalinput-gestureevent.md#threefingersswipe)&gt;): void

取消监听全局触控板的三指滑动事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[offThreeFingersSwipe](#off_threeFingersSwipe_sta)

**ArkTS-Dyn起始版本**：10

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | 是    | 输入设备事件类型，取值'threeFingersSwipe'。 |
| receiver | Callback&lt;[ThreeFingersSwipe](js-apis-multimodalinput-gestureevent.md#threefingersswipe)&gt; | 否    | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';
import { ThreeFingersSwipe } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (threeFingersSwipe: ThreeFingersSwipe) => {
            console.log(`Monitor on success ${JSON.stringify(threeFingersSwipe)}`);
            return false;
          };
          try {
            inputMonitor.on('threeFingersSwipe', callback);
            inputMonitor.off("threeFingersSwipe", callback);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { ThreeFingersSwipe } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (threeFingersSwipe: ThreeFingersSwipe) => {
            console.log(`Monitor on success ${JSON.stringify(threeFingersSwipe)}`);
            return false;
          };
          try {
            inputMonitor.on("threeFingersSwipe", callback);
            inputMonitor.off("threeFingersSwipe");
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_threeFingersSwipe_sta">inputMonitor.offThreeFingersSwipe<sup>22+</sup></span>

offThreeFingersSwipe(receiver?: Callback&lt;[ThreeFingersSwipe](js-apis-multimodalinput-gestureevent.md#threefingersswipe)&gt;): void

取消监听全局触控板的三指滑动事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[off](#off_threeFingersSwipe_dyn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| receiver | Callback&lt;[ThreeFingersSwipe](js-apis-multimodalinput-gestureevent.md#threefingersswipe)&gt; | 否    | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';
import { ThreeFingersSwipe } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (threeFingersSwipe: ThreeFingersSwipe) => {
            console.log(`Monitor on success ${JSON.stringify(threeFingersSwipe)}`);
            return false;
          };
          try {
            inputMonitor.onThreeFingersSwipe(callback);
            inputMonitor.offThreeFingersSwipe(callback);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { ThreeFingersSwipe } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (threeFingersSwipe: ThreeFingersSwipe) => {
            console.log(`Monitor on success ${JSON.stringify(threeFingersSwipe)}`);
            return false;
          };
          try {
            inputMonitor.onThreeFingersSwipe(callback);
            inputMonitor.offThreeFingersSwipe();
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_fourFingersSwipe_dyn">inputMonitor.on('fourFingersSwipe')<sup>10+</sup></span>

on(type: 'fourFingersSwipe', receiver: Callback&lt;[FourFingersSwipe](js-apis-multimodalinput-gestureevent.md#fourfingersswipe)&gt;): void

监听全局触控板的四指滑动事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[onFourFingersSwipe](#on_fourFingersSwipe_sta)

**ArkTS-Dyn起始版本**：10

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | 是    | 输入设备事件类型，取值'fourFingersSwipe'。 |
| receiver | Callback&lt;[FourFingersSwipe](js-apis-multimodalinput-gestureevent.md#fourfingersswipe)&gt; | 是    | 回调函数，异步上报四指滑动输入事件。  |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputMonitor.on('fourFingersSwipe', (fourFingersSwipe) => {
              console.log(`Monitor on success ${JSON.stringify(fourFingersSwipe)}`);
              return false;
            });
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_fourFingersSwipe_sta">inputMonitor.onFourFingersSwipe<sup>22+</sup></span>

onFourFingersSwipe(receiver: Callback&lt;[FourFingersSwipe](js-apis-multimodalinput-gestureevent.md#fourfingersswipe)&gt;): void

监听全局触控板的四指滑动事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[on](#on_fourFingersSwipe_dyn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| receiver | Callback&lt;[FourFingersSwipe](js-apis-multimodalinput-gestureevent.md#fourfingersswipe)&gt; | 是    | 回调函数，异步上报四指滑动输入事件。  |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputMonitor.onFourFingersSwipe((fourFingersSwipe) => {
              console.log(`Monitor on success ${JSON.stringify(fourFingersSwipe)}`);
              return false;
            });
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_fourFingersSwipe_dyn">inputMonitor.off('fourFingersSwipe')<sup>10+</sup></span>

off(type: 'fourFingersSwipe', receiver?: Callback&lt;[FourFingersSwipe](js-apis-multimodalinput-gestureevent.md#fourfingersswipe)&gt;): void

取消监听全局触控板的四指滑动事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[offFourFingersSwipe](#off_fourFingersSwipe_sta)

**ArkTS-Dyn起始版本**：10

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | 是    | 输入设备事件类型，取值'fourFingersSwipe'。 |
| receiver | Callback&lt;[FourFingersSwipe](js-apis-multimodalinput-gestureevent.md#fourfingersswipe)&gt; | 否    | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';
import { FourFingersSwipe } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (fourFingersSwipe: FourFingersSwipe) => {
            console.log(`Monitor on success ${JSON.stringify(fourFingersSwipe)}`);
            return false;
          };
          try {
            inputMonitor.on('fourFingersSwipe', callback);
            inputMonitor.off('fourFingersSwipe', callback);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { FourFingersSwipe } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (fourFingersSwipe: FourFingersSwipe) => {
            console.log(`Monitor on success ${JSON.stringify(fourFingersSwipe)}`);
            return false;
          };
          try {
            inputMonitor.on('fourFingersSwipe', callback);
            inputMonitor.off('fourFingersSwipe');
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_fourFingersSwipe_sta">inputMonitor.off('fourFingersSwipe')<sup>22+</sup></span>

offFourFingersSwipe(receiver?: Callback&lt;[FourFingersSwipe](js-apis-multimodalinput-gestureevent.md#fourfingersswipe)&gt;): void

取消监听全局触控板的四指滑动事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[off](#off_fourFingersSwipe_dyn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| receiver | Callback&lt;[FourFingersSwipe](js-apis-multimodalinput-gestureevent.md#fourfingersswipe)&gt; | 否    | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';
import { FourFingersSwipe } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (fourFingersSwipe: FourFingersSwipe) => {
            console.log(`Monitor on success ${JSON.stringify(fourFingersSwipe)}`);
            return false;
          };
          try {
            inputMonitor.onFourFingersSwipe(callback);
            inputMonitor.offFourFingersSwipe(callback);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { FourFingersSwipe } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (fourFingersSwipe: FourFingersSwipe) => {
            console.log(`Monitor on success ${JSON.stringify(fourFingersSwipe)}`);
            return false;
          };
          try {
            inputMonitor.onFourFingersSwipe(callback);
            inputMonitor.offFourFingersSwipe();
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_rotate_dyn">inputMonitor.on('rotate')<sup>11+</sup></span>

on(type: 'rotate', fingers: number, receiver: Callback&lt;Rotate&gt;): void

监听全局触控板的旋转事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[onRotate](#on_rotate_sta)

**ArkTS-Dyn起始版本**：11

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | 是    | 输入设备事件类型，取值'rotate'。 |
| fingers     | number                     | 是    | 旋转的手指数，目前支持监听手指数是2。 |
| receiver | Callback&lt;[Rotate](js-apis-multimodalinput-gestureevent.md#rotate11)&gt; | 是    | 回调函数，异步上报旋转输入事件。  |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';
import { Rotate } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputMonitor.on('rotate', 2, (rotateEvent: Rotate) => {
              console.log(`Monitor on success ${JSON.stringify(rotateEvent)}`);
              return false;
            });
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_rotate_sta">inputMonitor.on('rotate')<sup>22+</sup></span>

onRotate(fingers: int, receiver: Callback&lt;Rotate&gt;): void

监听全局触控板的旋转事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[on](#on_rotate_dyn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| fingers     | int                     | 是    | 旋转的手指数，目前支持监听手指数是2。 |
| receiver | Callback&lt;[Rotate](js-apis-multimodalinput-gestureevent.md#rotate11)&gt; | 是    | 回调函数，异步上报旋转输入事件。  |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';
import { Rotate } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputMonitor.onRotate(2, (rotateEvent: Rotate) => {
              console.log(`Monitor on success ${JSON.stringify(rotateEvent)}`);
              return false;
            });
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_rotate_dyn">inputMonitor.off('rotate')<sup>11+</sup></span>

off(type: 'rotate', fingers: number, receiver?: Callback&lt;Rotate&gt;): void

取消监听全局触控板的旋转事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[offRotate](#off_rotate_sta)

**ArkTS-Dyn起始版本**：11

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | 是    | 输入设备事件类型，取值'rotate'。 |
| fingers     | number                     | 是    | 旋转的手指数，目前支持监听手指数是2。 |
| receiver | Callback&lt;[Rotate](js-apis-multimodalinput-gestureevent.md#rotate11)&gt; | 否    | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';
import { Rotate } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (rotateEvent: Rotate) => {
            console.log(`Monitor on success ${JSON.stringify(rotateEvent)}`);
            return false;
          };
          try {
            inputMonitor.on('rotate', 2, callback);
            inputMonitor.off('rotate', 2, callback);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { Rotate } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (rotateEvent: Rotate) => {
            console.log(`Monitor on success ${JSON.stringify(rotateEvent)}`);
            return false;
          };
          try {
            inputMonitor.on('rotate', 2, callback);
            inputMonitor.off('rotate', 2);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_rotate_sta">inputMonitor.offRotate<sup>22+</sup></span>

offRotate(fingers: int, receiver?: Callback&lt;Rotate&gt;): void

取消监听全局触控板的旋转事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[off](#off_rotate_dyn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| fingers     | int                     | 是    | 旋转的手指数，目前支持监听手指数是2。 |
| receiver | Callback&lt;[Rotate](js-apis-multimodalinput-gestureevent.md#rotate11)&gt; | 否    | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';
import { Rotate } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (rotateEvent: Rotate) => {
            console.log(`Monitor on success ${JSON.stringify(rotateEvent)}`);
            return false;
          };
          try {
            inputMonitor.onRotate(2, callback);
            inputMonitor.offRotate(2, callback);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { Rotate } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (rotateEvent: Rotate) => {
            console.log(`Monitor on success ${JSON.stringify(rotateEvent)}`);
            return false;
          };
          try {
            inputMonitor.onRotate(2, callback);
            inputMonitor.offRrotate(2);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_pinch_dyn">inputMonitor.on('pinch')<sup>11+</sup></span>

on(type: 'pinch', fingers: number, receiver: Callback&lt;Pinch&gt;): void

监听全局触控板的捏合事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[onPinch](#on_pinch_sta)

**ArkTS-Dyn起始版本**：11

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | 是    | 输入设备事件类型，取值'pinch'。 |
| fingers     | number                     | 是    | 捏合的手指数，取值范围：大于等于2。 |
| receiver | Callback&lt;[Pinch](js-apis-multimodalinput-gestureevent.md#pinch)&gt; | 是    | 回调函数，异步上报捏合输入事件。  |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';
import { Pinch } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputMonitor.on('pinch', 2, (pinchEvent: Pinch) => {
              console.log(`Monitor on success ${JSON.stringify(pinchEvent)}`);
              return false;
            });
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_pinch_sta">inputMonitor.onPinch<sup>22+</sup></span>

onPinch(fingers: int, receiver: Callback&lt;Pinch&gt;): void

监听全局触控板的捏合事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[on](#on_pinch_dyn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| fingers     | int                     | 是    | 捏合的手指数，取值范围：大于等于2。 |
| receiver | Callback&lt;[Pinch](js-apis-multimodalinput-gestureevent.md#pinch)&gt; | 是    | 回调函数，异步上报捏合输入事件。  |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';
import { Pinch } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputMonitor.onPinch(2, (pinchEvent: Pinch) => {
              console.log(`Monitor on success ${JSON.stringify(pinchEvent)}`);
              return false;
            });
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_pinch_dyn">inputMonitor.off('pinch')<sup>11+</sup></span>

off(type: 'pinch', fingers: number, receiver?: Callback&lt;Pinch&gt;): void

取消监听全局触控板的捏合事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[offPinch](#off_pinch_sta)

**ArkTS-Dyn起始版本**：11

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | 是    | 输入设备事件类型，取值'pinch'。 |
| fingers     | number                     | 是    | 捏合的手指数，取值范围：大于等于2。 |
| receiver | Callback&lt;[Pinch](js-apis-multimodalinput-gestureevent.md#pinch)&gt; | 否    | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';
import { Pinch } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (pinchEvent: Pinch) => {
            console.log(`Monitor on success ${JSON.stringify(pinchEvent)}`);
            return false;
          };
          try {
            inputMonitor.on('pinch', 2, callback);
            inputMonitor.off('pinch', 2, callback);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { Pinch } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (pinchEvent: Pinch) => {
            console.log(`Monitor on success ${JSON.stringify(pinchEvent)}`);
            return false;
          };
          try {
            inputMonitor.on('pinch', 2, callback);
            inputMonitor.off('pinch', 2);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_pinch_sta">inputMonitor.offPinch<sup>22+</sup></span>

offPinch(fingers: int, receiver?: Callback&lt;Pinch&gt;): void

取消监听全局触控板的捏合事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[off](#off_pinch_dyn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名       | 类型                         | 必填   | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| fingers     | int                     | 是    | 捏合的手指数，取值范围：大于等于2。 |
| receiver | Callback&lt;[Pinch](js-apis-multimodalinput-gestureevent.md#pinch)&gt; | 否    | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';
import { Pinch } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (pinchEvent: Pinch) => {
            console.log(`Monitor on success ${JSON.stringify(pinchEvent)}`);
            return false;
          };
          try {
            inputMonitor.onPinch(2, callback);
            inputMonitor.offPinch(2, callback);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { Pinch } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (pinchEvent: Pinch) => {
            console.log(`Monitor on success ${JSON.stringify(pinchEvent)}`);
            return false;
          };
          try {
            inputMonitor.onPinch(2, callback);
            inputMonitor.offPinch(2);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_threeFingersTap_dyn">inputMonitor.on('threeFingersTap')<sup>11+</sup></span>

on(type: 'threeFingersTap', receiver: Callback&lt;[ThreeFingersTap](js-apis-multimodalinput-gestureevent.md#threefingerstap11)&gt;): void

监听全局触控板的三指轻点事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[onThreeFingersTap](#on_threeFingersTap_sta)

**ArkTS-Dyn起始版本**：11

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                      |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------- |
| type     | string                                                       | 是   | 输入设备事件类型，取值'threeFingersTap'。 |
| receiver | Callback&lt;[ThreeFingersTap](js-apis-multimodalinput-gestureevent.md#threefingerstap11)&gt; | 是   | 回调函数，异步上报三指轻点输入事件。      |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputMonitor.on('threeFingersTap', (threeFingersTap) => {
              console.log(`Monitor on success ${JSON.stringify(threeFingersTap)}`);
              return false;
            });
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_threeFingersTap_sta">inputMonitor.onThreeFingersTap<sup>22+</sup></span>

onThreeFingersTap(receiver: Callback&lt;[ThreeFingersTap](js-apis-multimodalinput-gestureevent.md#threefingerstap11)&gt;): void

监听全局触控板的三指轻点事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[on](#on_threeFingersTap_dyn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                      |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------- |
| receiver | Callback&lt;[ThreeFingersTap](js-apis-multimodalinput-gestureevent.md#threefingerstap11)&gt; | 是   | 回调函数，异步上报三指轻点输入事件。      |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputMonitor.onThreeFingersTap((threeFingersTap) => {
              console.log(`Monitor on success ${JSON.stringify(threeFingersTap)}`);
              return false;
            });
          } catch (error) {
            console.error(`Monitor on failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_threeFingersTap_dyn">inputMonitor.off('threeFingersTap')<sup>11+</sup></span>

off(type: 'threeFingersTap', receiver?: Callback&lt;[ThreeFingersTap](js-apis-multimodalinput-gestureevent.md#threefingerstap11)&gt;): void

取消监听全局触控板的三指轻点事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[offThreeFingersTap](#off_threeFingersTap_sta)

**ArkTS-Dyn起始版本**：11

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 输入设备事件类型，取值'threeFingersTap'。                    |
| receiver | Callback&lt;[ThreeFingersTap](js-apis-multimodalinput-gestureevent.md#threefingerstap11)&gt; | 否   | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';
import { ThreeFingersTap } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (threeFingersTap: ThreeFingersTap) => {
            console.log(`Monitor on success ${JSON.stringify(threeFingersTap)}`);
            return false;
          };
          try {
            inputMonitor.on('threeFingersTap', callback);
            inputMonitor.off("threeFingersTap", callback);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { ThreeFingersTap } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (threeFingersTap: ThreeFingersTap) => {
            console.log(`Monitor on success ${JSON.stringify(threeFingersTap)}`);
            return false;
          };
          try {
            inputMonitor.on('threeFingersTap', callback);
            inputMonitor.off("threeFingersTap");
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_threeFingersTap_sta">inputMonitor.offThreeFingersTap<sup>22+</sup></span>

offThreeFingersTap(receiver?: Callback&lt;[ThreeFingersTap](js-apis-multimodalinput-gestureevent.md#threefingerstap11)&gt;): void

取消监听全局触控板的三指轻点事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[off](#off_threeFingersTap_dyn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| receiver | Callback&lt;[ThreeFingersTap](js-apis-multimodalinput-gestureevent.md#threefingerstap11)&gt; | 否   | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';
import { ThreeFingersTap } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (threeFingersTap: ThreeFingersTap) => {
            console.log(`Monitor on success ${JSON.stringify(threeFingersTap)}`);
            return false;
          };
          try {
            inputMonitor.onThreeFingersTap(callback);
            inputMonitor.offThreeFingersTap(callback);
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { ThreeFingersTap } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (threeFingersTap: ThreeFingersTap) => {
            console.log(`Monitor on success ${JSON.stringify(threeFingersTap)}`);
            return false;
          };
          try {
            inputMonitor.onThreeFingersTap', callback);
            inputMonitor.offThreeFingersTap();
            console.log(`Monitor off success`);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_touchscreenSwipe_dyn">inputMonitor.on('touchscreenSwipe')<sup>18+</sup></span>

on(type: 'touchscreenSwipe', fingers: number, receiver: Callback&lt;TouchGestureEvent&gt;): void

监听触摸屏滑动手势事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[onTouchscreenSwipe](#on_touchscreenSwipe_sta)

**ArkTS-Dyn起始版本**：18

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 输入设备事件类型，取值'touchscreenSwipe'。                    |
| fingers  | number                                                       | 是   | 滑动手势的手指数，取值范围：[3,5]。 |
| receiver | Callback&lt;[TouchGestureEvent](js-apis-multimodalinput-gestureevent-sys.md#touchgestureevent)&gt; | 是   | 回调函数，异步上报触摸屏滑动手势事件。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@ohos.multimodalInput.gestureEvent';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let fingers: number = 4;
          try {
            inputMonitor.on('touchscreenSwipe', fingers, (event: TouchGestureEvent) => {
              console.log(`Monitor on success ${JSON.stringify(event)}`);
            });
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_touchscreenSwipe_sta">inputMonitor.onTouchscreenSwipe<sup>22+</sup></span>

onTouchscreenSwipe(fingers: int, receiver: Callback&lt;TouchGestureEvent&gt;): void

监听触摸屏滑动手势事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[on](#on_touchscreenSwipe_dyn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| fingers  | int                                                       | 是   | 滑动手势的手指数，取值范围：[3,5]。 |
| receiver | Callback&lt;[TouchGestureEvent](js-apis-multimodalinput-gestureevent-sys.md#touchgestureevent)&gt; | 是   | 回调函数，异步上报触摸屏滑动手势事件。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@ohos.multimodalInput.gestureEvent';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let fingers: int = 4;
          try {
            inputMonitor.onTouchscreenSwipe(fingers, (event: TouchGestureEvent) => {
              console.log(`Monitor on success ${JSON.stringify(event)}`);
            });
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_touchscreenSwipe_dyn">inputMonitor.off('touchscreenSwipe')<sup>18+</sup></span>

off(type: 'touchscreenSwipe', fingers: number, receiver?: Callback&lt;TouchGestureEvent&gt;): void

取消监听触摸屏滑动手势事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[offTouchscreenSwipe](#off_touchscreenSwipe_sta)

**ArkTS-Dyn起始版本**：18


**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 输入设备事件类型，取值'touchscreenSwipe'。                    |
| fingers  | number                                                       | 是   | 滑动手势的手指数，取值范围：[3,5]。 |
| receiver | Callback&lt;[TouchGestureEvent](js-apis-multimodalinput-gestureevent-sys.md#touchgestureevent)&gt; | 否   | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@ohos.multimodalInput.gestureEvent';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (event: TouchGestureEvent) => {
            console.log(`Monitor on success ${JSON.stringify(event)}`);
          };
          let fingers: number = 4;
          try {
            inputMonitor.on('touchscreenSwipe', fingers, callback);
            inputMonitor.off('touchscreenSwipe', fingers, callback);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@ohos.multimodalInput.gestureEvent';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let fingers: number = 4;
          try {
            inputMonitor.on('touchscreenSwipe', fingers, (event: TouchGestureEvent) => {
              console.log(`Monitor on success ${JSON.stringify(event)}`);
            });
            inputMonitor.off('touchscreenSwipe', fingers);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_touchscreenSwipe_sta">inputMonitor.offTouchscreenSwipe<sup>22+</sup></span>

offTouchscreenSwipe(fingers: int, receiver?: Callback&lt;TouchGestureEvent&gt;): void

取消监听触摸屏滑动手势事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[off](#off_touchscreenSwipe_dyn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| fingers  | int                                                       | 是   | 滑动手势的手指数，取值范围：[3,5]。 |
| receiver | Callback&lt;[TouchGestureEvent](js-apis-multimodalinput-gestureevent-sys.md#touchgestureevent)&gt; | 否   | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@ohos.multimodalInput.gestureEvent';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (event: TouchGestureEvent) => {
            console.log(`Monitor on success ${JSON.stringify(event)}`);
          };
          let fingers: int = 4;
          try {
            inputMonitor.onTouchscreenSwipe(fingers, callback);
            inputMonitor.offTouchscreenSwipe(fingers, callback);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@ohos.multimodalInput.gestureEvent';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let fingers: int = 4;
          try {
            inputMonitor.onTouchscreenSwipe(fingers, (event: TouchGestureEvent) => {
              console.log(`Monitor on success ${JSON.stringify(event)}`);
            });
            inputMonitor.offTouchscreenSwipe(fingers);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_touchscreenPinch_dyn">inputMonitor.on('touchscreenPinch')<sup>18+</sup></span>

on(type: 'touchscreenPinch', fingers: number, receiver: Callback&lt;TouchGestureEvent&gt;): void

监听触摸屏捏合手势事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[onTouchscreenPinch](#on_touchscreenPinch_sta)

**ArkTS-Dyn起始版本**：18

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 输入设备事件类型，取值'touchscreenPinch'。                    |
| fingers  | number                                                       | 是   | 捏合手势的手指数，取值范围：[4,5]。 |
| receiver | Callback&lt;[TouchGestureEvent](js-apis-multimodalinput-gestureevent-sys.md#touchgestureevent)&gt; | 是   | 回调函数，异步上报触摸屏捏合手势事件。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@ohos.multimodalInput.gestureEvent';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let fingers: number = 4;
          try {
            inputMonitor.on('touchscreenPinch', fingers, (event: TouchGestureEvent) => {
              console.log(`Monitor on success ${JSON.stringify(event)}`);
            });
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_touchscreenPinch_sta">inputMonitor.onTouchscreenPinch<sup>22+</sup></span>

onTouchscreenPinch(fingers: int, receiver: Callback&lt;TouchGestureEvent&gt;): void

监听触摸屏捏合手势事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[on](#on_touchscreenPinch_dyn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| fingers  | int                                                       | 是   | 捏合手势的手指数，取值范围：[4,5]。 |
| receiver | Callback&lt;[TouchGestureEvent](js-apis-multimodalinput-gestureevent-sys.md#touchgestureevent)&gt; | 是   | 回调函数，异步上报触摸屏捏合手势事件。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@ohos.multimodalInput.gestureEvent';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let fingers: int = 4;
          try {
            inputMonitor.onTouchscreenPinch(fingers, (event: TouchGestureEvent) => {
              console.log(`Monitor on success ${JSON.stringify(event)}`);
            });
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_touchscreenPinch_dyn">inputMonitor.off('touchscreenPinch')<sup>18+</sup>

off(type: 'touchscreenPinch', fingers: number, receiver?: Callback&lt;TouchGestureEvent&gt;): void

取消监听触摸屏捏合手势事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[offTouchscreenPinch](#off_touchscreenPinch_sta)

**ArkTS-Dyn起始版本**：18

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 输入设备事件类型，取值'touchscreenPinch'。                    |
| fingers  | number                                                       | 是   | 捏合手势的手指数，取值范围：[4,5]。 |
| receiver | Callback&lt;[TouchGestureEvent](js-apis-multimodalinput-gestureevent-sys.md#touchgestureevent)&gt; | 否   | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@ohos.multimodalInput.gestureEvent';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (event: TouchGestureEvent) => {
            console.log(`Monitor on success ${JSON.stringify(event)}`);
          };
          let fingers: number = 4;
          try {
            inputMonitor.on('touchscreenPinch', fingers, callback);
            inputMonitor.off("touchscreenPinch", fingers, callback);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@ohos.multimodalInput.gestureEvent';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let fingers: number = 4;
          try {
            inputMonitor.on('touchscreenPinch', fingers, (event: TouchGestureEvent) => {
              console.log(`Monitor on success ${JSON.stringify(event)}`);
            });
            inputMonitor.off("touchscreenPinch", fingers);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_touchscreenPinch_sta">inputMonitor.offTouchscreenPinch<sup>22+</sup>

offTouchscreenPinch(fingers: int, receiver?: Callback&lt;TouchGestureEvent&gt;): void

取消监听触摸屏捏合手势事件。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[offTouchscreenPinch](#off_touchscreenPinch_sta)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| fingers  | int                                                       | 是   | 捏合手势的手指数，取值范围：[4,5]。 |
| receiver | Callback&lt;[TouchGestureEvent](js-apis-multimodalinput-gestureevent-sys.md#touchgestureevent)&gt; | 否   | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@ohos.multimodalInput.gestureEvent';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (event: TouchGestureEvent) => {
            console.log(`Monitor on success ${JSON.stringify(event)}`);
          };
          let fingers: int = 4;
          try {
            inputMonitor.onTouchscreenPinch(fingers, callback);
            inputMonitor.offTouchscreenPinch(fingers, callback);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@ohos.multimodalInput.gestureEvent';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let fingers: int = 4;
          try {
            inputMonitor.onTouchscreenPinch(fingers, (event: TouchGestureEvent) => {
              console.log(`Monitor on success ${JSON.stringify(event)}`);
            });
            inputMonitor.offTouchscreenPinch(fingers);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_keyPressed_dyn">inputMonitor.on('keyPressed')<sup>15+</sup></span>

on(type: 'keyPressed', keys: Array&lt;KeyCode&gt;, receiver: Callback&lt;KeyEvent&gt;): void

监听指定按键的按下抬起事件，支持监听META_LEFT键、META_RIGHT键、电源键、音量键。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[onKeyPressed](#on_keyPressed_sta)

**ArkTS-Dyn起始版本**：15

**参数：**

| 参数名   | 类型                                                        | 必填 | 说明                                 |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------ |
| type     | string                                                      | 是   | 按键事件类型，取唯一值'keyPressed'。 |
| keys     | Array<[KeyCode](js-apis-keycode.md#keycode)> | 是   | 按键码列表，支持如下取值：KEYCODE_META_LEFT、KEYCODE_META_RIGHT、KEYCODE_POWER、KEYCODE_VOLUME_DOWN、KEYCODE_VOLUME_UP。                      |
| receiver | Callback&lt;[KeyEvent](js-apis-keyevent.md#keyevent)&gt;    | 是   | 用于接收上报数据的回调函数。         |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[按键监听错误码](./errorcode-inputmonitor.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | Permission denied, non-system app called system api.         |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| 4100001  | Event listening not supported for the key.                   |

**示例：**

```js
import { inputMonitor, KeyEvent, KeyCode } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let keys: Array<KeyCode> = [KeyCode.KEYCODE_VOLUME_UP];
            inputMonitor.on('keyPressed', keys, (event: KeyEvent ) => {
              console.log(`Monitor on success ${JSON.stringify(event)}`);
            });
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "on_keyPressed_sta">inputMonitor.onKeyPressed<sup>22+</sup></span>

onKeyPressed(keys: Array&lt;KeyCode&gt;, receiver: Callback&lt;KeyEvent&gt;): void

监听指定按键的按下抬起事件，支持监听META_LEFT键、META_RIGHT键、电源键、音量键。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[on](#on_keyPressed_dyn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名   | 类型                                                        | 必填 | 说明                                 |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------ |
| keys     | Array<[KeyCode](js-apis-keycode.md#keycode)> | 是   | 按键码列表，支持如下取值：KEYCODE_META_LEFT、KEYCODE_META_RIGHT、KEYCODE_POWER、KEYCODE_VOLUME_DOWN、KEYCODE_VOLUME_UP。                      |
| receiver | Callback&lt;[KeyEvent](js-apis-keyevent.md#keyevent)&gt;    | 是   | 用于接收上报数据的回调函数。         |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[按键监听错误码](./errorcode-inputmonitor.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | Permission denied, non-system app called system api.         |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| 4100001  | Event listening not supported for the key.                   |

示例：

```js
import { inputMonitor, KeyEvent, KeyCode } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let keys: Array<KeyCode> = [KeyCode.KEYCODE_VOLUME_UP];
            inputMonitor.onKeyPressed(keys, (event: KeyEvent ) => {
              console.log(`Monitor on success ${JSON.stringify(event)}`);
            });
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_keyPressed_dyn">inputMonitor.off('keyPressed')<sup>15+</sup></span>

off(type: 'keyPressed', receiver?: Callback&lt;KeyEvent&gt;): void

取消监听按键按下抬起事件。支持取消监听META_LEFT键、META_RIGHT键、电源键、音量键。需和inputMonitor.on('keyPressed')配套使用。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[offKeyPressed](#off_keyPressed_sta)

**ArkTS-Dyn起始版本**：15

**参数：**

| 参数名   | 类型                                                      | 必填 | 说明                                                         |
| -------- | --------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                                    | 是   | 按键事件类型，取唯一值'keyPressed'。                         |
| receiver | Callback&lt;[KeyEvent](js-apis-keyevent.md#keyevent)&gt; | 否   | 需要取消监听的回调函数。若不填，取消应用所有按键监听的回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | Permission denied, non-system app called system api.         |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```js
import { inputMonitor, KeyEvent, KeyCode } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          try {
            let callback = (event: KeyEvent) => {
              console.log(`Monitor on success ${JSON.stringify(event)}`);
            };
            let keys: Array<KeyCode> = [KeyCode.KEYCODE_VOLUME_UP];
            inputMonitor.on('keyPressed', keys, callback);
            inputMonitor.off("keyPressed", callback);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor, KeyEvent, KeyCode } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          try {
            let keys: Array<KeyCode> = [KeyCode.KEYCODE_VOLUME_UP];
            inputMonitor.on('keyPressed', keys, (event: KeyEvent) => {
              console.log(`Monitor on success ${JSON.stringify(event)}`);
            });
            inputMonitor.off("keyPressed");
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_keyPressed_sta">inputMonitor.offKeyPressed<sup>22+</sup></span>

offKeyPressed(receiver?: Callback&lt;KeyEvent&gt;): void

取消监听按键按下抬起事件。支持取消监听META_LEFT键、META_RIGHT键、电源键、音量键。需和inputMonitor.on('keyPressed')配套使用。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[off](#off_keyPressed_dyn)

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名   | 类型                                                      | 必填 | 说明                                                         |
| -------- | --------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| receiver | Callback&lt;[KeyEvent](js-apis-keyevent.md#keyevent)&gt; | 否   | 需要取消监听的回调函数。若不填，取消应用所有按键监听的回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | Permission denied, non-system app called system api.         |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputMonitor, KeyEvent, KeyCode } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          try {
            let callback = (event: KeyEvent) => {
              console.log(`Monitor on success ${JSON.stringify(event)}`);
            };
            let keys: Array<KeyCode> = [KeyCode.KEYCODE_VOLUME_UP];
            inputMonitor.onKeyPressed(keys, callback);
            inputMonitor.offKeyPressed(callback);
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor, KeyEvent, KeyCode } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          try {
            let keys: Array<KeyCode> = [KeyCode.KEYCODE_VOLUME_UP];
            inputMonitor.onKeyPressed(keys, (event: KeyEvent) => {
              console.log(`Monitor on success ${JSON.stringify(event)}`);
            });
            inputMonitor.offKeyPressed();
          } catch (error) {
            console.error(`Monitor execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputMonitor.queryTouchEvents()<sup>20+</sup>

ArkTS-Dyn: queryTouchEvents(count: number): Promise&lt;Array&lt;TouchEvent&gt;&gt;

ArkTS-Sta: queryTouchEvents(count: int): Promise&lt;Array&lt;TouchEvent&gt;&gt;

查询最近的触屏事件，最多支持查询 100 条事件，使用Promise异步回调。

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**ArkTS-Dyn起始版本**：20

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名   | 类型                                                      | 必填 | 说明                                                         |
| -------- | --------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| count     | ArkTS-Dyn: number<br/>ArkTS-Sta: int                                                    | 是   | 要查询的触屏事件数量。取值范围为1-100的整数。 |

**返回值：**

| 类型          | 说明                                |
| :------------ | :---------------------------------- |
| Promise&lt;Array&lt;[TouchEvent](js-apis-touchevent-sys.md#touchevent)&gt;&gt; | Promise对象，返回查询到的触屏事件。包含以下有效信息：<br/>- actionTime：触屏事件发生的时间，表示从1970.1.1 00:00:00 GMT逝去的微秒数。<br/>- [SourceType](js-apis-touchevent.md#sourcetype)：触摸来源的设备类型。<br/>- [isInject](js-apis-touchevent-sys.md#touchevent)：表示该触屏事件是否为注入事件。<br/>- pressure：压力值，取值范围是[0.0, 1.0]，0.0表示不支持。<br/>- tiltX：相对YZ平面的角度，取值的范围[-90, 90]，其中正值是向右倾斜。<br/>- tiltY：相对XZ平面的角度，取值的范围[-90, 90]，其中正值是向下倾斜。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | Permission denied, non-system app called system api.         |

示例：

```js
import { inputMonitor, TouchEvent } from '@kit.InputKit'
import { BusinessError } from '@kit.BasicServicesKit';

try {
  inputMonitor.queryTouchEvents(10).then((events: Array<TouchEvent>) => {
    events.forEach((event, index) => {
      console.info(`Touch event ${index}: actionTime=${event.actionTime}, sourceType=${event.sourceType}`);
    });
  }).catch((error: BusinessError) => {
    console.error('queryTouchEvents promise error: ' + JSON.stringify(error));
  });
} catch (error) {
  const code = (error as BusinessError).code;
  const message = (error as BusinessError).message;
  console.error(`queryTouchEvents failed, error code: ${code}, message: ${message}.`);
}
```
