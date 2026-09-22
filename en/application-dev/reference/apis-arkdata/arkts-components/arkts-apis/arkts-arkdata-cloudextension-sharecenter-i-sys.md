# ShareCenter (System API)

```TypeScript
export interface ShareCenter
```

Provides APIs for interacting with the sharedCenter service. You need to inherit this class and implement APIs of this class. The system calls these APIs to initiate, cancel, or exit a device-cloud share.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## changeConfirmation

```TypeScript
changeConfirmation(
      userId: number,
      bundleName: string,
      sharingResource: string,
      state: cloudData.sharing.State
    ): Promise<Result<void>>
```

Changes the confirmation state of a share invitation. This API uses a promise to return the result. The application, shared resource ID, and the new conformation state need to be specified. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. |
| bundleName | string | Yes | Bundle name of the application. |
| sharingResource | string | Yes | Shared resource ID. |
| state | [cloudData.sharing.State](arkts-arkdata-sharing-state-e-sys.md) | Yes | New confirmation state. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&lt;void&gt;&gt; | Promise used to return the result. |

**Examples**

```TypeScript
import { cloudData } from '@kit.ArkData';

class MyShareCenter implements cloudExtension.ShareCenter {
  constructor() {}
  async changeConfirmation(userId: number, bundleName: string, sharingResource: string, state: cloudData.sharing.State):
    Promise<cloudExtension.Result<void>> {
    console.info(`change confirm, bundle: ${bundleName}`);
    // Connect to ShareCenter and obtain the return value of the state change operation.
    // ...
    // Return the result obtained from ShareCenter.
    return {
      code: cloudData.sharing.SharingCode.SUCCESS,
      description: 'change confirm succeeded'
    };
  }
  // ...
}
```

## changePrivilege

```TypeScript
changePrivilege(
      userId: number,
      bundleName: string,
      sharingResource: string,
      participants: Array<cloudData.sharing.Participant>
    ): Promise<Result<Array<Result<cloudData.sharing.Participant>>>>
```

Changes the privilege (operation permissions) on the shared data. This API uses a promise to return the result. The application, shared resource ID, and the participants with new privilege need to be specified.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. |
| bundleName | string | Yes | Bundle name of the application. |
| sharingResource | string | Yes | Shared resource ID. |
| participants | Array&lt;[cloudData.sharing.Participant](arkts-arkdata-sharing-participant-i-sys.md)&gt; | Yes | Participants of the share. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&lt;Array&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&lt;[cloudData.sharing.Participant](arkts-arkdata-sharing-participant-i-sys.md)&gt;&gt;&gt;&gt; | Promise used to return the result. |

**Examples**

```TypeScript
import { cloudData } from '@kit.ArkData';

type Participant = cloudData.sharing.Participant;

class MyShareCenter implements cloudExtension.ShareCenter {
  constructor() {}
  async changePrivilege(userId: number, bundleName: string, sharingResource: string, participants: Array<Participant>):
    Promise<cloudExtension.Result<Array<cloudExtension.Result<Participant>>>> {
    console.info(`change privilege, bundle: ${bundleName}`);
    // Connect to ShareCenter and obtain the return value of the privilege change operation.
    // ...
    // Return the result obtained from ShareCenter.
    let result: Array<cloudExtension.Result<Participant>> = [];
    participants.forEach(() => {
      result.push({
        code: cloudData.sharing.SharingCode.SUCCESS,
        description: 'change privilege succeeded'    
      });
    });
    return {
      code: cloudData.sharing.SharingCode.SUCCESS,
      description: 'change privilege succeeded',
      value: result
    };
  }
  // ...
}
```

## confirmInvitation

```TypeScript
confirmInvitation(
      userId: number,
      bundleName: string,
      invitationCode: string,
      state: cloudData.sharing.State
    ): Promise<Result<string>>
```

Confirms the invitation for a share. This API uses a promise to return the result. The application, invitation code for the share, and the confirmation state need to be specified.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. |
| bundleName | string | Yes | Bundle name of the application. |
| invitationCode | string | Yes | Invitation code for the share. |
| state | [cloudData.sharing.State](arkts-arkdata-sharing-state-e-sys.md) | Yes | Confirmation state of the invitation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&lt;string&gt;&gt; | Promise used to return the shared resource ID. |

**Examples**

