# set (System API)

## Modules to Import

```TypeScript
import { systemParameter } from '@kit.BasicServicesKit';
```

## set

```TypeScript
function set(key: string, value: string, callback: AsyncCallback<void>): void
```

Sets a value of the specified key. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** set

**System capability:** SystemCapability.Startup.SystemInfo

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key to be set. |
| value | string | Yes | Value to set. For details about length limit, see [Parameter Management](../../../../device-dev/subsystems/subsys-boot-init-sysparam.md). |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the setting result asynchronously. If the setting is successful, **err** is **undefined**. If the setting fails, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  systemParameter.set('test.parameter.key', 'testValue', (err: BusinessError, data: void) => {
    if (err) {
      console.error(`Failed to set system parameter. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('set test.parameter.key value success');
    }
  });
} catch (e) {
  console.error('set unexpected error: ' + e);
}
```


<a id="set-1"></a>

## set

```TypeScript
function set(key: string, value: string): Promise<void>
```

Sets a value of the specified key. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** set

**System capability:** SystemCapability.Startup.SystemInfo

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key to be set. |
| value | string | Yes | Value to set. For details about length limit, see [Parameter Management](../../../../device-dev/subsystems/subsys-boot-init-sysparam.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  let setPromise: Promise<void> = systemParameter.set('test.parameter.key', 'testValue');
  setPromise.then(() => {
    console.info('set test.parameter.key success');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set system parameter. Code: ${err.code}, message: ${err.message}`);
  });
} catch (e) {
  console.error('set unexpected error: ' + e);
}
```
