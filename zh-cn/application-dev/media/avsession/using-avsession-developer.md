# 媒体会话提供方
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @liao_qian-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

音视频应用在实现音视频功能的同时，需要作为媒体会话提供方接入媒体会话，在媒体会话控制方（例如播控中心）中展示媒体相关信息，并响应媒体会话控制方下发的播控命令。

## 基本概念

- 媒体会话元数据（AVMetadata）： 用于描述媒体数据相关属性，包含标识当前媒体的ID（assetId），上一首媒体的ID（previousAssetId），下一首媒体的ID（nextAssetId），标题（title），专辑作者（author），专辑名称（album），词作者（writer），媒体时长（duration）等属性。

- 媒体播放状态（AVPlaybackState）：用于描述媒体播放状态的相关属性，包含当前媒体的播放状态（state）、播放位置（position）、播放倍速（speed）、缓冲时间（bufferedTime）、循环模式（loopMode）、是否收藏（isFavorite）、正在播放的媒体Id（activeItemId）、自定义媒体数据（extras）等属性。

## 接口说明

媒体会话提供方使用的关键接口如下表所示。接口返回值有两种返回形式：callback和promise，下表中为callback形式接口，promise和callback只是返回值方式不一样，功能相同。

更多API说明请参考文档：[模块描述](../../reference/apis-avsession-kit/arkts-apis-avsession.md)。

| 接口名 | 说明 | 
| -------- | -------- |
| createAVSession(context: Context, tag: string, type: AVSessionType, callback: AsyncCallback&lt;AVSession&gt;): void<sup>10+<sup> | 创建媒体会话。<br/>一个UIAbility只能存在一个媒体会话，重复创建会失败。 | 
| setAVMetadata(data: AVMetadata, callback: AsyncCallback&lt;void&gt;): void<sup>10+<sup> | 设置媒体会话元数据。 | 
| setAVPlaybackState(state: AVPlaybackState, callback: AsyncCallback&lt;void&gt;): void<sup>10+<sup> | 设置媒体会话播放状态。 | 
| setLaunchAbility(ability: WantAgent, callback: AsyncCallback&lt;void&gt;): void<sup>10+<sup> | 设置启动UIAbility。 | 
| getController(callback: AsyncCallback&lt;AVSessionController&gt;): void<sup>10+<sup> | 获取当前会话自身控制器。 | 
| getOutputDevice(callback: AsyncCallback&lt;OutputDeviceInfo&gt;): void<sup>10+<sup> | 获取播放设备相关信息。 |
| activate(callback: AsyncCallback&lt;void&gt;): void<sup>10+<sup> | 激活媒体会话。 | 
| deactivate(callback: AsyncCallback&lt;void&gt;): void<sup>10+<sup> | 禁用当前会话。 |
| destroy(callback: AsyncCallback&lt;void&gt;): void<sup>10+<sup> | 销毁媒体会话。 | 
| setAVQueueItems(items: Array&lt;AVQueueItem&gt;, callback: AsyncCallback&lt;void&gt;): void <sup>10+<sup> | 设置媒体播放列表。 |
| setAVQueueTitle(title: string, callback: AsyncCallback&lt;void&gt;): void<sup>10+<sup> | 设置媒体播放列表名称。 |
| dispatchSessionEvent(event: string, args: {[key: string]: Object}, callback: AsyncCallback&lt;void&gt;): void<sup>10+<sup> | 设置会话内自定义事件。 |
| setExtras(extras: {[key: string]: Object}, callback: AsyncCallback&lt;void&gt;): void<sup>10+<sup> | 设置键值对形式的自定义媒体数据包。|
| getOutputDeviceSync(): OutputDeviceInfo<sup>10+<sup> | 使用同步方法获取当前输出设备信息。 |

## 开发步骤

音视频应用作为媒体会话提供方接入媒体会话的基本步骤如下所示：

