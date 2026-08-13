# confirmInvitation（系统接口）

## confirmInvitation

```TypeScript
function confirmInvitation(invitationCode: string, state: State, callback: AsyncCallback<Result<string>>): void
```

被邀请者根据共享邀请码确认当前邀请，并获取当前邀请的共享资源标识，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sharing-function confirmInvitation(invitationCode: string, state: State, callback: AsyncCallback<Result<string>>): void--><!--Device-sharing-function confirmInvitation(invitationCode: string, state: State, callback: AsyncCallback<Result<string>>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| invitationCode | string | 是 | 端云共享的邀请码。 |
| state | State | 是 | 确认邀请的状态。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Result&lt;string&gt;&gt; | 是 | 回调函数。返回确认邀请的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let shareResource: string;
cloudData.sharing.confirmInvitation('sharing_invitation_code_test', cloudData.sharing.State.STATE_ACCEPTED, ((err: BusinessError|null, result) => {
  if (err) {
    console.error(`confirm invitation failed, code is ${err.code},message is ${err.message}`);
    return;
  }
  console.info(`confirm invitation succeeded, result: ${result}`);
  shareResource = result.value;
}))
```


## confirmInvitation

```TypeScript
function confirmInvitation(invitationCode: string, state: State): Promise<Result<string>>
```

被邀请者根据共享邀请码确认当前邀请，并获取当前邀请的共享资源标识，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sharing-function confirmInvitation(invitationCode: string, state: State): Promise<Result<string>>--><!--Device-sharing-function confirmInvitation(invitationCode: string, state: State): Promise<Result<string>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| invitationCode | string | 是 | 端云共享的邀请码。 |
| state | State | 是 | 确认邀请的状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;string&gt;&gt; | Promise对象，返回确认共享邀请的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let shareResource: string | undefined;
cloudData.sharing.confirmInvitation('sharing_invitation_code_test', cloudData.sharing.State.STATE_ACCEPTED).then((result: cloudData.sharing.Result<string>) => {
  console.info(`confirm invitation succeeded, result: ${result}`);
  shareResource = result.value;
}).catch((err) => {
  console.error(`confirm invitation failed, code is ${err.code},message is ${err.message}`);
})
```

