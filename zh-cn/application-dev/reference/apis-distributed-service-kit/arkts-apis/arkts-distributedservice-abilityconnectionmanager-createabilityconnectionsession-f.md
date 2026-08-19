# createAbilityConnectionSession

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## createAbilityConnectionSession

```TypeScript
function createAbilityConnectionSession(serviceName: string, context: Context, peerInfo: PeerInfo,
        connectOptions: ConnectOptions): int
```

创建应用间的协同会话。

**起始版本：** 23

**需要权限：** ohos.permission.INTERNET and ohos.permission.GET_NETWORK_INFO and ohos.permission.SET_NETWORK_INFO and ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function createAbilityConnectionSession(serviceName: string, context: Context, peerInfo: PeerInfo,        connectOptions: ConnectOptions): int--><!--Device-abilityConnectionManager-function createAbilityConnectionSession(serviceName: string, context: Context, peerInfo: PeerInfo,        connectOptions: ConnectOptions): int-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| serviceName | string | 是 | 应用设置的服务名称（两端必须一致），最大长度为256字符。 |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 表示应用上下文。 |
| peerInfo | [PeerInfo](arkts-distributedservice-abilityconnectionmanager-peerinfo-i.md) | 是 | 对端的协同信息。 |
| connectOptions | ConnectOptions | 是 | 应用设置的连接选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 成功创建的协同会话ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { abilityConnectionManager, distributedDeviceManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let dmClass: distributedDeviceManager.DeviceManager;

function initDmClass(): void {
  try {
    dmClass = distributedDeviceManager.createDeviceManager('com.example.remotephotodemo');
  } catch (err) {
    hilog.error(0x0000, 'testTag', 'createDeviceManager err: ' + JSON.stringify(err));
  }
}

function getRemoteDeviceId(): string | undefined {
  initDmClass();
  if (typeof dmClass === 'object' && dmClass !== null) {
    hilog.info(0x0000, 'testTag', 'getRemoteDeviceId begin');
    let list = dmClass.getAvailableDeviceListSync();
    if (typeof (list) === 'undefined' || typeof (list.length) === 'undefined') {
      hilog.info(0x0000, 'testTag', 'getRemoteDeviceId err: list is null');
      return;
    }
    if (list.length === 0) {
      hilog.info(0x0000, 'testTag', 'getRemoteDeviceId err: list is empty');
      return;
    }
    return list[0].networkId;
  } else {
    hilog.info(0x0000, 'testTag', 'getRemoteDeviceId err: dmClass is null');
    return;
  }
}

@Entry
@Component
struct Index {
  createSession(): void {
    // 定义peer信息
    const peerInfo: abilityConnectionManager.PeerInfo = {
      deviceId: getRemoteDeviceId()!,
      bundleName: 'com.example.remotephotodemo',
      moduleName: 'entry',
      abilityName: 'EntryAbility',
      serviceName: 'collabTest'
    };
    const myRecord: Record<string, string> = {
      'newKey1': 'value1',
    };

    // 定义连接选项
    const connectOptions: abilityConnectionManager.ConnectOptions = {
      needSendData: true,
      startOptions: abilityConnectionManager.StartOptionParams.START_IN_FOREGROUND,
      parameters: myRecord
    };
    let context = this.getUIContext().getHostContext();
    try {
      let sessionId = abilityConnectionManager.createAbilityConnectionSession("collabTest", context, peerInfo, connectOptions);
      hilog.info(0x0000, 'testTag', 'createSession sessionId is', sessionId);
    } catch (error) {
      hilog.error(0x0000, 'testTag', error);
    }
  }

  build() {
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { Entry, Component } from '@ohos.arkui.component'
import { AppStorage } from '@ohos.arkui.stateManagement';
import abilityConnectionManager from '@ohos.distributedsched.abilityConnectionManager';
import hilog from '@ohos.hilog';
import distributedDeviceManager from '@ohos.distributedDeviceManager'
import common from '@ohos.app.ability.common';

let dmClass: distributedDeviceManager.DeviceManager | null =null;

function initDmClass(): void {
  try {
    dmClass = distributedDeviceManager.createDeviceManager('com.example.remotephotodemo');
  } catch (err) {
    hilog.error(0x0000, 'testTag', 'createDeviceManager err: ' + JSON.stringify(err));
  }
}

function getRemoteDeviceId(): string | undefined {
  initDmClass();
  if (typeof dmClass === 'object' && dmClass !== null) {
    hilog.info(0x0000, 'testTag', 'getRemoteDeviceId begin');
    let list = dmClass!.getAvailableDeviceListSync();
    if (typeof (list) === 'undefined' || typeof (list.length) === 'undefined') {
      hilog.info(0x0000, 'testTag', 'getRemoteDeviceId err: list is null');
      return '';
    }
    if (list.length === 0) {
      hilog.info(0x0000, 'testTag', 'getRemoteDeviceId err: list is empty');
      return '';
    }
    return list[0].networkId;
  } else {
    hilog.info(0x0000, 'testTag', 'getRemoteDeviceId err: dmClass is null');
    return '';
  }
}

@Entry
@Component
struct Index {
  createSession(): void {
    // 定义peer信息
    const peerInfo: abilityConnectionManager.PeerInfo = {
      deviceId: getRemoteDeviceId()!,
      bundleName: 'com.example.remotephotodemo',
      moduleName: 'entry',
      abilityName: 'EntryAbility',
      serviceName: 'collabTest'
    };
    const myRecord: Record<string, string> = {
      "newKey1": "value1",
    };

    // 定义连接选项
    const connectOptions: abilityConnectionManager.ConnectOptions = {
      needSendData: true,
      startOptions: abilityConnectionManager.StartOptionParams.START_IN_FOREGROUND,
      parameters: myRecord
    };
    let context = AppStorage.get<common.UIAbilityContext>('abilityContextMainAbility2') as common.UIAbilityContext;
    try {
      let sessionId =
      abilityConnectionManager.createAbilityConnectionSession("collabTest", context, peerInfo, connectOptions);
      hilog.info(0x0000, 'testTag', 'createSession sessionId is', sessionId);
    } catch (error) {
      hilog.error(0x0000, 'testTag', error.message);
    }
  }

  build() {
  }
}
```

ArkTS-Dyn示例：

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
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
import Ability from '@ohos.app.ability.UIAbility';
import hilog from '@ohos.hilog';
import abilityConnectionManager from '@ohos.distributedsched.abilityConnectionManager';
import { ConfigurationConstant, UIAbility, Want, wantConstant } from '@kit.AbilityKit';
import AbilityConstant from '@ohos.app.ability.AbilityConstant';
import common from '@ohos.app.ability.common';
import { AppStorage } from '@ohos.arkui.stateManagement';

export default class EntryAbility extends UIAbility {
  onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult {
    hilog.info(0x0000, 'testTag', '%{public}s', 'on collaborate');
    let param = wantParam["ohos.extra.param.key.supportCollaborateIndex"] as Record<string, Object>;
    this.onCollab(param);
    return AbilityConstant.CollaborateResult.ACCEPT;
  }

  onCollab(collabParam: Record<string, Object>):void {
    const sessionId = this.createSessionFromWant(collabParam);
    if (sessionId == -1) {
      hilog.info(0x0000, 'testTag', 'Invalid session ID.');
      return;
    }
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
      AppStorage.setOrCreate<common.UIAbilityContext>('sessionId', this.context);
      hilog.info(0x0000, 'testTag', 'createSession sessionId is' + sessionId);
    } catch (error) {
      hilog.error(0x0000, 'testTag', error.message);
    }
    return sessionId;
  }
}
```

