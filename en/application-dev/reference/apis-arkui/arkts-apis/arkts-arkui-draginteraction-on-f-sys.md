# on (System API)

## Modules to Import

```TypeScript
import { dragInteraction } from '@kit.ArkUI';
```

## on('drag')

```TypeScript
function on(type: 'drag', callback: Callback<DragState>): void
```

Enables listening for dragging status changes.

**Since:** 10

**System capability:** SystemCapability.Msdp.DeviceStatus.Drag

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'drag' | Yes | Event type. This field has a fixed value of **drag**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DragState](arkts-arkui-draginteraction-dragstate-e-sys.md)&gt; | Yes | Callback used to return the dragging status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2.Incorrect parameter types.3.Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
try {
  dragInteraction.on('drag', (data: dragInteraction.DragState) => {
    console.info(`Drag interaction event: ${data}`);
  });
} catch (error) {
  console.error(`Register failed, code: ${error.code}, message: ${error.message}`);
}
```
