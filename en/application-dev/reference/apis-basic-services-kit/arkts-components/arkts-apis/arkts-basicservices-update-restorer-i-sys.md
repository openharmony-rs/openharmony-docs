# Restorer (System API)

```TypeScript
export interface Restorer
```

Defines a tool class for restoring factory settings, such as clearing data in the user partition, deeply clearing data in the user and OS partitions, and synchronously clearing file keys.

> **Factory reset**

- Call **getRestorer** to obtain a **Restorer** object.  
- Select a factory reset mode as required:  
1. **factoryReset**: Common factory reset. Only data in the user partition is cleared in this mode.
2. **forceFactoryReset**: Forcible factory reset. Both data in the user partition and file keys are cleared in
this mode.
3. **deepFactoryReset**: Deep factory reset. Data in the scope specified by **scope** is cleared in this mode.  
**DATA**: Clear data in the user partition only; **DATA_AND_OS**: Clear data in both the user partition and OS partition.  
- After corresponding factory reset method is called, the device will clear data and restore to its factory  
settings.

You are advised to select **factoryReset** for routine maintenance, **forceFactoryReset** when sensitive data or device handover is involved, and **deepFactoryReset** when devices are scrapped or data needs to be physically destroyed.

**Benefits**

This method quickly clears errors, releases storage space, and protects private data. It supports device handover and secure data destruction, meeting data clearing requirements at different security levels.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## deepFactoryReset

```TypeScript
deepFactoryReset(factoryResetStrategy: FactoryResetStrategy): Promise<void>
```

Deeply clears data in the user partition and OS partition by means of overwriting, completely destroys data, and restores the device to its factory settings. After the API is successfully called, the system performs deep factory reset. The process is as follows: Determine the clearance scope based on the policy. Overwrite data in the data partition for multiple times. Destroy key data in the OS partition. Verify whether data is completely destroyed. The device automatically restarts to restore its factory settings. Deep clearance uses physical overwriting to ensure that data cannot be restored by any tool. This API uses a promise to return the result.

Use scenarios: The device is lost, and data needs to be completely destroyed.

**Overview**

This method provides data clearance of the highest security level. Unlike **factoryReset** which clears only data in the user partition and **forceFactoryReset** which clears data in the user partition and keys, **deepFactoryReset** physically destroys data by overwriting multiple times, for example, by writing random data multiple times. This method can prevent residual data from being extracted using data recovery tools. The data clearing scope can be configured: **DATA**: Clear data in the user partition only; **DATA_AND_OS**: Clear data in both the user partition and OS partition.

**Constraints**

- Data destruction is irreversible and cannot be restored by any technical means. Explicit authorization from the  
user must be obtained before performing this operation.  
- The system permission **ohos.permission.FACTORY_RESET** is required.  
- Deep data clearance takes a long time, which may last for hours. Ensure that the device has sufficient battery  
power. It is recommended the battery level be above 50%.  
- The APIs of this module can be used only in the stage model.  
- This method is applicable to extreme scenarios such as device scrapping and complete data destruction with high  
security requirements. It is not recommended for common factory reset scenarios.  
- Before performing the operation, you must clearly inform the user of the consequences and obtain the user's  
confirmation.  
- You are advised to perform factory reset only after the user explicitly confirms the operation.  
- You must call **getDeepFactoryResetInfo** to obtain the estimated time required for the operation and inform  
the user of the waiting time. Ensure that the device has sufficient battery power before performing the deep factory reset.  
- After the operation is complete, the device automatically restarts and restores to its factory settings. The  
app status needs to be saved in advance.

**Since:** 26.0.0

