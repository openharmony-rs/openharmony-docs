# Config (System API)

```TypeScript
class Config
```

Provides APIs for setting device-cloud synergy, including enabling and disabling device-cloud synergy, clearing data, and notifying data changes.

**Since:** 10

<!--Device-cloudData-class Config--><!--Device-cloudData-class Config-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## batchQueryLastSyncInfo

```TypeScript
static batchQueryLastSyncInfo(
        accountId: string,
        bundleInfos: Array<BundleInfo>
    ): Promise<Record<string, Record<string, SyncInfo>>>
```

Queries information about the last device-cloud sync in batches.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

**Model restriction:** This API can be used only in the stage model.

<!--Device-Config-static batchQueryLastSyncInfo(        accountId: string,        bundleInfos: Array<BundleInfo>    ): Promise<Record<string, Record<string, SyncInfo>>>--><!--Device-Config-static batchQueryLastSyncInfo(        accountId: string,        bundleInfos: Array<BundleInfo>    ): Promise<Record<string, Record<string, SyncInfo>>>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | string | Yes | ID of the logged-in cloud account. |
| bundleInfos | Array&lt;[BundleInfo](arkts-arkdata-clouddata-bundleinfo-i-sys.md)&gt; | Yes | Array of application information to be queried in batches. Value range: The array length is [1, 30]. If the array length is out of range, error code 14800001 is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Record&lt;string, Record&lt;string, [SyncInfo](arkts-arkdata-clouddata-syncinfo-i-sys.md)&gt;&gt;&gt; | Promise used to return the application bundle name and the result set of the last device-cloud sync for the database. The key of the outer record is the application bundle name, and the key of the inner record is the database name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. the accountId is empty;         2. the bundlename is null; 3. the number of bundleInfos exceeds the upper limit or the number is 0. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const accountId: string = "accountId";
const bundleInfos: Array<cloudData.BundleInfo> = [
  { bundleName: "bundleName1", storeId: "storeId1" },
  { bundleName: "bundleName2" }
];

