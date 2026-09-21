# createAbilityConnectionSession

## Modules to Import

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## createAbilityConnectionSession

```TypeScript
function createAbilityConnectionSession(serviceName: string, context: Context, peerInfo: PeerInfo,
        connectOptions: ConnectOptions): number
```

Creates a collaboration session between applications.

**Since:** 18

**Required permissions:** ohos.permission.INTERNET and ohos.permission.GET_NETWORK_INFO and ohos.permission.SET_NETWORK_INFO and ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| serviceName | string | Yes | Service name for the application. The service name must be the same on the local end and peer end. The value contains a maximum of 256 characters. |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Application context. |
| peerInfo | [PeerInfo](arkts-distributedservice-abilityconnectionmanager-peerinfo-i.md) | Yes | Collaboration information of the peer end. |
| connectOptions | [ConnectOptions](arkts-distributedservice-abilityconnectionmanager-connectoptions-i.md) | Yes | Connection options for the application. |

**Return value:**

| Type | Description |
| --- | --- |
| number | ID of the collaboration session. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

On device A, an application calls createAbilityConnectionSession() to create a collaboration session and return the session ID.

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
    // Define peer device information.
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

    // Define connection options.
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

On device B, createAbilityConnectionSession can be called in onCollaborate, which is triggered when the application is started.

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
