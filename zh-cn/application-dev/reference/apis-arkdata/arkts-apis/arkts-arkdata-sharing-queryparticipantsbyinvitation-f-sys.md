# queryParticipantsByInvitation（系统接口）

## queryParticipantsByInvitation

```TypeScript
function queryParticipantsByInvitation(
      invitationCode: string,
      callback: AsyncCallback<Result<Array<Participant>>>
    ): void
```

根据指定的共享邀请码查询当前共享的参与者，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sharing-function queryParticipantsByInvitation(      invitationCode: string,      callback: AsyncCallback<Result<Array<Participant>>>    ): void--><!--Device-sharing-function queryParticipantsByInvitation(      invitationCode: string,      callback: AsyncCallback<Result<Array<Participant>>>    ): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| invitationCode | string | 是 | 端云共享的邀请码。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Result&lt;Array&lt;[Participant](arkts-arkdata-sharing-participant-i-sys.md)&gt;&gt;&gt; | 是 | 回调函数。返回查找共享参与者的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

cloudData.sharing.queryParticipantsByInvitation('sharing_invitation_code_test', ((err: BusinessError|null, result) => {
  if (err) {
    console.error(`query participants by invitation failed, code is ${err.code},message is ${err.message}`);
    return;
  }
  console.info(`query participants by invitation succeeded, result: ${result}`);
}))
```


## queryParticipantsByInvitation

```TypeScript
function queryParticipantsByInvitation(invitationCode: string): Promise<Result<Array<Participant>>>
```

根据指定的共享邀请码查询当前共享的参与者，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sharing-function queryParticipantsByInvitation(invitationCode: string): Promise<Result<Array<Participant>>>--><!--Device-sharing-function queryParticipantsByInvitation(invitationCode: string): Promise<Result<Array<Participant>>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| invitationCode | string | 是 | 端云共享的邀请码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;Array&lt;[Participant](arkts-arkdata-sharing-participant-i-sys.md)&gt;&gt;&gt; | Promise对象，返回查找共享参与者的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

cloudData.sharing.queryParticipantsByInvitation('sharing_invitation_code_test').then((result) => {
  console.info(`query participants by invitation succeeded, result: ${result}`);
}).catch((err) => {
  console.error(`query participants by invitation failed, code is ${err.code},message is ${err.message}`);
})
```

