# off（系统接口）

## off('touch')

```TypeScript
function off(type: 'touch', receiver?: TouchEventReceiver): void
```

取消监听全局触屏输入事件，使用callback异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function off(type: 'touch', receiver?: TouchEventReceiver): void--><!--Device-inputMonitor-function off(type: 'touch', receiver?: TouchEventReceiver): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'touch' | 是 | 输入设备事件类型，取值'touch'。 |
| receiver | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

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
          // 取消监听单个回调函数
          let callback = (touchEvent: TouchEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(touchEvent)}.`);
            return false;
          };
          try {
            // 订阅触摸事件
            inputMonitor.on('touch', callback);
            // 取消订阅触摸事件
            inputMonitor.off('touch', callback);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to monitor the touch screen event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

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
          // 取消监听所有回调函数
          let callback = (touchEvent: TouchEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(touchEvent)}.`);
            return false;
          };
          try {
            // 订阅触摸事件
            inputMonitor.on('touch', callback);
            // 取消订阅触摸事件
            inputMonitor.off('touch');
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to monitor the touch screen event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## off('mouse')

```TypeScript
function off(type: 'mouse', receiver?: Callback<MouseEvent>): void
```

取消监听全局鼠标事件。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function off(type: 'mouse', receiver?: Callback<MouseEvent>): void--><!--Device-inputMonitor-function off(type: 'mouse', receiver?: Callback<MouseEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'mouse' | 是 | 输入设备事件类型，取值'mouse'。 |
| receiver | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 否 | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

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
          // 取消监听单个回调函数
          let callback = (mouseEvent: MouseEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(mouseEvent)}.`);
            return false;
          };
          try {
            // 订阅鼠标事件
            inputMonitor.on('mouse', callback);
            // 取消订阅鼠标事件
            inputMonitor.off('mouse', callback);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to monitor the mouse event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

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
          // 取消监听所有回调函数
          let callback = (mouseEvent: MouseEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(mouseEvent)}.`);
            return false;
          };
          try {
            // 订阅鼠标事件
            inputMonitor.on('mouse', callback);
            // 取消订阅鼠标事件
            inputMonitor.off('mouse');
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to monitor the mouse event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## off('pinch')

```TypeScript
function off(type: 'pinch', receiver?: Callback<Pinch>): void
```

取消监听全局触控板的捏合事件。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function off(type: 'pinch', receiver?: Callback<Pinch>): void--><!--Device-inputMonitor-function off(type: 'pinch', receiver?: Callback<Pinch>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'pinch' | 是 | 输入设备事件类型，取值'pinch'。 |
| receiver | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Pinch&gt; | 否 | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

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
          // 取消监听单个回调函数
          let callback = (pinchEvent: Pinch) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(pinchEvent)}.`);
            return false;
          };
          try {
            // 订阅捏合事件
            inputMonitor.on('pinch', callback);
            // 取消订阅捏合事件
            inputMonitor.off('pinch', callback);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor pinch event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

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
          // 取消监听所有回调函数
          let callback = (pinchEvent: Pinch) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(pinchEvent)}.`);
            return false;
          };
          try {
            // 订阅捏合事件
            inputMonitor.on('pinch', callback);
            // 取消订阅捏合事件
            inputMonitor.off('pinch');
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor pinch event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## off('pinch')

```TypeScript
function off(type: 'pinch', fingers: number, receiver?: Callback<Pinch>): void
```

取消监听全局触控板的捏合事件。使用callback异步回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function off(type: 'pinch', fingers: number, receiver?: Callback<Pinch>): void--><!--Device-inputMonitor-function off(type: 'pinch', fingers: number, receiver?: Callback<Pinch>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'pinch' | 是 | 输入设备事件类型，取值'pinch'。 |
| fingers | number | 是 | 捏合的手指数，取值范围：大于等于2。 |
| receiver | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Pinch&gt; | 否 | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

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
          // 取消监听单个回调函数
          let callback = (pinchEvent: Pinch) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(pinchEvent)}.`);
            return false;
          };
          try {
            // 订阅捏合事件
            inputMonitor.on('pinch', 2, callback);
            // 取消订阅捏合事件
            inputMonitor.off('pinch', 2, callback);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor pinch event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

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
          // 取消监听所有回调函数
          let callback = (pinchEvent: Pinch) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(pinchEvent)}.`);
            return false;
          };
          try {
            // 捏合手势监听手指数2
            inputMonitor.on('pinch', 2, callback);
            // 取消订阅捏合事件
            inputMonitor.off('pinch', 2);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor pinch event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## off('rotate')

```TypeScript
function off(type: 'rotate', fingers: number, receiver?: Callback<Rotate>): void
```

取消监听全局触控板的旋转事件。使用callback异步回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function off(type: 'rotate', fingers: number, receiver?: Callback<Rotate>): void--><!--Device-inputMonitor-function off(type: 'rotate', fingers: number, receiver?: Callback<Rotate>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'rotate' | 是 | 输入设备事件类型，取值'rotate'。 |
| fingers | number | 是 | 旋转的手指数，目前支持监听手指数是2。 |
| receiver | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Rotate&gt; | 否 | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

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
          // 取消监听单个回调函数
          let callback = (rotateEvent: Rotate) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(rotateEvent)}.`);
            return false;
          };
          try {
            // 旋转手势监听手指数2
            inputMonitor.on('rotate', 2, callback);
            // 取消订阅旋转事件
            inputMonitor.off('rotate', 2, callback);
            console.info(`Succeeded in turning off monitor.`); 
          } catch (error) {
            console.error(`Failed to cancel monitor rotate event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

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
          // 取消监听所有回调函数
          let callback = (rotateEvent: Rotate) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(rotateEvent)}.`);
            return false;
          };
          try {
            // 旋转手势监听手指数2
            inputMonitor.on('rotate', 2, callback);
            // 取消订阅旋转事件
            inputMonitor.off('rotate', 2);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor rotate event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## off('threeFingersSwipe')

```TypeScript
function off(type: 'threeFingersSwipe', receiver?: Callback<ThreeFingersSwipe>): void
```

取消监听全局触控板的三指滑动事件。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function off(type: 'threeFingersSwipe', receiver?: Callback<ThreeFingersSwipe>): void--><!--Device-inputMonitor-function off(type: 'threeFingersSwipe', receiver?: Callback<ThreeFingersSwipe>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'threeFingersSwipe' | 是 | 输入设备事件类型，取值'threeFingersSwipe'。 |
| receiver | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ThreeFingersSwipe&gt; | 否 | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { ThreeFingersSwipe } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (threeFingersSwipe: ThreeFingersSwipe) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(threeFingersSwipe)}.`);
            return false;
          };
          try {
            // 订阅三指滑动事件
            inputMonitor.on('threeFingersSwipe', callback);
            // 取消订阅三指滑动事件
            inputMonitor.off('threeFingersSwipe', callback);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor three fingers swipe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { ThreeFingersSwipe } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (threeFingersSwipe: ThreeFingersSwipe) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(threeFingersSwipe)}.`);
            return false;
          };
          try {
            // 订阅三指滑动事件
            inputMonitor.on('threeFingersSwipe', callback);
            // 取消订阅三指滑动事件
            inputMonitor.off('threeFingersSwipe');
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor three fingers swipe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## off('fourFingersSwipe')

```TypeScript
function off(type: 'fourFingersSwipe', receiver?: Callback<FourFingersSwipe>): void
```

取消监听全局触控板的四指滑动事件。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function off(type: 'fourFingersSwipe', receiver?: Callback<FourFingersSwipe>): void--><!--Device-inputMonitor-function off(type: 'fourFingersSwipe', receiver?: Callback<FourFingersSwipe>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'fourFingersSwipe' | 是 | 输入设备事件类型，取值'fourFingersSwipe'。 |
| receiver | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FourFingersSwipe&gt; | 否 | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { FourFingersSwipe } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (fourFingersSwipe: FourFingersSwipe) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(fourFingersSwipe)}.`);
            return false;
          };
          try {
            // 订阅四指滑动事件
            inputMonitor.on('fourFingersSwipe', callback);
            // 取消订阅四指滑动事件
            inputMonitor.off('fourFingersSwipe', callback);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitoring four fingers swipe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { FourFingersSwipe } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (fourFingersSwipe: FourFingersSwipe) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(fourFingersSwipe)}.`);
            return false;
          };
          try {
            // 订阅四指滑动事件
            inputMonitor.on('fourFingersSwipe', callback);
            // 取消订阅四指滑动事件
            inputMonitor.off('fourFingersSwipe');
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitoring four fingers swipe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## off('threeFingersTap')

```TypeScript
function off(type: 'threeFingersTap', receiver?: Callback<ThreeFingersTap>): void
```

取消监听全局触控板的三指轻点事件。使用callback异步回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function off(type: 'threeFingersTap', receiver?: Callback<ThreeFingersTap>): void--><!--Device-inputMonitor-function off(type: 'threeFingersTap', receiver?: Callback<ThreeFingersTap>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'threeFingersTap' | 是 | 输入设备事件类型，取值'threeFingersTap'。 |
| receiver | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ThreeFingersTap&gt; | 否 | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { ThreeFingersTap } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (threeFingersTap: ThreeFingersTap) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(threeFingersTap)}.`);
            return false;
          };
          try {
            // 订阅三指点击事件
            inputMonitor.on('threeFingersTap', callback);
            // 取消订阅三指点击事件
            inputMonitor.off('threeFingersTap', callback);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor three fingers tap, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { ThreeFingersTap } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (threeFingersTap: ThreeFingersTap) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(threeFingersTap)}.`);
            return false;
          };
          try {
            // 订阅三指点击事件
            inputMonitor.on('threeFingersTap', callback);
            // 取消订阅三指点击事件
            inputMonitor.off('threeFingersTap');
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor three fingers tap, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## off('fingerprint')

```TypeScript
function off(type: 'fingerprint', receiver?: Callback<FingerprintEvent>): void
```

取消监听指纹手势输入事件。使用callback异步回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function off(type: 'fingerprint', receiver?: Callback<FingerprintEvent>): void--><!--Device-inputMonitor-function off(type: 'fingerprint', receiver?: Callback<FingerprintEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'fingerprint' | 是 | 输入事件类型，取值'fingerprint'。 |
| receiver | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FingerprintEvent&gt; | 否 | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { FingerprintEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听单个回调函数
          let callback = (fingerprintEvent: FingerprintEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(fingerprintEvent)}.`);
            return false;
          };
          try {
            // 订阅指纹事件
            inputMonitor.on('fingerprint', callback);
            // 取消订阅指纹事件
            inputMonitor.off('fingerprint', callback);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor finger print event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

```TypeScript
import { inputMonitor } from '@kit.InputKit';
import { FingerprintEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (fingerprintEvent: FingerprintEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(fingerprintEvent)}.`);
            return false;
          };
          try {
            // 订阅指纹事件
            inputMonitor.on('fingerprint', callback);
            // 取消订阅指纹事件
            inputMonitor.off('fingerprint');
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor finger print event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## off('swipeInward')

```TypeScript
function off(type: 'swipeInward', receiver?: Callback<SwipeInward>): void
```

取消监听向内滑动事件。使用callback异步回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function off(type: 'swipeInward', receiver?: Callback<SwipeInward>): void--><!--Device-inputMonitor-function off(type: 'swipeInward', receiver?: Callback<SwipeInward>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'swipeInward' | 是 | 输入事件类型，取值'swipeInward'。 |
| receiver | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;SwipeInward&gt; | 否 | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. |

**示例：**

```TypeScript
import { inputMonitor, SwipeInward } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
build() {
  RelativeContainer() {
    Text()
      .onClick(() => {
        // 取消监听单个回调函数
        let callback = (swipeInward: SwipeInward) => {
          console.info(`Succeeded in monitoring on ${JSON.stringify(swipeInward)}.`);
          return false;
        };
        try {
          // 订阅向内滑动事件
          inputMonitor.on('swipeInward', callback);
          // 取消订阅向内滑动事件
          inputMonitor.off('swipeInward', callback);
          console.info(`Succeeded in turning off monitor.`);
        } catch (error) {
          console.error(`Failed to cancel monitor swipe inward, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
        }
      })
  }
}
}
```

```TypeScript
import { inputMonitor, SwipeInward } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消监听所有回调函数
          let callback = (swipeInward: SwipeInward) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(swipeInward)}.`);
            return false;
          };
          try {
            // 订阅向内滑动事件
            inputMonitor.on('swipeInward', callback);
            // 取消订阅向内滑动事件
            inputMonitor.off('swipeInward');
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor swipe inward, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## off('touchscreenSwipe')

```TypeScript
function off(type: 'touchscreenSwipe', fingers: number, receiver?: Callback<TouchGestureEvent>): void
```

取消监听触摸屏滑动手势事件。使用callback异步回调。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function off(type: 'touchscreenSwipe', fingers: number, receiver?: Callback<TouchGestureEvent>): void--><!--Device-inputMonitor-function off(type: 'touchscreenSwipe', fingers: number, receiver?: Callback<TouchGestureEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'touchscreenSwipe' | 是 | 输入设备事件类型，取值'touchscreenSwipe'。 |
| fingers | number | 是 | 滑动手势的手指数，取值范围：[3,5]。 |
| receiver | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;TouchGestureEvent&gt; | 否 | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

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
          // 取消监听单个回调函数
          let callback = (event: TouchGestureEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
          };
          let fingers: number = 4;
          try {
            // 订阅触摸屏滑动事件
            inputMonitor.on('touchscreenSwipe', fingers, callback);
            // 取消订阅触摸屏滑动事件
            inputMonitor.off('touchscreenSwipe', fingers, callback);
          } catch (error) {
            console.error(`Failed to cancel monitor touch screen swipe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

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
          // 取消监听所有回调函数
          let fingers: number = 4;
          try {
            // 订阅触摸屏滑动事件
            inputMonitor.on('touchscreenSwipe', fingers, (event: TouchGestureEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            });
            // 取消订阅触摸屏滑动事件
            inputMonitor.off('touchscreenSwipe', fingers);
          } catch (error) {
            console.error(`Failed to monitor touch screen swipe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## off('touchscreenPinch')

```TypeScript
function off(type: 'touchscreenPinch', fingers: number, receiver?: Callback<TouchGestureEvent>): void
```

取消监听触摸屏捏合手势事件。使用callback异步回调。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function off(type: 'touchscreenPinch', fingers: number, receiver?: Callback<TouchGestureEvent>): void--><!--Device-inputMonitor-function off(type: 'touchscreenPinch', fingers: number, receiver?: Callback<TouchGestureEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'touchscreenPinch' | 是 | 输入设备事件类型，取值'touchscreenPinch'。 |
| fingers | number | 是 | 捏合手势的手指数，取值范围：[4,5]。 |
| receiver | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;TouchGestureEvent&gt; | 否 | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

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
          // 取消监听单个回调函数
          let callback = (event: TouchGestureEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
          };
          let fingers: number = 4;
          try {
            // 订阅触摸屏捏合事件
            inputMonitor.on('touchscreenPinch', fingers, callback);
            // 取消订阅触摸屏捏合事件
            inputMonitor.off('touchscreenPinch', fingers, callback);
          } catch (error) {
            console.error(`Failed to cancel monitor touch screen pinch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

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
          // 取消监听所有回调函数
          let fingers: number = 4;
          try {
            // 订阅触摸屏捏合事件
            inputMonitor.on('touchscreenPinch', fingers, (event: TouchGestureEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            });
            // 取消订阅触摸屏捏合事件
            inputMonitor.off('touchscreenPinch', fingers);
          } catch (error) {
            console.error(`Failed to cancel monitor touch screen pinch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## off('keyPressed')

```TypeScript
function off(type: 'keyPressed', receiver?: Callback<KeyEvent>): void
```

取消监听按键按下抬起事件。支持取消监听META\_LEFT键、META\_RIGHT键、电源键、音量键。需和inputMonitor.on('keyPressed')配套使用。使用callback异步回调。

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function off(type: 'keyPressed', receiver?: Callback<KeyEvent>): void--><!--Device-inputMonitor-function off(type: 'keyPressed', receiver?: Callback<KeyEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyPressed' | 是 | 按键事件类型，取唯一值'keyPressed'。 |
| receiver | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 否 | 需要取消监听的回调函数。若不填，取消应用所有按键监听的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

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
          // 取消监听单个回调函数
          try {
            let callback = (event: KeyEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            };
            let keys: Array<KeyCode> = [KeyCode.KEYCODE_VOLUME_UP];
            // 订阅按键按下事件
            inputMonitor.on('keyPressed', keys, callback);
            // 取消订阅按键按下事件
            inputMonitor.off('keyPressed', callback);
          } catch (error) {
            console.error(`Failed to cancel monitor key pressed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

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
          // 取消监听所有回调函数
          try {
            let keys: Array<KeyCode> = [KeyCode.KEYCODE_VOLUME_UP];
            // 订阅按键按下事件
            inputMonitor.on('keyPressed', keys, (event: KeyEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            });
            // 取消订阅按键按下事件
            inputMonitor.off('keyPressed');
          } catch (error) {
            console.error(`Failed to cancel monitor key pressed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

