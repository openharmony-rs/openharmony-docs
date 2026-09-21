# off

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
```

## off('accessibilityStateChange')

```TypeScript
function off(type: 'accessibilityStateChange', callback?: Callback<boolean>): void
```

Unsubscribes from the state changes of the accessibility application. This API uses an asynchronous callback to return the result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'accessibilityStateChange' | Yes | Event type, which is set to **'accessibilityStateChange'** in this API. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | No | Callback used to unregister. It must be consistent with the callback used in [accessibility.on('accessibilityStateChange')](arkts-accessibility-accessibility-on-f.md#onaccessibilitystatechange). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.<br>**Since:** 20 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe accessibility state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.on('accessibilityStateChange', this.callback);
  }

  aboutToDisappear(): void {
    accessibility.off('accessibilityStateChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```


## off('touchGuideStateChange')

```TypeScript
function off(type: 'touchGuideStateChange', callback?: Callback<boolean>): void
```

Unsubscribes from the state changes of touch guide mode. This API uses an asynchronous callback to return the result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'touchGuideStateChange' | Yes | Event type, which is set to **'touchGuideStateChange'** in this API. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | No | Callback used to unregister. It must be consistent with the callback used in [accessibility.on('touchGuideStateChange')](arkts-accessibility-accessibility-on-f.md#ontouchguidestatechange). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe touch guide state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.on('touchGuideStateChange', this.callback);
  }

  aboutToDisappear(): void {
    accessibility.off('touchGuideStateChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```


## off('screenReaderStateChange')

```TypeScript
function off(type: 'screenReaderStateChange', callback?: Callback<boolean>): void
```

Unsubscribes from the state changes of screen reader mode. This API uses an asynchronous callback to return the result.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'screenReaderStateChange' | Yes | Event type, which is set to **'screenReaderStateChange'** in this API. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | No | Callback used to unregister. It must be consistent with the callback used in [accessibility.on('screenReaderStateChange')](arkts-accessibility-accessibility-on-f.md#onscreenreaderstatechange). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe screen reader state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.on('screenReaderStateChange', this.callback);
  }

  aboutToDisappear(): void {
    accessibility.off('screenReaderStateChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```


## off('touchModeChange')

```TypeScript
function off(type: 'touchModeChange', callback?: Callback<string>): void
```

Unsubscribes from the single-tap/double-tap operation mode change event in touch guide mode. This API uses an asynchronous callback to return the result.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'touchModeChange' | Yes | Event type, which is set to **'touchModeChange'** in this API. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | No | Callback used to unregister. The value must be the same as the value of callback in [accessibility.on('touchModeChange')](arkts-accessibility-accessibility-on-f.md#ontouchmodechange). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (mode: string) => void = this.eventCallback;
  eventCallback(mode: string): void {
    console.info(`current touch mode: ${JSON.stringify(mode)}`);
  }

  aboutToAppear(): void {
    accessibility.on('touchModeChange', this.callback);
  }

  aboutToDisappear(): void {
    accessibility.off('touchModeChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```
