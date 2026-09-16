# AVSession Provider (ArkTS)
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_7KSyM10J; @devil_red-->
<!--Designer: @gcw_7KSyM10J-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=6db95933f92c36be892f64316b822565946ecf49 translatedAt=2026-09-03T09:03:12.600Z pushedAt=2026-09-03T09:04:52.955Z -->

An audio and video application needs to access the AVSession service as a provider in order to display media information in the controller (for example, Media Controller) and respond to playback control commands delivered by the controller.

## Basic Concepts

- AVMetadata: describes media data related properties, including the ID of the current media asset (`assetId`), the ID of the previous media asset (`previousAssetId`), the ID of the next media asset (`nextAssetId`), title, artist, album author (`author`), album name (`album`), lyricist (`writer`), and media duration (`duration`).

- AVPlaybackState: describes media playback state related properties, including the current media playback state (`state`), playback position (`position`), playback speed (`speed`), buffered time (`bufferedTime`), loop mode (`loopMode`), whether the media is marked as favorite (`isFavorite`), the ID of the media item being played (`activeItemId`), and custom media data (`extras`).

## Available APIs

The table below lists the key APIs used by the provider. The APIs use either a callback or promise to return the result. The APIs listed below use a callback. They provide the same functions as their counterparts that use a promise.

For details about the APIs, see [Module Description](../../reference/apis-avsession-kit/arkts-apis-avsession.md).

| Name | Description | 
| -------- | -------- |
| createAVSession(context: Context, tag: string, type: AVSessionType, callback: AsyncCallback&lt;AVSession&gt;): void<sup>10+</sup> | Creates an AVSession.<br/>A UIAbility can have only one AVSession. Repeated creation fails. | 
| setAVMetadata(data: AVMetadata, callback: AsyncCallback&lt;void&gt;): void<sup>10+</sup> | Sets the metadata of the AVSession. | 
| setAVPlaybackState(state: AVPlaybackState, callback: AsyncCallback&lt;void&gt;): void<sup>10+</sup> | Sets the playback state of the AVSession. | 
| setLaunchAbility(ability: WantAgent, callback: AsyncCallback&lt;void&gt;): void<sup>10+</sup> | Sets the UIAbility to launch. | 
| getController(callback: AsyncCallback&lt;AVSessionController&gt;): void<sup>10+</sup> | Obtains the controller of the current session. | 
| getOutputDevice(callback: AsyncCallback&lt;OutputDeviceInfo&gt;): void<sup>10+</sup> | Obtains information about the output device. |
| activate(callback: AsyncCallback&lt;void&gt;): void<sup>10+</sup> | Activates the AVSession. | 
| deactivate(callback: AsyncCallback&lt;void&gt;): void<sup>10+</sup> | Deactivates the current session. |
| destroy(callback: AsyncCallback&lt;void&gt;): void<sup>10+</sup> | Destroys the AVSession. | 
| setAVQueueItems(items: Array&lt;AVQueueItem&gt;, callback: AsyncCallback&lt;void&gt;): void <sup>10+</sup> | Sets the media playlist. |
| setAVQueueTitle(title: string, callback: AsyncCallback&lt;void&gt;): void<sup>10+</sup> | Sets the name of the media playlist. |
| dispatchSessionEvent(event: string, args: {[key: string]: Object}, callback: AsyncCallback&lt;void&gt;): void<sup>10+</sup> | Sets a custom event within the session. |
| setExtras(extras: {[key: string]: Object}, callback: AsyncCallback&lt;void&gt;): void<sup>10+</sup> | Sets a custom media data packet in key-value pairs.|
| getOutputDeviceSync(): OutputDeviceInfo<sup>10+</sup> | Obtains information about the current output device synchronously. |

## How to Develop

To enable an audio and video application to access the AVSession service as a provider, proceed as follows:

1. Call an API in the **AVSessionManager** class to create and activate an AVSession object.

   > **NOTE**
   >
   > The sample code below demonstrates only the API call for creating an AVSession object. When actually using it, the application must ensure that the AVSession object remains throughout the application's background playback activities. This prevents the system from reclaiming or releasing it, which could lead to playback being controlled by the system.

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
               // Start creating and activating the AVSession.
               // Create a session.
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

