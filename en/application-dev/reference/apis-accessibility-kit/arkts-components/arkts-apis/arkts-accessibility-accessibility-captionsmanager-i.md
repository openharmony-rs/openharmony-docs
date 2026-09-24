# CaptionsManager

```TypeScript
interface CaptionsManager
```

Manages captions configuration. Before calling any method of **CaptionsManager**, call [accessibility.getCaptionsManager()](arkts-accessibility-accessibility-getcaptionsmanager-f.md) to obtain a **CaptionsManager** instance.

**Since:** 8

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
```

## off('enableChange')

```TypeScript
off(type: 'enableChange', callback?: Callback<boolean>): void
```

Unsubscribes from the state changes of captions configuration. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'enableChange' | Yes | Event type, which is set to **'enableChange'** in this API. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | No | Callback used to unregister. It must be consistent with the callback used in [on('enableChange')](#onenablechange). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type. |

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
    console.info(`subscribe caption manager enable state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.on('enableChange', this.callback);
  }

  aboutToDisappear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.off('enableChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## off('styleChange')

```TypeScript
off(type: 'styleChange', callback?: Callback<CaptionsStyle>): void
```

Unsubscribes from the captions style changes. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'styleChange' | Yes | Event type, which is set to **'styleChange'** in this API. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CaptionsStyle](arkts-accessibility-accessibility-captionsstyle-i.md)&gt; | No | Callback used to unregister. It must be consistent with the callback used in [on('styleChange')](#onstylechange). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type. |

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
  callback: (data: accessibility.CaptionsStyle) => void = this.eventCallback;
  eventCallback(data: accessibility.CaptionsStyle): void {
    console.info(`subscribe caption manager style state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.on('styleChange', this.callback);
  }

  aboutToDisappear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.off('styleChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## on('enableChange')

```TypeScript
on(type: 'enableChange', callback: Callback<boolean>): void
```

Subscribes to the state changes of captions configuration. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - The callback parameter for registering a listener must use a named function instead of an anonymous function.Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> 
> - After calling this method, ensure that [off('enableChange')](#offenablechange)is used to unsubscribe before the component instance is destroyed (for example, in the **aboutToDisappear**lifecycle callback). Otherwise, a crash may occur.

**Since:** 8

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'enableChange' | Yes | Event type, which is set to **'enableChange'** in this API. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. When the enabled state changes, the state is notified through this callback. The value **true** indicates that the caption configuration is enabled, and **false** indicates that the caption configuration is disabled. |

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
    console.info(`subscribe caption manager enable state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.on('enableChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## on('styleChange')

```TypeScript
on(type: 'styleChange', callback: Callback<CaptionsStyle>): void
```

Subscribes to captions style changes. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - The callback parameter for registering a listener must use a named function instead of an anonymous function.Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> 
> - After calling this method, ensure that [off('styleChange')](#offstylechange)is used to unsubscribe before the component instance is destroyed (for example, in the **aboutToDisappear**lifecycle callback). Otherwise, a crash may occur.

**Since:** 8

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'styleChange' | Yes | Event type, which is set to **'styleChange'** in this API. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CaptionsStyle](arkts-accessibility-accessibility-captionsstyle-i.md)&gt; | Yes | Callback invoked when the style of captions changes. |

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
  callback: (data: accessibility.CaptionsStyle) => void = this.eventCallback;
  eventCallback(data: accessibility.CaptionsStyle): void {
    console.info(`subscribe caption manager style state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.on('styleChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## enabled

```TypeScript
enabled: boolean
```

Whether to enable captions configuration. The value **true** indicates that the caption configuration is enabled, and **false** indicates the opposite.

**Type:** boolean

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

## style

```TypeScript
style: CaptionsStyle
```

Style of captions.

**Type:** [CaptionsStyle](arkts-accessibility-accessibility-captionsstyle-i.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing
