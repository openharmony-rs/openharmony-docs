# 媒体会话控制方
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_7KSyM10J; @devil_red-->
<!--Designer: @gcw_7KSyM10J-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

从API版本23开始，支持应用通过AVSession Kit获取媒体会话的播放信息和控制媒体会话的播放暂停等，实现对系统中的音视频应用进行统一的播放控制。该文档介绍媒体会话控制方接口能力及开发基本流程，包括获取媒体会话提供方的元数据，播放状态信息等，也可向媒体会话提供方发送命令及事件，控制媒体会话提供方的播放、暂停等。

## 基本概念

- [媒体会话提供方](using-avsession-developer.md)：音视频应用在实现音视频功能的同时，需要作为媒体会话提供方接入媒体会话，并响应媒体会话控制方下发的播控命令。

- 媒体会话描述符（AVSessionDescriptor）：描述媒体会话的相关信息，包含标识媒体会话的ID（sessionId），媒体会话的类型type（音频Audio/视频Video），媒体会话自定义名称（sessionTag），媒体会话所属应用的信息（elementName）、是否为置顶会话（isTopSession）等。

- 媒体会话控制器（AVSessionController）：会话控制器，可用于查看会话ID，向会话发送命令及事件，获取会话元数据、播放状态信息等操作。

- 置顶会话（TopSession）：系统中优先级最高的媒体会话，例如当前处于正在播放状态的会话。

## 接口说明

媒体会话控制方使用的关键接口包括两类：

1. 获取媒体会话描述符及媒体会话控制器，监听媒体会话的创建及销毁：通过AVSessionManager来调用，例如接口`AVSessionManager.createController(sessionId)`。
2. 获取媒体会话的元数据、播放状态信息等，监听媒体会话的元数据、播放状态变化等：通过AVSessionController对象来调用，例如接口`controller.getAVPlaybackState()`。

异步的JavaScript接口返回值有callback和promise两种返回形式。promise和callback只是返回值方式不一样，功能相同。

更多API说明请参见@ohos.multimedia.avsession (媒体会话管理)的[模块描述](../../reference/apis-avsession-kit/arkts-apis-avsession.md)。

## 开发步骤

应用作为媒体会话控制方接入的基本步骤如下所示：

1. 应用申请受限开放权限[ohos.permission.MANAGE_MEDIA_RESOURCES_FOR_PUBLIC](../../security/AccessToken/restricted-permissions.md#ohospermissionmanage_media_resources_for_public)。当前仅少量符合特殊场景的应用可在通过审批后，使用受限权限，其申请方式请参考：[申请使用受限权限](../../security/AccessToken/declare-permissions-in-acl.md)。

2. 监听媒体会话的创建、销毁以及当前最新播放的媒体会话变更，并创建媒体会话对应的AVSessionController，从而对系统中的音视频应用进行统一的播放控制。

   <!-- @[getAVSessionDescriptorsInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionController/entry/src/main/ets/feature/MediaController.ets) --> 
   
   ``` TypeScript
   import { avSession } from '@kit.AVSessionKit';
   // ...
   
     // 获取媒体会话描述符及媒体会话控制器。
     async getAVSessionDescriptorsInfo(): Promise<void> {
       try {
         // 获取所有设置过媒体信息且注册过控制回调的会话的描述符信息。
         avSession.getAllSessionDescriptors().then(async (descriptors: avSession.AVSessionDescriptor[]) => {
           Log.info(TAG, 'Succeeded in getting all session descriptors, length: ' + descriptors.length);
           if (descriptors.length > 0) {
             avSession.createController(descriptors[0].sessionId).then(
               async (controller: avSession.AVSessionController) => {
               this.currentController = controller;
               this.currentControllerLink?.set(controller);
               await this.getControllerInfo();
               await this.listenControllerInfo();
               await this.getAVSessionValidCommands();
             });
           }
         });
   
         // 监听最新播放会话变更的事件。
         avSession.onTopSessionChange(async (descriptor: avSession.AVSessionDescriptor) => {
           Log.info(TAG, 'on topSessionChange : sessionTag: ' + descriptor.sessionTag);
           avSession.createController(descriptor.sessionId).then(async (controller: avSession.AVSessionController) => {
             this.currentController = controller;
             this.currentControllerLink?.set(controller);
             await this.getControllerInfo();
             await this.listenControllerInfo();
             await this.getAVSessionValidCommands();
           });
         });
   
         // 监听会话创建事件。
         avSession.onSessionCreate((descriptor: avSession.AVSessionDescriptor) => {
           Log.info(TAG, 'on sessionCreate: sessionTag: ' + descriptor.sessionTag);
         });
   
         // 监听会话的销毁事件。
         avSession.onSessionDestroy((descriptor: avSession.AVSessionDescriptor) => {
           Log.info(TAG, 'on sessionDestroy: ' + descriptor.sessionTag);
         });
       } catch (error) {
         if (error) {
           Log.error(TAG, `avSession Error: Code: ${error.code}, message: ${error.message}`);
         }
       }
     }
   ```

3. 获取媒体会话提供方传递的当前播放曲目及播放状态等。

   <!-- @[getControllerInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionController/entry/src/main/ets/feature/MediaController.ets) --> 

4. 监听媒体会话提供方的媒体信息变化及会话其他事件，从而应用可以根据回调及时刷新播放的曲目及播放状态。

   <!-- @[listenControllerInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionController/entry/src/main/ets/feature/MediaController.ets) --> 

5. 获取会话支持的有效命令，从而应用可以感知媒体会话提供方支持的命令。

   <!-- @[getAVSessionValidCommands](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionController/entry/src/main/ets/feature/MediaController.ets) --> 

6. 控制媒体会话行为，例如发送用户对当前曲目的操作（播放/暂停/上一首/下一首等）命令。

   <!-- @[commands](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionController/entry/src/main/ets/pages/PresentPage.ets) --> 

7. 媒体会话退出时，媒体会话控制方应及时取消监听，并释放资源。

   <!-- @[listenAVSessionDestroy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionController/entry/src/main/ets/feature/MediaController.ets) -->

   <div class="same-source-code">
   ``` TypeScript
   async listenAVSessionDestroy(): Promise<void> {
     try {
       // 注册会话销毁监听。
       this.currentController?.on('sessionDestroy', () => {
         Log.info(TAG, 'on sessionDestroy: SUCCESS');
         this.currentController?.destroy(() => { // 销毁当前控制器，销毁后当前控制器不可再用。
           Log.info(TAG, 'Succeeded in destroying.');
         });
       });
     } catch (error) {
       if (error) {
         Log.error(TAG, `destroy Error: Code: ${error.code}, message: ${error.message}`);
       }
     }
   }
   
   stopControl() {
     Log.info(TAG, 'stopControl');
     avSession.offSessionCreate();
     avSession.offTopSessionChange();
     Log.info(TAG, 'stopControl done');
   }
   ```

   <p class="same-source-code-link"><a href="https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionController/entry/src/main/ets/feature/MediaController.ets?same_code_link_text=listenAVSessionDestroy" target="_blank" rel="nofollow">MediaController.ets</a></p>

   </div>

