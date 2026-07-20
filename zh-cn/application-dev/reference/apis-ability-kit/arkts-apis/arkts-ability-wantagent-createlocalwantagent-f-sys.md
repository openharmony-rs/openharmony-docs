# createLocalWantAgent（系统接口）

## 导入模块

```TypeScript
import { WantAgent } from '@kit.AbilityKit';
```

<a id="createlocalwantagent"></a>
## createLocalWantAgent

```TypeScript
function createLocalWantAgent(info: LocalWantAgentInfo): WantAgent
```

创建本地WantAgent实例。

> **说明：**  
> 本接口创建的本地WantAgent实例仅存储于WantAgent客户端，不受WantAgent服务端管理。使用该本地实例时，需要校验实例，以保证安全性。  
> 本地WantAgent实例创建后，触发方法参见[wantAgent.triggerAsync](arkts-ability-wantagent-triggerasync-f-sys.md#triggerasync-1)接口说明。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wantAgent-function createLocalWantAgent(info: LocalWantAgentInfo): WantAgent--><!--Device-wantAgent-function createLocalWantAgent(info: LocalWantAgentInfo): WantAgent-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [LocalWantAgentInfo](arkts-ability-wantagent-localwantagentinfo-t-sys.md) | 是 | Information about the local WantAgent object to create. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WantAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent-wantagent-i.md) | Returns the created WantAgent. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |

**示例：**

```TypeScript
import { wantAgent, Want } from '@kit.AbilityKit';
import type { WantAgent } from '@kit.AbilityKit';

// 声明wantAgent实例
let wantAgentData: WantAgent;
// 创建LocalWantAgentInfo实例
let localWantAgentInfo: wantAgent.LocalWantAgentInfo = {
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
  operationType: wantAgent.OperationType.START_ABILITY,
  requestCode: 0
};
// 创建本地WantAgent实例
try {
  wantAgentData = wantAgent.createLocalWantAgent(localWantAgentInfo);
} catch (err) {
  console.error('createLocalWantAgent failed');
}

```

