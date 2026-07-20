# Config（系统接口）

提供配置端云协同的方法，包括云同步打开、关闭、清除数据、数据变化通知。

**起始版本：** 10

<!--Device-cloudData-class Config--><!--Device-cloudData-class Config-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudData } from '@kit.ArkData';
```

<a id="batchquerylastsyncinfo"></a>
## batchQueryLastSyncInfo

```TypeScript
static batchQueryLastSyncInfo(
        accountId: string,
        bundleInfos: Array<BundleInfo>
    ): Promise<Record<string, Record<string, SyncInfo>>>
```

批量查询上一次端云同步的信息，使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Config-static batchQueryLastSyncInfo(
        accountId: string,
        bundleInfos: Array<BundleInfo>
    ): Promise<Record<string, Record<string, SyncInfo>>>--><!--Device-Config-static batchQueryLastSyncInfo(
        accountId: string,
        bundleInfos: Array<BundleInfo>
    ): Promise<Record<string, Record<string, SyncInfo>>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 已登录的云账号ID。 |
| bundleInfos | Array&lt;BundleInfo&gt; | 是 | 批量查询的应用信息数组。取值范围：数组长度为[1, 30]，超过该范围返回14800001错误码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;string, Record&lt;string, SyncInfo&gt;&gt;&gt; | Promise对象，返回应用包名以及对应数据库的上一次端云同步信息结果集。外层Record的键为应用包名，内层Record的键为数据库名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed,usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed,application which is not a system application uses system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the device does not support the device-cloud capability. |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. the accountId is empty;2. the bundlename is null; 3. the number of bundleInfos exceeds the upper limit or the number is 0. |

**示例：**

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
} catch(e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="changeappcloudswitch"></a>
## changeAppCloudSwitch

```TypeScript
static changeAppCloudSwitch(
      accountId: string,
      bundleName: string,
      status: boolean,
      callback: AsyncCallback<void>
    ): void
```

修改单个应用端云协同开关，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static changeAppCloudSwitch(
      accountId: string,
      bundleName: string,
      status: boolean,
      callback: AsyncCallback<void>
    ): void--><!--Device-Config-static changeAppCloudSwitch(
      accountId: string,
      bundleName: string,
      status: boolean,
      callback: AsyncCallback<void>
    ): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 已登录的云账号ID。 |
| bundleName | string | 是 | 应用包名。 |
| status | boolean | 是 | 应用的端云协同开关信息。true为打开该应用端云开关，false为关闭该应用端云开关。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当修改单个应用端云协同开关成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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
} catch (e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="changeappcloudswitch-1"></a>
## changeAppCloudSwitch

```TypeScript
static changeAppCloudSwitch(accountId: string, bundleName: string, status: boolean): Promise<void>
```

修改单个应用端云协同开关，使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static changeAppCloudSwitch(accountId: string, bundleName: string, status: boolean): Promise<void>--><!--Device-Config-static changeAppCloudSwitch(accountId: string, bundleName: string, status: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 已登录的云账号ID。 |
| bundleName | string | 是 | 应用包名。 |
| status | boolean | 是 | 应用的端云协同开关信息。true为打开该应用端云开关，false为关闭该应用端云开关。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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
} catch (e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="changeappcloudswitch-2"></a>
## changeAppCloudSwitch

```TypeScript
static changeAppCloudSwitch(
      accountId: string,
      bundleName: string,
      status: boolean,
      config?: SwitchConfig
    ): Promise<void>
