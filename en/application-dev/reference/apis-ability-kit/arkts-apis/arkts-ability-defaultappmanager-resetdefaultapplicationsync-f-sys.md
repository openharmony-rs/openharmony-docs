# resetDefaultApplicationSync (System API)

## Modules to Import

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
```

## resetDefaultApplicationSync

```TypeScript
function resetDefaultApplicationSync(type: string, userId?: number): void
```

Resets the default application based on a system-defined application type, a file type that complies with the media type format (either specified by **type** or **subtype**), or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API returns the result synchronously.

**Since:** 10

**Required permissions:** ohos.permission.SET_DEFAULT_APPLICATION

**System capability:** SystemCapability.BundleManager.BundleFramework.DefaultApp

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the target application. It must be set to a value defined by [ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md), a file type that complies with the media type format, or a value defined by [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). |
| userId | number | No | User ID, which can be obtained by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). The default value is the user ID of the caller. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |
| [17700025](../errorcode-bundle.md#17700025-invalid-type) | The specified type is invalid. |

**Examples**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

let userId = 100;
try {
  defaultAppManager.resetDefaultApplicationSync(defaultAppManager.ApplicationType.BROWSER, userId);
  console.info('Operation successful.');
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
};

try {
  defaultAppManager.resetDefaultApplicationSync("image/png", userId);
  console.info('Operation successful.');
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
};

try {
  defaultAppManager.resetDefaultApplicationSync(uniformTypeDescriptor.UniformDataType.AVI, userId);
  console.info('Operation successful.');
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
};
```