```TypeScript
import { cloudData } from '@kit.ArkData';

class MyShareCenter implements cloudExtension.ShareCenter {
  constructor() {}
  async confirmInvitation(userId: number, bundleName: string, invitationCode: string, state: cloudData.sharing.State):
    Promise<cloudExtension.Result<string>> {
    console.info(`confirm invitation, bundle: ${bundleName}`);
    // Connect to ShareCenter and obtain the return value of the invitation confirmation operation.
    // ...
    // Return the result obtained from ShareCenter.
    return {
      code: cloudData.sharing.SharingCode.SUCCESS,
      description: 'confirm invitation succeeded',
      value: 'sharing_resource_test'
    };
  }
  // ...
}
```

## exit

```TypeScript
exit(userId: number, bundleName: string, sharingResource: string): Promise<Result<void>>
```

Exits a device-cloud share. This API uses a promise to return the result. The application and shared resource ID need to be specified.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. |
| bundleName | string | Yes | Bundle name of the application. |
| sharingResource | string | Yes | Shared resource ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&lt;void&gt;&gt; | Promise used to return the result. |

**Examples**

```TypeScript
import { cloudData } from '@kit.ArkData';

class MyShareCenter implements cloudExtension.ShareCenter {
  constructor() {}
  async exit(userId: number, bundleName: string, sharingResource: string):
    Promise<cloudExtension.Result<void>> {
    console.info(`exit share, bundle: ${bundleName}`);
    // Connect to ShareCenter and obtain the return value of the exit operation.
    // ...
    // Return the result obtained from ShareCenter.
    return {
      code: cloudData.sharing.SharingCode.SUCCESS,
      description: 'exit share succeeded'
    };
  }
  // ...
}
```

## queryParticipants

```TypeScript
queryParticipants(
      userId: number,
      bundleName: string,
      sharingResource: string
    ): Promise<Result<Array<cloudData.sharing.Participant>>>
```

Queries the participants of a share. This API uses a promise to return the result. The application and shared resource ID need to be specified.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. |
| bundleName | string | Yes | Bundle name of the application. |
| sharingResource | string | Yes | Shared resource ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&lt;Array&lt;[cloudData.sharing.Participant](arkts-arkdata-sharing-participant-i-sys.md)&gt;&gt;&gt; | Promise used to return the participants obtained. |

**Examples**

```TypeScript
import { cloudData } from '@kit.ArkData';

type Participant = cloudData.sharing.Participant;

class MyShareCenter implements cloudExtension.ShareCenter {
  constructor() {}
  async queryParticipants(userId: number, bundleName: string, sharingResource: string):
    Promise<cloudExtension.Result<Array<Participant>>> {
    console.info(`query participants, bundle: ${bundleName}`);
    // Connect to ShareCenter and obtain the return value of the query operation.
    // ...
    // Return the result obtained from ShareCenter.
    let participants = new Array<cloudData.sharing.Participant>();
    participants.push({
      identity: '000000000',
      role: cloudData.sharing.Role.ROLE_INVITEE,
      state: cloudData.sharing.State.STATE_ACCEPTED,
      privilege: {
        writable: false,
        readable: true,
        creatable: false,
        deletable: false,
        shareable: false
      },
      attachInfo: ''
    });
    participants.push({
      identity: '111111111',
      role: cloudData.sharing.Role.ROLE_INVITEE,
      state: cloudData.sharing.State.STATE_ACCEPTED,
      privilege: {
        writable: false,
        readable: true,
        creatable: false,
        deletable: false,
        shareable: false
      },
      attachInfo: ''
    });
    return {
      code: cloudData.sharing.SharingCode.SUCCESS,
      description: 'query participants succeeded',
      value: participants
    };
  }
  // ...
}
```

## queryParticipantsByInvitation

```TypeScript
queryParticipantsByInvitation(
      userId: number,
      bundleName: string,
      invitationCode: string
    ): Promise<Result<Array<cloudData.sharing.Participant>>>
```

Queries the participants of a share based on the invitation code. This API uses a promise to return the result. The application and the invitation code of the shared data need to be specified.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. |
| bundleName | string | Yes | Bundle name of the application. |
| invitationCode | string | Yes | Invitation code for the share. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&lt;Array&lt;[cloudData.sharing.Participant](arkts-arkdata-sharing-participant-i-sys.md)&gt;&gt;&gt; | Promise used to return the participants obtained. |

**Examples**