**Required permissions:** ohos.permission.FACTORY_RESET

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| factoryResetStrategy | [FactoryResetStrategy](arkts-basicservices-update-factoryresetstrategy-i-sys.md) | Yes | Factory reset strategy, which contains the **scope** (reset scope) and **strategy** (reset strategy description) fields. This parameter is used to control the scope and mode of factory reset. **scope** specifies the data clearance scope. **DATA** indicates that only data in the user partition is cleared; **DATA_AND_OS** indicates that data in both the user partition and OS partition is cleared. **strategy** is the custom description of the reset operation. The value is a string of 0 to 64 characters. The value can contain letters, digits, underscores (_), hyphens (-), and spaces. An exception is thrown if the value is out of range or contains invalid characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. If the operation is successful, **resolve** returns no value. If the operation fails, the return value of **reject** is an error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [203](../../errorcode-universal.md#203-system-function-prohibited-by-enterprise-management-policies) | This function is prohibited by enterprise management policies. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // Obtain a Restorer object for restoring factory settings.
  let factoryRestorer = update.getRestorer();
  // Create a FactoryResetStrategy object.
  let factoryResetStrategy: update.FactoryResetStrategy = {
    scope: update.FactoryResetScope.DATA, // The reset scope is user data.
    strategy: 'deepFactoryReset test' // Reset scope
  };
  // Perform deep factory reset.
  factoryRestorer.deepFactoryReset(factoryResetStrategy).then(() => {
    console.info(`deepFactoryReset success`);
  }).catch((deepResetError: BusinessError) => {
    console.error(`deepFactoryReset error, code:${deepResetError.code}, message:${deepResetError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get factoryRestorer: ${error}`);
}
```

## factoryReset

```TypeScript
factoryReset(callback: AsyncCallback<void>): void
```

Clears data in the user partition, deletes installed apps, user files, and personal settings, and restores the device to its factory settings. This API uses an asynchronous callback to return the result.

Use scenarios: A user chooses to restore the device to its factory settings.

**Overview**

The process is as follows: Verify the permission to call APIs. Clear data in the user partition by deleting the installed apps, user files, and personal settings. Retain the system partitions and pre-installed apps. Clear the system cache. Set the factory reset flag. The device automatically restarts. Data is cleared in quick erasure mode, and indexes and files in data partitions are deleted without being overwritten. Only data in the user partition is cleared. The OS partition and pre-installed apps are not affected. After the device is restarted, it is restored to its factory settings. The user data is cleared, and the system files remain intact.

**Constraints**

- The operation is irreversible. Remind the user to back up important data and obtain explicit confirmation.  
- The system permission **ohos.permission.FACTORY_RESET** is required.  
- During the operation, the device automatically restarts. The app status needs to be saved.  
- You are advised to perform factory reset only after the user explicitly confirms the operation.

**Since:** 9

**Required permissions:** ohos.permission.FACTORY_RESET

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to receive the factory reset result. The callback parameter is **err**. If the operation is successful, **err** is **null**; if the operation fails, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [203](../../errorcode-universal.md#203-system-function-prohibited-by-enterprise-management-policies) | This function is prohibited by enterprise management policies. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Obtain a Restorer object for restoring factory settings.
  let factoryRestorer = update.getRestorer();
  // Restore factory settings.
  factoryRestorer.factoryReset((resetError: BusinessError) => {
    if (resetError) {
      console.error(`factoryReset error, code:${resetError.code}, message:${resetError.message}.`);
      return;
    }
    console.info(`factoryReset success`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Fail to get factoryRestorer. Code: ${err.code}, message: ${err.message}.`);
}
```

<a id="factoryreset-1"></a>

## factoryReset

```TypeScript
factoryReset(): Promise<void>
```

Clears data in the user partition, deletes installed apps, user files, and personal settings, and restores the device to its factory settings. This API uses a promise to return the result.

Use scenarios: A user chooses to restore the device to its factory settings.

**Overview**

The process is as follows: Verify the permission to call APIs. Clear data in the user partition by deleting the installed apps, user files, and personal settings. Retain the system partitions and pre-installed apps. Clear the system cache. Set the factory reset flag. The device automatically restarts. Data is cleared in quick erasure mode, and indexes and files in data partitions are deleted without being overwritten. Only data in the user partition is cleared. The OS partition and pre-installed apps are not affected. After the device is restarted, it is restored to its factory settings. The user data is cleared, and the system files remain intact.

**Constraints**

- The operation is irreversible. Remind the user to back up important data and obtain explicit confirmation.  
- The system permission **ohos.permission.FACTORY_RESET** is required.  
- During the operation, the device automatically restarts. The app status needs to be saved.  
- You are advised to perform factory reset only after the user explicitly confirms the operation.

**Since:** 9

**Required permissions:** ohos.permission.FACTORY_RESET

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. If the operation is successful, **resolve** returns no value. If the operation fails, the return value of **reject** is an error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [203](../../errorcode-universal.md#203-system-function-prohibited-by-enterprise-management-policies) | This function is prohibited by enterprise management policies. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Obtain a Restorer object for restoring factory settings.
  let factoryRestorer = update.getRestorer();
  // Restore factory settings.
  factoryRestorer.factoryReset().then(() => {
    console.info(`factoryReset success`);
  }).catch((resetError: BusinessError) => {
    console.error(`factoryReset error, code:${resetError.code}, message:${resetError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get factoryRestorer: ${error}`);
}
```

## forceFactoryReset

```TypeScript
forceFactoryReset(): Promise<void>
```

Clears data in the user partition, clears the file key, deletes the installed apps and user files, and restores the device to factory settings. The file key is generated by the system for encrypting user data and is stored in a secure area to protect sensitive user data. After the API is successfully called, the system immediately performs forcible factory reset. The process is as follows: Clear data in the user partition. Clear the file key. Clear the system cache and temporary files. The device automatically restarts to restore its factory settings. This API uses a promise to return the result.

Use scenarios: This operation is performed to thoroughly delete sensitive data or clear data before device handover.

**Overview**

The difference between this method and **factoryReset** is that this method clears the file key synchronously. The file key is generated by the system to encrypt user data and is stored in a secure area such as the keystore or a dedicated partition. The file key is used to encrypt personal files, app data, and configuration information in the user data partition. After the file key is cleared, the residual encrypted data cannot be decrypted or restored, achieving more complete data destruction. **forceFactoryReset** not only deletes data in the user partition, but also sends a command of data clearing to the key management system to completely delete the key from the secure storage, ensuring that the encrypted data cannot be restored. This mechanism is applicable to secure data destruction.

**Constraints**

- The operation is irreversible and will permanently delete all user data and encryption keys. Therefore, remind  
users to back up important data in advance.  
- The system permission **ohos.permission.FORCE_FACTORY_RESET** is required.  
- Before calling this method, remind users to back up important data and confirm the operation.  
- You are advised to perform factory reset only after the user explicitly confirms the operation.  
- This method is applicable to scenarios with high security requirements, such as destruction of sensitive data  
and device handover.  
- During the operation, the device automatically restarts. The app status needs to be saved.

**Since:** 23

**Required permissions:** ohos.permission.FORCE_FACTORY_RESET

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. If the operation is successful, **resolve** returns no value. If the operation fails, the return value of **reject** is an error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [203](../../errorcode-universal.md#203-system-function-prohibited-by-enterprise-management-policies) | This function is prohibited by enterprise management policies. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // Obtain a Restorer object for restoring factory settings.
  let factoryRestorer = update.getRestorer();
  // Perform forcible factory reset.
  factoryRestorer.forceFactoryReset().then(() => {
    console.info(`forceFactoryReset success`);
  }).catch((forceResetError: BusinessError) => {
    console.error(`forceFactoryReset error, code:${forceResetError.code}, message:${forceResetError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get factoryRestorer: ${error}`);
}
```

## getDeepFactoryResetInfo

```TypeScript
getDeepFactoryResetInfo(factoryResetStrategy: FactoryResetStrategy): Promise<FactoryResetInfo>
```

Obtains the deep factory reset information, which is used to estimate the time required for the reset. After this method is called, the system calculates the time required for deep factory reset based on the clearance scope specified by **DATA** or **DATA_AND_OS** and the device storage capacity, and returns a **FactoryResetInfo** object that contains the estimated time required for reset. This API uses a promise to return the result.

Use scenarios: Before performing the deep factory reset, remind the user with the waiting time, plan the operation time, and ensure that the battery level is sufficient.

**Overview**

This method calculates the time required by analyzing the data clearance scope and storage medium. Deep data clearance destroys data by overwriting it multiple times. The time required is directly proportional to the clearance scope. It the clearance scope is set to **DATA**, it takes a shorter time because only data in the user partition needs to be cleared; if the scope is set to **DATA_AND_OS**, it takes a longer time because data in both the user partition and OS partition needs to be cleared. The system calculates the estimated time based on factors such as the storage capacity, number of overwrites, and write speed.

**Constraints**

- The APIs of this module can be used only in the stage model.  
- The system permission **ohos.permission.FACTORY_RESET** is required.  
- The returned time is an estimated value. The actual time required may vary depending on the device status.  
- It is recommended that the device power be higher than 50%. When the device power is lower than that level, do  
not perform the deep factory reset. Otherwise, the operation may fail due to power-off.  
- This API must be called before **deepFactoryReset** is called to help users prepare for time and power.

**Since:** 26.0.0

**Required permissions:** ohos.permission.FACTORY_RESET

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| factoryResetStrategy | [FactoryResetStrategy](arkts-basicservices-update-factoryresetstrategy-i-sys.md) | Yes | Factory reset strategy, which contains the **scope** (reset scope) and **strategy** (reset strategy description) fields. This parameter is used to control the scope and mode of factory reset. **scope** specifies the data clearance scope. **DATA** indicates that only data in the user partition is cleared; **DATA_AND_OS** indicates that data in both the user partition and OS partition is cleared. **strategy** is the custom description of the reset operation. The value is a string of 0 to 64 characters. The value can contain letters, digits, underscores (_), hyphens (-), and spaces. An exception is thrown if the value is out of range or contains invalid characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FactoryResetInfo](arkts-basicservices-update-factoryresetinfo-i-sys.md)&gt; | Promise used to return the result. If the operation is successful, the return value of **resolve** is a **FactoryResetInfo** object, including the estimated time required for reset. If the operation fails, the return value of **reject** is an error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Create a FactoryResetStrategy object.
let factoryResetStrategy: update.FactoryResetStrategy = {
  scope: update.FactoryResetScope.DATA, // The reset scope is user data.
  strategy: 'getDeepFactoryResetInfo test' // Reset scope
};
try {
  // Obtain a Restorer object for restoring factory settings.
  let factoryRestorer = update.getRestorer();
  // Query the deep factory reset strategy.
  factoryRestorer.getDeepFactoryResetInfo(factoryResetStrategy).then((deepResetInfo: update.FactoryResetInfo) => {
    console.info(`getDeepFactoryResetInfo success`);
  }).catch((resetInfoError: BusinessError) => {
    console.error(`getDeepFactoryResetInfo promise error, code:${resetInfoError.code}, message:${resetInfoError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get factoryRestorer: ${error}`);
}
```
