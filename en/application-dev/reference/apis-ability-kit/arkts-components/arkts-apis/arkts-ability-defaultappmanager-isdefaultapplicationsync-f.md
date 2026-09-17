# isDefaultApplicationSync

## Modules to Import

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
```

## isDefaultApplicationSync

```TypeScript
function isDefaultApplicationSync(type: string): boolean
```

Checks whether this application is the default application of a system-defined application type or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API returns the result synchronously.

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.DefaultApp

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the target application. It must be set to a value defined by [ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md) or [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the application is the default application; returns **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';

try {
  let data = defaultAppManager.isDefaultApplicationSync(defaultAppManager.ApplicationType.BROWSER)
  console.info('Operation successful. IsDefaultApplicationSync ? ' + JSON.stringify(data));
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
}
```
