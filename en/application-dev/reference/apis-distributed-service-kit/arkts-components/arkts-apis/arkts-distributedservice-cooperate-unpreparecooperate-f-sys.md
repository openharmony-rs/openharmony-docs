# unprepareCooperate (System API)

## Modules to Import

```TypeScript
import { cooperate } from '@kit.DistributedServiceKit';
```

## unprepareCooperate

```TypeScript
function unprepareCooperate(callback: AsyncCallback<void>): void
```

Cancels the preparation for screen hopping. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.COOPERATE_MANAGER

**System capability:** SystemCapability.Msdp.DeviceStatus.Cooperate

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the operation result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed.  **ArkTS mode:** This error code applies only to ArkTS-Dyn. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  cooperate.unprepareCooperate((error: BusinessError) => {
    if (error) {
      console.error(`Keyboard mouse crossing unprepareCooperate failed, error: ${JSON.stringify(error,
        [`code`, `message`])}`);
      return;
    }
    console.info(`Keyboard mouse crossing unprepareCooperate success.`);
  });
} catch (error) {
  console.error(`Keyboard mouse crossing unprepareCooperate failed, error: ${JSON.stringify(error,
    [`code`, `message`])}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  cooperate.unprepareCooperate().then(() => {
    console.info(`Keyboard mouse crossing unprepareCooperate success.`);
  }, (error: BusinessError) => {
    console.error(`Keyboard mouse crossing unprepareCooperate failed, error: ${JSON.stringify(error,
      [`code`, `message`])}`);
  });
} catch (error) {
  console.error(`Keyboard mouse crossing unprepareCooperate failed, error: ${JSON.stringify(error,
    [`code`, `message`])}`);
}
```


## unprepareCooperate

```TypeScript
function unprepareCooperate(): Promise<void>
```

Cancels the preparation for screen hopping. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.COOPERATE_MANAGER

**System capability:** SystemCapability.Msdp.DeviceStatus.Cooperate

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

See [unprepareCooperate](#unpreparecooperate)
