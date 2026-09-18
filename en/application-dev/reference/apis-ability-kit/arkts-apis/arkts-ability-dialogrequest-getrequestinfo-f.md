# getRequestInfo

## Modules to Import

```TypeScript
import { dialogRequest } from '@kit.AbilityKit';
```

## getRequestInfo

```TypeScript
function getRequestInfo(want: Want): RequestInfo
```


> **NOTE:** 
> 
> This API can be used by a ServiceExtensionAbility. If the ServiceExtensionAbility implements modal dialog boxes,
> the request information can be obtained from Want. If this API is used in other scenarios, no return value is
> obtained.

Obtains the request information from Want.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want passed in the request for a modal dialog box. |

**Return value:**

| Type | Description |
| --- | --- |
| [RequestInfo](arkts-ability-dialogrequest-requestinfo-i.md) | RequestInfo object obtained, which is used to bind a modal dialog box. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want, dialogRequest } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // Obtain the RequestInfo of the requester.
      let requestInfo = dialogRequest.getRequestInfo(want);
    } catch (err) {
      console.error(`Failed to getRequestInfo. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```