```

修改单个应用端云协同开关，使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Config-static changeAppCloudSwitch(
      accountId: string,
      bundleName: string,
      status: boolean,
      config?: SwitchConfig
    ): Promise<void>--><!--Device-Config-static changeAppCloudSwitch(
      accountId: string,
      bundleName: string,
      status: boolean,
      config?: SwitchConfig
    ): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 已登录的云账号ID。 |
| bundleName | string | 是 | 应用包名。 |
| status | boolean | 是 | 应用的端云协同开关信息。true为打开该应用端云开关，false为关闭该应用端云开关。 |
| config | [SwitchConfig](arkts-arkdata-clouddata-switchconfig-i-sys.md) | 否 | 端云协同数据库级开关配置信息。端云协同开关优先级：应用级 > 数据库级 > 表级。当未配置该参数时，默认使用应用级的开关配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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
}
try {
  cloudData.Config.changeAppCloudSwitch(account, bundleName, true, config).then(() => {
    console.info('Succeeded in changing App cloud switch');
  }).catch((err: BusinessError) => {
    console.error(`Failed to change App cloud switch. Code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="clear"></a>
## clear

```TypeScript
static clear(
      accountId: string,
      appActions: Record<string, ClearAction>,
      callback: AsyncCallback<void>
    ): void
```

清除本地下载的云端数据，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static clear(
      accountId: string,
      appActions: Record<string, ClearAction>,
      callback: AsyncCallback<void>
    ): void--><!--Device-Config-static clear(
      accountId: string,
      appActions: Record<string, ClearAction>,
      callback: AsyncCallback<void>
    ): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 已登录的云账号ID。 |
