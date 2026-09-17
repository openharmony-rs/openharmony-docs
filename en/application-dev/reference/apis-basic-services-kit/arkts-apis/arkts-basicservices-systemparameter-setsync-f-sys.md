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

**Since:** 6

**Deprecated since:** 9

**Substitutes:** setSync

**System capability:** SystemCapability.Startup.SystemInfo

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Target key. |
| value | string | Yes | Value to set. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  systemParameter.setSync('test.parameter.key', 'default');
} catch (e) {
  console.error(`Failed to set system parameter. Code: ${(e as BusinessError).code}, message: ${(e as BusinessError).message}`);
}
```
