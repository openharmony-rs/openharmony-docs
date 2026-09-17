# getRemoteAbilityInfo (System API)

## Modules to Import

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
```

## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementName: ElementName, callback: AsyncCallback<RemoteAbilityInfo>): void
```

Obtains information about the remote ability that matches the given element name. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.DistributedBundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementName | [ElementName](arkts-ability-elementname-i.md) | Yes | Target element name. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[RemoteAbilityInfo](arkts-ability-distributedbundlemanager-remoteabilityinfo-t-sys.md)&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the operation is successful, **err** is **null** and **data** is the RemoteAbilityInfo object obtained. Otherwise, **err** is an error object and **data** is **undefined**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700003](../errorcode-bundle.md#17700003-ability-name-does-not-exist) | The specified ability name is not found. |
| [17700007](../errorcode-bundle.md#17700007-incorrect-device-id) | The specified device ID is not found. |
| [17700027](../errorcode-bundle.md#17700027-distributed-service-is-not-started) | The distributed service is not running. |

**Examples**

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    distributedBundleManager.getRemoteAbilityInfo(
        {
            deviceId: '1',
            bundleName: 'com.example.application',
            abilityName: 'EntryAbility'
        }, (err: BusinessError, data: distributedBundleManager.RemoteAbilityInfo) => {
            if (err) {
                console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
            } else {
                console.info('Operation succeed:' + JSON.stringify(data));
            }
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    distributedBundleManager.getRemoteAbilityInfo(
        {
            deviceId: '1',
            bundleName: 'com.example.application',
            abilityName: 'EntryAbility'
        }).then((data: distributedBundleManager.RemoteAbilityInfo) => {
            console.info('Operation succeed:' + JSON.stringify(data));
        }).catch((err: BusinessError) => {
            console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    distributedBundleManager.getRemoteAbilityInfo(
        [
            {
                deviceId: '1',
                bundleName: 'com.example.application1',
                abilityName: 'EntryAbility1'
            },
            {
                deviceId: '1',
                bundleName: 'com.example.application2',
                abilityName: 'EntryAbility'
            }
        ], (err: BusinessError, data: distributedBundleManager.RemoteAbilityInfo[]) => {
          if (err) {
            console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
          } else {
            console.info('Operation succeed:' + JSON.stringify(data));
          }
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    distributedBundleManager.getRemoteAbilityInfo(
        [
            {
                deviceId: '1',
                bundleName: 'com.example.application',
                abilityName: 'EntryAbility'
            },
            {
                deviceId: '1',
                bundleName: 'com.example.application2',
                abilityName: 'EntryAbility'
            }
        ]).then((data: distributedBundleManager.RemoteAbilityInfo[]) => {
            console.info('Operation succeed:' + JSON.stringify(data));
        }).catch((err: BusinessError) => {
            console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    distributedBundleManager.getRemoteAbilityInfo(
        {
            deviceId: '1',
            bundleName: 'com.example.application',
            abilityName: 'EntryAbility'
        }, 'zh-Hans-CN', (err: BusinessError, data: distributedBundleManager.RemoteAbilityInfo) => {
          if (err) {
            console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
          } else {
            console.info('Operation succeed:' + JSON.stringify(data));
          }
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    distributedBundleManager.getRemoteAbilityInfo(
        {
            deviceId: '1',
            bundleName: 'com.example.application',
            abilityName: 'EntryAbility'
        }, 'zh-Hans-CN').then((data: distributedBundleManager.RemoteAbilityInfo) => {
            console.info('Operation succeed:' + JSON.stringify(data));
        }).catch((err: BusinessError) => {
            console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    distributedBundleManager.getRemoteAbilityInfo(
        [
            {
                deviceId: '1',
                bundleName: 'com.example.application1',
                abilityName: 'EntryAbility1'
            },
            {
                deviceId: '1',
                bundleName: 'com.example.application2',
                abilityName: 'EntryAbility'
            }
        ], 'zh-Hans-CN', (err: BusinessError, data: distributedBundleManager.RemoteAbilityInfo[]) => {
          if (err) {
           console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
          } else {
            console.info('Operation succeed:' + JSON.stringify(data));
          }
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    distributedBundleManager.getRemoteAbilityInfo(
        [
            {
                deviceId: '1',
                bundleName: 'com.example.application',
                abilityName: 'EntryAbility'
            },
            {
                deviceId: '1',
                bundleName: 'com.example.application2',
                abilityName: 'EntryAbility'
            }
        ], 'zh-Hans-CN').then((data: distributedBundleManager.RemoteAbilityInfo[]) => {
            console.info('Operation succeed:' + JSON.stringify(data));
        }).catch((err: BusinessError) => {
            console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementName: ElementName): Promise<RemoteAbilityInfo>
```

Obtains information about the remote ability that matches the given element name. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.DistributedBundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementName | [ElementName](arkts-ability-elementname-i.md) | Yes | Target element name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RemoteAbilityInfo](arkts-ability-distributedbundlemanager-remoteabilityinfo-t-sys.md)&gt; | Promise used to return the result. If the operation is successful, the RemoteAbilityInfo object is returned. Otherwise, an error object is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700003](../errorcode-bundle.md#17700003-ability-name-does-not-exist) | The specified ability name is not found. |
| [17700007](../errorcode-bundle.md#17700007-incorrect-device-id) | The specified device ID is not found. |
| [17700027](../errorcode-bundle.md#17700027-distributed-service-is-not-started) | The distributed service is not running. |

**Examples**

See [getRemoteAbilityInfo](#getremoteabilityinfo)


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementNames: Array<ElementName>, callback: AsyncCallback<Array<RemoteAbilityInfo>>): void
```

Obtains information about the remote abilities that match the given element names. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.DistributedBundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementNames | Array&lt;[ElementName](arkts-ability-elementname-i.md)&gt; | Yes | **ElementName** array, whose maximum length is 10. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[RemoteAbilityInfo](arkts-ability-distributedbundlemanager-remoteabilityinfo-t-sys.md)&gt;&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the operation is successful, **err** is **null** and **data** is the array of RemoteAbilityInfo objects obtained. Otherwise, **err** is an error object and **data** is **undefined**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700003](../errorcode-bundle.md#17700003-ability-name-does-not-exist) | The specified ability name is not found. |
| [17700007](../errorcode-bundle.md#17700007-incorrect-device-id) | The specified device ID is not found. |
| [17700027](../errorcode-bundle.md#17700027-distributed-service-is-not-started) | The distributed service is not running. |

**Examples**

See [getRemoteAbilityInfo](#getremoteabilityinfo)


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementNames: Array<ElementName>): Promise<Array<RemoteAbilityInfo>>
```

Obtains information about the remote abilities that match the given element names. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.DistributedBundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementNames | Array&lt;[ElementName](arkts-ability-elementname-i.md)&gt; | Yes | **ElementName** array, whose maximum length is 10. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[RemoteAbilityInfo](arkts-ability-distributedbundlemanager-remoteabilityinfo-t-sys.md)&gt;&gt; | Promise used to return the result. If the operation is successful, an array of RemoteAbilityInfo objects is returned. Otherwise, an error object is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700003](../errorcode-bundle.md#17700003-ability-name-does-not-exist) | The specified ability name is not found. |
| [17700007](../errorcode-bundle.md#17700007-incorrect-device-id) | The specified device ID is not found. |
| [17700027](../errorcode-bundle.md#17700027-distributed-service-is-not-started) | The distributed service is not running. |

**Examples**

See [getRemoteAbilityInfo](#getremoteabilityinfo)


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementName: ElementName, locale: string, callback: AsyncCallback<RemoteAbilityInfo>): void
```

Obtains information about the remote ability that matches the given element name and locale. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.DistributedBundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementName | [ElementName](arkts-ability-elementname-i.md) | Yes | Target element name. |
| locale | string | Yes | Target locale. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[RemoteAbilityInfo](arkts-ability-distributedbundlemanager-remoteabilityinfo-t-sys.md)&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the operation is successful, **err** is **null** and **data** is the RemoteAbilityInfo object obtained. Otherwise, **err** is an error object and **data** is **undefined**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700003](../errorcode-bundle.md#17700003-ability-name-does-not-exist) | The specified ability name is not found. |
| [17700007](../errorcode-bundle.md#17700007-incorrect-device-id) | The specified device ID is not found. |
| [17700027](../errorcode-bundle.md#17700027-distributed-service-is-not-started) | The distributed service is not running. |

**Examples**

See [getRemoteAbilityInfo](#getremoteabilityinfo)


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementName: ElementName, locale: string): Promise<RemoteAbilityInfo>
```

Obtains information about the remote ability that matches the given element name and locale. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.DistributedBundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementName | [ElementName](arkts-ability-elementname-i.md) | Yes | Target element name. |
| locale | string | Yes | Target locale. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RemoteAbilityInfo](arkts-ability-distributedbundlemanager-remoteabilityinfo-t-sys.md)&gt; | Promise used to return the result. If the operation is successful, the RemoteAbilityInfo object is returned. Otherwise, an error object is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700003](../errorcode-bundle.md#17700003-ability-name-does-not-exist) | The specified ability name is not found. |
| [17700007](../errorcode-bundle.md#17700007-incorrect-device-id) | The specified device ID is not found. |
| [17700027](../errorcode-bundle.md#17700027-distributed-service-is-not-started) | The distributed service is not running. |

**Examples**

See [getRemoteAbilityInfo](#getremoteabilityinfo)


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementNames: Array<ElementName>, locale: string, callback: AsyncCallback<Array<RemoteAbilityInfo>>): void
```

Obtains information about the remote abilities that match the given element names and locale. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.DistributedBundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementNames | Array&lt;[ElementName](arkts-ability-elementname-i.md)&gt; | Yes | **ElementName** array, whose maximum length is 10. |
| locale | string | Yes | Target locale. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[RemoteAbilityInfo](arkts-ability-distributedbundlemanager-remoteabilityinfo-t-sys.md)&gt;&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the operation is successful, **err** is **null** and **data** is the array of RemoteAbilityInfo objects obtained. Otherwise, **err** is an error object and **data** is **undefined**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700003](../errorcode-bundle.md#17700003-ability-name-does-not-exist) | The specified ability name is not found. |
| [17700007](../errorcode-bundle.md#17700007-incorrect-device-id) | The specified device ID is not found. |
| [17700027](../errorcode-bundle.md#17700027-distributed-service-is-not-started) | The distributed service is not running. |

**Examples**

See [getRemoteAbilityInfo](#getremoteabilityinfo)


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementNames: Array<ElementName>, locale: string): Promise<Array<RemoteAbilityInfo>>
```

Obtains information about the remote abilities that match the given element names and locale. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.DistributedBundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementNames | Array&lt;[ElementName](arkts-ability-elementname-i.md)&gt; | Yes | **ElementName** array, whose maximum length is 10. |
| locale | string | Yes | Target locale. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[RemoteAbilityInfo](arkts-ability-distributedbundlemanager-remoteabilityinfo-t-sys.md)&gt;&gt; | Promise used to return the result. If the operation is successful, an array of RemoteAbilityInfo objects is returned. Otherwise, an error object is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700003](../errorcode-bundle.md#17700003-ability-name-does-not-exist) | The specified ability name is not found. |
| [17700007](../errorcode-bundle.md#17700007-incorrect-device-id) | The specified device ID is not found. |
| [17700027](../errorcode-bundle.md#17700027-distributed-service-is-not-started) | The distributed service is not running. |

**Examples**

See [getRemoteAbilityInfo](#getremoteabilityinfo)