2. Set AVSession information, which includes:
   - AVMetadata
   - AVPlaybackState

   The controller will call an API in the **AVSessionController** class to obtain the information and display or process the information.

   <!-- @[setAVSessionInformation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/SetAVSessionInformation.ets) -->

   ``` TypeScript
   import { avSession as AVSessionManager } from '@kit.AVSessionKit';
   import { BusinessError } from '@kit.BasicServicesKit';
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
             let context = this.getUIContext().getHostContext() as Context;
             // Assume that a session has been created. For details about how to create a session, see the previous example.
             let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', 'audio');
             // Player logic... triggers changes to the media information and playback state.
             // Set the required media information.
             let metadata: AVSessionManager.AVMetadata = {
               assetId: '0', // Specified by the application to identify the media in the application media library.
               title: 'TITLE',
               mediaImage: 'IMAGE',
               artist: 'ARTIST'
             };
             session.setAVMetadata(metadata).then(() => {
               console.info(`SetAVMetadata successfully`);
               // ...
             }).catch((err: BusinessError) => {
               console.error(`Failed to set AVMetadata. Code: ${err.code}, message: ${err.message}`);
               // ...
             });
             // Simply set a playback state - paused and not favorited.
             let playbackState: AVSessionManager.AVPlaybackState = {
               state: AVSessionManager.PlaybackState.PLAYBACK_STATE_PAUSE,
               isFavorite: false
             };
             session.setAVPlaybackState(playbackState, (err) => {
               if (err) {
                 console.error(`Failed to set AVPlaybackState. Code: ${err.code}, message: ${err.message}`);
                 // ...
               } else {
                 console.info(`SetAVPlaybackState successfully`);
                 // ...
               }
             });
             // Set a playlist.
             let queueItemDescription1: AVSessionManager.AVMediaDescription = {
               assetId: '001',
               title: 'music_name',
               subtitle: 'music_sub_name',
               description: 'music_description',
               mediaImage: 'PIXELMAP_OBJECT',
               extras: { 'extras': 'any' }
             };
             let queueItem1: AVSessionManager.AVQueueItem = {
               itemId: 1,
               description: queueItemDescription1
             };
             let queueItemDescription2: AVSessionManager.AVMediaDescription = {
               assetId: '002',
               title: 'music_name',
               subtitle: 'music_sub_name',
               description: 'music_description',
               mediaImage: 'PIXELMAP_OBJECT',
               extras: { 'extras': 'any' }
             };
             let queueItem2: AVSessionManager.AVQueueItem = {
               itemId: 2,
               description: queueItemDescription2
             };
             let queueItemsArray = [queueItem1, queueItem2];
             session.setAVQueueItems(queueItemsArray).then(() => {
               console.info(`SetAVQueueItems successfully`);
               // ...
             }).catch((err: BusinessError) => {
               console.error(`Failed to set AVQueueItem, error code: ${err.code}, error message: ${err.message}`);
               // ...
             });
             // Set the name of the media playlist.
             let queueTitle = 'QUEUE_TITLE';
             session.setAVQueueTitle(queueTitle).then(() => {
               console.info(`SetAVQueueTitle successfully`);
               // ...
             }).catch((err: BusinessError) => {
               console.error(`Failed to set AVQueueTitle, error code: ${err.code}, error message: ${err.message}`);
               // ...
             });
             // ...
           })
       }
       .width('100%')
       .height('100%')
     }
   }
   ```


