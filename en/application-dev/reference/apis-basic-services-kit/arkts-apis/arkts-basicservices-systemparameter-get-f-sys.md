# get (System API)

## Modules to Import

```TypeScript
import { systemParameter } from '@kit.BasicServicesKit';
```

## get

```TypeScript
function get(key: string, callback: AsyncCallback<string>): void
```

Obtains a value of the specified key. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** get

**System capability:** SystemCapability.Startup.SystemInfo

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key to be queried. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the system parameter value asynchronously. If the operation is successful, **err** is **undefined** and **data** is the system parameter value. If the operation fails, **err** is an error object and **data** is **undefined**. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  systemParameter.get('const.ohos.apiversion', (err: BusinessError, data: string) => {
    if (err) {
      console.error(`Failed to get system parameter. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('get const.ohos.apiversion success: ' + data);
    }
  });
} catch (e) {
  console.error('get unexpected error: ' + e);
}
```


<a id="get-1"></a>

## get

```TypeScript
function get(key: string, def: string, callback: AsyncCallback<string>): void
```

Obtains a value of the specified key. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** get

**System capability:** SystemCapability.Startup.SystemInfo

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key to be queried. |
| def | string | Yes | Default value of the system parameter. This parameter must be passed during the call, but its value can be a random character string. **def** takes effect only when the system parameter does not exist. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the system parameter value asynchronously. If the operation is successful, **err** is **undefined** and **data** is the system parameter value. If the operation fails, **err** is an error object and **data** is **undefined**. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  systemParameter.get('const.ohos.apiversion', 'default', (err: BusinessError, data: string) => {
    if (err) {
      console.error(`Failed to get system parameter. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('get const.ohos.apiversion success: ' + data);
    }
  });
} catch (e) {
  console.error('get unexpected error: ' + e);
}
```


<a id="get-2"></a>

## get

```TypeScript
function get(key: string, def?: string): Promise<string>
```

Obtains a value of the specified key. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** get

**System capability:** SystemCapability.Startup.SystemInfo

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key to be queried. |
| def | string | No | Default value of the system parameter.<br> It works only when the system parameter does not exist. <br> Its value can be **undefined** or a random character string. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  let getPromise: Promise<string> = systemParameter.get('const.ohos.apiversion');
  getPromise.then((value: string) => {
    console.info('get const.ohos.apiversion success: ' + value);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get system parameter. Code: ${err.code}, message: ${err.message}`);
  });
} catch (e) {
  console.error('get unexpected error: ' + e);
}
```
