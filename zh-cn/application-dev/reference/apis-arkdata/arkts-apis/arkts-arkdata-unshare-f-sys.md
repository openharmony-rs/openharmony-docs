# unshare（系统接口）

## unshare

```TypeScript
function unshare(
      sharingResource: string,
      participants: Array<Participant>,
      callback: AsyncCallback<Result<Array<Result<Participant>>>>
    ): void
```

根据指定的共享资源标识和共享参与者发起共享邀请，使用callback异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sharingResource | string | 是 | 端云共享数据的资源标识。 |
| participants | Array&lt;Participant&gt; | 是 | 端云共享的参与者。 |
| callback | AsyncCallback&lt;Result&lt;Array&lt;Result&lt;Participant&gt;&gt;&gt;&gt; | 是 | 回调函数。返回端云共享的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed,application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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
})
cloudData.sharing.unshare('sharing_resource_test', participants, ((err: BusinessError, result) => {
  if (err) {
    console.error(`unshare failed, code is ${err.code},message is ${err.message}`);
    return;
  }
  console.info(`unshare succeeded, result: ${result}`);
}))

```


## unshare

```TypeScript
function unshare(
      sharingResource: string,
      participants: Array<Participant>
    ): Promise<Result<Array<Result<Participant>>>>
```

根据指定的共享资源标识和共享参与者发起共享邀请，使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sharingResource | string | 是 | 端云共享数据的资源标识。 |
| participants | Array&lt;Participant&gt; | 是 | 端云共享的参与者。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;Array&lt;Result&lt;Participant&gt;&gt;&gt;&gt; | Promise对象，返回端云共享的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed,application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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
})
cloudData.sharing.unshare('sharing_resource_test', participants).then((result) => {
  console.info(`unshare succeeded, result: ${result}`);
}).catch((err: BusinessError) => {
  console.error(`unshare failed, code is ${err.code},message is ${err.message}`);
})

```

