# IPC与RPC通信开发指导(ArkTS)
<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

## 场景介绍

IPC/RPC的主要工作是跨进程建立对象通信的连接（客户端进程的Proxy和服务端进程的Stub建立一一对应关系），从而通过Proxy的接口可以和Stub进行IPC/RPC通信。

## 开发步骤

> **说明：**
>
> - 当前不支持三方应用实现ServiceExtensionAbility，三方应用的UIAbility组件可以通过[Context](../application-models/uiability-usage.md#获取uiability的上下文信息)连接系统提供的ServiceExtensionAbility。
>
> - 使用场景约束：客户端可以是第三方应用或系统应用，服务端必须是系统应用或系统服务。

<!--Del-->
### 服务端实现

在工程中手动新建一个ServiceExtensionAbility，具体步骤如下：

1. 在工程Module的ets目录下，右键选择“New > Directory”，新建一个目录并命名为ServiceExtAbility。

2. 在ServiceExtAbility目录，右键选择“New > ArkTS File”，新建一个文件并命名为ServiceExtAbility.ets。

    ```txt
    ├── ets
    │ ├── ServiceExtAbility
    │ │   ├── ServiceExtAbility.ets
    └
    ```

3. 在ServiceExtAbility.ets文件中，导入ServiceExtensionAbility的依赖包，自定义类继承ServiceExtensionAbility并实现生命周期回调。定义一个继承自[rpc.RemoteObject](../reference/apis-ipc-kit/js-apis-rpc.md#remoteobject)的stub类，实现[onRemoteMessageRequest](../reference/apis-ipc-kit/js-apis-rpc.md#onremotemessagerequest9)方法，用来处理客户端的请求。在onConnect生命周期回调函数里，创建之前定义的Stub对象并返回。

    <!-- @[service_impl](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/IPC/IPC_sendMessage/IPC_Stub/entry/src/main/ets/ServiceExtAbility/ServiceExtAbility.ets) -->
    
    ``` TypeScript
    import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
    import { rpc } from '@kit.IPCKit';
    import { hilog } from '@kit.PerformanceAnalysisKit';
    
    // 定义服务端
    class Stub extends rpc.RemoteObject {
      constructor(descriptor: string) {
        super(descriptor);
      }
      onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
        option: rpc.MessageOption): boolean | Promise<boolean> {
        // 服务端Stub根据不同的请求code分别执行对应的处理流程
        if (code == 1) {
          let str = data.readString();
          hilog.info(0x0000, 'testTag', 'IPCStub: stub receive str : ' + str);
          // 服务端使用reply回传请求处理的结果给客户端
          reply.writeString('hello rpc');
          return true;
        } else {
          hilog.info(0x0000, 'testTag', 'IPCStub: stub unknown code: ' + code);
          return false;
        }
      }
    }
    
    // 定义后台服务
    export default class ServiceAbility extends ServiceExtensionAbility {
      onCreate(want: Want): void {
        hilog.info(0x0000, 'testTag', 'IPCStub: onCreate');
      }
    
      onRequest(want: Want, startId: number): void {
        hilog.info(0x0000, 'testTag', 'IPCStub: onRequest');
      }
    
      onConnect(want: Want): rpc.RemoteObject {
        hilog.info(0x0000, 'testTag', 'IPCStub: onConnect');
        // 返回Stub对象，客户端获取后便可以与ServiceExtensionAbility进行通信
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

### 客户端实现

1. 创建变量want，指定要连接的Ability所在应用的包名、组件名。

2. 创建变量connect，指定连接成功、连接失败和断开连接时的回调函数。

3. 连接服务，获取服务代理对象Proxy，并注册死亡监听。

4. 客户端发送消息给服务端。

5. 通信结束后，断开连接，移除服务代理对象Proxy的死亡监听。

> **说明：**
>
> - 在本文档的示例中，通过this.getUIContext().getHostContext()来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../application-models/uiability-usage.md#获取uiability的上下文信息)。

  在IPC（同设备的跨进程通信）场景中，客户端的示例如下：

  导入相关依赖，并定义所需的变量；

  <!-- @[front-end_dependencies](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/IPC/IPC_sendMessage/IPC_Client/entry/src/main/ets/pages/Index.ets) -->
  
  ``` TypeScript
  import { BusinessError } from '@kit.BasicServicesKit';
  import { Want, common } from '@kit.AbilityKit';
  import { rpc } from '@kit.IPCKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';
  
  let proxy: rpc.IRemoteObject | undefined;
  let connectId: number | undefined;
  
  // 死亡通知
  class MyDeathRecipient implements rpc.DeathRecipient{
    onRemoteDied() {
      hilog.info(0x0000, 'testTag', 'IPCClient: server is died');
    }
  }
  let deathRecipient = new MyDeathRecipient();
  ```

  连接服务，获取代理对象，发送信息给服务端，通信结束后断开连接。

  <!-- @[funcation_implement](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/IPC/IPC_sendMessage/IPC_Client/entry/src/main/ets/pages/Index.ets) -->
  
  ``` TypeScript
  // 连接服务
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
        // 客户端注册死亡监听
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
        // 客户端移除死亡监听
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
  
  // 发送消息
  function sendString() {
    hilog.info(0x00000, 'testTag', 'IPCClient: begin to send String');
    let option = new rpc.MessageOption();
    let data = rpc.MessageSequence.create();
    let reply = rpc.MessageSequence.create();
    // 在data里写入参数，以传递字符串为例
    data.writeString('hello world');
    if (proxy != undefined) {
      proxy.sendMessageRequest(1, data, reply, option)
        .then((result: rpc.RequestResult) => {
          if (result.errCode != 0) {
            hilog.error(0x0000, 'testTag', 'IPCClient: sendMessageRequest failed, errCode: ' + result.errCode);
            return;
          }
          // 从result.reply里读取结果
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
  
  // 断开连接
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

  在RPC（跨设备的跨进程通信）场景中，具体客户端的示例如下：

  导入相关依赖，并定义所需的变量；

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
  
  // 死亡通知
  class MyDeathRecipient implements rpc.DeathRecipient{
    onRemoteDied() {
      hilog.info(0x0000, 'testTag', 'server is died');
    }
  };
  let deathRecipient = new MyDeathRecipient();
  ```

获取[允许多设备协同的权限](../security/AccessToken/permissions-for-all-user.md#ohospermissiondistributed_datasync)，在组网的情况下获取到对端的设备ID（组网场景下对应设备的唯一网络标识符，可以使用distributedDeviceManager获取目标设备的NetworkId）后连接服务，获取代理对象并发送信息给服务端，当代理对象与服务端的通信结束后，进行断连。

  <!-- @[rpc_funcation_implement](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/IPC/RPC_sendMessage/RPC_Client/entry/src/main/ets/pages/Index.ets) -->
  
  ``` TypeScript
  // 获取权限
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
  
  // 获取对端设备信息
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
  
  // 连接服务
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
        // 客户端注册死亡监听
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
        // 客户端移除死亡监听
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
  
  // 断开连接
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
  
  // 发送消息
  function sendString() {
    hilog.info(0x00000, 'testTag', 'RpcClient: begin to send string');
    let option = new rpc.MessageOption();
    let data = rpc.MessageSequence.create();
    let reply = rpc.MessageSequence.create();
    // 在data里写入参数，以传递字符串为例
    data.writeString('hello world');
  
    if (proxy != undefined) {
      proxy.sendMessageRequest(1, data, reply, option)
        .then((result: rpc.RequestResult) => {
          if (result.errCode != 0) {
            hilog.error(0x0000, 'testTag', 'RpcClient: sendMessageRequest failed, errCode: ' + result.errCode);
            return;
          }
          // 从result.reply里读取结果
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
FA模型使用[connectAbility](../reference/apis-ability-kit/js-apis-ability-featureAbility.md#featureabilityconnectability7)接口连接Ability。
IPC通信结束后，使用[disconnectAbility](../reference/apis-ability-kit/js-apis-ability-featureAbility.md#featureabilitydisconnectability7)接口断开连接，此处的connectId是在连接服务时保存的。

<!--code_no_check_fa-->
``` TypeScript
import { featureAbility } from '@kit.AbilityKit';

// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let connectId = featureAbility.connectAbility(want, connect);

function disconnectCallback() {
  hilog.info(0x0000, 'testTag', 'disconnect ability done');
}
// 断开连接，使用连接服务成功时保存下来的connectId断开连接
featureAbility.disconnectAbility(connectId, disconnectCallback);
```
<!--DelEnd-->

## 完整示例

针对IPC与RPC通信开发，端到端的完整示例，请参考：

- [IPC通信完整样例-使用Parcelable/ArrayBuffer通信](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/IPC/ObjectTransfer)