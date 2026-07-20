# sharing

提供端云共享的方法，包括发起共享、取消共享、退出共享、更改共享数据权限、查找共享参与者、确认邀请、更改已确认的邀请、查找共享资源。

**起始版本：** 11

<!--Device-cloudData-export namespace sharing--><!--Device-cloudData-export namespace sharing-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [allocResourceAndShare](arkts-arkdata-sharing-allocresourceandshare-f-sys.md#allocresourceandshare) | 根据谓词条件匹配的数据申请共享资源标识并发起共享，返回已共享资源的结果集。如果指定了列字段，则返回的结果集中同时包含对应列的字段值，使用Promise异步回调。 |
| [allocResourceAndShare](arkts-arkdata-sharing-allocresourceandshare-f-sys.md#allocresourceandshare-1) | 根据谓词条件匹配的数据申请共享资源标识并发起共享，返回已共享资源的结果集，使用callback异步回调。 |
| [allocResourceAndShare](arkts-arkdata-sharing-allocresourceandshare-f-sys.md#allocresourceandshare-2) | 根据谓词条件匹配的数据申请共享资源标识并发起共享，返回已共享资源的结果集并根据指定的列字段，返回的结果集中同时包含对应列的字段值，使用callback异步回调。 |
| [share](arkts-arkdata-sharing-share-f-sys.md#share) | 根据指定的共享资源标识和共享参与者发起共享邀请，使用callback异步回调。 |
| [share](arkts-arkdata-sharing-share-f-sys.md#share-1) | 根据指定的共享资源标识和共享参与者发起共享邀请，使用Promise异步回调。 |
| [unshare](arkts-arkdata-sharing-unshare-f-sys.md#unshare) | 根据指定的共享资源标识和共享参与者发起共享邀请，使用callback异步回调。 |
| [unshare](arkts-arkdata-sharing-unshare-f-sys.md#unshare-1) | 根据指定的共享资源标识和共享参与者发起共享邀请，使用Promise异步回调。 |
| [exit](arkts-arkdata-sharing-exit-f-sys.md#exit) | 根据指定的共享资源标识退出共享，使用callback异步回调。 |
| [exit](arkts-arkdata-sharing-exit-f-sys.md#exit-1) | 根据指定的共享资源标识退出共享，使用Promise异步回调。 |
| [changePrivilege](arkts-arkdata-sharing-changeprivilege-f-sys.md#changeprivilege) | 根据指定的共享资源标识更改共享参与者对共享数据的操作权限，使用callback异步回调。 |
| [changePrivilege](arkts-arkdata-sharing-changeprivilege-f-sys.md#changeprivilege-1) | 根据指定的共享资源标识更改共享参与者对共享数据的操作权限，使用Promise异步回调。 |
| [queryParticipants](arkts-arkdata-sharing-queryparticipants-f-sys.md#queryparticipants) | 根据指定的共享资源标识查询当前共享的参与者，使用callback异步回调。 |
| [queryParticipants](arkts-arkdata-sharing-queryparticipants-f-sys.md#queryparticipants-1) | 根据指定的共享资源标识查询当前共享的参与者，使用Promise异步回调。 |
| [queryParticipantsByInvitation](arkts-arkdata-sharing-queryparticipantsbyinvitation-f-sys.md#queryparticipantsbyinvitation) | 根据指定的共享邀请码查询当前共享的参与者，使用callback异步回调。 |
| [queryParticipantsByInvitation](arkts-arkdata-sharing-queryparticipantsbyinvitation-f-sys.md#queryparticipantsbyinvitation-1) | 根据指定的共享邀请码查询当前共享的参与者，使用Promise异步回调。 |
| [confirmInvitation](arkts-arkdata-sharing-confirminvitation-f-sys.md#confirminvitation) | 被邀请者根据共享邀请码确认当前邀请，并获取当前邀请的共享资源标识，使用callback异步回调。 |
| [confirmInvitation](arkts-arkdata-sharing-confirminvitation-f-sys.md#confirminvitation-1) | 被邀请者根据共享邀请码确认当前邀请，并获取当前邀请的共享资源标识，使用Promise异步回调。 |
| [changeConfirmation](arkts-arkdata-sharing-changeconfirmation-f-sys.md#changeconfirmation) | 根据共享资源标识更改共享邀请的状态，使用callback异步回调。 |
| [changeConfirmation](arkts-arkdata-sharing-changeconfirmation-f-sys.md#changeconfirmation-1) | 根据共享资源标识更改共享邀请的状态，使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Result](arkts-arkdata-sharing-result-i-sys.md) | 端云共享结果的返回值。 |
| [Privilege](arkts-arkdata-sharing-privilege-i-sys.md) | 指定的端云共享数据的权限。 |
| [Participant](arkts-arkdata-sharing-participant-i-sys.md) | 端云共享的参与者。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Role](arkts-arkdata-sharing-role-e-sys.md) | 端云共享参与者的角色。 |
| [State](arkts-arkdata-sharing-state-e-sys.md) | 端云共享状态。 |
| [SharingCode](arkts-arkdata-sharing-sharingcode-e-sys.md) | 端云共享错误码。 |
<!--DelEnd-->

