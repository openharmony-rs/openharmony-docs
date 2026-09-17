# allocResourceAndShare (System API)

## Modules to Import

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## allocResourceAndShare

```TypeScript
function allocResourceAndShare(
      storeId: string,
      predicates: relationalStore.RdbPredicates,
      participants: Array<Participant>,
      columns?: Array<string>
    ): Promise<relationalStore.ResultSet>
```

Allocates a shared resource ID based on the data that matches the specified predicates. This API uses a promise to return the result set of the data to share, which also includes the column names if they are specified.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| storeId | string | Yes | Name of the RDB store. |
| predicates | [relationalStore.RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | Predicates for matching the data to share. |
| participants | Array&lt;[Participant](arkts-arkdata-sharing-participant-i-sys.md)&gt; | Yes | Participants of the share. |
| columns | Array&lt;string&gt; | No | Columns in which the data is located. The default value is undefined, which means column names are not returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[relationalStore.ResultSet](arkts-arkdata-relationalstore-resultset-i.md)&gt; | Promise used to return the result set of the data to share. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { relationalStore } from '@kit.ArkData';

let participants = new Array<cloudData.sharing.Participant>();
participants.push({
  identity: '000000000',
  role: cloudData.sharing.Role.ROLE_INVITER,
  state: cloudData.sharing.State.STATE_UNKNOWN,
  privilege: {
    writable: true,
    readable: true,
    creatable: false,
    deletable: false,
    shareable: false
  },
  attachInfo: ''
});
let sharingResource: string;
let predicates = new relationalStore.RdbPredicates('test_table');
predicates.equalTo('data', 'data_test');
cloudData.sharing.allocResourceAndShare('storeName', predicates, participants, ['uuid', 'data']).then((resultSet) => {
  if (resultSet === undefined || resultSet === null) {
    console.error(`resultSet is null`);
    return;
  }
  try {
    if (!resultSet.goToFirstRow()) {
      console.error(`row error`);
      return;
    }
    const res = resultSet.getString(resultSet.getColumnIndex(relationalStore.Field.SHARING_RESOURCE_FIELD));
    console.info(`sharing resource: ${res}`);
    sharingResource = res;
  } catch (err) {
    console.error(`Failed to get sharing resource: ${err}`);
  } finally {
    resultSet.close();
  }
}).catch((err: BusinessError) => {
  console.error(`alloc resource and share failed, code is ${err.code},message is ${err.message}`);
});
```

```TypeScript
import { relationalStore } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let participants = new Array<cloudData.sharing.Participant>();
participants.push({
  identity: '000000000',
  role: cloudData.sharing.Role.ROLE_INVITER,
  state: cloudData.sharing.State.STATE_UNKNOWN,
  privilege: {
    writable: true,
    readable: true,
    creatable: false,
    deletable: false,
    shareable: false
  },
  attachInfo: ''
});
let sharingResource: string;
let predicates = new relationalStore.RdbPredicates('test_table');
predicates.equalTo('data', 'data_test');
cloudData.sharing.allocResourceAndShare('storeName', predicates, participants, ['uuid', 'data'], (err: BusinessError, resultSet: relationalStore.ResultSet) => {
  if (err) {
    console.error(`alloc resource and share failed, code is ${err.code},message is ${err.message}`);
    return;
  }
  if (resultSet === undefined || resultSet === null) {
    console.error(`resultSet is null`);
    return;
  }
  try {
    if (!resultSet.goToFirstRow()) {
      console.error(`row error`);
      return;
    }
    const res = resultSet.getString(resultSet.getColumnIndex(relationalStore.Field.SHARING_RESOURCE_FIELD));
    console.info(`sharing resource: ${res}`);
    sharingResource = res;
  } catch (err) {
    console.error(`Failed to get sharing resource: ${err}`);
  } finally {
    resultSet.close();
  }
});
```

```TypeScript
import { relationalStore } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let participants = new Array<cloudData.sharing.Participant>();
participants.push({
  identity: '000000000',
  role: cloudData.sharing.Role.ROLE_INVITER,
  state: cloudData.sharing.State.STATE_UNKNOWN,
  privilege: {
    writable: true,
    readable: true,
    creatable: false,
    deletable: false,
    shareable: false
  },
  attachInfo: ''
});
let sharingResource: string;
let predicates = new relationalStore.RdbPredicates('test_table');
predicates.equalTo('data', 'data_test');
cloudData.sharing.allocResourceAndShare('storeName', predicates, participants, (err: BusinessError, resultSet: relationalStore.ResultSet) => {
  if (err) {
    console.error(`alloc resource and share failed, code is ${err.code},message is ${err.message}`);
    return;
  }
  if (resultSet === undefined || resultSet === null) {
    console.error(`resultSet is null`);
    return;
  }
  try {
    if (!resultSet.goToFirstRow()) {
      console.error(`row error`);
      return;
    }
    const res = resultSet.getString(resultSet.getColumnIndex(relationalStore.Field.SHARING_RESOURCE_FIELD));
    console.info(`sharing resource: ${res}`);
    sharingResource = res;
  } catch (err) {
    console.error(`Failed to get sharing resource: ${err}`);
  } finally {
    resultSet.close();
  }
});
```


## allocResourceAndShare

```TypeScript
function allocResourceAndShare(
      storeId: string,
      predicates: relationalStore.RdbPredicates,
      participants: Array<Participant>,
      callback: AsyncCallback<relationalStore.ResultSet>
    ): void
```

Allocates a shared resource ID based on the data that matches the specified predicates. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| storeId | string | Yes | Name of the RDB store. |
| predicates | [relationalStore.RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | Predicates for matching the data to share. |
| participants | Array&lt;[Participant](arkts-arkdata-sharing-participant-i-sys.md)&gt; | Yes | Participants of the share. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[relationalStore.ResultSet](arkts-arkdata-relationalstore-resultset-i.md)&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

**Examples**

See [allocResourceAndShare](#allocresourceandshare)


## allocResourceAndShare

```TypeScript
function allocResourceAndShare(
      storeId: string,
      predicates: relationalStore.RdbPredicates,
      participants: Array<Participant>,
      columns: Array<string>,
      callback: AsyncCallback<relationalStore.ResultSet>
    ): void
```

Allocates a shared resource ID based on the data that matches the specified predicates. This API uses an asynchronous callback to return the result set of the data to share, which includes the shared resource ID and column names.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| storeId | string | Yes | Name of the RDB store. |
| predicates | [relationalStore.RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | Predicates for matching the data to share. |
| participants | Array&lt;[Participant](arkts-arkdata-sharing-participant-i-sys.md)&gt; | Yes | Participants of the share. |
| columns | Array&lt;string&gt; | Yes | Columns in which the data is located. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[relationalStore.ResultSet](arkts-arkdata-relationalstore-resultset-i.md)&gt; | Yes | Callback used to return the result set of the data to share. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

**Examples**

See [allocResourceAndShare](#allocresourceandshare)