try {
  cloudData.Config.batchQueryLastSyncInfo(accountId, bundleInfos).then((result) => {
    console.info(`Succeeded in querying last sync info. Result is ${JSON.stringify(result)}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to query last sync info. Error code is ${err.code}, message is ${err.message}`);
  });
} catch(err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## changeAppCloudSwitch

```TypeScript
static changeAppCloudSwitch(
      accountId: string,
      bundleName: string,
      status: boolean,
      callback: AsyncCallback<void>
    ): void
```

Changes the device-cloud synergy setting for an application. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static changeAppCloudSwitch(      accountId: string,      bundleName: string,      status: boolean,      callback: AsyncCallback<void>    ): void--><!--Device-Config-static changeAppCloudSwitch(      accountId: string,      bundleName: string,      status: boolean,      callback: AsyncCallback<void>    ): void-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | string | Yes | ID of the logged-in cloud account. |
| bundleName | string | Yes | Bundle name of the application. |
| status | boolean | Yes | New device-cloud synergy setting. The value **true** means to enable device-cloud synergy; the value **false** means the opposite. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;         3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let account: string = "test_id";
let bundleName: string = "test_bundleName";
try {
  cloudData.Config.changeAppCloudSwitch(account, bundleName, true, (err: BusinessError) => {
    if (err === undefined) {
      console.info('Succeeded in changing App cloud switch');
    } else {
      console.error(`Failed to change App cloud switch. Code: ${err.code}, message: ${err.message}`);
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## changeAppCloudSwitch

```TypeScript
static changeAppCloudSwitch(accountId: string, bundleName: string, status: boolean): Promise<void>
```

Changes the device-cloud synergy setting for an application. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static changeAppCloudSwitch(accountId: string, bundleName: string, status: boolean): Promise<void>--><!--Device-Config-static changeAppCloudSwitch(accountId: string, bundleName: string, status: boolean): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | string | Yes | ID of the logged-in cloud account. |
| bundleName | string | Yes | Bundle name of the application. |
| status | boolean | Yes | New device-cloud synergy setting. The value **true** means to enable device-cloud synergy; the value **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;         3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let account: string = "test_id";
let bundleName: string = "test_bundleName";
try {
  cloudData.Config.changeAppCloudSwitch(account, bundleName, true).then(() => {
    console.info('Succeeded in changing App cloud switch');
  }).catch((err: BusinessError) => {
    console.error(`Failed to change App cloud switch. Code is ${err.code}, message is ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## changeAppCloudSwitch

```TypeScript
static changeAppCloudSwitch(
      accountId: string,
      bundleName: string,
      status: boolean,
      config?: SwitchConfig
    ): Promise<void>
```

Changes the device-cloud synergy setting for an application. This API uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

**Model restriction:** This API can be used only in the stage model.

<!--Device-Config-static changeAppCloudSwitch(      accountId: string,      bundleName: string,      status: boolean,      config?: SwitchConfig    ): Promise<void>--><!--Device-Config-static changeAppCloudSwitch(      accountId: string,      bundleName: string,      status: boolean,      config?: SwitchConfig    ): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | string | Yes | ID of the logged-in cloud account. |
| bundleName | string | Yes | Bundle name of the application. |
| status | boolean | Yes | New device-cloud synergy setting. The value **true** means to enable device-cloud synergy; the value **false** means the opposite. |
| config | [SwitchConfig](arkts-arkdata-clouddata-switchconfig-i-sys.md) | No | Switch configuration of a device-cloud synergy database. Device-cloud synergy priority: application &gt; database &gt; table. If this parameter is not set, the application-level device-cloud synergy is used by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let account: string = "test_id";
let bundleName: string = "test_bundleName";
let config: cloudData.SwitchConfig = {
  dbInfo: {
    'test_storeName1': {
      enable: true,
      tableInfo: {
        'test_tableName1': true,
        'test_tableName2': false
      }
    }
  }
};
try {
  cloudData.Config.changeAppCloudSwitch(account, bundleName, true, config).then(() => {
    console.info('Succeeded in changing App cloud switch');
  }).catch((err: BusinessError) => {
    console.error(`Failed to change App cloud switch. Code is ${err.code}, message is ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## clear

```TypeScript
static clear(
      accountId: string,
      appActions: Record<string, ClearAction>,
      callback: AsyncCallback<void>
    ): void
```

Clears the cloud data locally. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static clear(      accountId: string,      appActions: Record<string, ClearAction>,      callback: AsyncCallback<void>    ): void--><!--Device-Config-static clear(      accountId: string,      appActions: Record<string, ClearAction>,      callback: AsyncCallback<void>    ): void-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | string | Yes | ID of the logged-in cloud account. |
| appActions | Record&lt;string, [ClearAction](arkts-arkdata-clouddata-clearaction-e-sys.md)&gt; | Yes | Application information of the data to be cleared and the clearing rule of each application. The key is the application bundle name, and the value is the clearing rule.<br>**Since:** 11 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;         3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let account: string = "test_id";
type dataType = Record<string, cloudData.ClearAction>;
let appActions: dataType = {
  'test_bundleName1': cloudData.ClearAction.CLEAR_CLOUD_INFO,
  'test_bundleName2': cloudData.ClearAction.CLEAR_CLOUD_DATA_AND_INFO
};
try {
  cloudData.Config.clear(account, appActions, (err: BusinessError) => {
    if (err === undefined) {
      console.info('Succeeded in clearing cloud data');
    } else {
      console.error(`Failed to clear cloud data. Code: ${err.code}, message: ${err.message}`);
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## clear

```TypeScript
static clear(accountId: string, appActions: Record<string, ClearAction>): Promise<void>
```

Clears the cloud data locally. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static clear(accountId: string, appActions: Record<string, ClearAction>): Promise<void>--><!--Device-Config-static clear(accountId: string, appActions: Record<string, ClearAction>): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | string | Yes | ID of the logged-in cloud account. |
| appActions | Record&lt;string, [ClearAction](arkts-arkdata-clouddata-clearaction-e-sys.md)&gt; | Yes | Information about the application whose data is to be cleared and the operation to perform.<br>**Since:** 11 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types;         3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let account: string = "test_id";
type dataType = Record<string, cloudData.ClearAction>;
let appActions: dataType = {
  'test_bundleName1': cloudData.ClearAction.CLEAR_CLOUD_INFO,
  'test_bundleName2': cloudData.ClearAction.CLEAR_CLOUD_DATA_AND_INFO
};
try {
  cloudData.Config.clear(account, appActions).then(() => {
    console.info('Succeeded in clearing cloud data');
  }).catch((err: BusinessError) => {
    console.error(`Failed to clear cloud data. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## clear

```TypeScript
static clear(
      accountId: string,
      appActions: Record<string, ClearAction>,
      config?: Record<string, ClearConfig>
    ): Promise<void>
```

Clears the cloud data locally. This API uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

**Model restriction:** This API can be used only in the stage model.

<!--Device-Config-static clear(      accountId: string,      appActions: Record<string, ClearAction>,      config?: Record<string, ClearConfig>    ): Promise<void>--><!--Device-Config-static clear(      accountId: string,      appActions: Record<string, ClearAction>,      config?: Record<string, ClearConfig>    ): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | string | Yes | ID of the logged-in cloud account. |
| appActions | Record&lt;string, [ClearAction](arkts-arkdata-clouddata-clearaction-e-sys.md)&gt; | Yes | Application information of the data to be cleared and the clearing rule of each application. The key is the application bundle name, and the value is the clearing rule. |
| config | Record&lt;string, [ClearConfig](arkts-arkdata-clouddata-clearconfig-i-sys.md)&gt; | No | Database-level clearing rule for device-cloud synergy. The key is the application package name, and the value is the database clearing rule of the application. Clearing rule priority: table level &gt; database level &gt; application level. If this parameter is not configured, the application-level data clearing rule is used by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let account: string = "test_id";
let appActions: Record<string, cloudData.ClearAction> = {
  'test_bundleName1': cloudData.ClearAction.CLEAR_CLOUD_INFO,
  'test_bundleName2': cloudData.ClearAction.CLEAR_CLOUD_DATA_AND_INFO,
  'test_bundleName3': cloudData.ClearAction.CLEAR_CLOUD_NONE,
};
let config: Record<string, cloudData.ClearConfig> = {
  'test_bundleName': {
    dbInfo: {
      'test_storeName': {
        action: cloudData.ClearAction.CLEAR_CLOUD_INFO,
        tableInfo: {
          'test_tableName1': cloudData.ClearAction.CLEAR_CLOUD_INFO,
          'test_tableName2': cloudData.ClearAction.CLEAR_CLOUD_DATA_AND_INFO,
        }
      }
    }
  }
};
try {
  cloudData.Config.clear(account, appActions, config).then(() => {
    console.info('Succeeded in clearing cloud data');
  }).catch((err: BusinessError) => {
    console.error(`Failed to clear cloud data. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## cloudSync

```TypeScript
static cloudSync(
      bundleName: string,
      storeId: string,
      mode: relationalStore.SyncMode,
      progress: Callback<relationalStore.ProgressDetails>
    ): Promise<void>
```

Synchronizes data of a specified application on the device to the cloud. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static cloudSync(      bundleName: string,      storeId: string,      mode: relationalStore.SyncMode,      progress: Callback<relationalStore.ProgressDetails>    ): Promise<void>--><!--Device-Config-static cloudSync(      bundleName: string,      storeId: string,      mode: relationalStore.SyncMode,      progress: Callback<relationalStore.ProgressDetails>    ): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application to sync. |
| storeId | string | Yes | Name of the database to sync. |
| mode | [relationalStore.SyncMode](arkts-arkdata-relationalstore-syncmode-e.md) | Yes | Device-cloud sync mode. |
| progress | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[relationalStore.ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md)&gt; | Yes | Callback used to return the sync progress. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Empty conditions; <br>2. Missing GROUP BY clause. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { relationalStore } from '@kit.ArkData';

try {
  cloudData.Config.cloudSync("bundleName", "storeId", relationalStore.SyncMode.SYNC_MODE_TIME_FIRST, (progress) => {
    console.info('Succeeded in getting progress details.');
  }).then(() => {
    console.info('Succeeded in syncing cloud data.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to sync cloud data. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to sync cloud data. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## cloudSyncEx

```TypeScript
static cloudSyncEx(
        bundleInfo: BundleInfo,
        config: relationalStore.CloudSyncConfig,
        progress: Callback<relationalStore.ProgressDetails>
    ): Promise<void>
```

Synchronizes data of a specified application between the device and cloud based on the cloud sync configuration. When **downloadOnly** in **CloudSyncConfig** is set to **true**, only the data on the cloud is synchronized to the device. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

**Model restriction:** This API can be used only in the stage model.

<!--Device-Config-static cloudSyncEx(        bundleInfo: BundleInfo,        config: relationalStore.CloudSyncConfig,        progress: Callback<relationalStore.ProgressDetails>    ): Promise<void>--><!--Device-Config-static cloudSyncEx(        bundleInfo: BundleInfo,        config: relationalStore.CloudSyncConfig,        progress: Callback<relationalStore.ProgressDetails>    ): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleInfo | [BundleInfo](arkts-arkdata-clouddata-bundleinfo-i-sys.md) | Yes | Application bundle information configuration, which is a **BundleInfo** instance. |
| config | [relationalStore.CloudSyncConfig](arkts-arkdata-relationalstore-cloudsyncconfig-i.md) | Yes | Cloud sync configuration. |
| progress | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[relationalStore.ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md)&gt; | Yes | Callback used to return the **ProgressDetails** instance. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Empty conditions. |

<!--Del-->
**Examples**

```TypeScript
import { relationalStore } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleInfo: cloudData.BundleInfo = {
  bundleName: 'com.example.myapplication',
  // Other BundleInfo fields
};

let config: relationalStore.CloudSyncConfig = {
  mode: relationalStore.SyncMode.SYNC_MODE_TIME_FIRST,
  enablePredicate: true
};

try {
  cloudData.Config.cloudSyncEx(bundleInfo, config, (progressDetails: relationalStore.ProgressDetails) => {
    console.info(`Cloud sync progress: ${progressDetails.schedule}, code: ${progressDetails.code}`);
  }).then(() => {
    console.info('Succeeded in cloud sync');
  }).catch((err: BusinessError) => {
    console.error(`Failed to cloud sync. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## disableCloud

```TypeScript
static disableCloud(accountId: string, callback: AsyncCallback<void>): void
```

Disables device-cloud synergy. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static disableCloud(accountId: string, callback: AsyncCallback<void>): void--><!--Device-Config-static disableCloud(accountId: string, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | string | Yes | ID of the logged-in cloud account. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;         3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let account: string = "test_id";
try {
  cloudData.Config.disableCloud(account, (err: BusinessError) => {
    if (err === undefined) {
      console.info('Succeeded in disabling cloud');
    } else {
      console.error(`Failed to disableCloud. Code: ${err.code}, message: ${err.message}`);
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## disableCloud

```TypeScript
static disableCloud(accountId: string): Promise<void>
```

Disables device-cloud synergy. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static disableCloud(accountId: string): Promise<void>--><!--Device-Config-static disableCloud(accountId: string): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | string | Yes | ID of the logged-in cloud account. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;         3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let account: string = "test_id";
try {
  cloudData.Config.disableCloud(account).then(() => {
    console.info('Succeeded in disabling cloud');
  }).catch((err: BusinessError) => {
    console.error(`Failed to disableCloud. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## enableCloud

```TypeScript
static enableCloud(
      accountId: string,
      switches: Record<string, boolean>,
      callback: AsyncCallback<void>
    ): void
```

Enables device-cloud synergy. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static enableCloud(      accountId: string,      switches: Record<string, boolean>,      callback: AsyncCallback<void>    ): void--><!--Device-Config-static enableCloud(      accountId: string,      switches: Record<string, boolean>,      callback: AsyncCallback<void>    ): void-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | string | Yes | ID of the logged-in cloud account. |
| switches | Record&lt;string, boolean&gt; | Yes | Device-cloud synergy switch information of each application. The key is the bundle name of the application, and the value is the switch status of the application. The value **true** means to enable the device-cloud switch of the application, and **false** means to disable it.<br>**Since:** 11 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;         3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let account: string = "test_id";
let switches: Record<string, boolean> = { 'test_bundleName1': true, 'test_bundleName2': false };
try {
  cloudData.Config.enableCloud(account, switches, (err: BusinessError) => {
    if (err === undefined) {
      console.info('Succeeded in enabling cloud');
    } else {
      console.error(`Failed to enable.Code: ${err.code}, message: ${err.message}`);
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## enableCloud

```TypeScript
static enableCloud(accountId: string, switches: Record<string, boolean>): Promise<void>
```

Enables device-cloud synergy. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static enableCloud(accountId: string, switches: Record<string, boolean>): Promise<void>--><!--Device-Config-static enableCloud(accountId: string, switches: Record<string, boolean>): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | string | Yes | ID of the logged-in cloud account. |
| switches | Record&lt;string, boolean&gt; | Yes | Device-cloud synergy settings for applications. The value **true** means to enable device-cloud synergy; the value **false** means the opposite.<br>**Since:** 11 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types;         3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let account: string = "test_id";
let switches: Record<string, boolean> = { 'test_bundleName1': true, 'test_bundleName2': false };
try {
  cloudData.Config.enableCloud(account, switches).then(() => {
    console.info('Succeeded in enabling cloud');
  }).catch((err: BusinessError) => {
    console.error(`Failed to enable.Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## notifyDataChange

```TypeScript
static notifyDataChange(extInfo: ExtraData, userId?: number): Promise<void>
```

Notifies the data changes in the cloud. This API uses a promise to return the result. You can specify the database and tables with data changes in the **extraData** field in **extInfo**, and specify the user ID.

**Since:** 11

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static notifyDataChange(extInfo: ExtraData, userId?: int): Promise<void>--><!--Device-Config-static notifyDataChange(extInfo: ExtraData, userId?: int): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| extInfo | [ExtraData](arkts-arkdata-clouddata-extradata-i-sys.md) | Yes | Transparently transmitted data, including information about the application that has data changes. |
| userId | number | No | User ID. This parameter is optional. The default value is the current user ID. If this parameter is specified, the value must be an existing user ID in the system. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;         3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let eventId: string = "cloud_data_change";
let extraData: string = '{"data":"{"accountId":"aaa","bundleName":"com.bbb.xxx","containerName":"alias", "databaseScopes": ["private", "shared"],"recordTypes":"["xxx","yyy","zzz"]"}"}';
let userId: number = 100;
try {
  cloudData.Config.notifyDataChange({
    eventId: eventId, extraData: extraData
  }, userId).then(() => {
    console.info('Succeeded in notifying the change of data');
  }).catch((err: BusinessError) => {
    console.error(`Failed to notify the change of data. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## notifyDataChange

```TypeScript
static notifyDataChange(extInfo: ExtraData, callback: AsyncCallback<void>): void
```

Notifies the data changes in the cloud with the specified information, such as the database and table names (specified by the **extraData** field in **extInfo**). This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static notifyDataChange(extInfo: ExtraData, callback: AsyncCallback<void>): void--><!--Device-Config-static notifyDataChange(extInfo: ExtraData, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| extInfo | [ExtraData](arkts-arkdata-clouddata-extradata-i-sys.md) | Yes | Transparently transmitted data, including information about the application that has data changes. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;         3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let eventId: string = "cloud_data_change";
let extraData: string = '{"data":"{"accountId":"aaa","bundleName":"com.bbb.xxx","containerName":"alias", "databaseScopes": ["private", "shared"],"recordTypes":"["xxx","yyy","zzz"]"}"}';
try {
  cloudData.Config.notifyDataChange({
    eventId: eventId, extraData: extraData
  }, (err: BusinessError) => {
    if (err === undefined) {
      console.info('Succeeded in notifying the change of data');
    } else {
      console.error(`Failed to notify the change of data. Code: ${err.code}, message: ${err.message}`);
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## notifyDataChange

```TypeScript
static notifyDataChange(extInfo: ExtraData, userId: number, callback: AsyncCallback<void>): void
```

Notifies the data changes of a user in the cloud. This API uses an asynchronous callback to return the result. You can also specify the database and tables with data changes in the **extraData** field in **extInfo**, and specify the user ID.

**Since:** 11

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static notifyDataChange(extInfo: ExtraData, userId: int, callback: AsyncCallback<void>): void--><!--Device-Config-static notifyDataChange(extInfo: ExtraData, userId: int, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| extInfo | [ExtraData](arkts-arkdata-clouddata-extradata-i-sys.md) | Yes | Transparently transmitted data, including information about the application that has data changes. |
| userId | number | Yes | User account ID, which refers to the existing user account ID in the system. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;         3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let eventId: string = "cloud_data_change";
let extraData: string = '{"data":"{"accountId":"aaa","bundleName":"com.bbb.xxx","containerName":"alias", "databaseScopes": ["private", "shared"],"recordTypes":"["xxx","yyy","zzz"]"}"}';
let userId: number = 100;
try {
  cloudData.Config.notifyDataChange({
    eventId: eventId, extraData: extraData
  }, userId, (err: BusinessError) => {
    if (err === undefined) {
      console.info('Succeeded in notifying the change of data');
    } else {
      console.error(`Failed to notify the change of data. Code: ${err.code}, message: ${err.message}`);
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## notifyDataChange

```TypeScript
static notifyDataChange(accountId: string, bundleName: string): Promise<void>
```

Notifies the data changes in the cloud. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static notifyDataChange(accountId: string, bundleName: string): Promise<void>--><!--Device-Config-static notifyDataChange(accountId: string, bundleName: string): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | string | Yes | ID of the logged-in cloud account. |
| bundleName | string | Yes | Bundle name of the application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;         3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let account: string = "test_id";
let bundleName: string = "test_bundleName";
try {
  cloudData.Config.notifyDataChange(account, bundleName).then(() => {
    console.info('Succeeded in notifying the change of data');
  }).catch((err: BusinessError) => {
    console.error(`Failed to notify the change of data. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## notifyDataChange

```TypeScript
static notifyDataChange(accountId: string, bundleName: string, callback: AsyncCallback<void>): void
```

Notifies the data changes in the cloud. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static notifyDataChange(accountId: string, bundleName: string, callback: AsyncCallback<void>): void--><!--Device-Config-static notifyDataChange(accountId: string, bundleName: string, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | string | Yes | ID of the logged-in cloud account. |
| bundleName | string | Yes | Bundle name of the application. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the data changes in the cloud are successfully notified, the value of **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;         3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let account: string = "test_id";
let bundleName: string = "test_bundleName";
try {
  cloudData.Config.notifyDataChange(account, bundleName, (err: BusinessError) => {
    if (err === undefined) {
      console.info('Succeeded in notifying the change of data');
    } else {
      console.error(`Failed to notify the change of data. Code: ${err.code}, message: ${err.message}`);
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## offSyncInfoChanged

```TypeScript
static offSyncInfoChanged(
        bundleInfos: Array<BundleInfo>,
        progress?: Callback<Record<string, Record<string, SyncInfo>>>
    ): void
```

Unsubscribes from application sync information changes. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

**Model restriction:** This API can be used only in the stage model.

<!--Device-Config-static offSyncInfoChanged(        bundleInfos: Array<BundleInfo>,        progress?: Callback<Record<string, Record<string, SyncInfo>>>    ): void--><!--Device-Config-static offSyncInfoChanged(        bundleInfos: Array<BundleInfo>,        progress?: Callback<Record<string, Record<string, SyncInfo>>>    ): void-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleInfos | Array&lt;[BundleInfo](arkts-arkdata-clouddata-bundleinfo-i-sys.md)&gt; | Yes | Array of application information to be unsubscribed from. Value range: The array length is [1, 30]. If the array length is out of range, error code 14800001 is returned. The storeId of the application information during unsubscription must be the same as that during subscription. |
| progress | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Record&lt;string, Record&lt;string, [SyncInfo](arkts-arkdata-clouddata-syncinfo-i-sys.md)&gt;&gt;&gt; | No | Callback used to return the result. If this parameter is passed, the specified callback is unsubscribed. If this parameter is not passed, all callbacks of the application are unsubscribed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. bundlename is null; <br>2. the number of bundleInfos exceeds the upper limit or the number is 0. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const bundleInfos: Array<cloudData.BundleInfo> = [
  { bundleName: "bundleName1", storeId: "storeId1" },
  { bundleName: "bundleName2" }
];

const progressCallback = (result: Record<string, Record<string, cloudData.SyncInfo>>) => {
  console.info(`Sync info changed. Result is ${JSON.stringify(result)}`);
};

// Subscribe to sync information changes.
try {
  cloudData.Config.onSyncInfoChanged(bundleInfos, progressCallback);
} catch(err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

// Unsubscribe from a specified callback.
try {
  cloudData.Config.offSyncInfoChanged(bundleInfos, progressCallback);
} catch(err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

// Unsubscribe from all callbacks.
try {
  cloudData.Config.offSyncInfoChanged(bundleInfos);
} catch(err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## onSyncInfoChanged

```TypeScript
static onSyncInfoChanged(
        bundleInfos: Array<BundleInfo>,
        progress: Callback<Record<string, Record<string, SyncInfo>>>
    ): void
```

Subscribes to application sync information changes. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

**Model restriction:** This API can be used only in the stage model.

<!--Device-Config-static onSyncInfoChanged(        bundleInfos: Array<BundleInfo>,        progress: Callback<Record<string, Record<string, SyncInfo>>>    ): void--><!--Device-Config-static onSyncInfoChanged(        bundleInfos: Array<BundleInfo>,        progress: Callback<Record<string, Record<string, SyncInfo>>>    ): void-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleInfos | Array&lt;[BundleInfo](arkts-arkdata-clouddata-bundleinfo-i-sys.md)&gt; | Yes | Array of application information to be subscribed to. Value range: The array length is [1, 30]. If the array length is out of range, error code 14800001 is returned. |
| progress | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Record&lt;string, Record&lt;string, [SyncInfo](arkts-arkdata-clouddata-syncinfo-i-sys.md)&gt;&gt;&gt; | Yes | Callback used to return the application bundle name and the sync result set of the database. The key of the outer record is the application bundle name, and the key of the inner record is the database name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. bundlename is null; <br>2. the number of bundleInfos exceeds the upper limit or the number is 0. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const bundleInfos: Array<cloudData.BundleInfo> = [
  { bundleName: "bundleName1", storeId: "storeId1" },
  { bundleName: "bundleName2" }
];

try {
  cloudData.Config.onSyncInfoChanged(bundleInfos, (result) => {
    console.info(`Sync info changed. Result is ${JSON.stringify(result)}`);
  });
} catch(err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## queryLastSyncInfo

```TypeScript
static queryLastSyncInfo(
        accountId: string,
        bundleName: string,
        storeId?: string
    ): Promise<Record<string, SyncInfo>>
```

Queries information about the last device-cloud sync. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static queryLastSyncInfo(        accountId: string,        bundleName: string,        storeId?: string    ): Promise<Record<string, SyncInfo>>--><!--Device-Config-static queryLastSyncInfo(        accountId: string,        bundleName: string,        storeId?: string    ): Promise<Record<string, SyncInfo>>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | string | Yes | ID of the logged-in cloud account. |
| bundleName | string | Yes | Bundle name of the application. |
| storeId | string | No | Name of the RDB store. The default value is an empty string. If the default value is used, this API queries the last device-cloud sync information of all databases of this application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Record&lt;string, [SyncInfo](arkts-arkdata-clouddata-syncinfo-i-sys.md)&gt;&gt; | Result set with database names as keys and the last device-cloud sync information as values. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;         3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const accountId: string = "accountId";
const bundleName: string = "bundleName";
const storeId: string = "storeId";
try {
  cloudData.Config.queryLastSyncInfo(accountId, bundleName, storeId).then((result) => {
    console.info(`Succeeded in querying last syncinfo. Info is ${JSON.stringify(result)}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to query last syncinfo. Error code is ${err.code}, message is ${err.message}`);
  });
} catch(err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## queryStatistics

```TypeScript
static queryStatistics(
        accountId: string,
        bundleName: string,
        storeId?: string
    ): Promise<Record<string, Array<StatisticInfo>>>
```

Queries device-cloud data statistics, which include the data not synced, data synced and consistent, and data synced but inconsistent between the device and the cloud. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static queryStatistics(        accountId: string,        bundleName: string,        storeId?: string    ): Promise<Record<string, Array<StatisticInfo>>>--><!--Device-Config-static queryStatistics(        accountId: string,        bundleName: string,        storeId?: string    ): Promise<Record<string, Array<StatisticInfo>>>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | string | Yes | ID of the logged-in cloud account. |
| bundleName | string | Yes | Bundle name of the application. |
| storeId | string | No | Name of the RDB store. If this parameter is not specified, all local databases of this application are queried by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Record&lt;string, Array&lt;[StatisticInfo](arkts-arkdata-clouddata-statisticinfo-i-sys.md)&gt;&gt;&gt; | Promise used to return the result set where the table name is the key and the statistics array is the value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;         3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const accountId: string = "accountId";
const bundleName: string = "bundleName";
const storeId: string = "storeId";

cloudData.Config.queryStatistics(accountId, bundleName, storeId).then((result) => {
  console.info(`Succeeded in querying statistics. Info is ${JSON.stringify(result)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to query statistics. Error code is ${err.code}, message is ${err.message}`);
});
```

<!--DelEnd-->

## setGlobalCloudStrategy

```TypeScript
static setGlobalCloudStrategy(strategy: StrategyType, param?: Array<commonType.ValueType>): Promise<void>
```

Sets a global device-cloud sync strategy. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static setGlobalCloudStrategy(strategy: StrategyType, param?: Array<commonType.ValueType>): Promise<void>--><!--Device-Config-static setGlobalCloudStrategy(strategy: StrategyType, param?: Array<commonType.ValueType>): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strategy | [StrategyType](arkts-arkdata-clouddata-strategytype-e.md) | Yes | Type of the strategy to set. |
| param | Array&lt;[commonType.ValueType](arkts-arkdata-commontype-valuetype-t.md)&gt; | No | Strategy parameters to set. If this parameter is not specified, the strategy configuration is deleted by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;         3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

cloudData.Config.setGlobalCloudStrategy(cloudData.StrategyType.NETWORK, [cloudData.NetWorkStrategy.WIFI]).then(() => {
  console.info('Succeeded in setting the global cloud strategy');
}).catch((err: BusinessError) => {
  console.error(`Failed to set global cloud strategy. Code: ${err.code}, message: ${err.message}`);
});
```

<!--DelEnd-->

## stopCloudSync

```TypeScript
static stopCloudSync(bundleInfos: Array<BundleInfo>): Promise<void>
```

Stops data syncing with the cloud. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CLOUDDATA_CONFIG

**Model restriction:** This API can be used only in the stage model.

<!--Device-Config-static stopCloudSync(bundleInfos: Array<BundleInfo>): Promise<void>--><!--Device-Config-static stopCloudSync(bundleInfos: Array<BundleInfo>): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleInfos | Array&lt;[BundleInfo](arkts-arkdata-clouddata-bundleinfo-i-sys.md)&gt; | Yes | Array of application bundle information configurations. Value range: The array length is [1, 30]. If the array length is out of range, error code 14800001 is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. bundlename is null; <br>2. the number of bundleInfos exceeds the upper limit or the number is 0. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundleInfos: Array<cloudData.BundleInfo> = [
  { bundleName: 'com.example.myapplication1' },
  { bundleName: 'com.example.myapplication2' }
];

try {
  cloudData.Config.stopCloudSync(bundleInfos).then(() => {
    console.info('Succeeded in stopping cloud sync');
  }).catch((err: BusinessError) => {
    console.error(`Failed to stop cloud sync. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->
