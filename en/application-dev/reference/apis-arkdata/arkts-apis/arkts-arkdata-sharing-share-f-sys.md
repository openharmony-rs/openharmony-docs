# share (System API)

## Modules to Import

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## share

```TypeScript
function share(
      sharingResource: string,
      participants: Array<Participant>,
      callback: AsyncCallback<Result<Array<Result<Participant>>>>
    ): void
```

Shares data based on the specified shared resource ID and participants. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sharingResource | string | Yes | Shared resource ID. |
| participants | Array&lt;[Participant](arkts-arkdata-sharing-participant-i-sys.md)&gt; | Yes | Participants of the share. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&lt;Array&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&lt;[Participant](arkts-arkdata-sharing-participant-i-sys.md)&gt;&gt;&gt;&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

**Examples**

```TypeScript
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
cloudData.sharing.share('sharing_resource_test', participants, (err: BusinessError, result) => {
  if (err) {
    console.error(`share failed, code is ${err.code},message is ${err.message}`);
    return;
  }
  console.info(`share succeeded, result: ${result}`);
});
```


<a id="share-1"></a>

## share

```TypeScript
function share(
      sharingResource: string,
      participants: Array<Participant>
    ): Promise<Result<Array<Result<Participant>>>>
```

Shares data based on the specified shared resource ID and participants. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sharingResource | string | Yes | Shared resource ID. |
| participants | Array&lt;[Participant](arkts-arkdata-sharing-participant-i-sys.md)&gt; | Yes | Participants of the share. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&lt;Array&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&lt;[Participant](arkts-arkdata-sharing-participant-i-sys.md)&gt;&gt;&gt;&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

**Examples**

```TypeScript
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
cloudData.sharing.share('sharing_resource_test', participants).then((result) => {
  console.info(`share success, result: ${result}`);
}).catch((err: BusinessError) => {
  console.error(`share failed, code is ${err.code},message is ${err.message}`);
});
```
