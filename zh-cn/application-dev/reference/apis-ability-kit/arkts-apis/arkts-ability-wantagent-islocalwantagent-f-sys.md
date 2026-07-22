# isLocalWantAgent（系统接口）

## 导入模块

```TypeScript
import { WantAgent } from '@kit.AbilityKit';
```

## isLocalWantAgent

```TypeScript
function isLocalWantAgent(agent: WantAgent): boolean
```

判断WantAgent实例是否为本地实例。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wantAgent-function isLocalWantAgent(agent: WantAgent): boolean--><!--Device-wantAgent-function isLocalWantAgent(agent: WantAgent): boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | [WantAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent-wantagent-i.md) | 是 | Indicates the WantAgent. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the WantAgent is local. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System app. Interface caller is not a system app. |

**示例：**

```TypeScript
import { wantAgent } from '@kit.AbilityKit';
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

// 创建WantAgent实例并获取是否为本地WantAgent实例
try {
  wantAgentData = wantAgent.createLocalWantAgent(localWantAgentInfo);
  // 判断WantAgent实例是否为本地实例
  let isLocal: boolean = wantAgent.isLocalWantAgent(wantAgentData);
} catch (err) {
  console.error('call isLocalWantAgent failed');
}

```

