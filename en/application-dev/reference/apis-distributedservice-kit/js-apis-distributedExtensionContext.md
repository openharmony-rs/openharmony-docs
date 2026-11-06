# @ohos.application.DistributedExtensionContext (Distributed Extension Context)

<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=9197609ec1776b6b3ebd6130e77c90d43ce956ee translatedAt=2026-08-04T03:14:02.555Z pushedAt=2026-08-06T11:21:57.663Z -->

The DistributedExtensionContext module is the context environment of DistributedExtensionAbility and inherits from ExtensionContext.

> **NOTE**
>
> The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Usage

Obtains the DistributedExtensionContext through a DistributedExtensionAbility subclass instance.

<!--code_no_check-->

```ts
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onCreate() {
    let context = this.context; // Obtain the DistributedExtensionContext.
  }
}
```

## DistributedExtensionContext.connectServiceExtensionAbility

connectServiceExtensionAbility(want: Want, options: ConnectOptions): number

Connects the current DistributedExtensionAbility to a remote ServiceExtensionAbility (on another device). After the connection is established, the [rpc.IRemoteObject](../apis-ipc-kit/js-apis-rpc.md#iremoteobject) proxy returned through the onConnect callback can be used for cross-device IPC communication with the remote ServiceExtensionAbility, so as to use the capabilities it provides. This API is applicable to multi-device collaborative scenarios, for example, invoking the background service capability of another device from the current device. To use this API, the developer first specifies the target device through **deviceId** in **Want** and the target ServiceExtensionAbility through **bundleName** and **abilityName**, and constructs [ConnectOptions](../apis-ability-kit/js-apis-inner-ability-connectOptions.md) to implement the **onConnect**, **onDisconnect**, and **onFailed** callbacks for handling the connection successful, disconnection, and connection failure states respectively. Then, the developer calls **connectServiceExtensionAbility** to initiate the connection and obtain the returned connection ID. After the connection is successful, the **IRemoteObject** proxy object is obtained in the **onConnect** callback, based on which IPC communication with the remote ServiceExtensionAbility can be performed. After use, [disconnectServiceExtensionAbility](#distributedextensioncontextdisconnectserviceextensionability) must be called to disconnect and release resources.

**Since:** 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Parameters**

| Name | Type                                                         | Mandatory | Description                                                         |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| want    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)      | Yes   | Want information of the remote ServiceExtensionAbility to connect to. The system establishes a connection to the remote device based on this information. |
| options | [ConnectOptions](../apis-ability-kit/js-apis-inner-ability-connectOptions.md) | Yes   | Configuration object of the **ConnectOptions** type, containing service connection state callbacks. **onConnect** is triggered when the connection is successful, **onDisconnect** is triggered when the connection is disconnected, and **onFailed** is triggered when the connection fails. |

**Return value**

| Type   | Description                                                         |
| ------ | ------------------------------------------------------------ |
| number | Connection ID, which is used to disconnect the connection later. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID | Error Message |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled. |
| 16000013 | The application is controlled by EDM. |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |

**Example**

<!--code_no_check-->

```ts
import { AbilityConstant, Want } from '@kit.AbilityKit';
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleManager } from '@kit.AbilityKit';

const TAG = 'DistributedExtAbility';
const DOMAIN = 0xFF00;

export default class DistributedExtAbility extends DistributedExtensionAbility {


  onCreate (want:Want) {
    hilog.info(DOMAIN, TAG, 'onCreate');
    this.testConnectServiceExtensionAbility();
  }

  onCollaborate (wantParam: Record<string, Object>) {
    hilog.info(DOMAIN, TAG, 'onCollaborate');
    return AbilityConstant.CollaborateResult.ACCEPT;
  }

  onDestroy () {
    hilog.info(DOMAIN, TAG, 'onDestroy');
  }

  connectId:number = -1;
  private testConnectServiceExtensionAbility() {
    hilog.info(DOMAIN, TAG, 'testConnectServiceExtensionAbility');
    let deviceId1: string = '';
    try {
      let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
      deviceId1 = dmInstance.getLocalDeviceId();
      const message: string = 'local device id: ' + deviceId1;
      hilog.info(DOMAIN, TAG, message);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error('getLocalDeviceId errCode:' + e.code + ',errMessage:' + e.message);
    }
    const targetWant:Want = {
      deviceId: deviceId1,
      bundleName: 'com.example.test0002',
      abilityName: 'ServiceExtAbility',
    }
    const options: common.ConnectOptions = {
      onConnect: (name: bundleManager.ElementName, remote: rpc.IRemoteObject): void => {
        const message: string = 'onConnect: ' + name;
        hilog.info(DOMAIN, TAG, message);
      },
      onDisconnect: (name: bundleManager.ElementName): void => {
        const message: string = 'onDisconnect: ' + name;
        hilog.info(DOMAIN, TAG, message);
      },
      onFailed: (code: number): void => {
        const message: string = 'onFailed: code=' + code;
        hilog.info(DOMAIN, TAG, message);
      }
    };
    try {
      const id: number = this.context.connectServiceExtensionAbility(targetWant, options);
      this.connectId = id;
      const message: string = 'connect called, id=' + id;
      hilog.info(DOMAIN, TAG, message);
    } catch (err) {
      const message: string = 'connect error: ' + err;
      hilog.info(DOMAIN, TAG, message);
    }
  }
}
```

## DistributedExtensionContext.disconnectServiceExtensionAbility

disconnectServiceExtensionAbility(connection: number): Promise&lt;void&gt;

Disconnects from a remote ServiceExtensionAbility. It is used in pair with [connectServiceExtensionAbility](#distributedextensioncontextconnectserviceextensionability). After connectServiceExtensionAbility is called, this method must be called to release connection resources when they are no longer needed. This method must be called with the connection ID returned by connectServiceExtensionAbility. After disconnection, the developer must set the remote object returned in the onConnect callback upon successful connection to null to avoid subsequent misuse of the invalidated proxy object. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Parameters**

| Name     | Type   | Mandatory | Description                                                     |
| ---------- | ------ | ---- | -------------------------------------------------------- |
| connection | number | Yes   | Connection ID, which must be the value returned by connectServiceExtensionAbility. |

**Return value**

| Type            | Description                               |
| --------------- | ---------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Ability Kit Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID | Error Message |
| -------- | ------------------------------------------------------------ |
| 16000003 | The connection id does not exist.                            |
| 16000011 | The ability has been destroyed. The context is no longer valid, meaning the context does not exist. |
| 16000050 | Internal error.                                              |

**Example**

<!--code_no_check-->

```ts
import { AbilityConstant, Want } from '@kit.AbilityKit';
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleManager } from '@kit.AbilityKit';


const TAG = 'DistributedExtAbility';
const DOMAIN = 0xFF00;

export default class DistributedExtAbility extends DistributedExtensionAbility {


  onCreate (want:Want) {
    hilog.info(DOMAIN, TAG, 'onCreate');
  }

  onCollaborate (wantParam: Record<string, Object>) {
    hilog.info(DOMAIN, TAG, 'onCollaborate');
    return AbilityConstant.CollaborateResult.ACCEPT;
  }

  onDestroy () {
    hilog.info(DOMAIN, TAG, 'onDestroy');
    this.testDisconnectServiceExtensionAbility();
  }

  connectId:number = -1;

  private testDisconnectServiceExtensionAbility() {
    hilog.info(DOMAIN, TAG, 'testDisconnectServiceExtensionAbility');
    this.context.disconnectServiceExtensionAbility(this.connectId);
  }
}
```