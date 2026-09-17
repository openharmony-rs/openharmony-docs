# setDefaultApplicationSync (System API)

## Modules to Import

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
```

## setDefaultApplicationSync

```TypeScript
function setDefaultApplicationSync(type: string, elementName: ElementName, userId?: number): void
```

Sets the default application based on a system-defined application type, a file type that complies with the media type format (either specified by **type** or **subtype**), or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API returns the result synchronously. To set an application as the default browser, the target application must have been granted the ohos.permission.DEFAULT_WEB_BROWSER permission. Otherwise, error 18000001 is returned. [since 26.1.0]

**Since:** 10

**Required permissions:** ohos.permission.SET_DEFAULT_APPLICATION

**System capability:** SystemCapability.BundleManager.BundleFramework.DefaultApp

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the target application. It must be set to a value defined by [ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md), a file type that complies with the media type format, or a value defined by [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). |
| elementName | [ElementName](arkts-ability-elementname-i.md) | Yes | Information about the element to be set as the default application. |
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
| [17700028](../errorcode-bundle.md#17700028-mismatch-between-ability-and-type) | The specified ability does not match the type. |
| 18000001 | The specified type is Web Browser and the specified application does not have the ohos.permission.DEFAULT_WEB_BROWSER permission.<br>**Applicable version:** 26.1.0 and later |

**Examples**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

try {
  defaultAppManager.setDefaultApplicationSync(defaultAppManager.ApplicationType.BROWSER, {
    bundleName: "com.example.myapplication",
    moduleName: "module01",
    abilityName: "EntryAbility"
  });
  console.info('Operation successful.');
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
};

let userId = 100;
try {
  defaultAppManager.setDefaultApplicationSync(defaultAppManager.ApplicationType.BROWSER, {
    bundleName: "com.example.myapplication",
    moduleName: "module01",
    abilityName: "EntryAbility"
  }, userId);
  console.info('Operation successful.');
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
};

try {
  defaultAppManager.setDefaultApplicationSync("image/png", {
    bundleName: "com.example.myapplication",
    moduleName: "module01",
    abilityName: "EntryAbility"
  }, userId);
  console.info('Operation successful.');
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
};

try {
  defaultAppManager.setDefaultApplicationSync(uniformTypeDescriptor.UniformDataType.AVI, {
    bundleName: "com.example.myapplication",
    moduleName: "module01",
    abilityName: "EntryAbility"
  }, userId);
  console.info('Operation successful.');
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
};
```