| appActions | Record&lt;string, ClearAction&gt; | 是 | 要清除数据的应用信息及清除规则。<br>**起始版本：** 10 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当清除本地下载的云端数据成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let account: string = "test_id";
type dataType = Record<string, cloudData.ClearAction>
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
} catch (e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="clear-1"></a>
## clear

```TypeScript
static clear(accountId: string, appActions: Record<string, ClearAction>): Promise<void>
```

清除本地下载的云端数据，使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static clear(accountId: string, appActions: Record<string, ClearAction>): Promise<void>--><!--Device-Config-static clear(accountId: string, appActions: Record<string, ClearAction>): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 已登录的云账号ID。 |
| appActions | Record&lt;string, ClearAction&gt; | 是 | 要清除数据的应用信息及清除规则。<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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
} catch (e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="clear-2"></a>
## clear

```TypeScript
static clear(
      accountId: string,
      appActions: Record<string, ClearAction>,
      config?: Record<string, ClearConfig>
    ): Promise<void>
```

清除本地下载的云端数据，使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Config-static clear(
      accountId: string,
      appActions: Record<string, ClearAction>,
      config?: Record<string, ClearConfig>
    ): Promise<void>--><!--Device-Config-static clear(
      accountId: string,
      appActions: Record<string, ClearAction>,
      config?: Record<string, ClearConfig>
    ): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 已登录的云账号ID。 |
| appActions | Record&lt;string, ClearAction&gt; | 是 | 要清除数据的应用信息及清除规则。 |
| config | Record&lt;string, ClearConfig&gt; | 否 | 端云协同数据库级清除配置信息。键为应用包名，值为该应用数据库清除规则。清除规则优先级：表级 > 数据库级 > 应用级。当未配置该参数时，默认使用应用级的数据清除方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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
}
try {
  cloudData.Config.clear(account, appActions, config).then(() => {
    console.info('Succeeded in clearing cloud data');
  }).catch((err: BusinessError) => {
    console.error(`Failed to clear cloud data. Code: ${err.code}, message: ${err.message}`);
  });
} catch (e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="cloudsync"></a>
## cloudSync

```TypeScript
static cloudSync(
      bundleName: string,
      storeId: string,
      mode: relationalStore.SyncMode,
      progress: Callback<relationalStore.ProgressDetails>
    ): Promise<void>
```

对指定应用的数据进行端云同步，使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static cloudSync(
      bundleName: string,
      storeId: string,
      mode: relationalStore.SyncMode,
      progress: Callback<relationalStore.ProgressDetails>
    ): Promise<void>--><!--Device-Config-static cloudSync(
      bundleName: string,
      storeId: string,
      mode: relationalStore.SyncMode,
      progress: Callback<relationalStore.ProgressDetails>
    ): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 待端云同步数据的应用包名。 |
| storeId | string | 是 | 待端云同步的数据库名。 |
| mode | relationalStore.SyncMode | 是 | 端云同步类型。 |
| progress | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;relationalStore.ProgressDetails&gt; | 是 | 同步进度回调。返回ProgressDetails实例对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed,<br>usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed,<br>application which is not a system application uses system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Empty conditions;<br>2. Missing GROUP BY clause. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { relationalStore } from '@kit.ArkData';

try {
  cloudData.Config.cloudSync("bundleName", "storeId", relationalStore.SyncMode.SYNC_MODE_TIME_FIRST, (progress)=>{
    console.info('Succeeded in getting progress details.');
  }).then(() => {
    console.info('Succeeded in syncing cloud data.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to sync cloud data. Code: ${err.code}, message: ${err.message}`);
  });
} catch (e) {
  let error = e as BusinessError;
  console.error(`Failed to sync cloud data. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="cloudsyncex"></a>
## cloudSyncEx

```TypeScript
static cloudSyncEx(
        bundleInfo: BundleInfo,
        config: relationalStore.CloudSyncConfig,
        progress: Callback<relationalStore.ProgressDetails>
    ): Promise<void>
```

对指定应用的数据按照云同步配置信息进行端云同步，当[CloudSyncConfig](docroot://reference/apis-arkdata/js-apis-data-relationalStore-sys.md#cloudsyncconfig)中的downloadOnly为true时，端云同步仅把云侧数据同步到本地，使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Config-static cloudSyncEx(
        bundleInfo: BundleInfo,
        config: relationalStore.CloudSyncConfig,
        progress: Callback<relationalStore.ProgressDetails>
    ): Promise<void>--><!--Device-Config-static cloudSyncEx(
        bundleInfo: BundleInfo,
        config: relationalStore.CloudSyncConfig,
        progress: Callback<relationalStore.ProgressDetails>
    ): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleInfo | [BundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleinfo-i.md) | 是 | 应用包信息配置。BundleInfo的实例对象。 |
| config | relationalStore.CloudSyncConfig | 是 | 云同步配置。 |
| progress | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;relationalStore.ProgressDetails&gt; | 是 | 进度回调函数。返回ProgressDetails实例对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed,<br>usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application is not a system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the device does not support the device-cloud capability. |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Empty conditions. |

**示例：**

```TypeScript
import { relationalStore } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleInfo: cloudData.BundleInfo = {
  bundleName: 'com.example.myapplication',
  // 其他BundleInfo字段...
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
} catch (e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="disablecloud"></a>
## disableCloud

```TypeScript
static disableCloud(accountId: string, callback: AsyncCallback<void>): void
```

关闭端云协同，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static disableCloud(accountId: string, callback: AsyncCallback<void>): void--><!--Device-Config-static disableCloud(accountId: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 已登录的云账号ID。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当关闭端云协同成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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
} catch (e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="disablecloud-1"></a>
## disableCloud

```TypeScript
static disableCloud(accountId: string): Promise<void>
```

关闭端云协同，使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static disableCloud(accountId: string): Promise<void>--><!--Device-Config-static disableCloud(accountId: string): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 已登录的云账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let account: string = "test_id";
try {
  cloudData.Config.disableCloud(account).then(() => {
    console.info('Succeeded in disabling cloud');
  }).catch((err: BusinessError) => {
    console.error(`Failed to disableCloud. Code: ${err.code}, message: ${err.message}`);
  });
} catch (e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="enablecloud"></a>
## enableCloud

```TypeScript
static enableCloud(
      accountId: string,
      switches: Record<string, boolean>,
      callback: AsyncCallback<void>
    ): void
```

打开端云协同开关，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static enableCloud(
      accountId: string,
      switches: Record<string, boolean>,
      callback: AsyncCallback<void>
    ): void--><!--Device-Config-static enableCloud(
      accountId: string,
      switches: Record<string, boolean>,
      callback: AsyncCallback<void>
    ): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 已登录的云账号ID。 |
| switches | Record&lt;string, boolean&gt; | 是 | 各应用的端云协同开关信息。true为打开该应用端云开关，false为关闭该应用端云开关。<br>**起始版本：** 11 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当打开端云协同功能成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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
} catch (e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="enablecloud-1"></a>
## enableCloud

```TypeScript
static enableCloud(accountId: string, switches: Record<string, boolean>): Promise<void>
```

打开端云协同开关，使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static enableCloud(accountId: string, switches: Record<string, boolean>): Promise<void>--><!--Device-Config-static enableCloud(accountId: string, switches: Record<string, boolean>): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 已登录的云账号ID。 |
| switches | Record&lt;string, boolean&gt; | 是 | 各应用的端云协同开关信息。true为打开该应用端云开关，false为关闭该应用端云开关。<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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
} catch (e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="notifydatachange"></a>
## notifyDataChange

```TypeScript
static notifyDataChange(extInfo: ExtraData, userId?: number): Promise<void>
```

通知云端的数据变更，可以通过extInfo中的extraData字段指定变更的数据库名和表名，可通过userId指定用户ID，使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static notifyDataChange(extInfo: ExtraData, userId?: int): Promise<void>--><!--Device-Config-static notifyDataChange(extInfo: ExtraData, userId?: int): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| extInfo | [ExtraData](../../apis-core-file-kit/arkts-apis/arkts-corefile-cloudsyncmanager-extradata-i-sys.md) | 是 | 透传数据，包含通知数据变更后的应用信息。 |
| userId | number | 否 | 表示用户账号ID。此参数是可选的，默认值是当前用户账号ID，如果指定了此参数，则该值必须是系统中现有的用户账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, which is usually returned by <b>VerifyAccessToken</b>. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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
} catch (e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="notifydatachange-1"></a>
## notifyDataChange

```TypeScript
static notifyDataChange(extInfo: ExtraData, callback: AsyncCallback<void>): void
```

通知云端的数据变更，可以通过extInfo中的extraData字段指定变更的数据库名和表名，使用callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static notifyDataChange(extInfo: ExtraData, callback: AsyncCallback<void>): void--><!--Device-Config-static notifyDataChange(extInfo: ExtraData, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| extInfo | [ExtraData](../../apis-core-file-kit/arkts-apis/arkts-corefile-cloudsyncmanager-extradata-i-sys.md) | 是 | 透传数据，包含通知数据变更后的应用信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当数据变更通知成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, which is usually returned by <b>VerifyAccessToken</b>. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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
} catch (e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="notifydatachange-2"></a>
## notifyDataChange

```TypeScript
static notifyDataChange(extInfo: ExtraData, userId: number, callback: AsyncCallback<void>): void
```

通知云端的数据变更，可以通过extInfo中的extraData字段指定变更的数据库名和表名，可通过userId指定用户ID，使用callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static notifyDataChange(extInfo: ExtraData, userId: int, callback: AsyncCallback<void>): void--><!--Device-Config-static notifyDataChange(extInfo: ExtraData, userId: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| extInfo | [ExtraData](../../apis-core-file-kit/arkts-apis/arkts-corefile-cloudsyncmanager-extradata-i-sys.md) | 是 | 透传数据，包含通知数据变更后的应用信息。 |
| userId | number | 是 | 用户ID，对应为系统中现有的用户ID。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当数据变更通知成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, which is usually returned by <b>VerifyAccessToken</b>. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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
} catch (e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="notifydatachange-3"></a>
## notifyDataChange

```TypeScript
static notifyDataChange(accountId: string, bundleName: string): Promise<void>
```

通知云端的数据变更，使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static notifyDataChange(accountId: string, bundleName: string): Promise<void>--><!--Device-Config-static notifyDataChange(accountId: string, bundleName: string): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 已登录的云账号ID。 |
| bundleName | string | 是 | 应用包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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
} catch (e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="notifydatachange-4"></a>
## notifyDataChange

```TypeScript
static notifyDataChange(accountId: string, bundleName: string, callback: AsyncCallback<void>): void
```

通知云端的数据变更，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static notifyDataChange(accountId: string, bundleName: string, callback: AsyncCallback<void>): void--><!--Device-Config-static notifyDataChange(accountId: string, bundleName: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 已登录的云账号ID。 |
| bundleName | string | 是 | 应用包名。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当通知云端的数据变更成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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
} catch (e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="offsyncinfochanged"></a>
## offSyncInfoChanged

```TypeScript
static offSyncInfoChanged(
        bundleInfos: Array<BundleInfo>,
        progress?: Callback<Record<string, Record<string, SyncInfo>>>
    ): void
```

取消订阅应用同步信息变化，使用callback异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Config-static offSyncInfoChanged(
        bundleInfos: Array<BundleInfo>,
        progress?: Callback<Record<string, Record<string, SyncInfo>>>
    ): void--><!--Device-Config-static offSyncInfoChanged(
        bundleInfos: Array<BundleInfo>,
        progress?: Callback<Record<string, Record<string, SyncInfo>>>
    ): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleInfos | Array&lt;BundleInfo&gt; | 是 | 取消订阅的应用信息数组。取值范围：数组长度为[1, 30]，超过该范围返回14800001错误码。取消订阅时应用信息的storeId需要与订阅时保持一致。 |
| progress | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Record&lt;string, Record&lt;string, SyncInfo&gt;&gt;&gt; | 否 | 回调函数。如果传入此参数，则取消订阅指定的回调函数；如果不传此参数，则取消该应用的所有订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed,usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed,application which is not a system application uses system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the device does not support the device-cloud capability. |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. bundlename is null;<br>2. the number of bundleInfos exceeds the upper limit or the number is 0. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const bundleInfos: Array<cloudData.BundleInfo> = [
  { bundleName: "bundleName1", storeId: "storeId1" },
  { bundleName: "bundleName2" }
];

const progressCallback = (result: Record<string, Record<string, cloudData.SyncInfo>>) => {
  console.info(`Sync info changed. Result is ${JSON.stringify(result)}`);
};

// 订阅同步信息变化
try {
  cloudData.Config.onSyncInfoChanged(bundleInfos, progressCallback);
} catch(e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

// 取消订阅指定的回调
try {
  cloudData.Config.offSyncInfoChanged(bundleInfos, progressCallback);
} catch(e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

// 取消所有订阅
try {
  cloudData.Config.offSyncInfoChanged(bundleInfos);
} catch(e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="onsyncinfochanged"></a>
## onSyncInfoChanged

```TypeScript
static onSyncInfoChanged(
        bundleInfos: Array<BundleInfo>,
        progress: Callback<Record<string, Record<string, SyncInfo>>>
    ): void
```

订阅应用同步信息变化，使用callback异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Config-static onSyncInfoChanged(
        bundleInfos: Array<BundleInfo>,
        progress: Callback<Record<string, Record<string, SyncInfo>>>
    ): void--><!--Device-Config-static onSyncInfoChanged(
        bundleInfos: Array<BundleInfo>,
        progress: Callback<Record<string, Record<string, SyncInfo>>>
    ): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleInfos | Array&lt;BundleInfo&gt; | 是 | 订阅的应用信息数组。取值范围：数组长度为[1, 30]，超过该范围返回14800001错误码。 |
| progress | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Record&lt;string, Record&lt;string, SyncInfo&gt;&gt;&gt; | 是 | 回调函数。返回应用包名以及对应数据库的同步信息结果集。外层Record的键为应用包名，内层Record的键为数据库名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed,usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed,application which is not a system application uses system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the device does not support the device-cloud capability. |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. bundlename is null;<br>2. the number of bundleInfos exceeds the upper limit or the number is 0. |

**示例：**

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
} catch(e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="querylastsyncinfo"></a>
## queryLastSyncInfo

```TypeScript
static queryLastSyncInfo(
        accountId: string,
        bundleName: string,
        storeId?: string
    ): Promise<Record<string, SyncInfo>>
```

查询上一次端云同步信息，使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static queryLastSyncInfo(
        accountId: string,
        bundleName: string,
        storeId?: string
    ): Promise<Record<string, SyncInfo>>--><!--Device-Config-static queryLastSyncInfo(
        accountId: string,
        bundleName: string,
        storeId?: string
    ): Promise<Record<string, SyncInfo>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 已登录的云账号ID。 |
| bundleName | string | 是 | 应用包名。 |
| storeId | string | 否 | 数据库名称。默认值为空字符串，此时查询当前应用下所有数据库上一次端云同步信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;string, SyncInfo&gt;&gt; | 返回数据库名以及上一次端云同步的信息结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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
} catch(e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="querystatistics"></a>
## queryStatistics

```TypeScript
static queryStatistics(
        accountId: string,
        bundleName: string,
        storeId?: string
    ): Promise<Record<string, Array<StatisticInfo>>>
```

查询端云统计信息，返回未同步、已同步且端云信息一致和已同步且端云信息不一致的统计信息，使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static queryStatistics(
        accountId: string,
        bundleName: string,
        storeId?: string
    ): Promise<Record<string, Array<StatisticInfo>>>--><!--Device-Config-static queryStatistics(
        accountId: string,
        bundleName: string,
        storeId?: string
    ): Promise<Record<string, Array<StatisticInfo>>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 已登录的云账号ID。 |
| bundleName | string | 是 | 应用包名。 |
| storeId | string | 否 | 数据库名称。默认值为空字符串，此时将查询当前应用所有的本地数据库。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;string, Array&lt;StatisticInfo&gt;&gt;&gt; | 返回以表名为键、统计信息数组为值的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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

<a id="setglobalcloudstrategy"></a>
## setGlobalCloudStrategy

```TypeScript
static setGlobalCloudStrategy(strategy: StrategyType, param?: Array<commonType.ValueType>): Promise<void>
```

设置全局云同步策略，使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

<!--Device-Config-static setGlobalCloudStrategy(strategy: StrategyType, param?: Array<commonType.ValueType>): Promise<void>--><!--Device-Config-static setGlobalCloudStrategy(strategy: StrategyType, param?: Array<commonType.ValueType>): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strategy | [StrategyType](arkts-arkdata-clouddata-strategytype-e.md) | 是 | 配置的策略类型。 |
| param | Array&lt;commonType.ValueType&gt; | 否 | 策略参数。不填写时默认为空，默认取消所有配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

cloudData.Config.setGlobalCloudStrategy(cloudData.StrategyType.NETWORK, [cloudData.NetWorkStrategy.WIFI]).then(() => {
  console.info('Succeeded in setting the global cloud strategy');
}).catch((err: BusinessError) => {
  console.error(`Failed to set global cloud strategy. Code: ${err.code}, message: ${err.message}`);
});

```

<a id="stopcloudsync"></a>
## stopCloudSync

```TypeScript
static stopCloudSync(bundleInfos: Array<BundleInfo>): Promise<void>
```

停止与云端的数据同步，使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDDATA_CONFIG

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Config-static stopCloudSync(bundleInfos: Array<BundleInfo>): Promise<void>--><!--Device-Config-static stopCloudSync(bundleInfos: Array<BundleInfo>): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleInfos | Array&lt;BundleInfo&gt; | 是 | 应用包信息配置数组。取值范围：数组长度为[1, 30]，超过该范围返回14800001错误码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed,<br>usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | if permission verification failed, application which is not a system application uses system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the device does not support the device-cloud capability. |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. bundlename is null;<br>2. the number of bundleInfos exceeds the upper limit or the number is 0. |

**示例：**

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
} catch (e) {
  let error = e as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