3. Set the UIAbility to be started by the controller. The UIAbility configured here is started when a user operates the UI of the controller, for example, clicking a widget in Media Controller.

   The UIAbility is set through the **WantAgent** API. For details, see [WantAgent](../../reference/apis-ability-kit/js-apis-app-ability-wantAgent.md).

   <!-- @[wantAgent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/WantAgent.ets) -->

   ``` TypeScript
   import { avSession as AVSessionManager } from '@kit.AVSessionKit';
   import { wantAgent } from '@kit.AbilityKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   
   @Entry
   @Component
   struct Index {
     @State message: string = 'hello world';
   
     build() {
       Column() {
         Text(this.message)
           .onClick(async () => {
             let context = this.getUIContext().getHostContext() as Context;
             let type: AVSessionManager.AVSessionType = 'audio';
             // Assume that a session has been created. For details about how to create a session, see the previous example.
             let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);
             let wantAgentInfo: wantAgent.WantAgentInfo = {
               wants: [
                 {
                   bundleName: 'com.example.musicdemo',
                   abilityName: 'MainAbility'
                 }
               ],
               // OperationType.START_ABILITIES
               operationType: 2,
               requestCode: 0,
               wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
             }
             wantAgent.getWantAgent(wantAgentInfo).then((agent) => {
               session.setLaunchAbility(agent);
             }).catch((err: BusinessError) => {
               console.error(`Failed to getWantAgent. Code: ${err.code}, message: ${err.message}`);
             })
             // ...
           })
       }
       .width('100%')
       .height('100%')
     }
   }
   ```

4. Send an immediate custom session event so that the controller performs a corresponding operation after receiving the event.

   > **NOTE**<br>
   > The data sent via the **dispatchSessionEvent** method is not saved in the session object or the AVSession service.

   <!-- @[dispatchSessionEvent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/DispatchSessionEvent.ets) -->

   ``` TypeScript
   import { avSession as AVSessionManager } from '@kit.AVSessionKit';
   import { BusinessError } from '@kit.BasicServicesKit';
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
             let context = this.getUIContext().getHostContext() as Context;
             // Assume that a session has been created. For details about how to create a session, see the previous example.
             let type: AVSessionManager.AVSessionType = 'audio';
             let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);
             let eventName = 'dynamic_lyric';
             await session.dispatchSessionEvent(eventName, { lyric: 'This is my lyric' }).then(() => {
               console.info(`Dispatch session event successfully`);
               // ...
             }).catch((err: BusinessError) => {
               console.error(`Failed to dispatch session event. Code: ${err.code}, message: ${err.message}`);
               // ...
             })
             // ...
           })
       }
       .width('100%')
       .height('100%')
     }
   }
   ```

5. Set a custom media packet so that the controller can perform corresponding operations after receiving the event.

   > **NOTE**<br>
   > The data set by using **setExtras** is stored in the AVSession service. The data lifecycle is the same as that of the AVSession object, and the controller corresponding to the object can use **getExtras** to obtain the data.

   <!-- @[setExtras](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/SetExtras.ets) -->

   ``` TypeScript
   import { avSession as AVSessionManager } from '@kit.AVSessionKit';
   import { BusinessError } from '@kit.BasicServicesKit';
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
             let context = this.getUIContext().getHostContext() as Context;
             // Assume that a session has been created. For details about how to create a session, see the previous example.
             let type: AVSessionManager.AVSessionType = 'audio';
             let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);
             await session.setExtras({ extra: 'This is my custom media packet' }).then(() => {
               console.info(`Set extras successfully`);
               // ...
             }).catch((err: BusinessError) => {
               console.error(`Failed to set extras. Code: ${err.code}, message: ${err.message}`);
               // ...
             })
             // ...
           })
       }
       .width('100%')
       .height('100%')
     }
   }
   ```

