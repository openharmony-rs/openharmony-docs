# acceptConnect

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## acceptConnect

```TypeScript
function acceptConnect(sessionId: int, token: string): Promise<void>
```

设备B上的应用，在创建协同会话成功并获得会话ID后，调用acceptConnect()方法接受连接。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function acceptConnect(sessionId: int, token: string): Promise<void>--><!--Device-abilityConnectionManager-function acceptConnect(sessionId: int, token: string): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | int | 是 | 已创建的协同会话ID。 |
| token | string | 是 | 设备A应用传入的token值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
  }

  onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult {
    hilog.info(0x0000, 'testTag', '%{public}s', 'on collaborate');
    let param = wantParam["ohos.extra.param.key.supportCollaborateIndex"] as Record<string, Object>
    this.onCollab(param);
    return 0;
  }

  onCollab(collabParam: Record<string, Object>) {
    const sessionId = this.createSessionFromWant(collabParam);
    if (sessionId == -1) {
      hilog.info(0x0000, 'testTag', 'Invalid session ID.');
      return;
    }
    const collabToken = collabParam["ohos.dms.collabToken"] as string;
    abilityConnectionManager.acceptConnect(sessionId, collabToken).then(() => {
      hilog.info(0x0000, 'testTag', 'acceptConnect success');
    }).catch(() => {
      hilog.error(0x0000, 'testTag', 'failed'); 
    })
  }

  createSessionFromWant(collabParam: Record<string, Object>): number {
    let sessionId = -1;
    const peerInfo = collabParam["PeerInfo"] as abilityConnectionManager.PeerInfo;
    if (peerInfo == undefined) {
      return sessionId;
    }

    const options = collabParam["ConnectOption"] as abilityConnectionManager.ConnectOptions;
    try {
      sessionId = abilityConnectionManager.createAbilityConnectionSession("collabTest", this.context, peerInfo, options);
      AppStorage.setOrCreate('sessionId', sessionId);
      hilog.info(0x0000, 'testTag', 'createSession sessionId is' + sessionId);
    } catch (error) {
      hilog.error(0x0000, 'testTag', error);
    }
    return sessionId;
  }
}
```

ArkTS-Sta示例：

```TypeScript
import AbilityConstant from '@ohos.app.ability.AbilityConstant';
import { UIAbility, Want } from '@kit.AbilityKit';
import abilityConnectionManager from '@ohos.distributedsched.abilityConnectionManager';
import hilog from '@ohos.hilog';
import { AppStorage } from '@ohos.arkui.stateManagement';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
  }

  onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult {
    hilog.info(0x0000, 'testTag', '%{public}s', 'on collaborate');
    let param = wantParam["ohos.extra.param.key.supportCollaborateIndex"] as Record<string, Object>
    this.onCollab(param);
    return AbilityConstant.CollaborateResult.ACCEPT;
  }

  onCollab(collabParam: Record<string, Object>): void {
    const sessionId = this.createSessionFromWant(collabParam);
    if (sessionId == -1) {
      hilog.info(0x0000, 'testTag', 'Invalid session ID.');
      return;
    }
    const collabToken = collabParam["ohos.dms.collabToken"] as string;
    abilityConnectionManager.acceptConnect(sessionId as Int, collabToken).then(() => {
      hilog.info(0x0000, 'testTag', 'acceptConnect success');
    }).catch(() => {
      hilog.error(0x0000, 'testTag', 'failed');
    })
  }

  createSessionFromWant(collabParam: Record<string, Object>): number {
    let sessionId = -1;
    const peerInfo = collabParam["PeerInfo"] as abilityConnectionManager.PeerInfo;
    if (peerInfo == undefined) {
      return sessionId;
    }

    const options = collabParam["ConnectOption"] as abilityConnectionManager.ConnectOptions;
    try {
      sessionId = abilityConnectionManager.createAbilityConnectionSession("collabTest", this.context, peerInfo, options);
      AppStorage.setOrCreate('sessionId', sessionId);
      hilog.info(0x0000, 'testTag', 'createSession sessionId is' + sessionId);
    } catch (error) {
      hilog.error(0x0000, 'testTag', error.message);
    }
    return sessionId;
  }
}
```

