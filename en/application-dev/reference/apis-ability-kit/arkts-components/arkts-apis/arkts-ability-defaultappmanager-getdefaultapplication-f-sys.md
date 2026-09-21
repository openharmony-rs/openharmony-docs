# getDefaultApplication (System API)

## Modules to Import

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
```

## getDefaultApplication

```TypeScript
function getDefaultApplication(type: string, userId: number, callback: AsyncCallback<BundleInfo>) : void
```

Obtains the default application based on a system-defined application type, a file type that complies with the media type format (either specified by **type** or **subtype**), or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.GET_DEFAULT_APPLICATION

**System capability:** SystemCapability.BundleManager.BundleFramework.DefaultApp

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the target application. It must be set to a value defined by [ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md), a file type that complies with the media type format, or a value defined by [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). |
| userId | number | Yes | User ID, which can be obtained by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[BundleInfo](arkts-ability-bundleinfo-i.md)&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the information is successfully obtained, **err** is **null** and **data** is the application information. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |
| [17700023](../errorcode-bundle.md#17700023-default-application-does-not-exist) | The specified default app does not exist. |
| [17700025](../errorcode-bundle.md#17700025-invalid-type) | The specified type is invalid. |

**Examples**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

let userId = 100;
defaultAppManager.getDefaultApplication(defaultAppManager.ApplicationType.BROWSER, userId, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. bundleInfo:' + JSON.stringify(data));
});

defaultAppManager.getDefaultApplication("image/png", userId, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. bundleInfo:' + JSON.stringify(data));
});

defaultAppManager.getDefaultApplication(uniformTypeDescriptor.UniformDataType.AVI, userId, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. bundleInfo:' + JSON.stringify(data));
});
```


<a id="getdefaultapplication-1"></a>

## getDefaultApplication

```TypeScript
function getDefaultApplication(type: string, callback: AsyncCallback<BundleInfo>) : void
```

Obtains the default application based on a system-defined application type, a file type that complies with the media type format (either specified by **type** or **subtype**), or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.GET_DEFAULT_APPLICATION

**System capability:** SystemCapability.BundleManager.BundleFramework.DefaultApp

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the target application. It must be set to a value defined by [ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md), a file type that complies with the media type format, or a value defined by [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[BundleInfo](arkts-ability-bundleinfo-i.md)&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the information is successfully obtained, **err** is **null** and **data** is the application information. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700023](../errorcode-bundle.md#17700023-default-application-does-not-exist) | The specified default app does not exist. |
| [17700025](../errorcode-bundle.md#17700025-invalid-type) | The specified type is invalid. |

**Examples**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

defaultAppManager.getDefaultApplication(defaultAppManager.ApplicationType.BROWSER, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. bundleInfo:' + JSON.stringify(data));
});

defaultAppManager.getDefaultApplication("image/png", (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. bundleInfo:' + JSON.stringify(data));
});

defaultAppManager.getDefaultApplication(uniformTypeDescriptor.UniformDataType.AVI, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. bundleInfo:' + JSON.stringify(data));
});
```


<a id="getdefaultapplication-2"></a>

## getDefaultApplication

```TypeScript
function getDefaultApplication(type: string, userId?: number) : Promise<BundleInfo>
```

Obtains the default application based on a system-defined application type, a file type that complies with the media type format (either specified by **type** or **subtype**), or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.GET_DEFAULT_APPLICATION

**System capability:** SystemCapability.BundleManager.BundleFramework.DefaultApp

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the target application. It must be set to a value defined by [ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md), a file type that complies with the media type format, or a value defined by [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). |
| userId | number | No | User ID, which can be obtained by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). The default value is the user ID of the caller. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[BundleInfo](arkts-ability-bundleinfo-i.md)&gt; | Promise used to return the default application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |
| [17700023](../errorcode-bundle.md#17700023-default-application-does-not-exist) | The specified default app does not exist. |
| [17700025](../errorcode-bundle.md#17700025-invalid-type) | The specified type is invalid. |

**Examples**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

defaultAppManager.getDefaultApplication(defaultAppManager.ApplicationType.BROWSER)
  .then((data) => {
    console.info('Operation successful. bundleInfo: ' + JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  });

defaultAppManager.getDefaultApplication("image/png")
  .then((data) => {
    console.info('Operation successful. bundleInfo: ' + JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  });

defaultAppManager.getDefaultApplication(uniformTypeDescriptor.UniformDataType.AVI)
  .then((data) => {
    console.info('Operation successful. bundleInfo: ' + JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  });
```
