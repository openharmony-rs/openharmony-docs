# IPC and RPC Development (ArkTS)
<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

## When to Use

IPC/RPC is used to implement object communication across processes (one-to-one mapping between the client proxy and the server stub).

## How to Develop

> **NOTE**
>
> - Currently, third-party applications cannot implement ServiceExtensionAbility. The UIAbility component of a third-party application can connect to the ServiceExtensionAbility provided by the system through [Context](../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
>
> - Application scenario constraints: The client can be a third-party application or system application, and the server must be a system application or system service.

<!--Del-->
### Server Implementation

Create a ServiceExtensionAbility as follows:

1. In the **ets** directory of a module in the project, right-click and choose **New > Directory** to create a directory named **ServiceExtAbility**.

2. In the **ServiceExtAbility** directory, right-click and choose **New > ArkTS File** to create a file named **ServiceExtAbility.ets**.

    ```txt
    ├── ets
    │ ├── ServiceExtAbility
    │ │   ├── ServiceExtAbility.ets
    └
    ```

3. In the **ServiceExtAbility.ets** file, import the dependency package of the ServiceExtensionAbility. The custom class inherits the ServiceExtensionAbility and implements lifecycle callbacks. Define a stub class that inherits from [rpc.RemoteObject](../reference/apis-ipc-kit/js-apis-rpc.md#remoteobject) and implement the [onRemoteMessageRequest](../reference/apis-ipc-kit/js-apis-rpc.md#onremotemessagerequest9) method to process requests from the client. In the **onConnect** lifecycle callback, create the defined stub object and return it.

    <!-- @[service_impl](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/IPC/IPC_sendMessage/IPC_Stub/entry/src/main/ets/ServiceExtAbility/ServiceExtAbility.ets) -->
    
    ``` TypeScript
    import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
    import { rpc } from '@kit.IPCKit';
    import { hilog } from '@kit.PerformanceAnalysisKit';
    
    // Define the server.
    class Stub extends rpc.RemoteObject {
      constructor(descriptor: string) {
        super(descriptor);
      }
      onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
        option: rpc.MessageOption): boolean | Promise<boolean> {
        // The server stub executes the corresponding processing based on the request code.
        if (code == 1) {
          let str = data.readString();
          hilog.info(0x0000, 'testTag', 'IPCStub: stub receive str : ' + str);
          // The server sends the request processing result to the client.
          reply.writeString('hello rpc');
          return true;
        } else {
          hilog.info(0x0000, 'testTag', 'IPCStub: stub unknown code: ' + code);
          return false;
        }
      }
    }
    
    // Define the background service.
    export default class ServiceAbility extends ServiceExtensionAbility {
      onCreate(want: Want): void {
        hilog.info(0x0000, 'testTag', 'IPCStub: onCreate');
      }
    
      onRequest(want: Want, startId: number): void {
        hilog.info(0x0000, 'testTag', 'IPCStub: onRequest');
      }
    
      onConnect(want: Want): rpc.RemoteObject {
        hilog.info(0x0000, 'testTag', 'IPCStub: onConnect');
        // Return a stub object, through which the client can communicate with the ServiceExtensionAbility.
        return new Stub('IPCStubTest');
      }
    
      onDisconnect(want: Want): void {
        hilog.info(0x0000, 'testTag', 'IPCStub: onDisconnect');
      }
    
      onDestroy(): void {
        hilog.info(0x0000, 'testTag', 'IPCStub: onDestroy');
      }
    }
    ```
<!--DelEnd-->

### Client Implementation

1. Create a **want** variable, and specify the bundle name and component name of the application where the ability is located.

2. Create a **connect** variable, and specify the callback that is called when the binding is successful, the binding fails, or the ability is disconnected.

3. Connect to the service, obtain the service proxy, and register the death listener.

4. Send a message from the client to the server.

5. Tear down the connection and remove the death listener of the service proxy when the communication is over.

> **NOTE**
>
> - In the sample code provided in this topic, **this.getUIContext().getHostContext()** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  In the IPC (inter-process communication on the same device) scenario, the following is an example of the client:

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

  Connect to the service, obtain the proxy object, send information to the server, and tear down the connection when the communication is over.

  <!-- @[funcation_implement](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/IPC/IPC_sendMessage/IPC_Client/entry/src/main/ets/pages/Index.ets) -->
  
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
  
  // Send a message.
  function sendString() {
    hilog.info(0x00000, 'testTag', 'IPCClient: begin to send String');
    let option = new rpc.MessageOption();
    let data = rpc.MessageSequence.create();
    let reply = rpc.MessageSequence.create();
    // Write parameters in data. The following uses the string as an example.
    data.writeString('hello world');
    if (proxy != undefined) {
      proxy.sendMessageRequest(1, data, reply, option)
        .then((result: rpc.RequestResult) => {
          if (result.errCode != 0) {
            hilog.error(0x0000, 'testTag', 'IPCClient: sendMessageRequest failed, errCode: ' + result.errCode);
            return;
          }
          // Read the result from result.reply.
          let str = result.reply.readString();
          hilog.info(0x0000, 'testTag', 'IPCClient: sendMessageRequest receive str is  ' + str);
        })
        .catch((e: Error) => {
          hilog.error(0x0000, 'testTag', 'IPCClient: sendMessageRequest failed, error is ' + JSON.stringify(e));
        })
        .finally(() => {
          data.reclaim();
          reply.reclaim();
        })
    }
  }
  
  // Close the connection.
  function disconnectAbility(context: common.UIAbilityContext) {
    hilog.info(0x00000, 'testTag', 'IPCClient: begin to disconnect Ability');
    if (connectId != undefined) {
      try {
        context.disconnectServiceExtensionAbility(connectId);
      }catch (err) {
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        hilog.error(0x0000, 'testTag', 'IPCClient: disconnect failed, code is ' + code + ', message is ' + message);
      }
    }
  }
  ```

  In the RPC (inter-process communication across devices) scenario, the following is an example of the client:

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

Obtain the [permission for multi-device collaboration](../security/AccessToken/permissions-for-all-user.md#ohospermissiondistributed_datasync), obtain the peer device ID (unique network identifier of the device, which can be retrieved via **distributedDeviceManager**) in the networking scenario, connect to the service, acquire the proxy object, and send messages to the server. Disconnect once the communication between the proxy object and server ends.

  <!-- @[rpc_funcation_implement](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/IPC/RPC_sendMessage/RPC_Client/entry/src/main/ets/pages/Index.ets) -->
  
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
  
  // Close the connection.
  function disconnectAbility(context: common.UIAbilityContext) {
    hilog.info(0x00000, 'testTag', 'RpcClient: begin to disconnect Ability');
    if (connectId != undefined) {
      try {
        context.disconnectServiceExtensionAbility(connectId);
      }catch (err) {
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        hilog.error(0x0000, 'testTag', 'pcClient: disconnectService failed, code is ' + code + ', message is ' + message);
      }
    }
  }
  
  // Send a message.
  function sendString() {
    hilog.info(0x00000, 'testTag', 'RpcClient: begin to send string');
    let option = new rpc.MessageOption();
    let data = rpc.MessageSequence.create();
    let reply = rpc.MessageSequence.create();
    // Write parameters in data. The following uses the string as an example.
    data.writeString('hello world');
  
    if (proxy != undefined) {
      proxy.sendMessageRequest(1, data, reply, option)
        .then((result: rpc.RequestResult) => {
          if (result.errCode != 0) {
            hilog.error(0x0000, 'testTag', 'RpcClient: sendMessageRequest failed, errCode: ' + result.errCode);
            return;
          }
          // Read the result from result.reply.
          let str = result.reply.readString();
          hilog.info(0x0000, 'testTag', 'RpcClient: sendMessageRequest receiver, str: ' + str);
        })
        .catch((e: Error) => {
          hilog.error(0x0000, 'testTag', 'pcClient: sendMessageRequest failed, error is ' + JSON.stringify(e));
        })
        .finally(() => {
          data.reclaim();
          reply.reclaim();
        })
    }
  }
  ```

<!--Del-->
In the FA model, the [connectAbility](../reference/apis-ability-kit/js-apis-ability-featureAbility.md#featureabilityconnectability7) API is used to connect to an ability.

After IPC is complete, call [disconnectAbility](../reference/apis-ability-kit/js-apis-ability-featureAbility.md#featureabilitydisconnectability7) to disable the connection. The **connectId** is saved when the service is connected.

<!--code_no_check_fa-->
``` TypeScript
import { featureAbility } from '@kit.AbilityKit';

// Save the connection ID, which will be used when the ability is disconnected.
let connectId = featureAbility.connectAbility(want, connect);

function disconnectCallback() {
  hilog.info(0x0000, 'testTag', 'disconnect ability done');
}
// Use the connectId saved when the service is successfully connected to disable the connection.
featureAbility.disconnectAbility(connectId, disconnectCallback);
```
<!--DelEnd-->

## Sample

For the end-to-end complete example of IPC and RPC development, see the following:

- [Complete IPC Example - Using Parcelable/ArrayBuffer](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/IPC/ObjectTransfer)
