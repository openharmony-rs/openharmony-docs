# setSync (System API)

## Modules to Import

```TypeScript
import { systemParameter } from '@kit.BasicServicesKit';
```

## setSync

```TypeScript
function setSync(key: string, value: string): void
```

Sets a value for the specified key.

> **NOTE:** 
> 
> Both **setSync** and **set** can be used to set system parameter values.
> - **setSync**: synchronous method, which directly sets the system parameter and returns the result immediately. This method is suitable for simple synchronization scenarios.
> - **set**: asynchronous method, which uses a callback or promise to return the result asynchronously. This method is suitable for scenarios that require asynchronous processing.
> 
> You should select a proper method based on the specific scenario.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** setSync

**System capability:** SystemCapability.Startup.SystemInfo

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key to be set. |
| value | string | Yes | Value to set. For details about length limit, see [Parameter Management](../../../../device-dev/subsystems/subsys-boot-init-sysparam.md). |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  systemParameter.setSync('test.parameter.key', 'default');
} catch (e) {
  console.error(`Failed to set system parameter. Code: ${(e as BusinessError).code}, message: ${(e as BusinessError).message}`);
}
```