```TypeScript
import { cloudData } from '@kit.ArkData';

type Participant = cloudData.sharing.Participant;

class MyShareCenter implements cloudExtension.ShareCenter {
  constructor() {}
  async queryParticipantsByInvitation(userId: number, bundleName: string, invitationCode: string):
    Promise<cloudExtension.Result<Array<Participant>>> {
    console.info(`query participants by invitation, bundle: ${bundleName}`);
    // Connect to ShareCenter and obtain the return value of the query operation.
    // ...
    // Return the result obtained from ShareCenter.
    let participants = new Array<cloudData.sharing.Participant>();
    participants.push({
      identity: '000000000',
      role: cloudData.sharing.Role.ROLE_INVITEE,
      state: cloudData.sharing.State.STATE_ACCEPTED,
      privilege: {
        writable: false,
        readable: true,
        creatable: false,
        deletable: false,
        shareable: false
      },
      attachInfo: ''
    });
    participants.push({
      identity: '111111111',
      role: cloudData.sharing.Role.ROLE_INVITEE,
      state: cloudData.sharing.State.STATE_ACCEPTED,
      privilege: {
        writable: false,
        readable: true,
        creatable: false,
        deletable: false,
        shareable: false
      },
      attachInfo: ''
    });
    return {
      code: cloudData.sharing.SharingCode.SUCCESS,
      description: 'query participants by invitation succeeded',
      value: participants
    };
  }
  // ...
}
```

## share

```TypeScript
share(
      userId: number,
      bundleName: string,
      sharingResource: string,
      participants: Array<cloudData.sharing.Participant>
    ): Promise<Result<Array<Result<cloudData.sharing.Participant>>>>
```

Shares data. This API uses a promise to return the result. The application that initiates the share, shared resource ID, participants of the share need to be specified.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. |
| bundleName | string | Yes | Bundle name of the application. |
| sharingResource | string | Yes | Shared resource ID. |
| participants | Array&lt;[cloudData.sharing.Participant](arkts-arkdata-sharing-participant-i-sys.md)&gt; | Yes | Participants of the share. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&lt;Array&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&lt;[cloudData.sharing.Participant](arkts-arkdata-sharing-participant-i-sys.md)&gt;&gt;&gt;&gt; | Promise used to return the result. |

**Examples**

```TypeScript
import { cloudData } from '@kit.ArkData';

type Participant = cloudData.sharing.Participant;

class MyShareCenter implements cloudExtension.ShareCenter {
  constructor() {}
  async share(userId: number, bundleName: string, sharingResource: string, participants: Array<Participant>):
    Promise<cloudExtension.Result<Array<cloudExtension.Result<Participant>>>> {
    console.info(`share, bundle: ${bundleName}`);
    // Connect to ShareCenter and obtain the return value.
    // ...
    // Return the result obtained from ShareCenter.
    let result: Array<cloudExtension.Result<Participant>> = [];
    participants.forEach(() => {
      result.push({
        code: cloudData.sharing.SharingCode.SUCCESS,
        description: 'share succeeded'    
      });
    });
    return {
      code: cloudData.sharing.SharingCode.SUCCESS,
      description: 'share succeeded',
      value: result
    };
  }
  // ...
}
```

## unshare

```TypeScript
unshare(
      userId: number,
      bundleName: string,
      sharingResource: string,
      participants: Array<cloudData.sharing.Participant>
    ): Promise<Result<Array<Result<cloudData.sharing.Participant>>>>
```

Unshares data. This API uses a promise to return the result. The application, shared resource ID, and participants for the data to unshare need to be specified.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. |
| bundleName | string | Yes | Bundle name of the application. |
| sharingResource | string | Yes | Shared resource ID. |
| participants | Array&lt;[cloudData.sharing.Participant](arkts-arkdata-sharing-participant-i-sys.md)&gt; | Yes | Participants of the share. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&lt;Array&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&lt;[cloudData.sharing.Participant](arkts-arkdata-sharing-participant-i-sys.md)&gt;&gt;&gt;&gt; | Promise used to return the result. |

**Examples**

```TypeScript
import { cloudData } from '@kit.ArkData';

type Participant = cloudData.sharing.Participant;

class MyShareCenter implements cloudExtension.ShareCenter {
  constructor() {}
  async unshare(userId: number, bundleName: string, sharingResource: string, participants: Array<Participant>):
    Promise<cloudExtension.Result<Array<cloudExtension.Result<Participant>>>> {
    console.info(`unshare, bundle: ${bundleName}`);
    // Connect to ShareCenter and obtain the return value of the unshare operation.
    // ...
    // Return the result obtained from ShareCenter.
    let result: Array<cloudExtension.Result<Participant>> = [];
    participants.forEach(() => {
      result.push({
        code: cloudData.sharing.SharingCode.SUCCESS,
        description: 'unshare succeeded'    
      });
    });
    return {
      code: cloudData.sharing.SharingCode.SUCCESS,
      description: 'unshare succeeded',
      value: result
    };
  }
  // ...
}
```
