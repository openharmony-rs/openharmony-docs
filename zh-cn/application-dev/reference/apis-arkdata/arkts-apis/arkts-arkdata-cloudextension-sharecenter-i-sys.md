# ShareCenter（系统接口）

提供对接共享云服务的类。开发者需要继承此类并实现类的接口，系统内部通过该类的接口连接并使用共享云服务，实现端云共享的发起、取消或退出等能力。

**起始版本：** 11

<!--Device-cloudExtension-export interface ShareCenter--><!--Device-cloudExtension-export interface ShareCenter-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## 导入模块

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

更改端云共享邀请。更改共享邀请时，需指定当前更改共享邀请的应用、共享数据的共享资源标识以及更改的状态，使用Promise异步回调。

**起始版本：** 11

<!--Device-ShareCenter-changeConfirmation(      userId: int,      bundleName: string,      sharingResource: string,      state: cloudData.sharing.State    ): Promise<Result<void>>--><!--Device-ShareCenter-changeConfirmation(      userId: int,      bundleName: string,      sharingResource: string,      state: cloudData.sharing.State    ): Promise<Result<void>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 表示用户账号ID。 |
| bundleName | string | 是 | 应用包名。 |
| sharingResource | string | 是 | 端云共享资源标识。 |
| state | cloudData.sharing.State | 是 | 共享邀请的更改状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;void&gt;&gt; | Promise对象，返回更改共享邀请的结果。 |

**示例：**

```TypeScript
import { cloudData } from '@kit.ArkData';

class MyShareCenter implements cloudExtension.ShareCenter {
  constructor() {}
  async changeConfirmation(userId: number, bundleName: string, sharingResource: string, state: cloudData.sharing.State):
    Promise<cloudExtension.Result<void>> {
    console.info(`change confirm, bundle: ${bundleName}`);
    // 对接云共享服务端，并获得更改共享邀请的返回值
    // ...
    // 返回服务端更改共享邀请的返回结果
    return {
      code: cloudData.sharing.SharingCode.SUCCESS,
      description: 'change confirm succeeded'
    }
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

更改已共享数据的操作权限。更改权限时，需指定当前更改权限的应用、更改权限数据的资源标识和更改权限的参与者，使用Promise异步回调。

**起始版本：** 11

<!--Device-ShareCenter-changePrivilege(      userId: int,      bundleName: string,      sharingResource: string,      participants: Array<cloudData.sharing.Participant>    ): Promise<Result<Array<Result<cloudData.sharing.Participant>>>>--><!--Device-ShareCenter-changePrivilege(      userId: int,      bundleName: string,      sharingResource: string,      participants: Array<cloudData.sharing.Participant>    ): Promise<Result<Array<Result<cloudData.sharing.Participant>>>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 表示用户账号ID。 |
| bundleName | string | 是 | 应用包名。 |
| sharingResource | string | 是 | 端云共享资源标识。 |
| participants | Array&lt;cloudData.sharing.Participant&gt; | 是 | 端云共享参与者。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;Array&lt;Result&lt;cloudData.sharing.Participant&gt;&gt;&gt;&gt; | Promise对象，返回更改权限的结果。 |

**示例：**

```TypeScript
import { cloudData } from '@kit.ArkData';

type Participant = cloudData.sharing.Participant;

