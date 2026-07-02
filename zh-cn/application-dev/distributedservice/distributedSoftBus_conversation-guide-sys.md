# 跨设备唤醒与消息传输开发指导
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @wangrui7-->
<!--Designer: @yangyang2-->
<!--Tester: @Ytt-test-->
<!--Adviser: @hu-zhiqiong-->

## 简介

随着分布式场景的发展，智能体间的消息通信需求日益增长。OpenHarmony提供了分布式软总线跨设备智能体唤醒与消息传输能力，基于分布式软总线能力，实现跨设备智能体的唤醒和消息传递。该模块提供了设备查询、快速设备唤醒和消息监听与发送等核心能力，使应用能够在同账号可信设备智能体之间进行高效、可靠的消息交互。

### 实现原理

分布式软总线跨设备智能体唤醒与消息传输模块实现跨设备精准执行用户意图：

![conversation-process](figures/conversation-process.png)

应用通过注册会话监听器，可以接收来自其他设备的消息；通过发送会话数据接口，可以向指定设备的特定能力发送消息。整个通信过程依赖于设备的network ID或UDID进行寻址，确保消息能够准确投递到目标设备的目标应用能力。

### 约束与限制

- 需要配置`ohos.permission.DISTRIBUTED_DATASYNC`和`ohos.permission.sec.ACCESS_UDID`权限。
- 不同设备间只有相同`bundleName`的应用才能进行消息交互。
- 目标设备必须是同账号可信设备。
- 支持系统原生的快速唤醒能力，设备在插电合盖状态下依然可达。
- 该能力从API 26.1.0开始支持。

## 环境准备

### 环境要求

确保设备是同账号设备。

### 搭建环境

