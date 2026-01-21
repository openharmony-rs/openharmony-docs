# Subscribing to State Changes of a Remote Object
<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

IPC/RPC allows you to subscribe to the state changes of a remote stub object. When the remote stub object dies, a death notification will be sent to your local proxy. To subscribe to death notifications, you need to call the [registerDeathRecipient](../reference/apis-ipc-kit/js-apis-rpc.md#registerdeathrecipient9-1) API. To unsubscribe from death notifications, call the [unregisterDeathRecipient](../reference/apis-ipc-kit/js-apis-rpc.md#unregisterdeathrecipient9-1) API.

To be specific, you need to inherit the death notification class [DeathRecipient](../reference/apis-ipc-kit/js-apis-rpc.md#deathrecipient) and implement the [onRemoteDied](../reference/apis-ipc-kit/js-apis-rpc.md#onremotedied) method to clear resources. This callback is invoked when the process accommodating the remote stub object exits or the DSoftBus connection on which RPC depends is disabled.

> **NOTE**
> - The proxy object must first subscribe to death notifications of the stub object. If the stub object is in the normal state, the proxy object can cancel the subscription as required.
> - If the process of the stub object exits or the DSoftBus connection on which RPC depends is disabled, the [onRemoteDied](../reference/apis-ipc-kit/js-apis-rpc.md#onremotedied) method customized by the proxy object will be automatically triggered.

## When to Use

IPC/RPC subscription is applicable to the following scenarios:<br>
1. In IPC, the proxy object needs to detect the status of the process hosting the remote stub object.
2. In RPC, the proxy object needs to detect the status of the process hosting the remote stub object, or the DSoftBus connection status on which RPC depends.

When the proxy detects the death of the remote stub object, proxy objects and clear local resources should be cleared.
> **NOTE**
>
> Subscription to death notifications of anonymous stub objects (not registered with SAMgr) is supported in IPC, but not in RPC.

## **Development Using ArkTS APIs**

> **NOTE**
>
> - The sample code in this topic implements communication between system applications across processes.
>
> - Application scenario constraints: The client is a third-party or system application, and the server is a system application or service.

| API                                                      | Return Value Type| Description                                                    |
| ------------------------------------------------------------ | ---------- | ------------------------------------------------------------ |
| [registerDeathRecipient](../reference/apis-ipc-kit/js-apis-rpc.md#registerdeathrecipient9-1) | void       | Registers a callback for receiving death notifications of the remote object. This method should be called on the proxy side.|
| [unregisterDeathRecipient](../reference/apis-ipc-kit/js-apis-rpc.md#unregisterdeathrecipient9-1) | void       | Unregisters from the callback used to receive death notifications of the remote object.                        |
| [onRemoteDied](../reference/apis-ipc-kit/js-apis-rpc.md#onremotedied) | void       | Called when the process accommodating the remote stub object dies after the proxy successfully registers the death notification.|

### Sample Code

  In the IPC (inter-process communication on the same device) scenario, the sample code is as follows:

Import dependencies and define required variables.

<!-- @[front-end_dependencies](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/IPC/IPC_sendMessage/IPC_Client/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let proxy: rpc.IRemoteObject | undefined;
let connectId: number | undefined;

// Death notification
class MyDeathRecipient implements rpc.DeathRecipient{
  onRemoteDied() {
    hilog.info(0x0000, 'testTag', 'IPCClient: server is died');
  }
}
let deathRecipient = new MyDeathRecipient();
```

Connect to the service, obtain the proxy, and register the death listener. Remove the death listener when the connection is torn down.

<!-- @[connect_ability](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/IPC/IPC_sendMessage/IPC_Client/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
// Connect to the service.
function connectAbility(context:common.UIAbilityContext) {
  hilog.info(0x00000, 'testTag', 'IPCClient: begin to connect Ability');
  let want: Want = {
    bundleName: 'com.example.ipc_stub',
    abilityName: 'ServiceAbility',
  };
  let connect: common.ConnectOptions = {
    onConnect: (elementName, remoteProxy) => {
      hilog.info(0x00000, 'testTag', 'IPCClient: onConnect. elementName is :' + JSON.stringify(elementName));
      proxy = remoteProxy;
      // Register a death listener on the client.
      try {
        proxy.registerDeathRecipient(deathRecipient, 0);
        hilog.info(0x00000, 'testTag', 'IPCClient: registerDeathRecipient success');
      }catch (err) {
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        hilog.error(0x0000, 'testTag', 'IPCClient: register failed, code is ' + code + ', message is ' + message);
      }
    },
    onDisconnect: (elementName) => {
      hilog.info(0x0000, 'testTag', 'IPCClient: onDisconnect. elementName is ' + JSON.stringify(elementName));
      // Remove the death listener from the client.
      try {
        proxy?.unregisterDeathRecipient(deathRecipient, 0);
        hilog.info(0x00000, 'testTag', 'IPCClient: unregisterDeathRecipient success');
      }catch (err) {
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        hilog.error(0x0000, 'testTag', 'IPCClient: unregister failed, code is ' + code + ', message is ' + message);
      }
      proxy = undefined;
    },
    onFailed: (code: number) => {
      hilog.info(0x0000, 'testTag', 'IPCClient: onFailed. code is ' + code);
    },
  }

  try {
    connectId = context.connectServiceExtensionAbility(want, connect);
  }catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    hilog.error(0x0000, 'testTag', 'IPCClient: connectAbility failed, code is ' + code + ', message is ' + message);
  }
}
```

 In the RPC (inter-process communication across devices) scenario, the sample code is as follows:

Import dependencies and define required variables.

<!-- @[rpc_front-end_dependencies](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/IPC/RPC_sendMessage/RPC_Client/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import rpc from '@ohos.rpc';
import hilog from '@ohos.hilog';
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { abilityAccessCtrl, PermissionRequestResult, common, Want} from '@kit.AbilityKit';
import { JSON } from '@kit.ArkTS';

let proxy: rpc.IRemoteObject | undefined
let connectId: number | undefined
let dmInstance: distributedDeviceManager.DeviceManager
let deviceList: Array<distributedDeviceManager.DeviceBasicInfo> | undefined;
let deviceId: string| undefined;

// Death notification
class MyDeathRecipient implements rpc.DeathRecipient{
  onRemoteDied() {
    hilog.info(0x0000, 'testTag', 'server is died');
  }
};
let deathRecipient = new MyDeathRecipient();
```

Obtain the [permission for multi-device collaboration](../security/AccessToken/permissions-for-all-user.md#ohospermissiondistributed_datasync), obtain the peer device ID (unique network identifier of the device, which can be retrieved via **distributedDeviceManager**) in the networking scenario, connect to the service, acquire the proxy object, and register a death listener. Remove the death listener when the connection is torn down after the communication between the proxy object and the server ends.

<!-- @[rpc_connect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/IPC/RPC_sendMessage/RPC_Client/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
// Obtain the permission.
function getPermission(context:common.UIAbilityContext) {
  hilog.info(0x00000, 'testTag', 'RpcClient: begin to requestPermissions');
  try {
    let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
    atManager.requestPermissionsFromUser(context, ['ohos.permission.DISTRIBUTED_DATASYNC'],
      (err: BusinessError, data: PermissionRequestResult) => {
      if (err) {
        hilog.error(0x0000, 'testTag', 'RpcClient: requestPermissions failed, code is ' +
          err.code + ', message is ' + err.message);
      } else {
        hilog.info(0x0000, 'testTag','RpcClient: requestPermissions success, result is ' + JSON.stringify(data));
        hilog.info(0x0000, 'testTag','RpcClient: data permissions is ' + data.permissions);
        hilog.info(0x0000, 'testTag','RpcClient: data authResults is ' + data.authResults);
        hilog.info(0x0000, 'testTag','RpcClient: data dialogShownResults is ' + data.dialogShownResults);
      }
    });
  }catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    hilog.error(0x0000, 'testTag', 'RpcClient: getPermission failed, code is  ' + code + ', message is ' + message);
  }
}

// Obtain the peer device information.
function getDeviceId(){
  hilog.info(0x00000, 'testTag', 'RpcClient: begin to getDeviceId');
  try {
    dmInstance = distributedDeviceManager.createDeviceManager('com.example.rpc_client');
    hilog.info(0x0000, 'testTag', 'RpcClient: createDeviceManager success');
    deviceList = dmInstance.getAvailableDeviceListSync();
    hilog.info(0x0000, 'testTag', 'RpcClient: deviceList is' + JSON.stringify(deviceList));
    if (deviceList.length !== 0) {
      deviceId = deviceList[0].networkId;
      hilog.info(0x0000, 'testTag', 'RpcClient: networkId is ' + deviceId);
    }
  }catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    hilog.error(0x0000, 'testTag', 'RpcClient: getDeviceId failed, code is  ' + code + ', message is ' + message);
  }
}

// Connect to the service.
function connectAbility(context:common.UIAbilityContext) {
  hilog.info(0x00000, 'testTag', 'RpcClient: begin to connect Ability');
  let want: Want = {
    bundleName: 'com.example.rpc_stub',
    abilityName: 'ServiceAbility',
    deviceId: deviceId,
  }

  let connect: common.ConnectOptions = {
    onConnect: (elementName, remoteProxy) => {
      hilog.info(0x00000, 'testTag', 'RpcClient: onConnect. elementName is :' +  JSON.stringify(elementName));
      proxy = remoteProxy;
      // Register a death listener on the client.
      try {
        proxy.registerDeathRecipient(deathRecipient, 0);
        hilog.info(0x00000, 'testTag', 'RpcClient: registerDeathRecipient success');
      }catch (err) {
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        hilog.error(0x0000, 'testTag', 'RpcClient: register failed, code is ' + code + ', message is ' + message);
      }
    },
    onDisconnect: (elementName) => {
      hilog.info(0x0000, 'testTag', 'RpcClient: onDisconnect. elementName is ' + JSON.stringify(elementName));
      // Remove the death listener from the client.
      try {
        proxy?.unregisterDeathRecipient(deathRecipient, 0);
        hilog.info(0x00000, 'testTag', 'RpcClient: unregisterDeathRecipient success');
      }catch (err) {
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        hilog.error(0x0000, 'testTag', 'RpcClient: unregister failed, code is ' + code + ', message is ' + message);
      }
      proxy = undefined;
    },
    onFailed: (code: number) => {
      hilog.info(0x0000, 'testTag', 'RpcClient: onFailed. code is :' + code);
    },
  }

  try {
    connectId = context.connectServiceExtensionAbility(want, connect);
  }catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    hilog.error(0x0000, 'testTag', 'RpcClient: connectService failed, code is ' + code + ', message is ' + message);
  }
}
```

## Reverse Death Notification (Anonymous Stub)

Forward dead notification is a mechanism that allows the proxy to detect death notifications of the stub. To achieve reverse dead notification, you can leverage the forward dead notification mechanism. Suppose there are two processes, A (the process hosting the original stub) and B (the process hosting the original proxy). After obtaining the proxy object of process A, process B creates an anonymous stub object (that is, a stub object not registered with SAMgr), which can be called a callback stub. Then, process B calls [sendMessageRequest](../reference/apis-ipc-kit/js-apis-rpc.md#sendmessagerequest9-2) to send the callback stub to the original stub of process A. Then, process A obtains the callback proxy of process B. As long as the death notification is registered with the callback proxy, when process B (callback stub) dies or the DSoftBus connection on which RPC depends is disabled, the callback proxy can detect the death and notify process A (original stub). In this way, the reverse death notification is implemented.

> **NOTE**
> - Reverse death notification can only be used for cross-process communication within a device.
> - When an anonymous stub object is not referenced by any proxy, the object is automatically released.