6. Listen for playback control commands or events delivered by the controller, for example, Media Controller.

   Both fixed playback control commands and advanced playback control events can be listened for.

   6.1 Listen for fixed playback control commands.
   > **NOTE**
   >
   > After the provider registers a listener for fixed playback control commands, the commands will be reflected in **getValidCommands()** of the controller. In other words, the controller determines that the command is valid and triggers the corresponding event as required. To ensure that the playback control commands delivered by the controller can be executed normally, the provider should not use a null implementation for listening.

   Fixed playback control commands on the session side include basic operation commands such as play, pause, previous, and next. For details, see [AVControlCommand](../../reference/apis-avsession-kit/arkts-apis-avsession-i.md#avcontrolcommand10).

   Control scenarios include tapping the Media Controller, removing notifications from the Media Controller, wearing Bluetooth earphones, pressing buttons on Bluetooth or wired earphones, and using voice assistant controls.

   <!-- @[fixedPlaybackControlCommands](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/FixedPlaybackControlCommands.ets) -->

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
             let context = this.getUIContext().getHostContext() as Context;
             // Assume that a session has been created. For details about how to create a session, see the previous example.
             let type: AVSessionManager.AVSessionType = 'audio';
             let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);
             // ...
             // Generally, perform the corresponding logic on the player in the listener.
             // Do not forget to synchronize the playback information via the set API after processing. For details, see the example above.
             session.on('play', () => {
               console.info(`on play , do play task`);
               // ...
               // If the command is not supported yet, do not register it. If it is registered but not used temporarily, cancel the listener via session.off('play').
               // After processing, use SetAVPlaybackState to report the playback state.
             });
             session.on('pause', () => {
               console.info(`on pause , do pause task`);
               // ...
               // If the command is not supported yet, do not register it. If it is registered but not used temporarily, cancel the listener via session.off('pause').
               // After processing, use SetAVPlaybackState to report the playback state.
             });
             session.on('stop', () => {
               console.info(`on stop , do stop task`);
               // ...
               // If this command is not supported yet, do not register it; or if it is registered but not used for the time being, unregister it via session.off('stop').
               // After processing, use SetAVPlaybackState to report the playback state.
             });
             session.on('playNext', () => {
               console.info(`on playNext , do playNext task`);
               // ...
               // If this command is not supported yet, do not register it; or if it is registered but not used for the time being, unregister it via session.off('playNext').
               // After processing, use SetAVPlaybackState to report the playback state and use SetAVMetadata to report the media information.
             });
             session.on('playPrevious', () => {
               console.info(`on playPrevious , do playPrevious task`);
               // ...
               // If this command is not supported yet, do not register it; or if it is registered but not used for the time being, unregister it via session.off('playPrevious').
               // After processing, use SetAVPlaybackState to report the playback state and use SetAVMetadata to report the media information.
             });
             session.on('fastForward', () => {
               console.info(`on fastForward , do fastForward task`);
               // ...
               // If this command is not supported yet, do not register it; or if it is registered but not used for the time being, unregister it via session.off('fastForward').
               // After processing, use SetAVPlaybackState to report the playback state and the playback position.
             });
             session.on('rewind', () => {
               console.info(`on rewind , do rewind task`);
               // ...
               // If this command is not supported yet, do not register it; or if it is registered but not used for the time being, unregister it via session.off('rewind').
               // After processing, use SetAVPlaybackState to report the playback state and the playback position.
             });
             session.on('seek', (time: number) => {
               console.info(`on seek , the time is ${time}`);
               // ...
               // If this command is not supported yet, do not register it. If it is registered but not in use, cancel the listener via session.off('seek').
               // After processing, use SetAVPlaybackState to report the playback state and position.
             });
             session.on('setSpeed', (speed) => {
               console.info(`on setSpeed , the speed is ${speed}`);
               // ...
               // Implement the specific function.
             });
             session.on('setLoopMode', (mode) => {
               console.info(`on setLoopMode , the loop mode is ${mode}`);
               // ...
               // If this command is not supported yet, do not register it. If it is registered but not in use, cancel the listener via session.off('setLoopMode').
               // The application defines the next mode. After processing, use SetAVPlaybackState to report the switched LoopMode.
             });
             session.on('toggleFavorite', (assetId) => {
               console.info(`on toggleFavorite , the target asset Id is ${assetId}`);
               // ...
               // If this command is not supported yet, do not register it. If it is registered but not in use, cancel the listener via session.off('toggleFavorite').
               // After processing, use SetAVPlaybackState to report the favorite result isFavorite.
             });
             // ...
           })
       }
       .width('100%')
       .height('100%')
     }
   }
   ```

   6.2 Listen for advanced playback control events.

   The following advanced playback control events can be listened for:

   - **skipToQueueItem**: triggered when an item in the playlist is selected.
   - **handleKeyEvent**: triggered when a key is pressed.
   - **outputDeviceChange**: triggered when the output device changes.
   - **commonCommand**: triggered when a custom playback control command changes.

   <!-- @[advancedPlayback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/AdvancedPlaybackControlEvents.ets) -->

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
               let context = this.getUIContext().getHostContext() as Context;
               // Assume that a session has been created. For details about how to create a session, see the previous example.
               let type: AVSessionManager.AVSessionType = 'audio';
               let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);
               // ...
               // Generally, the listener performs the corresponding logic on the player.
               // Do not forget to synchronize the playback-related information via the set API after processing. See the example above.
               session.on('skipToQueueItem', (itemId) => {
                 console.info(`on skipToQueueItem , do skip task`);
                 // ...
                 // Implement the specific function.
               });
               session.on('handleKeyEvent', (event) => {
                 console.info(`on handleKeyEvent , the event is ${JSON.stringify(event)}`);
                 // ...
                 // Implement the specific function.
               });
               session.on('outputDeviceChange', (state: AVSessionManager.ConnectionState, device: AVSessionManager.OutputDeviceInfo) => {
                 console.info(`on outputDeviceChange , the state is ${JSON.stringify(state)} and device info is ${JSON.stringify(device)}`);
                 // ...
                 // Implement the specific function.
               });
               session.on('commonCommand', (commandString, args) => {
                 console.info(`on commonCommand , command is ${commandString}, args are ${JSON.stringify(args)}`);
                 // ...
                 // Implement the specific function.
               });
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

7. Obtain an AVSessionController object for this AVSession object for interaction.

   <!-- @[getController](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/GetController.ets) -->

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
               let context = this.getUIContext().getHostContext() as Context;
               // Assume that a session has been created. For details about how to create a session, see the previous example.
               let type: AVSessionManager.AVSessionType = 'audio';
               let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);
   
               // Obtain a controller object from the existing session.
               let controller = await session.getController();
               // ...
   
               // The controller can perform basic communication and interaction with the original session object, for example, sending playback commands.
               let avCommand: AVSessionManager.AVControlCommand = { command: 'play' };
               controller.sendControlCommand(avCommand);
   
               // Alternatively, listen for state changes.
               controller.on('playbackStateChange', 'all', (state) => {
   
                 // do some things.
               });
               // ...
             } catch (err) {
               if (err) {
                 console.error(`AVSession create or getController Error: Code: ${err.code}, message: ${err.message}`);
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

8. When the audio and video application exits and does not need to continue playback, cancel the listener and destroy the AVSession object.

   The code snippet below is used for canceling the listener for playback control commands:

   <!-- @[off](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/Off.ets) -->

   ``` TypeScript
   import { avSession as AVSessionManager } from '@kit.AVSessionKit';
   
   @Entry
   @Component
   struct Index {
     @State message: string = 'hello world';
   
     build() {
       Column() {
         Text(this.message)
           .onClick(async () => {
             let context = this.getUIContext().getHostContext() as Context;
             // Assume that a session has been created. For details about how to create a session, see the previous example.
             let type: AVSessionManager.AVSessionType = 'audio';
             let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);
   
             // Cancel the related listeners of the specified session.
             session.off('play');
             session.off('pause');
             session.off('stop');
             session.off('playNext');
             session.off('playPrevious');
             session.off('skipToQueueItem');
             session.off('handleKeyEvent');
             session.off('outputDeviceChange');
             session.off('commonCommand');
             // ...
           })
       }
       .width('100%')
       .height('100%')
     }
   }
   ```

   The code snippet below is used for destroying the AVSession object:

   <!-- @[destroy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/Destroy.ets) -->

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
             let context = this.getUIContext().getHostContext() as Context;
             // Assume that a session has been created. For details about how to create a session, see the previous example.
             let type: AVSessionManager.AVSessionType = 'audio';
             let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);
             // Destroy the created session proactively.
             session.destroy((err) => {
               if (err) {
                 console.error(`Failed to destroy session. Code: ${err.code}, message: ${err.message}`);
                 // ...
               } else {
                 console.info(`Destroy : SUCCESS `);
                 // ...
               }
             });
           })
       }
       .width('100%')
       .height('100%')
     }
   }
   ```

## Samples

The following sample is provided to help you better understand how to develop the provider:

- [AVSession - Provider (ArkTS, Full SDK, API version 10)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AVSession/MediaProvider)