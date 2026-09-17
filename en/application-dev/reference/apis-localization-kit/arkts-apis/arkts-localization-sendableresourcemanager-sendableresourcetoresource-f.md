# sendableResourceToResource

## Modules to Import

```TypeScript
import { sendableResourceManager } from '@kit.LocalizationKit';
```

## sendableResourceToResource

```TypeScript
export function sendableResourceToResource(resource: SendableResource): Resource
```

Converts a `SendableResource` object transmitted across threads to a `Resource` object.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [SendableResource](arkts-localization-sendableresourcemanager-sendableresource-t.md) | Yes | **SendableResource** object. |

**Return value:**

| Type | Description |
| --- | --- |
| [Resource](arkts-localization-sendableresourcemanager-resource-t.md) | **Resource** object after conversion. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}
```

```TypeScript
import { sendableResourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let resource: sendableResourceManager.Resource = sendableResourceManager.sendableResourceToResource(sendableResourceManager.resourceToSendableResource($r('app.string.test')));
} catch (error) {
    let code = (error as BusinessError).code;
    let message = (error as BusinessError).message;
    console.error(`sendableResourceToResource failed, error code: ${code}, message: ${message}.`);
}
```
