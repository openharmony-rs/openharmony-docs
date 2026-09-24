# disableAbility (System API)

## Modules to Import

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

## disableAbility

```TypeScript
function disableAbility(name: string): Promise<void>
```

Disables an accessibility extension. This API must be used together with [config.enableAbility](arkts-accessibility-config-enableability-f-sys.md) or [config.enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md). This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the accessibility extension application, in the format 'bundleName/abilityName'. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300001](../errorcode-accessibility.md#9300001-invalid-bundle-name-or-ability-name) | Invalid bundle name or ability name. |

**Examples**

```TypeScript
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let name: string = 'com.ohos.example/axExtension';

config.disableAbility(name).then(() => {
  console.info(`Succeeded in disabling ability, name is ${name}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to disable ability. Code: ${err.code}, message: ${err.message}`);
});
```


<a id="disableability-1"></a>

## disableAbility

```TypeScript
function disableAbility(name: string, callback: AsyncCallback<void>): void
```

Disables an accessibility extension. This API must be used together with [config.enableAbility](arkts-accessibility-config-enableability-f-sys.md) or [config.enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md). This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the accessibility extension app, in the format of 'bundleName/abilityName'. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the accessibility extension is disabled successfully, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300001](../errorcode-accessibility.md#9300001-invalid-bundle-name-or-ability-name) | Invalid bundle name or ability name. |

**Examples**

```TypeScript
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let name: string = 'com.ohos.example/axExtension';

config.disableAbility(name, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to disable ability. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in disabling, name is ${name}`);
});
```