class MyShareCenter implements cloudExtension.ShareCenter {
  constructor() {}
  async changePrivilege(userId: number, bundleName: string, sharingResource: string, participants: Array<Participant>):
    Promise<cloudExtension.Result<Array<cloudExtension.Result<Participant>>>> {
    console.info(`change privilege, bundle: ${bundleName}`);
    // 对接云共享服务端，并获得更改权限的返回值
    // ...
    // 返回服务端更改权限的返回结果
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
    }
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

被邀请者确认端云共享邀请。确认时，需指定当前确认邀请的应用、共享数据的邀请码以及确认状态，使用Promise异步回调。

**起始版本：** 11

<!--Device-ShareCenter-confirmInvitation(      userId: int,      bundleName: string,      invitationCode: string,      state: cloudData.sharing.State    ): Promise<Result<string>>--><!--Device-ShareCenter-confirmInvitation(      userId: int,      bundleName: string,      invitationCode: string,      state: cloudData.sharing.State    ): Promise<Result<string>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 表示用户账号ID。 |
| bundleName | string | 是 | 应用包名。 |
| invitationCode | string | 是 | 端云共享邀请码。 |
| state | cloudData.sharing.State | 是 | 共享邀请的确认状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;string&gt;&gt; | Promise对象，返回确认端云共享邀请数据的共享资源标识。 |

**示例：**

```TypeScript
import { cloudData } from '@kit.ArkData';

class MyShareCenter implements cloudExtension.ShareCenter {
  constructor() {}
  async confirmInvitation(userId: number, bundleName: string, invitationCode: string, state: cloudData.sharing.State):
    Promise<cloudExtension.Result<string>> {
    console.info(`confirm invitation, bundle: ${bundleName}`);
    // 对接云共享服务端，并获得确认共享邀请的返回值
    // ...
    // 返回服务端确认共享邀请的返回结果
    return {
      code: cloudData.sharing.SharingCode.SUCCESS,
      description: 'confirm invitation succeeded',
      value: 'sharing_resource_test'
    }
  }
  // ...
}

```

## exit

```TypeScript
exit(userId: number, bundleName: string, sharingResource: string): Promise<Result<void>>
```

退出端云共享。退出共享时，需指定当前退出共享的应用以及退出共享数据的资源标识，使用Promise异步回调。

**起始版本：** 11

<!--Device-ShareCenter-exit(userId: int, bundleName: string, sharingResource: string): Promise<Result<void>>--><!--Device-ShareCenter-exit(userId: int, bundleName: string, sharingResource: string): Promise<Result<void>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 表示用户账号ID。 |
| bundleName | string | 是 | 应用包名。 |
| sharingResource | string | 是 | 端云共享资源标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;void&gt;&gt; | Promise对象，返回退出共享的结果。 |

**示例：**

```TypeScript
import { cloudData } from '@kit.ArkData';

class MyShareCenter implements cloudExtension.ShareCenter {
  constructor() {}
  async exit(userId: number, bundleName: string, sharingResource: string):
    Promise<cloudExtension.Result<void>> {
    console.info(`exit share, bundle: ${bundleName}`);
    // 对接云共享服务端，并获得退出共享的返回值
    // ...
    // 返回服务端退出共享的返回结果
    return {
      code: cloudData.sharing.SharingCode.SUCCESS,
      description: 'exit share succeeded'
    }
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

查询当前端云共享的参与者。查询时，需指定当前查询参与者的应用、查询参与者数据的资源标识，使用Promise异步回调。

**起始版本：** 11

<!--Device-ShareCenter-queryParticipants(      userId: int,      bundleName: string,      sharingResource: string    ): Promise<Result<Array<cloudData.sharing.Participant>>>--><!--Device-ShareCenter-queryParticipants(      userId: int,      bundleName: string,      sharingResource: string    ): Promise<Result<Array<cloudData.sharing.Participant>>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 表示用户账号ID。 |
| bundleName | string | 是 | 应用包名。 |
| sharingResource | string | 是 | 端云共享资源标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;Array&lt;cloudData.sharing.Participant&gt;&gt;&gt; | Promise对象，返回查询共享参与者的结果。 |

**示例：**

```TypeScript
import { cloudData } from '@kit.ArkData';

type Participant = cloudData.sharing.Participant;

class MyShareCenter implements cloudExtension.ShareCenter {
  constructor() {}
  async queryParticipants(userId: number, bundleName: string, sharingResource: string):
    Promise<cloudExtension.Result<Array<Participant>>> {
    console.info(`query participants, bundle: ${bundleName}`);
    // 对接云共享服务端，并获得查询参与者的返回值
    // ...
    // 返回服务端查询参与者的返回结果
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
    })
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
    })
    return {
      code: cloudData.sharing.SharingCode.SUCCESS,
      description: 'query participants succeeded',
      value: participants
    }
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

根据邀请码查询端云共享参与者。查询时，需指定当前查询参与者的应用、共享数据的邀请码，使用Promise异步回调。

**起始版本：** 11

<!--Device-ShareCenter-queryParticipantsByInvitation(      userId: int,      bundleName: string,      invitationCode: string    ): Promise<Result<Array<cloudData.sharing.Participant>>>--><!--Device-ShareCenter-queryParticipantsByInvitation(      userId: int,      bundleName: string,      invitationCode: string    ): Promise<Result<Array<cloudData.sharing.Participant>>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 表示用户账号ID。 |
| bundleName | string | 是 | 应用包名。 |
| invitationCode | string | 是 | 端云共享邀请码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;Array&lt;cloudData.sharing.Participant&gt;&gt;&gt; | Promise对象，返回根据邀请码查询共享参与者的结果。 |