1. 在开发PC上安装[DevEco Studio](https://developer.huawei.com/consumer/cn/download)，版本要求在4.1及以上。
2. 将public-SDK更新到API 26.1.0或以上，具体操作参见[更新指南](../tools/openharmony_sdk_upgrade_assistant.md)。
3. 用USB线缆将两台调测设备（设备A和设备B）连接到开发PC。
4. 确保两台设备已开启网络连接，并登录相同账号。

## 接口说明

常用接口说明如下表。具体API说明详见API参考：[@ohos.distributedSoftBus.conversation](../reference/apis-distributedservice-kit/js-apis-conversation-sys.md)。

| 接口名                                      | 功能描述                                                                                               |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| getTrustedDevices()                        | 获取所有可信设备列表。                                                                               |
| postConversationData(deviceId, bundleName, abilityName, msg) | 向指定设备发送会话消息。                                                                                     |
| registerConversationListener(bundleName, abilityName, dataCallback) | 注册会话监听器，接收来自其他设备的消息。                                                                              |
| unregisterConversationListener(bundleName, abilityName) | 注销会话监听器，停止接收消息。                                                                                  |

## 分布式软总线会话开发指导

- 接收端调用[registerConversationListener()接口](../reference/apis-distributedservice-kit/js-apis-conversation-sys.md#registerconversationlistener)注册会话监听器，监听来自其他设备的消息。
- 发送端调用[getTrustedDevices()接口](../reference/apis-distributedservice-kit/js-apis-conversation-sys.md#gettrusteddevices)获取可信设备列表，选择目标设备后调用[postConversationData()接口](../reference/apis-distributedservice-kit/js-apis-conversation-sys.md#postconversationdata)发送消息。
- 不再需要接收消息时，调用[unregisterConversationListener()接口](../reference/apis-distributedservice-kit/js-apis-conversation-sys.md#unregisterconversationlistener)注销监听器。

### 接收端开发指导

1. 导入所需的模块。

   <!-- @[import_conversation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code\DocsSample\DistributedAppDev\DistributedSoftbusConversationDemo\entry\src\main\ets\pages\Index.ets) -->

   ```ts
   import { conversation } from '@kit.DistributedServiceKit';
   ```

2. 在module.json5配置文件中配置分布式数据同步权限和UDID访问权限。

   ```json
   {
     "module" : {
       "requestPermissions":[
         {
           "name" : "ohos.permission.DISTRIBUTED_DATASYNC",
           "reason": "$string:distributed_permission",
           "usedScene": {
             "abilities": [
               "EntryAbility"
             ],
             "when": "always"
           }
         },
         {
           "name" : "ohos.permission.sec.ACCESS_UDID",
           "reason": "$string:access_udid_permission",
           "usedScene": {
             "abilities": [
               "EntryAbility"
             ],
             "when": "always"
           }
         }
       ]
     }
   }
   ```

3. 定义会话监听器回调函数。

   <!-- @[data_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code\DocsSample\DistributedAppDev\DistributedSoftbusConversationDemo\entry\src\main\ets\pages\Index.ets) -->

   ```ts
   let messageCallback: conversation.DataCallback = (deviceId: string, msg: ArrayBuffer): void => {
     hilog.info(DOMAIN, TAG, 'Received message from: %{public}s', deviceId);
     hilog.info(DOMAIN, TAG, 'Message length: %{public}d', msg.byteLength);
     let bufferView = new Uint8Array(msg);
     let messageStr = '';
     for (let i = 0; i< bufferView.length; i++) {
         messageStr = String.fromCharCode(bufferView[i]);
       }
     hilog.info(DOMAIN, TAG, 'Message content: %{public}s', messageStr);
   }
   ```

4. 注册会话监听器，接收来自其他设备的消息。

   <!-- @[register_listener](https://gitcode.com/openharmony/applications_app_samples/blob/master/code\DocsSample\DistributedAppDev\DistributedSoftbusConversationDemo\entry\src\main\ets\pages\Index.ets) -->

   ```ts
   registerListener(): void {
     hilog.info(DOMAIN, TAG, 'registerListener called');
     try {
       conversation.registerConversationListener(bundleName, abilityName, messageCallback);
       hilog.info(DOMAIN, TAG, 'Listener registered for %{public}s/%{public}s', bundleName, abilityName);
     } catch (err) {
       let error = err as BusinessError;
       hilog.error(DOMAIN, TAG, 'registerDataListener error: %{public}s - %{public}s', error.code, error.message);
     }
   }
   ```

5. 注销会话监听器。

   <!-- @[unregister_listener](https://gitcode.com/openharmony/applications_app_samples/blob/master/code\DocsSample\DistributedAppDev\DistributedSoftbusConversationDemo\entry\src\main\ets\pages\Index.ets) -->

   ```ts
   unregisterListener(): void {
     hilog.info(DOMAIN, TAG, 'unregisterListener called');
     try {
       conversation.unregisterConversationListener(bundleName, abilityName);
       hilog.info(DOMAIN, TAG, 'Listener unregistered');
     } catch (err) {
       let error = err as BusinessError;
       hilog.error(DOMAIN, TAG, 'unregisterDataListener error: %{public}s - %{public}s', error.code, error.message);
     }
   }
   ```

### 发送端开发指导

1. 导入所需的模块。

   <!-- @[import_conversation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code\DocsSample\DistributedAppDev\DistributedSoftbusConversationDemo\entry\src\main\ets\pages\Index.ets) -->

   ```ts
   import { conversation } from '@kit.DistributedServiceKit';
   ```

2. 在module.json5配置文件中配置分布式数据同步权限和UDID访问权限。

   ```json
   {
     "module" : {
       "requestPermissions":[
         {
           "name" : "ohos.permission.DISTRIBUTED_DATASYNC",
           "reason": "$string:distributed_permission",
           "usedScene": {
             "abilities": [
               "EntryAbility"
             ],
             "when": "always"
           }
         },
         {
           "name" : "ohos.permission.sec.ACCESS_UDID",
           "reason": "$string:access_udid_permission",
           "usedScene": {
             "abilities": [
               "EntryAbility"
             ],
             "when": "always"
           }
         }
       ]
     }
   }
   ```

3. 获取可信设备列表，选择目标设备。

   <!-- @[get_trusted_devices](https://gitcode.com/openharmony/applications_app_samples/blob/master/code\DocsSample\DistributedAppDev\DistributedSoftbusConversationDemo\entry\src\main\ets\pages\Index.ets) -->

   ```ts
   getTrustedDevices(): void {
     hilog.info(DOMAIN, TAG, 'getTrustedDevices called');
     try {
       let devices = conversation.getTrustedDevices() as conversation.DeviceNodeInfo[];
       if (devices && devices.length > 0) {
           let deviceInfo = devices.map((d, idx) =>
           `${idx + 1}. ${d.deviceName} (${d.networkId}) - Type:${d.deviceTypeId} - Nearby:${d.nearby}`
             ).join('\n');
           hilog.info(DOMAIN, TAG, 'Found %{public}s devices', devices.length);
           hilog.info(DOMAIN, TAG, 'Devices list: \n %{public}s', deviceInfo);
         } else {
           hilog.info(DOMAIN, TAG, 'Found %{public}s devices', devices.length);
         }
     } catch (err) {
       let error = err as BusinessError;
       hilog.error(DOMAIN, TAG, 'getTrustedDevices error: %{public}s - %{public}s', error.code, error.message);
     }
   }
   ```

4. 向指定设备发送会话消息。

   <!-- @[send_message](https://gitcode.com/openharmony/applications_app_samples/blob/master/code\DocsSample\DistributedAppDev\DistributedSoftbusConversationDemo\entry\src\main\ets\pages\Index.ets) -->

   ```ts
   sendMessage(): void {
     hilog.info(DOMAIN, TAG, 'sendMessage called');
     try {
       let arrayBuffer = new ArrayBuffer(messageToSend.length);
       let bufferView = new Uint8Array(arrayBuffer);
       for (let i = 0; i < messageToSend.length; i++) {
           bufferView[i] = messageToSend.charCodeAt(i);
         }

       conversation.postConversationData(deviceId, bundleName, abilityName, arrayBuffer)
           .then(() => {
             hilog.info(DOMAIN, TAG, 'Message sent successfully to %{public}s', deviceId);
           })
           .catch((err : BusinessError) => {
             hilog.error(DOMAIN, TAG, 'sendMessage error: %{public}s - %{public}s', err.code, err.message);
           });
     } catch (err) {
       let error = err as BusinessError;
       hilog.error(DOMAIN, TAG, 'sendMessage error: %{public}s - %{public}s', error.code, error.message);
     }
   }
   ```