1. 通过AVSessionManager的方法创建并激活媒体会话。

   > **说明：**
   >
   > 以下示例代码仅展示创建AVSession对象的接口调用，应用在真正使用时，需要确保AVSession对象实例在应用后台播放业务活动期间一直存在，避免被系统回收、释放，导致后台发声时被系统管控。

      <!-- @[createAVSession](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/CreateAVSession.ets) -->
      
      ``` TypeScript
      import { avSession as AVSessionManager } from '@kit.AVSessionKit';
      // ...
      
      @Entry
      @Component
      struct Index {
        @State message: string = 'hello world';
        // ...
      
        build() {
          Column() {
            // ...
            Text(this.message)
              .onClick(async () => {
                try {
                  // 开始创建并激活媒体会话。
                  // 创建session。
                  let context = this.getUIContext().getHostContext() as Context;
                  let type: AVSessionManager.AVSessionType = 'audio';
                  let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);
                  await session.activate();
                  console.info(`session create done : sessionId : ${session.sessionId}`);
                  // ...
                } catch (err) {
                  if (err) {
                    console.error(`AVSession create Error: Code: ${err.code}, message: ${err.message}`);
                    // ...
                  }
                }
              })
          }
          .width('100%')
          .height('100%')
        }
      }
      ```

2. 跟随媒体信息的变化，及时设置媒体会话信息。需要设置的媒体会话信息主要包括：
   - 媒体会话元数据AVMetadata。
   - 媒体播放状态AVPlaybackState。

   音视频应用设置的媒体会话信息，会被媒体会话控制方通过AVSessionController相关方法获取后进行显示或处理。
     
      <!-- @[setAVSessionInformation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/SetAVSessionInformation.ets) -->


3. 设置用于被媒体会话控制方拉起的UIAbility。当用户操作媒体会话控制方的界面时，例如点击播控中心的卡片，可以拉起此处配置的UIAbility。

   设置UIAbility时通过WantAgent接口实现，更多关于WantAgent的信息请参考[WantAgent](../../reference/apis-ability-kit/js-apis-app-ability-wantAgent.md)。

      <!-- @[wantAgent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/WantAgent.ets) -->
    
4. 设置一个即时的自定义会话事件，以供媒体控制方接收到事件后进行相应的操作。

   > **说明：**<br>
   > 通过dispatchSessionEvent方法设置的数据不会保存在会话对象或AVSession服务中。
    <!-- @[dispatchSessionEvent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/DispatchSessionEvent.ets) -->

5. 设置与当前会话相关的自定义媒体数据包，以供媒体控制方接收到事件后进行相应的操作。

   > **说明：**<br>
   > 通过setExtras方法设置的数据包会被存储在AVSession服务中，数据的生命周期与会话一致；会话对应的Controller可以使用getExtras来获取该数据。

    <!-- @[setExtras](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/SetExtras.ets) -->
    
6. 注册播控命令事件监听，便于响应用户通过媒体会话控制方，例如播控中心，下发的播控命令。
    
   在Session侧注册的监听分为`固定播控命令`和`高级播控事件`两种。
    
   6.1 固定控制命令的监听 
   > **说明：**
   > 媒体会话提供方在注册相关固定播控命令事件监听时，监听的事件会在媒体会话控制方的getValidCommands()方法中体现，即媒体会话控制方会认为对应的方法有效，进而根据需要触发相应暂不使用时的事件。为了保证媒体会话控制方下发的播控命令可以被正常执行，媒体会话提供方请勿进行无逻辑的空实现监听。

   Session侧的固定播控命令主要包括播放、暂停、上一首、下一首等基础操作命令，详细介绍请参见[AVControlCommand](../../reference/apis-avsession-kit/arkts-apis-avsession-i.md#avcontrolcommand10)。

     
    <!-- @[fixedPlaybackControlCommands](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/FixedPlaybackControlCommands.ets) -->

   6.2 高级播控事件的监听

   Session侧的可以注册的高级播控事件主要包括：

   - skipToQueueItem: 播放列表其中某项被选中的事件。
   - handleKeyEvent: 按键事件。
   - outputDeviceChange: 播放设备变化的事件。
   - commonCommand: 自定义控制命令变化的事件。

    <!-- @[advancedPlayback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/AdvancedPlaybackControlEvents.ets) -->

7. 获取当前媒体会话自身的控制器，与媒体会话对应进行通信交互。
     
      <!-- @[getController](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/GetController.ets) -->

8. 音视频应用在退出，并且不需要继续播放时，及时取消监听以及销毁媒体会话释放资源。

   取消播控命令监听的示例代码如下所示 ：

      <!-- @[off](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/Off.ets) -->

      销毁媒体会话示例代码如下所示：
     
      <!-- @[destroy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/Destroy.ets) -->

## 相关实例

针对媒体会话提供方开发，有以下相关实例可供参考：

- [媒体会话——提供方（ArkTS）（Full SDK）（API10）](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AVSession/MediaProvider)