# sharing(Device-Cloud Service)

Provides APIs for device-cloud data sharing, including sharing or unsharing data, exiting a share, changing the privilege on the shared data, querying participants, confirming an invitation, changing the invitation confirmation state, and querying the shared resource.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [allocResourceAndShare](arkts-arkdata-sharing-allocresourceandshare-f-sys.md) | Allocates a shared resource ID based on the data that matches the specified predicates. This API uses a promise to return the result set of the data to share, which also includes the column names if they are specified. |
| [allocResourceAndShare](arkts-arkdata-sharing-allocresourceandshare-f-sys.md) | Allocates a shared resource ID based on the data that matches the specified predicates. This API uses an asynchronous callback to return the result. |
| [allocResourceAndShare](arkts-arkdata-sharing-allocresourceandshare-f-sys.md) | Allocates a shared resource ID based on the data that matches the specified predicates. This API uses an asynchronous callback to return the result set of the data to share, which includes the shared resource ID and column names. |
| [share](arkts-arkdata-sharing-share-f-sys.md) | Shares data based on the specified shared resource ID and participants. This API uses an asynchronous callback to return the result. |
| [share](arkts-arkdata-sharing-share-f-sys.md) | Shares data based on the specified shared resource ID and participants. This API uses a promise to return the result. |
| [unshare](arkts-arkdata-sharing-unshare-f-sys.md) | Unshares data based on the specified shared resource ID and participants. This API uses an asynchronous callback to return the result. |
| [unshare](arkts-arkdata-sharing-unshare-f-sys.md) | Unshares data based on the specified shared resource ID and participants. This API uses a promise to return the result. |
| [exit](arkts-arkdata-sharing-exit-f-sys.md) | Exits the share of the specified shared resource. This API uses an asynchronous callback to return the result. |
| [exit](arkts-arkdata-sharing-exit-f-sys.md) | Exits the share of the specified shared resource. This API uses a promise to return the result. |
| [changePrivilege](arkts-arkdata-sharing-changeprivilege-f-sys.md) | Changes the privilege on the shared data. This API uses an asynchronous callback to return the result. |
| [changePrivilege](arkts-arkdata-sharing-changeprivilege-f-sys.md) | Changes the privilege on the shared data. This API uses a promise to return the result. |
| [queryParticipants](arkts-arkdata-sharing-queryparticipants-f-sys.md) | Queries the participants of the specified shared data. This API uses an asynchronous callback to return the result. |
| [queryParticipants](arkts-arkdata-sharing-queryparticipants-f-sys.md) | Queries the participants of the specified shared data. This API uses a promise to return the result. |
| [queryParticipantsByInvitation](arkts-arkdata-sharing-queryparticipantsbyinvitation-f-sys.md) | Queries the participants based on the sharing invitation code. This API uses an asynchronous callback to return the result. |
| [queryParticipantsByInvitation](arkts-arkdata-sharing-queryparticipantsbyinvitation-f-sys.md) | Queries the participants based on the sharing invitation code. This API uses a promise to return the result. |
| [confirmInvitation](arkts-arkdata-sharing-confirminvitation-f-sys.md) | Confirms the invitation based on the sharing invitation code and obtains the shared resource ID. This API uses an asynchronous callback to return the result. |
| [confirmInvitation](arkts-arkdata-sharing-confirminvitation-f-sys.md) | Confirms the invitation based on the sharing invitation code and obtains the shared resource ID. This API uses a promise to return the result. |
| [changeConfirmation](arkts-arkdata-sharing-changeconfirmation-f-sys.md) | Changes the invitation confirmation state based on the shared resource ID. This API uses an asynchronous callback to return the result. |
| [changeConfirmation](arkts-arkdata-sharing-changeconfirmation-f-sys.md) | Changes the invitation confirmation state based on the shared resource ID. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [Result](arkts-arkdata-sharing-result-i-sys.md) | Represents the device-cloud sharing result. |
| [Privilege](arkts-arkdata-sharing-privilege-i-sys.md) | Defines the privilege (permissions) on the shared data. |
| [Participant](arkts-arkdata-sharing-participant-i-sys.md) | Represents information about a participant of device-cloud sharing. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [Role](arkts-arkdata-sharing-role-e-sys.md) | Enumerates the roles of the participants in a device-cloud share. |
| [State](arkts-arkdata-sharing-state-e-sys.md) | Enumerates the device-cloud sharing states. |
| [SharingCode](arkts-arkdata-sharing-sharingcode-e-sys.md) | Enumerates the error codes for device-cloud sharing. |
<!--DelEnd-->
