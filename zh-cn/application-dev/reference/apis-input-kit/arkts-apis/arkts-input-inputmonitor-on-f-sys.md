# on（系统接口）

## 导入模块

```TypeScript
import { inputMonitor } from '@kit.InputKit';
```

## on('touch')

```TypeScript
function on(type: 'touch', receiver: TouchEventReceiver): void
```

监听全局触屏输入事件，使用callback异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function on(type: 'touch', receiver: TouchEventReceiver): void--><!--Device-inputMonitor-function on(type: 'touch', receiver: TouchEventReceiver): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'touch' | 是 | 输入设备事件类型，取值'touch'。 |
| receiver | [TouchEventReceiver](arkts-input-inputmonitor-toucheventreceiver-t-sys.md) | 是 | 回调函数，返回触摸屏输入事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { TouchEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 订阅触摸事件
            inputMonitor.on('touch', (touchEvent: TouchEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(touchEvent)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor the touch screen event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## on('mouse')

```TypeScript
function on(type: 'mouse', receiver: Callback<MouseEvent>): void
```

监听全局鼠标事件。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function on(type: 'mouse', receiver: Callback<MouseEvent>): void--><!--Device-inputMonitor-function on(type: 'mouse', receiver: Callback<MouseEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'mouse' | 是 | 输入设备事件类型，取值'mouse'。 |
| receiver | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;MouseEvent&gt; | 是 | 回调函数，返回鼠标输入事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { MouseEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 订阅鼠标事件
            inputMonitor.on('mouse', (mouseEvent: MouseEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(mouseEvent)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor the mouse event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## on('mouse')

```TypeScript
function on(type: 'mouse', rect: display.Rect[], receiver: Callback<MouseEvent>): void
```

监听鼠标事件，当鼠标移动至指定矩形区域内时，触发回调任务。使用callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function on(type: 'mouse', rect: display.Rect[], receiver: Callback<MouseEvent>): void--><!--Device-inputMonitor-function on(type: 'mouse', rect: display.Rect[], receiver: Callback<MouseEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'mouse' | 是 | 输入设备事件类型，取值'mouse'。 |
| rect | display.Rect[] | 是 | 可以触发回调任务的矩形区域，可传入1至2个。 |
| receiver | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;MouseEvent&gt; | 是 | 回调函数，返回鼠标输入事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { MouseEvent } from '@kit.InputKit';
import { display } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

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
            console.info(`Succeeded in monitoring on ${JSON.stringify(mouseEvent)}.`);
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
            // 订阅鼠标事件
            inputMonitor.on('mouse', rect, callback);
          } catch (error) {
            console.error(`Failed to monitor the mouse event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## on('pinch')

```TypeScript
function on(type: 'pinch', receiver: Callback<Pinch>): void
```

监听全局触控板的捏合事件。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function on(type: 'pinch', receiver: Callback<Pinch>): void--><!--Device-inputMonitor-function on(type: 'pinch', receiver: Callback<Pinch>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'pinch' | 是 | 输入设备事件类型，取值'pinch'。 |
| receiver | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Pinch&gt; | 是 | 回调函数，返回捏合输入事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 订阅捏合事件
            inputMonitor.on('pinch', (pinchEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(pinchEvent)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor the pinch event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## on('pinch')

```TypeScript
function on(type: 'pinch', fingers: number, receiver: Callback<Pinch>): void
```

监听全局触控板的捏合事件。使用callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function on(type: 'pinch', fingers: number, receiver: Callback<Pinch>): void--><!--Device-inputMonitor-function on(type: 'pinch', fingers: number, receiver: Callback<Pinch>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'pinch' | 是 | 输入设备事件类型，取值'pinch'。 |
| fingers | number | 是 | 捏合的手指数，取值范围：大于等于2。 |
| receiver | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Pinch&gt; | 是 | 回调函数，返回捏合输入事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { Pinch } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 捏合手势监听手指数2
            inputMonitor.on('pinch', 2, (pinchEvent: Pinch) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(pinchEvent)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor pinch event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## on('rotate')

```TypeScript
function on(type: 'rotate', fingers: number, receiver: Callback<Rotate>): void
```

监听全局触控板的旋转事件。使用callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function on(type: 'rotate', fingers: number, receiver: Callback<Rotate>): void--><!--Device-inputMonitor-function on(type: 'rotate', fingers: number, receiver: Callback<Rotate>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'rotate' | 是 | 输入设备事件类型，取值'rotate'。 |
| fingers | number | 是 | 旋转的手指数，目前支持监听手指数是2。 |
| receiver | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Rotate&gt; | 是 | 回调函数，返回旋转输入事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { Rotate } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 旋转手势监听手指数2
            inputMonitor.on('rotate', 2, (rotateEvent: Rotate) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(rotateEvent)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor rotate event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## on('threeFingersSwipe')

```TypeScript
function on(type: 'threeFingersSwipe', receiver: Callback<ThreeFingersSwipe>): void
```

监听全局触控板的三指滑动事件。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function on(type: 'threeFingersSwipe', receiver: Callback<ThreeFingersSwipe>): void--><!--Device-inputMonitor-function on(type: 'threeFingersSwipe', receiver: Callback<ThreeFingersSwipe>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'threeFingersSwipe' | 是 | 输入设备事件类型，取值'threeFingersSwipe'。 |
| receiver | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;ThreeFingersSwipe&gt; | 是 | 回调函数，返回三指滑动输入事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 订阅三指滑动事件
            inputMonitor.on('threeFingersSwipe', (threeFingersSwipe) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(threeFingersSwipe)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor three fingers swipe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## on('fourFingersSwipe')

```TypeScript
function on(type: 'fourFingersSwipe', receiver: Callback<FourFingersSwipe>): void
```

监听全局触控板的四指滑动事件。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function on(type: 'fourFingersSwipe', receiver: Callback<FourFingersSwipe>): void--><!--Device-inputMonitor-function on(type: 'fourFingersSwipe', receiver: Callback<FourFingersSwipe>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'fourFingersSwipe' | 是 | 输入设备事件类型，取值'fourFingersSwipe'。 |
| receiver | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;FourFingersSwipe&gt; | 是 | 回调函数，返回四指滑动输入事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 订阅四指滑动事件
            inputMonitor.on('fourFingersSwipe', (fourFingersSwipe) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(fourFingersSwipe)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor four fingers swipe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## on('threeFingersTap')

```TypeScript
function on(type: 'threeFingersTap', receiver: Callback<ThreeFingersTap>): void
```

监听全局触控板的三指轻点事件。使用callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function on(type: 'threeFingersTap', receiver: Callback<ThreeFingersTap>): void--><!--Device-inputMonitor-function on(type: 'threeFingersTap', receiver: Callback<ThreeFingersTap>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'threeFingersTap' | 是 | 输入设备事件类型，取值'threeFingersTap'。 |
| receiver | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;ThreeFingersTap&gt; | 是 | 回调函数，返回三指轻点输入事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 订阅三指点击事件
            inputMonitor.on('threeFingersTap', (threeFingersTap) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(threeFingersTap)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor three fingers tap, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## on('fingerprint')

```TypeScript
function on(type: 'fingerprint', receiver: Callback<FingerprintEvent>): void
```

监听指纹手势输入事件。使用callback异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function on(type: 'fingerprint', receiver: Callback<FingerprintEvent>): void--><!--Device-inputMonitor-function on(type: 'fingerprint', receiver: Callback<FingerprintEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'fingerprint' | 是 | 输入事件类型，取唯一值'fingerprint'。 |
| receiver | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;FingerprintEvent&gt; | 是 | 回调函数，返回指纹器件手势输入事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 订阅指纹事件
            inputMonitor.on('fingerprint', (FingerprintEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(FingerprintEvent)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor finger print event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## on('swipeInward')

```TypeScript
function on(type: 'swipeInward', receiver: Callback<SwipeInward>): void
```

监听向内滑动事件。使用callback异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function on(type: 'swipeInward', receiver: Callback<SwipeInward>): void--><!--Device-inputMonitor-function on(type: 'swipeInward', receiver: Callback<SwipeInward>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'swipeInward' | 是 | 输入事件类型，取唯一值'SwipeInward'。 |
| receiver | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;SwipeInward&gt; | 是 | 回调函数，返回向内滑动事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. |

**示例：**

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 订阅向内滑动事件
            inputMonitor.on('swipeInward', (SwipeInward) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(SwipeInward)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor swipe inward, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## on('touchscreenSwipe')

```TypeScript
function on(type: 'touchscreenSwipe', fingers: number, receiver: Callback<TouchGestureEvent>): void
```

监听触摸屏滑动手势事件。使用callback异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function on(type: 'touchscreenSwipe', fingers: number, receiver: Callback<TouchGestureEvent>): void--><!--Device-inputMonitor-function on(type: 'touchscreenSwipe', fingers: number, receiver: Callback<TouchGestureEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'touchscreenSwipe' | 是 | 输入设备事件类型，取值'touchscreenSwipe'。 |
| fingers | number | 是 | 滑动手势的手指数，取值范围：[3,5]。 |
| receiver | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;TouchGestureEvent&gt; | 是 | 回调函数，返回触摸屏滑动手势事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types.3.Parameter verification failed. |

**示例：**

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let fingers: number = 4;
          try {
            // 订阅触摸屏滑动事件
            inputMonitor.on('touchscreenSwipe', fingers, (event: TouchGestureEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            });
          } catch (error) {
            console.error(`Failed to monitor touch screen swipe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## on('touchscreenPinch')

```TypeScript
function on(type: 'touchscreenPinch', fingers: number, receiver: Callback<TouchGestureEvent>): void
```

监听触摸屏捏合手势事件。使用callback异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function on(type: 'touchscreenPinch', fingers: number, receiver: Callback<TouchGestureEvent>): void--><!--Device-inputMonitor-function on(type: 'touchscreenPinch', fingers: number, receiver: Callback<TouchGestureEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'touchscreenPinch' | 是 | 输入设备事件类型，取值'touchscreenPinch'。 |
| fingers | number | 是 | 捏合手势的手指数，取值范围：[4,5]。 |
| receiver | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;TouchGestureEvent&gt; | 是 | 回调函数，返回触摸屏捏合手势事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types.3.Parameter verification failed. |

**示例：**

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let fingers: number = 4;
          try {
            // 订阅触摸屏捏合事件
            inputMonitor.on('touchscreenPinch', fingers, (event: TouchGestureEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            });
          } catch (error) {
            console.error(`Failed to monitor touch screen pinch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## on('keyPressed')

```TypeScript
function on(type: 'keyPressed', keys: Array<KeyCode>, receiver: Callback<KeyEvent>): void
```

监听指定按键的按下抬起事件，支持监听META_LEFT键、META_RIGHT键、电源键、音量键。使用callback异步回调。

**起始版本：** 15

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function on(type: 'keyPressed', keys: Array<KeyCode>, receiver: Callback<KeyEvent>): void--><!--Device-inputMonitor-function on(type: 'keyPressed', keys: Array<KeyCode>, receiver: Callback<KeyEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyPressed' | 是 | 按键事件类型，取唯一值'keyPressed'。 |
| keys | Array&lt;KeyCode&gt; | 是 | 键值，支持如下键值：KEYCODE_META_LEFT、KEYCODE_META_RIGHT、KEYCODE_POWER、KEYCODE_VOLUME_DOWN、KEYCODE_VOLUME_UP。 |
| receiver | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;KeyEvent&gt; | 是 | 回调函数，返回按键输入事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [4100001](../errorcode-inputmonitor.md#4100001-按键不支持前置监听) | Event listening not supported for the key. |

**示例：**

```TypeScript
import { inputMonitor, KeyEvent, KeyCode } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let keys: Array<KeyCode> = [KeyCode.KEYCODE_VOLUME_UP];
            // 订阅按键按下事件
            inputMonitor.on('keyPressed', keys, (event: KeyEvent ) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            });
          } catch (error) {
            console.error(`Failed to monitor key pressed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

