# equal

## 导入模块

```TypeScript
import { WantAgent } from '@kit.AbilityKit';
```

<a id="equal"></a>
## equal

```TypeScript
function equal(agent: WantAgent, otherAgent: WantAgent, callback: AsyncCallback<boolean>): void
```

判断两个WantAgent实例是否相等，使用callback异步回调，以此来确定是否是来自同一应用的相同操作。当两个WantAgent实例由当前用户下的同一应用使用相同的WantAgentInfo信息创建，并且实例未被cancel取消，这两个实例相等。在通知（携带WantAgent实例）场景，通知更新时会比较2个通知中的WantAgent实例，不相等时会把旧通知的WantAgent实例删除。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-wantAgent-function equal(agent: WantAgent, otherAgent: WantAgent, callback: AsyncCallback<boolean>): void--><!--Device-wantAgent-function equal(agent: WantAgent, otherAgent: WantAgent, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | [WantAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent-wantagent-i.md) | 是 | WantAgent对象。 |
| otherAgent | [WantAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent-wantagent-i.md) | 是 | WantAgent对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 判断两个WantAgent实例是否相等的回调方法。返回true表示两个WantAgent实例相等，false表示两个WantAgent实例不相等。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |

**示例：**

```TypeScript
import { wantAgent, Want } from '@kit.AbilityKit';
import type { WantAgent } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// wantAgent对象
let wantAgent1: WantAgent;
let wantAgent2: WantAgent;
// WantAgentInfo对象
let wantAgentInfo: wantAgent.WantAgentInfo = {
  wants: [
    {
      deviceId: 'deviceId',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility',
      action: 'action1',
      entities: ['entity1'],
      type: 'MIMETYPE',
      uri: 'key={true,true,false}',
      parameters:
      {
        mykey0: 2222,
        mykey1: [1, 2, 3],
        mykey2: '[1, 2, 3]',
        mykey3: 'ssssssssssssssssssssssssss',
        mykey4: [false, true, false],
        mykey5: ['qqqqq', 'wwwwww', 'aaaaaaaaaaaaaaaaa'],
        mykey6: true,
      }
    } as Want
  ],
  actionType: wantAgent.OperationType.START_ABILITY,
  requestCode: 0,
  wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
};

// getWantAgent回调
let getWantAgentCallback = (err: BusinessError, data: WantAgent) => {
  if (err) {
    console.error(`getWantAgent failed, code: ${JSON.stringify(err.code)}, message: ${JSON.stringify(err.message)}`);
  } else {
    // 创建WantAgent成功，保存返回的WantAgent对象
    wantAgent1 = data;
    wantAgent2 = data;
  }
  // equal回调
  let equalCallback = (err: BusinessError, data: boolean) => {
    if (err) {
      console.error(`equal failed! ${err.code} ${err.message}`);
    } else {
      console.info(`equal ok! ${JSON.stringify(data)}`);
    }
  }
  try {
    // 调用equal接口判断两个WantAgent实例是否相等
    wantAgent.equal(wantAgent1, wantAgent2, equalCallback);
  } catch (err) {
    console.error(`equal failed! ${(err as BusinessError).code} ${(err as BusinessError).message}`);
  }
}

try {
  // 调用getWantAgent接口创建WantAgent对象
  wantAgent.getWantAgent(wantAgentInfo, getWantAgentCallback);
} catch (err) {
  console.error(`getWantAgent failed! ${(err as BusinessError).code} ${(err as BusinessError).message}`);
}

```


<a id="equal-1"></a>
## equal

```TypeScript
function equal(agent: WantAgent, otherAgent: WantAgent): Promise<boolean>
```

判断两个WantAgent实例是否相等，使用Promise异步回调，以此来确定是否是来自同一应用的相同操作。当两个WantAgent实例由当前用户下的同一应用使用相同的WantAgentInfo信息创建，并且实例未被cancel取消，这两个实例相等。在通知（携带WantAgent实例）场景，通知更新时会比较2个通知中的WantAgent实例，不相等时会把旧通知的WantAgent实例删除。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-wantAgent-function equal(agent: WantAgent, otherAgent: WantAgent): Promise<boolean>--><!--Device-wantAgent-function equal(agent: WantAgent, otherAgent: WantAgent): Promise<boolean>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | [WantAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent-wantagent-i.md) | 是 | WantAgent对象。 |
| otherAgent | [WantAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent-wantagent-i.md) | 是 | WantAgent对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回获取判断两个WantAgent实例是否相等的结果。返回true表示两个WantAgent实例相等，false表示两个WantAgent实例不相等。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |

**示例：**

```TypeScript
import { wantAgent, Want } from '@kit.AbilityKit';
import type { WantAgent } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// wantAgent对象
let wantAgent1: WantAgent;
let wantAgent2: WantAgent;
// WantAgentInfo对象
let wantAgentInfo: wantAgent.WantAgentInfo = {
  wants: [
    {
      deviceId: 'deviceId',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility',
      action: 'action1',
      entities: ['entity1'],
      type: 'MIMETYPE',
      uri: 'key={true,true,false}',
      parameters:
      {
        mykey0: 2222,
        mykey1: [1, 2, 3],
        mykey2: '[1, 2, 3]',
        mykey3: 'ssssssssssssssssssssssssss',
        mykey4: [false, true, false],
        mykey5: ['qqqqq', 'wwwwww', 'aaaaaaaaaaaaaaaaa'],
        mykey6: true,
      }
    } as Want
  ],
  actionType: wantAgent.OperationType.START_ABILITY,
  requestCode: 0,
  wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
};

// getWantAgent回调
let getWantAgentCallback = (err: BusinessError, data: WantAgent) => {
  if (err) {
    console.error(`getWantAgent failed, code: ${JSON.stringify(err.code)}, message: ${JSON.stringify(err.message)}`);
  } else {
    // 创建WantAgent成功，保存返回的WantAgent对象
    wantAgent1 = data;
    wantAgent2 = data;
  }
  try {
    // 使用Promise方式判断两个WantAgent实例是否相等
    wantAgent.equal(wantAgent1, wantAgent2).then((data) => {
      console.info(`equal ok! ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
    console.error(`equal failed! ${err.code} ${err.message}`);
  });
  } catch (err) {
    console.error(`equal failed! ${(err as BusinessError).code} ${(err as BusinessError).message}`);
  }
}

try {
  // 调用getWantAgent接口创建WantAgent对象
  wantAgent.getWantAgent(wantAgentInfo, getWantAgentCallback);
} catch (err) {
  console.error(`getWantAgent failed! ${(err as BusinessError).code} ${(err as BusinessError).message}`);
}

```

