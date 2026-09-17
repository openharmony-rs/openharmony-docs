# isDefaultApplication

## Modules to Import

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
```

## isDefaultApplication

```TypeScript
function isDefaultApplication(type: string, callback: AsyncCallback<boolean>) : void
```

Checks whether this application is the default application of a system-defined application type or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.DefaultApp

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the target application. It must be set to a value defined by [ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md) or [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the operation is successful, **err** is **null** and **data** is a Boolean value (**true** if the application is the default application, **false** otherwise). If the operation fails, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

defaultAppManager.isDefaultApplication(defaultAppManager.ApplicationType.BROWSER)
  .then((data) => {
    console.info('Operation successful. IsDefaultApplication ? ' + JSON.stringify(data));
  }).catch((error: BusinessError) => {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
});
```

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

defaultAppManager.isDefaultApplication(defaultAppManager.ApplicationType.BROWSER, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. IsDefaultApplication ? ' + JSON.stringify(data));
});
```


## isDefaultApplication

```TypeScript
function isDefaultApplication(type: string) : Promise<boolean>
```

Checks whether this application is the default application of a system-defined application type or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.DefaultApp

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the target application. It must be set to a value defined by [ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md) or [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result, indicating whether the application is the default application. **true** if the application is the default application, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

See [isDefaultApplication](#isdefaultapplication)
