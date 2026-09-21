# on (System API)

## Modules to Import

```TypeScript
import { screen } from '@kit.ArkUI';
```

## on

```TypeScript
function on(eventType: 'connect' | 'disconnect' | 'change', callback: Callback<number>): void
```

Subscribes to events related to the screen state.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| eventType | 'connect' &#124; 'disconnect' &#124; 'change' | Yes | Event type.<br>- **connect**: an event indicating that the screen is connected.<br>- **disconnect**: an event indicating that the screen is disconnected.<br>- **change**: an event indicating that the screen state changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to return the screen ID, which is an integer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

**Examples**

```TypeScript
let callback: Callback<number> = (data: number) => {
  console.info(`Succeeded in registering the callback for screen changes. Data: ${data}`);
};
// Subscribe to the screen connection event.
screen.on('connect', callback);
```


<a id="on-1"></a>

## on

```TypeScript
function on(eventType: 'connect' | 'disconnect' | 'change', callback: Callback<number>): void
```

Subscribes to events related to the screen state.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| eventType | 'connect' &#124; 'disconnect' &#124; 'change' | Yes | Event type.<br>- **connect**: an event indicating that the screen is connected.<br>- **disconnect**: an event indicating that the screen is disconnected.<br>- **change**: an event indicating that the screen state changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to return the screen ID, which is an integer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

**Examples**

See [on](#on)


<a id="on-2"></a>

## on

```TypeScript
function on(eventType: 'connect' | 'disconnect' | 'change', callback: Callback<number>): void
```

Subscribes to events related to the screen state.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| eventType | 'connect' &#124; 'disconnect' &#124; 'change' | Yes | Event type.<br>- **connect**: an event indicating that the screen is connected.<br>- **disconnect**: an event indicating that the screen is disconnected.<br>- **change**: an event indicating that the screen state changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to return the screen ID, which is an integer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

**Examples**

See [on](#on)
