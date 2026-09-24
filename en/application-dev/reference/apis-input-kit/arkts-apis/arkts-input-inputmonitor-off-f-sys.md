# off (System API)

## Modules to Import

```TypeScript
import { inputMonitor } from '@kit.InputKit';
```

## off('touch')

```TypeScript
function off(type: 'touch', receiver?: TouchEventReceiver): void
```

Cancels listening for global touchscreen input events. This API uses an asynchronous callback to return the result.

**Since:** 7

**Required permissions:** ohos.permission.INPUT_MONITORING

**System capability:** SystemCapability.MultimodalInput.Input.InputMonitor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'touch' | Yes | Event type. This field has a fixed value of **touch**. |
| receiver | [TouchEventReceiver](arkts-input-inputmonitor-toucheventreceiver-t-sys.md) | No | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { inputMonitor, TouchEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (touchEvent: TouchEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(touchEvent)}.`);
            return false;
          };
          try {
            // Subscribe to Touch Events
            inputMonitor.on('touch', callback);
            // Unsubscribe from Touch Events
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
import { inputMonitor, TouchEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let callback = (touchEvent: TouchEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(touchEvent)}.`);
            return false;
          };
          try {
            // Subscribe to Touch Events
            inputMonitor.on('touch', callback);
            // Unsubscribe from Touch Events
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

Disables listening for global mouse events. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.INPUT_MONITORING

**System capability:** SystemCapability.MultimodalInput.Input.InputMonitor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'mouse' | Yes | Event type. This field has a fixed value of **mouse**. |
| receiver | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MouseEvent](arkts-input-multimodalinput-mouseevent-mouseevent-i.md)&gt; | No | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { inputMonitor, MouseEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (mouseEvent: MouseEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(mouseEvent)}.`);
            return false;
          };
          try {
            // Subscribe to Mouse Events
            inputMonitor.on('mouse', callback);
            // Unsubscribe from Mouse Events
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
import { inputMonitor, MouseEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let callback = (mouseEvent: MouseEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(mouseEvent)}.`);
            return false;
          };
          try {
            // Subscribe to Mouse Events
            inputMonitor.on('mouse', callback);
            // Unsubscribe from Mouse Events
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

Disables listening for global touchpad pinch events. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.INPUT_MONITORING

**System capability:** SystemCapability.MultimodalInput.Input.InputMonitor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'pinch' | Yes | Event type. This field has a fixed value of **pinch**. |
| receiver | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Pinch](arkts-input-multimodalinput-gestureevent-pinch-i.md)&gt; | No | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | SystemAPI permit error. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { inputMonitor, Pinch } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (pinchEvent: Pinch) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(pinchEvent)}.`);
            return false;
          };
          try {
            // Subscribe to Pinch Event
            inputMonitor.on('pinch', callback);
            // Unsubscribe from Pinch Event
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
import { inputMonitor, Pinch } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let callback = (pinchEvent: Pinch) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(pinchEvent)}.`);
            return false;
          };
          try {
            // Subscribe to Pinch Event
            inputMonitor.on('pinch', callback);
            // Unsubscribe from Pinch Event
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

Disables listening for global touchpad pinch events. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.INPUT_MONITORING

**System capability:** SystemCapability.MultimodalInput.Input.InputMonitor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'pinch' | Yes | Event type. This field has a fixed value of **pinch**. |
| fingers | number | Yes | Number of fingers that trigger the pinch. The value must be greater than or equal to **2**. |
| receiver | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Pinch](arkts-input-multimodalinput-gestureevent-pinch-i.md)&gt; | No | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | SystemAPI permit error. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { inputMonitor, Pinch } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (pinchEvent: Pinch) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(pinchEvent)}.`);
            return false;
          };
          try {
            // Subscribe to Pinch Event
            inputMonitor.on('pinch', 2, callback);
            // Unsubscribe from Pinch Event
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
import { inputMonitor, Pinch } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let callback = (pinchEvent: Pinch) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(pinchEvent)}.`);
            return false;
          };
          try {
            // Number of fingers for pinch gesture monitoring: 2
            inputMonitor.on('pinch', 2, callback);
            // Unsubscribe from pinch events
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

Disables listening for rotation events of the touchpad. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.INPUT_MONITORING

**System capability:** SystemCapability.MultimodalInput.Input.InputMonitor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'rotate' | Yes | Event type. This field has a fixed value of **rotate**. |
| fingers | number | Yes | Number of fingers that trigger a rotation. The value must not be greater than **2**. |
| receiver | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Rotate](arkts-input-multimodalinput-gestureevent-rotate-i.md)&gt; | No | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | SystemAPI permit error. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { inputMonitor, Rotate } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (rotateEvent: Rotate) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(rotateEvent)}.`);
            return false;
          };
          try {
            // Rotation gesture listening finger count 2
            inputMonitor.on('rotate', 2, callback);
            // Unsubscribe from rotation events
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
import { inputMonitor, Rotate } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let callback = (rotateEvent: Rotate) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(rotateEvent)}.`);
            return false;
          };
          try {
            // Number of fingers for rotation gesture monitoring: 2
            inputMonitor.on('rotate', 2, callback);
            // Unsubscribe from rotation events
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

Disables listening for three-finger swipe events. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.INPUT_MONITORING

**System capability:** SystemCapability.MultimodalInput.Input.InputMonitor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'threeFingersSwipe' | Yes | Event type. This field has a fixed value of **threeFingersSwipe**. |
| receiver | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ThreeFingersSwipe](arkts-input-multimodalinput-gestureevent-threefingersswipe-i.md)&gt; | No | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | SystemAPI permit error. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { inputMonitor, ThreeFingersSwipe } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (threeFingersSwipe: ThreeFingersSwipe) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(threeFingersSwipe)}.`);
            return false;
          };
          try {
            // Subscribe to Three-Finger Swipe Event
            inputMonitor.on('threeFingersSwipe', callback);
            // Unsubscribe from Three-Finger Swipe Event
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
import { inputMonitor, ThreeFingersSwipe } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let callback = (threeFingersSwipe: ThreeFingersSwipe) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(threeFingersSwipe)}.`);
            return false;
          };
          try {
            // Subscribe to Three-Finger Swipe Events
            inputMonitor.on('threeFingersSwipe', callback);
            // Unsubscribe from Three-Finger Swipe Events
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

Disables listening for four-finger swipe events. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.INPUT_MONITORING

**System capability:** SystemCapability.MultimodalInput.Input.InputMonitor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'fourFingersSwipe' | Yes | Event type. This field has a fixed value of **fourFingersSwipe**. |
| receiver | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FourFingersSwipe](arkts-input-multimodalinput-gestureevent-fourfingersswipe-i.md)&gt; | No | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | SystemAPI permit error. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { inputMonitor, FourFingersSwipe } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (fourFingersSwipe: FourFingersSwipe) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(fourFingersSwipe)}.`);
            return false;
          };
          try {
            // Subscribe to Four-Finger Swipe Event
            inputMonitor.on('fourFingersSwipe', callback);
            // Unsubscribe from Four-Finger Swipe Event
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
import { inputMonitor, FourFingersSwipe } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let callback = (fourFingersSwipe: FourFingersSwipe) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(fourFingersSwipe)}.`);
            return false;
          };
          try {
            // Subscribe to Four-Finger Swipe Event
            inputMonitor.on('fourFingersSwipe', callback);
            // Unsubscribe from Four-Finger Swipe Event
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

Disables listening for three-finger tap events. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.INPUT_MONITORING

**System capability:** SystemCapability.MultimodalInput.Input.InputMonitor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'threeFingersTap' | Yes | Event type. This field has a fixed value of **threeFingersTap**. |
| receiver | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ThreeFingersTap](arkts-input-multimodalinput-gestureevent-threefingerstap-i.md)&gt; | No | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | SystemAPI permit error. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { inputMonitor, ThreeFingersTap } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (threeFingersTap: ThreeFingersTap) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(threeFingersTap)}.`);
            return false;
          };
          try {
            // Subscribe to three-finger tap event
            inputMonitor.on('threeFingersTap', callback);
            // Unsubscribe from three-finger tap event
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
import { inputMonitor, ThreeFingersTap } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let callback = (threeFingersTap: ThreeFingersTap) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(threeFingersTap)}.`);
            return false;
          };
          try {
            // Subscribe to three-finger tap event
            inputMonitor.on('threeFingersTap', callback);
            // Unsubscribe from three-finger tap event
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

Disables listening for fingerprint gesture input events. This API uses an asynchronous callback to return the result.

**Since:** 12

**Required permissions:** ohos.permission.INPUT_MONITORING

**System capability:** SystemCapability.MultimodalInput.Input.InputMonitor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'fingerprint' | Yes | Input event type. The value is **fingerprint**. |
| receiver | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FingerprintEvent](arkts-input-multimodalinput-shortkey-fingerprintevent-i-sys.md)&gt; | No | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | SystemAPI permit error. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { inputMonitor, FingerprintEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (fingerprintEvent: FingerprintEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(fingerprintEvent)}.`);
            return false;
          };
          try {
            // Subscribe to Fingerprint Events
            inputMonitor.on('fingerprint', callback);
            // Unsubscribe from Fingerprint Events
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
import { inputMonitor, FingerprintEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let callback = (fingerprintEvent: FingerprintEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(fingerprintEvent)}.`);
            return false;
          };
          try {
            // Subscribe to Fingerprint Events
            inputMonitor.on('fingerprint', callback);
            // Unsubscribe from Fingerprint Events
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

Cancels listening for inward swipe events. This API uses an asynchronous callback to return the result.

**Since:** 12

**Required permissions:** ohos.permission.INPUT_MONITORING

**System capability:** SystemCapability.MultimodalInput.Input.InputMonitor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'swipeInward' | Yes | Input event type. The value is fixed at **SwipeInward**. |
| receiver | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SwipeInward](arkts-input-multimodalinput-gestureevent-swipeinward-i-sys.md)&gt; | No | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | SystemAPI permit error. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

**Examples**

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
        // Disable listening for a single callback.
        let callback = (swipeInward: SwipeInward) => {
          console.info(`Succeeded in monitoring on ${JSON.stringify(swipeInward)}.`);
          return false;
        };
        try {
          // Subscribe to Swipe Inward Event
          inputMonitor.on('swipeInward', callback);
          // Unsubscribe from Swipe Inward Event
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
        // Cancel listening for all callbacks.
        let callback = (swipeInward: SwipeInward) => {
          console.info(`Succeeded in monitoring on ${JSON.stringify(swipeInward)}.`);
          return false;
        };
        try {
          // Subscribe to Swipe Inward Event
          inputMonitor.on('swipeInward', callback);
          // Unsubscribe from Swipe Inward Event
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

Disables listening for touchscreen swipe events. This API uses an asynchronous callback to return the result.

**Since:** 18

**Required permissions:** ohos.permission.INPUT_MONITORING

**System capability:** SystemCapability.MultimodalInput.Input.InputMonitor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'touchscreenSwipe' | Yes | Event type. This field has a fixed value of **touchscreenSwipe**. |
| fingers | number | Yes | Number of fingers that trigger the swipe. The value range is [3, 5]. |
| receiver | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[TouchGestureEvent](arkts-input-multimodalinput-gestureevent-touchgestureevent-i-sys.md)&gt; | No | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. 3.Parameter verification failed. |

**Examples**

```TypeScript
import { inputMonitor, TouchGestureEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (event: TouchGestureEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
          };
          let fingers: number = 4;
          try {
            // Subscribe to Touchscreen Swipe Events
            inputMonitor.on('touchscreenSwipe', fingers, callback);
            // Unsubscribe from Touchscreen Swipe Events
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
import { inputMonitor, TouchGestureEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let fingers: number = 4;
          try {
            // Subscribe to Touchscreen Swipe Events
            inputMonitor.on('touchscreenSwipe', fingers, (event: TouchGestureEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            });
            // Unsubscribe from Touchscreen Swipe Events
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

Disables listening for touchscreen pinch events. This API uses an asynchronous callback to return the result.

**Since:** 18

**Required permissions:** ohos.permission.INPUT_MONITORING

**System capability:** SystemCapability.MultimodalInput.Input.InputMonitor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'touchscreenPinch' | Yes | Event type. This field has a fixed value of **touchscreenPinch**. |
| fingers | number | Yes | Number of fingers that trigger the pinch. The value range is [4, 5]. |
| receiver | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[TouchGestureEvent](arkts-input-multimodalinput-gestureevent-touchgestureevent-i-sys.md)&gt; | No | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. 3.Parameter verification failed. |

**Examples**

```TypeScript
import { inputMonitor, TouchGestureEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (event: TouchGestureEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
          };
          let fingers: number = 4;
          try {
            // Subscribe to Touchscreen Pinch Event
            inputMonitor.on('touchscreenPinch', fingers, callback);
            // Unsubscribe from Touchscreen Pinch Event
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
import { inputMonitor, TouchGestureEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let fingers: number = 4;
          try {
            // Subscribe to Touchscreen Pinch Event
            inputMonitor.on('touchscreenPinch', fingers, (event: TouchGestureEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            });
            // Unsubscribe from Touchscreen Pinch Event
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

Cancels listening for the press and release events of the specified key, which can be the **META_LEFT**, **META_RIGHT**, power, or volume key. This API must be used together with **inputMonitor.on ('keyPressed')**. This API uses an asynchronous callback to return the result.

**Since:** 15

**Required permissions:** ohos.permission.INPUT_MONITORING

**System capability:** SystemCapability.MultimodalInput.Input.InputMonitor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyPressed' | Yes | Event type. This parameter has a fixed value of **keyPressed**. |
| receiver | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[KeyEvent](arkts-input-multimodalinput-keyevent-keyevent-i.md)&gt; | No | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

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
          // Disable listening for a single callback.
          try {
            let callback = (event: KeyEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            };
            let keys: Array<KeyCode> = [KeyCode.KEYCODE_VOLUME_UP];
            // Subscribe to Key Press Event
            inputMonitor.on('keyPressed', keys, callback);
            // Unsubscribe from Key Press Event
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
          // Cancel listening for all callbacks.
          try {
            let keys: Array<KeyCode> = [KeyCode.KEYCODE_VOLUME_UP];
            // Subscribe to Key Press Events
            inputMonitor.on('keyPressed', keys, (event: KeyEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            });
            // Unsubscribe from Key Press Events
            inputMonitor.off('keyPressed');
          } catch (error) {
            console.error(`Failed to cancel monitor key pressed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