**示例：**

```TypeScript
import { cloudData } from '@kit.ArkData';

type Participant = cloudData.sharing.Participant;

class MyShareCenter implements cloudExtension.ShareCenter {
  constructor() {}
  async queryParticipantsByInvitation(userId: number, bundleName: string, invitationCode: string):
    Promise<cloudExtension.Result<Array<Participant>>> {
    console.info(`query participants by invitation, bundle: ${bundleName}`);
    // 对接云共享服务端，并获得查询参与者的返回值
    // ...
    // 返回服务端查询参与者的返回结果
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
    })
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
    })
    return {
      code: cloudData.sharing.SharingCode.SUCCESS,
      description: 'query participants by invitation succeeded',
      value: participants
    }
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

发起端云共享邀请。共享邀请时，需指定当前发起共享的应用、共享数据的资源标识和共享参与者，使用Promise异步回调。

**起始版本：** 11

<!--Device-ShareCenter-share(      userId: int,      bundleName: string,      sharingResource: string,      participants: Array<cloudData.sharing.Participant>    ): Promise<Result<Array<Result<cloudData.sharing.Participant>>>>--><!--Device-ShareCenter-share(      userId: int,      bundleName: string,      sharingResource: string,      participants: Array<cloudData.sharing.Participant>    ): Promise<Result<Array<Result<cloudData.sharing.Participant>>>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 表示用户账号ID。 |
| bundleName | string | 是 | 应用包名。 |
| sharingResource | string | 是 | 端云共享资源的标识。 |
| participants | Array&lt;cloudData.sharing.Participant&gt; | 是 | 端云共享参与者。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;Array&lt;Result&lt;cloudData.sharing.Participant&gt;&gt;&gt;&gt; | Promise对象，返回发起共享的结果。 |

**示例：**

```TypeScript
import { cloudData } from '@kit.ArkData';

type Participant = cloudData.sharing.Participant;

class MyShareCenter implements cloudExtension.ShareCenter {
  constructor() {}
  async share(userId: number, bundleName: string, sharingResource: string, participants: Array<Participant>):
    Promise<cloudExtension.Result<Array<cloudExtension.Result<Participant>>>> {
    console.info(`share, bundle: ${bundleName}`);
    // 对接云共享服务端，并获得共享的返回值
    // ...
    // 返回服务端发起共享的返回结果
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
    }
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

取消端云共享。取消共享时，需指定当前取消共享的应用、取消共享数据的资源标识和取消共享的参与者，使用Promise异步回调。

**起始版本：** 11

<!--Device-ShareCenter-unshare(      userId: int,      bundleName: string,      sharingResource: string,      participants: Array<cloudData.sharing.Participant>    ): Promise<Result<Array<Result<cloudData.sharing.Participant>>>>--><!--Device-ShareCenter-unshare(      userId: int,      bundleName: string,      sharingResource: string,      participants: Array<cloudData.sharing.Participant>    ): Promise<Result<Array<Result<cloudData.sharing.Participant>>>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 表示用户账号ID。 |
| bundleName | string | 是 | 应用包名。 |
| sharingResource | string | 是 | 端云共享数据的资源标识。 |
| participants | Array&lt;cloudData.sharing.Participant&gt; | 是 | 端云共享参与者。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;Array&lt;Result&lt;cloudData.sharing.Participant&gt;&gt;&gt;&gt; | Promise对象，返回取消共享的结果。 |

**示例：**

```TypeScript
import { cloudData } from '@kit.ArkData';

type Participant = cloudData.sharing.Participant;

class MyShareCenter implements cloudExtension.ShareCenter {
  constructor() {}
  async unshare(userId: number, bundleName: string, sharingResource: string, participants: Array<Participant>):
    Promise<cloudExtension.Result<Array<cloudExtension.Result<Participant>>>> {
    console.info(`unshare, bundle: ${bundleName}`);
    // 对接云共享服务端，并获得取消共享的返回值
    // ...
    // 返回服务端取消共享的返回结果
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
    }
  }
  // ...
}

```

