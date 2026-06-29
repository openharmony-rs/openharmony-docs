# Interface (AVSessionController)
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

AVSessionController控制器可查看会话ID，并可完成对会话发送命令及事件，获取会话元数据，播放状态信息等操作。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 10开始支持。

## 导入模块

```ts
import { avSession } from '@kit.AVSessionKit';
```

## 属性

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

| 名称      | 类型   | 只读 | 可选 | 说明                                    |
| :-------- | :----- | :--- | :--- | :-------------------------------------- |
| sessionId<sup>10+</sup> | string | 是   | 否   | AVSessionController对象唯一的会话标识。 |

**示例：**

```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  private tag: string = "createNewSession";
  private sessionId: string = "";
  private AVSessionController?: avSession.AVSessionController;
  private currentAVSession?: avSession.AVSession;
  context = this.getUIContext();

  aboutToAppear(): void {

    avSession.createAVSession(this.getUIContext().getHostContext(), this.tag, "audio").then(async (data: avSession.AVSession) => {
      this.currentAVSession = data;
      this.sessionId = this.currentAVSession.sessionId;
      this.AVSessionController = await this.currentAVSession.getController();
      console.info(`Succeeded in creating AV session, sessionId: ${this.sessionId}`);
    });
  }

  build() {
    Column() {
      Text('AVSession Demo')
        .fontSize(20)
        .margin(10)
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

## getAVPlaybackState<sup>10+</sup>

getAVPlaybackState(callback: AsyncCallback\<AVPlaybackState>): void

获取当前的远端播放状态。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                                                        | 必填 | 说明                                                         |
| --------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback  | AsyncCallback<[AVPlaybackState](arkts-apis-avsession-i.md#avplaybackstate10)\> | 是   | 回调函数，返回远端播放状态。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.getAVPlaybackState((state: avSession.AVPlaybackState) => {
  console.info('Succeeded in getting AV playback state.');
});
```

## getAVPlaybackState<sup>10+</sup>

getAVPlaybackState(): Promise\<AVPlaybackState>

获取当前的远端播放状态。使用Promise异步回调。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                                        | 说明                                                         |
| --------- | ------------------------------------------------------------ |
| Promise<[AVPlaybackState](arkts-apis-avsession-i.md#avplaybackstate10)\>  | Promise对象。返回远端播放状态。  |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.getAVPlaybackState().then((state: avSession.AVPlaybackState) => {
  console.info('Succeeded in getting AV playback state.');
});
```

## getAVMetadata<sup>10+</sup>

getAVMetadata(): Promise\<AVMetadata>

获取会话元数据。使用Promise异步回调。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                | 说明                          |
| ----------------------------------- | ----------------------------- |
| Promise<[AVMetadata](arkts-apis-avsession-i.md#avmetadata10)\> | Promise对象，返回会话元数据。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.getAVMetadata().then((metadata: avSession.AVMetadata) => {
  console.info(`Succeeded in getting AV metadata, assetId: ${metadata.assetId}`);
});
```

## getAVMetadata<sup>10+</sup>

getAVMetadata(callback: AsyncCallback\<AVMetadata>): void

获取会话元数据。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                      | 必填 | 说明                       |
| -------- | ----------------------------------------- | ---- | -------------------------- |
| callback | AsyncCallback<[AVMetadata](arkts-apis-avsession-i.md#avmetadata10)\> | 是   | 回调函数，返回会话元数据。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.getAVMetadata((metadata: avSession.AVMetadata) => {
  console.info(`Succeeded in getting AV metadata, assetId: ${metadata.assetId}`);
});
```

## getAVQueueTitle<sup>10+</sup>

getAVQueueTitle(): Promise\<string>

获取当前会话播放列表的名称。使用Promise异步回调。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型             | 说明                           |
| ---------------- | ----------------------------- |
| Promise<string\> | Promise对象。返回播放列表名称。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.getAVQueueTitle().then((title: string) => {
  console.info(`Succeeded in getting AV queue title: ${title}`);
});
```

## getAVQueueTitle<sup>10+</sup>

getAVQueueTitle(callback: AsyncCallback\<string>): void

获取当前播放列表的名称。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                    | 必填 | 说明                      |
| -------- | ---------------------- | ---- | ------------------------- |
| callback | AsyncCallback<string\> | 是   | 回调函数，返回播放列表名称。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.getAVQueueTitle((title: string) => {
  console.info(`Succeeded in getting AV queue title: ${title}`);
});
```

## getAVQueueItems<sup>10+</sup>

getAVQueueItems(): Promise\<Array\<AVQueueItem>>

获取当前会话播放列表相关信息。使用Promise异步回调。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                          | 说明                           |
| --------------------------------------------- | ----------------------------- |
| Promise<Array<[AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10)\>\> | Promise对象。返回播放列表队列。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.getAVQueueItems().then((items: avSession.AVQueueItem[]) => {
  console.info(`Succeeded in getting AV queue items, length: ${items.length}`);
});
```

## getAVQueueItems<sup>10+</sup>

getAVQueueItems(callback: AsyncCallback\<Array\<AVQueueItem>>): void

获取当前播放列表相关信息。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                      |
| -------- | --------------------------------------------------- | ---- | ------------------------- |
| callback | AsyncCallback<Array<[AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10)\>\> | 是   | 回调函数，返回播放列表队列。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.getAVQueueItems((items: avSession.AVQueueItem[]) => {
  console.info(`Succeeded in getting AV queue items, length: ${items.length}`);
});
```

## skipToQueueItem<sup>10+</sup>

ArkTS-Dyn: skipToQueueItem(itemId: number): Promise\<void>

ArkTS-Sta: skipToQueueItem(itemId: int): Promise\<void>

设置指定播放列表单项的ID，发送给session端处理，session端可以选择对这个单项歌曲进行播放。使用Promise异步回调。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型    | 必填 | 说明                                        |
| ------ | ------- | ---- | ------------------------------------------- |
| itemId | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 播放列表单项的ID值，用以表示选中的播放列表单项。 |

**返回值：**

| 类型           | 说明                                                             |
| -------------- | --------------------------------------------------------------- |
| Promise\<void> | Promise对象。当播放列表单项ID设置成功，无返回结果，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
let queueItemId = 0;
avsessionController.skipToQueueItem(queueItemId).then(() => {
  console.info('Succeeded in skipping to queue item.');
});
```

## skipToQueueItem<sup>10+</sup>

ArkTS-Dyn: skipToQueueItem(itemId: number, callback: AsyncCallback\<void>): void

ArkTS-Sta: skipToQueueItem(itemId: int, callback: AsyncCallback\<void>): void

设置指定播放列表单项的ID，发送给session端处理，session端可以选择对这个单项歌曲进行播放。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                  | 必填 | 说明                                                        |
| -------- | --------------------- | ---- | ----------------------------------------------------------- |
| itemId   | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 播放列表单项的ID值，用以表示选中的播放列表单项。                |
| callback | AsyncCallback\<void>  | 是   | 回调函数。<br>ArkTS-Dyn：当播放状态设置成功，err为undefined，否则返回错误对象。<br>ArkTS-Sta：当播放状态设置成功，err为null，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
let queueItemId = 0;
avsessionController.skipToQueueItem(queueItemId, () => {
  console.info('Succeeded in skipping to queue item.');
});
```

## getOutputDevice<sup>10+</sup>

getOutputDevice(): Promise\<OutputDeviceInfo>

获取播放设备信息。使用Promise异步回调。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                            | 说明                              |
| ----------------------------------------------- | --------------------------------- |
| Promise<[OutputDeviceInfo](arkts-apis-avsession-i.md#outputdeviceinfo10)\> | Promise对象，返回播放设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 600101  | Session service exception. |
| 600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.getOutputDevice().then((deviceInfo: avSession.OutputDeviceInfo) => {
  console.info('Succeeded in getting output device.');
});
```

## getOutputDevice<sup>10+</sup>

getOutputDevice(callback: AsyncCallback\<OutputDeviceInfo>): void

获取播放设备信息。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                  | 必填 | 说明                           |
| -------- | ----------------------------------------------------- | ---- | ------------------------------ |
| callback | AsyncCallback<[OutputDeviceInfo](arkts-apis-avsession-i.md#outputdeviceinfo10)\> | 是   | 回调函数，返回播放设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 600101  | Session service exception. |
| 600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.getOutputDevice((deviceInfo: avSession.OutputDeviceInfo) => {
  console.info('Succeeded in getting output device.');
});
```

## sendAVKeyEvent<sup>10+</sup>

sendAVKeyEvent(event: KeyEvent): Promise\<void>

发送按键事件到控制器对应的会话。使用Promise异步回调。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                                         | 必填 | 说明       |
| ------ | ------------------------------------------------------------ | ---- | ---------- |
| event  | [KeyEvent](../apis-input-kit/js-apis-keyevent.md) | 是   | 按键事件。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 600101  | Session service exception. |
| 600102  | The session does not exist. |
| 600103  | The session controller does not exist. |
| 600105  | Invalid session command. |
| 600106  | The session is not activated. |

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<void> | Promise对象。当事件发送成功，无返回结果，否则返回错误对象。 |

**示例：**

```ts
import { Key, KeyEvent } from '@kit.InputKit';

let keyItem: Key = {code:0x49, pressedTime:2, deviceId:0};
let event:KeyEvent = {id:1, deviceId:0, actionTime:1, screenId:1, windowId:1, action:2, key:keyItem, unicodeChar:0, keys:[keyItem], ctrlKey:false, altKey:false, shiftKey:false, logoKey:false, fnKey:false, capsLock:false, numLock:false, scrollLock:false};


avsessionController.sendAVKeyEvent(event).then(() => {
  console.info('Succeeded in sending AV key event.');
});
```

## sendAVKeyEvent<sup>10+</sup>

sendAVKeyEvent(event: KeyEvent, callback: AsyncCallback\<void>): void

发送按键事件到会话。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明       |
| -------- | ------------------------------------------------------------ | ---- | ---------- |
| event    | [KeyEvent](../apis-input-kit/js-apis-keyevent.md) | 是   | 按键事件。 |
| callback | AsyncCallback\<void>                                         | 是   | 回调函数。<br>ArkTS-Dyn：当事件发送成功，err为undefined，否则返回错误对象。<br>ArkTS-Sta：当事件发送成功，err为null，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 600101  | Session service exception. |
| 600102  | The session does not exist. |
| 600103  | The session controller does not exist. |
| 600105  | Invalid session command. |
| 600106  | The session is not activated. |

**示例：**

```ts
import { Key, KeyEvent } from '@kit.InputKit';

let keyItem: Key = {code:0x49, pressedTime:2, deviceId:0};
let event:KeyEvent = {id:1, deviceId:0, actionTime:1, screenId:1, windowId:1, action:2, key:keyItem, unicodeChar:0, keys:[keyItem], ctrlKey:false, altKey:false, shiftKey:false, logoKey:false, fnKey:false, capsLock:false, numLock:false, scrollLock:false};
avsessionController.sendAVKeyEvent(event, () => {
  console.info('Succeeded in sending AV key event.');
});
```

## getLaunchAbility<sup>10+</sup>

getLaunchAbility(): Promise\<WantAgent>

获取应用在会话中保存的WantAgent对象。使用Promise异步回调。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                                    | 说明                                                         |
| ------------------------------------------------------- | ------------------------------------------------------------ |
| Promise<[WantAgent](../apis-ability-kit/js-apis-app-ability-wantAgent.md)\> | Promise对象，返回在[setLaunchAbility](arkts-apis-avsession-AVSession.md#setlaunchability10)保存的对象，包括应用的相关属性信息，如bundleName，abilityName，deviceId等。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.getLaunchAbility().then((agent: object) => {
  console.info(`Succeeded in getting launch ability: ${agent}`);
});
```

## getLaunchAbility<sup>10+</sup>

getLaunchAbility(callback: AsyncCallback\<WantAgent>): void

获取应用在会话中保存的WantAgent对象。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback<[WantAgent](../apis-ability-kit/js-apis-app-ability-wantAgent.md)\> | 是   | 回调函数。返回在[setLaunchAbility](arkts-apis-avsession-AVSession.md#setlaunchability10)保存的对象，包括应用的相关属性信息，如bundleName，abilityName，deviceId等。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.getLaunchAbility((agent: object) => {
  console.info(`Succeeded in getting launch ability: ${agent}`);
});
```

## getRealPlaybackPositionSync<sup>10+</sup>

ArkTS-Dyn: getRealPlaybackPositionSync(): number

ArkTS-Sta: getRealPlaybackPositionSync(): long

使用同步方法获取当前播放位置。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                 | 说明               |
| ------------------------------------ | ------------------ |
| ArkTS-Dyn: number<br>ArkTS-Sta: long | 时间节点，毫秒数。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

ArkTS-Dyn示例：

```ts
let time: number = avsessionController.getRealPlaybackPositionSync();
```

ArkTS-Sta示例：

```ts
let time: long = avsessionController.getRealPlaybackPositionSync();
```

## isActive<sup>10+</sup>

isActive(): Promise\<boolean>

获取会话是否被激活。使用Promise异步回调。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型              | 说明                                                         |
| ----------------- | ------------------------------------------------------------ |
| Promise<boolean\> | Promise对象，返回会话是否为激活状态，true表示被激活，false表示禁用。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.isActive().then((isActive: boolean) => {
  console.info(`Succeeded in checking active state: ${isActive}`);
});
```

## isActive<sup>10+</sup>

isActive(callback: AsyncCallback\<boolean>): void

判断会话是否被激活。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback<boolean\> | 是   | 回调函数。返回会话是否为激活状态，true表示被激活，false表示禁用。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.isActive((isActive: boolean) => {
  console.info(`Succeeded in checking active state: ${isActive}`);
});
```

## destroy<sup>10+</sup>

destroy(): Promise\<void>

销毁当前控制器，销毁后当前控制器不可再用。使用Promise异步回调。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<void> | Promise对象。当控制器销毁成功，无返回结果，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.destroy().then(() => {
  console.info('Succeeded in destroying.');
});
```

## destroy<sup>10+</sup>

destroy(callback: AsyncCallback\<void>): void

销毁当前控制器，销毁后当前控制器不可再用。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                 | 必填 | 说明       |
| -------- | -------------------- | ---- | ---------- |
| callback | AsyncCallback\<void> | 是   | 回调函数。<br>ArkTS-Dyn：当控制器销毁成功，err为undefined，否则返回错误对象。<br>ArkTS-Sta：当控制器销毁成功，err为null，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.destroy(() => {
  console.info('Succeeded in destroying.');
});
```

## getValidCommands<sup>10+</sup>

getValidCommands(): Promise\<Array\<AVControlCommandType>>

获取会话支持的有效命令。使用Promise异步回调。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                                         | 说明                              |
| ------------------------------------------------------------ | --------------------------------- |
| Promise<Array<[AVControlCommandType](arkts-apis-avsession-t.md#avcontrolcommandtype10)\>\> | Promise对象。返回有效命令的集合。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.getValidCommands().then((validCommands: avSession.AVControlCommandType[]) => {
  console.info(`Succeeded in getting valid commands, size: ${validCommands.length}`);
});
```

## getValidCommands<sup>10+</sup>

getValidCommands(callback: AsyncCallback\<Array\<AVControlCommandType>>): void

获取会话支持的有效命令。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                           |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------ |
| callback | AsyncCallback\<Array\<[AVControlCommandType](arkts-apis-avsession-t.md#avcontrolcommandtype10)\>\> | 是   | 回调函数，返回有效命令的集合。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.getValidCommands((validCommands: avSession.AVControlCommandType[]) => {
  console.info(`Succeeded in getting valid commands, size: ${validCommands.length}`);
});
```

## sendControlCommand<sup>10+</sup>

sendControlCommand(command: AVControlCommand): Promise\<void>

通过控制器发送命令到其对应的会话。使用Promise异步回调。

> **说明：**
>
> 媒体控制方在使用sendControlCommand命令前，需要确保控制对应的媒体会话注册了对应的监听，注册媒体会话相关监听的方法请参见接口[on('play')](arkts-apis-avsession-AVSession.md#onplay10)、[on('pause')](arkts-apis-avsession-AVSession.md#onpause10)等。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                                  | 必填 | 说明                           |
| ------- | ------------------------------------- | ---- | ------------------------------ |
| command | [AVControlCommand](arkts-apis-avsession-i.md#avcontrolcommand10) | 是   | 会话的相关命令和命令相关参数。 |

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<void> | Promise对象。当命令发送成功，无返回结果，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |
| 6600105  | Invalid session command. |
| 6600106  | The session is not activated. |
| 6600107  | Too many commands or events. |

**示例：**

```ts
let avCommand: avSession.AVControlCommand = {command:'play'};
avsessionController.sendControlCommand(avCommand).then(() => {
  console.info('Succeeded in sending control command.');
});
```

## sendControlCommand<sup>10+</sup>

sendControlCommand(command: AVControlCommand, callback: AsyncCallback\<void>): void

通过会话控制器发送命令到其对应的会话。使用callback异步回调。

> **说明：**
>
> 媒体控制方在使用sendControlCommand命令前，需要确保控制对应的媒体会话注册了对应的监听，注册媒体会话相关监听的方法请参见接口[on('play')](arkts-apis-avsession-AVSession.md#onplay10)、[on('pause')](arkts-apis-avsession-AVSession.md#onpause10)等。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                  | 必填 | 说明                           |
| -------- | ------------------------------------- | ---- | ------------------------------ |
| command  | [AVControlCommand](arkts-apis-avsession-i.md#avcontrolcommand10) | 是   | 会话的相关命令和命令相关参数。 |
| callback | AsyncCallback\<void>                                         | 是   | 回调函数。<br>ArkTS-Dyn：当命令发送成功，err为undefined，否则返回错误对象。<br>ArkTS-Sta：当命令发送成功，err为null，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist.     |
| 6600103  | The session controller does not exist.   |
| 6600105  | Invalid session command. |
| 6600106  | The session is not activated.                |
| 6600107  | Too many commands or events. |

**示例：**

```ts
let avCommand: avSession.AVControlCommand = {command:'play'};
avsessionController.sendControlCommand(avCommand, () => {
  console.info('Succeeded in sending control command.');
});
```

## sendCommonCommand<sup>10+</sup>

ArkTS-Dyn: sendCommonCommand(command: string, args: {[key: string]: Object}): Promise\<void>

ArkTS-Sta: sendCommonCommand(command: string, args: Record<string, Object>): Promise\<void>

通过会话控制器发送自定义控制命令到其对应的会话。使用Promise异步回调。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                                  | 必填 | 说明                           |
| ------- | ------------------------------------- | ---- | ------------------------------ |
| command | string | 是   | 需要设置的自定义控制命令的名称。 |
| args | ArkTS-Dyn: {[key: string]: Object}<br>ArkTS-Sta: Record<string, Object> | 是   | 需要传递的控制命令键值对。 |

> **说明：**
>
> 参数args支持的数据类型有：字符串、数字、布尔、对象、数组和文件描述符等，详细介绍请参见[@ohos.app.ability.Want (Want)](../apis-ability-kit/js-apis-app-ability-want.md)。
**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<void> | Promise对象。无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 401 | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed.<br>**ArkTS模式：** 该错误码仅适用于ArkTS-Dyn。 |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |
| 6600105  | Invalid session command. |
| 6600106  | The session is not activated. |
| 6600107  | Too many commands or events. |

**示例：**

```ts
import { avSession } from '@kit.AVSessionKit';

let tag: string = "createNewSession";
let sessionId: string = "";
let controller:avSession.AVSessionController | undefined = undefined;
avSession.createAVSession(context, tag, "audio").then(async (data:avSession.AVSession)=> {
  currentAVSession = data;
  sessionId = currentAVSession.sessionId;
  controller = await currentAVSession.getController();
  console.info(`Succeeded in creating AV session, sessionId: ${sessionId}`);
});
let commandName = "my_command";
if (controller !== undefined) {
  (controller as avSession.AVSessionController).sendCommonCommand(commandName, {command : "This is my command"}).then(() => {
    console.info('Succeeded in sending common command.');
  })
}
```

## sendCommonCommand<sup>10+</sup>

ArkTS-Dyn: sendCommonCommand(command: string, args: {[key: string]: Object}, callback: AsyncCallback\<void>): void

ArkTS-Sta: sendCommonCommand(command: string, args: Record\<string, Object>, callback: AsyncCallback\<void>): void

通过会话控制器发送自定义命令到其对应的会话。使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                                  | 必填 | 说明                           |
| ------- | ------------------------------------- | ---- | ------------------------------ |
| command | string | 是   | 需要设置的自定义控制命令的名称。 |
| args | ArkTS-Dyn: {[key: string]: Object}<br>ArkTS-Sta: Record<string, Object> | 是   | 需要传递的控制命令键值对。 |
| callback | AsyncCallback\<void>                  | 是   | 回调函数。<br>ArkTS-Dyn：当命令发送成功，err为undefined，否则返回错误对象。<br>ArkTS-Sta：当命令发送成功，err为null，否则返回错误对象。 |

> **说明：**
>
> 参数args支持的数据类型有：字符串、数字、布尔、对象、数组和文件描述符等，详细介绍请参见[@ohos.app.ability.Want (Want)](../apis-ability-kit/js-apis-app-ability-want.md)。

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------- |
| 401 | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed.<br>**ArkTS模式：** 该错误码仅适用于ArkTS-Dyn。 |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist.     |
| 6600103  | The session controller does not exist.   |
| 6600105  | Invalid session command. |
| 6600106  | The session is not activated. |
| 6600107  | Too many commands or events. |

**示例：**

```ts
import { avSession } from '@kit.AVSessionKit';
          
let tag: string = "createNewSession";
let sessionId: string = "";
let controller:avSession.AVSessionController | undefined = undefined;
avSession.createAVSession(context, tag, "audio").then(async (data:avSession.AVSession)=> {
  currentAVSession = data;
  sessionId = currentAVSession.sessionId;
  controller = await currentAVSession.getController();
  console.info(`Succeeded in creating AV session, sessionId: ${sessionId}`);
});
let commandName = "my_command";
if (controller !== undefined) {
  (controller as avSession.AVSessionController).sendCommonCommand(commandName, {command : "This is my command"}, () => {
    console.info('Succeeded in sending common command.');
  })
}
```

## sendCustomData<sup>20+</sup>

sendCustomData(data: Record\<string, Object>): Promise\<void>

发送私有数据到远端设备。使用Promise异步回调。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

**参数：**

 | 参数名 | 类型                   | 必填 | 说明                                                         |
 | ------ | ---------------------- | ---- | ------------------------------------------------------------ |
 | data   | Record\<string, Object> | 是   | 应用程序填充的自定义数据。服务端仅解析key为'customData'，且Object为string类型的对象。 |

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息                                                      |
| -------- | ------------------------------------------------------------ |
| 6600101  | Session service exception. You are advised to: 1. Scheduled retry. 2. Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  private tag: string = "createNewSession";
  private sessionId: string = "";
  private controller: avSession.AVSessionController | undefined = undefined;
  private currentAVSession?: avSession.AVSession;
  context = this.getUIContext();

  aboutToAppear(): void {
    avSession.createAVSession(this.getUIContext().getHostContext(), this.tag, "audio")
      .then(async (data: avSession.AVSession) => {
        this.currentAVSession = data;
        this.sessionId = this.currentAVSession.sessionId;
        this.controller = await this.currentAVSession.getController();
        console.info(`Succeeded in creating AV session, sessionId: ${this.sessionId}`);
      });

    if (this.controller !== undefined) {
      (this.controller as avSession.AVSessionController).sendCustomData({ customData: "This is my data" })
    }
  }

  build() {
    Column() {
      Text('AVSession Demo')
        .fontSize(20)
        .margin(10)
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

## getExtras<sup>10+</sup>

ArkTS-Dyn: getExtras(): Promise\<{[key: string]: Object}>

ArkTS-Sta: getExtras(): Promise<Record<string, Object>>

获取媒体提供方设置的自定义媒体数据包。使用Promise异步回调。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

|  类型                                |  说明                          |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ArkTS-Dyn: Promise<{[key: string]: Object}\><br>ArkTS-Sta: Promise<Record<string, Object>>| Promise对象，返回媒体提供方设置的自定义媒体数据包，数据包的内容与setExtras设置的内容完全一致。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 401 | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed.<br>**ArkTS模式：** 该错误码仅适用于ArkTS-Dyn。 |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |
| 6600105  | Invalid session command.|
| 6600107  | Too many commands or events.|

**示例：**

```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  private tag: string = "createNewSession";
  private sessionId: string = "";
  private controller: avSession.AVSessionController | undefined = undefined;
  private currentAVSession?: avSession.AVSession;
  context = this.getUIContext();

  aboutToAppear(): void {

    avSession.createAVSession(this.getUIContext().getHostContext(), this.tag, "audio")
      .then(async (data: avSession.AVSession) => {
        this.currentAVSession = data;
        this.sessionId = this.currentAVSession.sessionId;
        this.controller = await this.currentAVSession.getController();
        console.info(`Succeeded in creating AV session, sessionId: ${this.sessionId}`);
      });
    if (this.controller !== undefined) {
      (this.controller as avSession.AVSessionController).getExtras().then((extras) => {
        console.info(`Succeeded in getting extras: ${extras}`);
      });
    }
  }

  build() {
    Column() {
      Text('AVSession Demo')
        .fontSize(20)
        .margin(10)
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

## getExtras<sup>10+</sup>

ArkTS-Dyn: getExtras(callback: AsyncCallback\<{[key: string]: Object}>): void

ArkTS-Sta: getExtras(callback: AsyncCallback<Record<string, Object>>): void

获取媒体提供方设置的自定义媒体数据包,使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   |类型                                      | 必填 | 说明                       |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | ArkTS-Dyn: AsyncCallback<{[key: string]: Object}\><br>ArkTS-Sta: AsyncCallback<Record<string, Object>> | 是   | 回调函数，返回媒体提供方设置的自定义媒体数据包，数据包的内容与setExtras设置的内容完全一致。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 401 | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed.<br>**ArkTS模式：** 该错误码仅适用于ArkTS-Dyn。 |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |
| 6600105  | Invalid session command. |
| 6600107  |Too many commands or events. |

**示例：**

```ts
import { avSession } from '@kit.AVSessionKit';

let tag: string = "createNewSession";
let sessionId: string = "";
let controller:avSession.AVSessionController | undefined = undefined;
avSession.createAVSession(context, tag, "audio").then(async (data:avSession.AVSession)=> {
  currentAVSession = data;
  sessionId = currentAVSession.sessionId;
  controller = await currentAVSession.getController();
  console.info(`Succeeded in creating AV session, sessionId: ${sessionId}`);
});
if (controller !== undefined) {
  (controller as avSession.AVSessionController).getExtras((extras) => {
    console.info(`Succeeded in getting extras: ${extras}`);
  });
}
```

## getExtrasWithEvent<sup>18+</sup>

getExtrasWithEvent(extraEvent: string): Promise\<ExtraInfo>

根据远端分布式事件类型，获取远端分布式媒体提供方设置的自定义媒体数据包。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                      | 必填 | 说明                       |
| -------- | ----------------------------------------- | ---- | -------------------------- |
| extraEvent | string | 是 |  远端分布式事件类型。可获取的事件类型来自于[setExtras](arkts-apis-avsession-AVSession.md#setextras10)。<br>对Wearable设备类型，额外提供以下预设的事件类型：<br>'AUDIO_GET_VOLUME'：获取远端设备音量。<br>'AUDIO_GET_AVAILABLE_DEVICES'：获取远端所有可连接设备。<br>'AUDIO_GET_PREFERRED_OUTPUT_DEVICE_FOR_RENDERER_INFO'：获取远端实际发声设备。|

**返回值：**

| 类型                                | 说明                          |
| ----------------------------------- | ----------------------------- |
| Promise<[ExtraInfo](arkts-apis-avsession-t.md#extrainfo18)\>   | Promise对象，返回远端分布式媒体提供方设置的自定义媒体数据包。<br>参数ExtraInfo支持的数据类型有：字符串、数字、布尔、对象、数组和文件描述符等，详细介绍请参见[@ohos.app.ability.Want (Want)](../apis-ability-kit/js-apis-app-ability-want.md)。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |
| 6600105  | Invalid session command. |

**示例：**

```ts
let controller: avSession.AVSessionController | ESObject;
const COMMON_COMMAND_STRING_1 = 'AUDIO_GET_VOLUME';
const COMMON_COMMAND_STRING_2 = 'AUDIO_GET_AVAILABLE_DEVICES';
const COMMON_COMMAND_STRING_3 = 'AUDIO_GET_PREFERRED_OUTPUT_DEVICE_FOR_RENDERER_INFO';
if (controller !== undefined) {
  controller.getExtrasWithEvent(COMMON_COMMAND_STRING_1).then(() => {
    console.info(`${[COMMON_COMMAND_STRING_1]}`);
  })

  controller.getExtrasWithEvent(COMMON_COMMAND_STRING_2).then(() => {
    console.info(`${[COMMON_COMMAND_STRING_2]}`);
  })

  controller.getExtrasWithEvent(COMMON_COMMAND_STRING_3).then(() => {
    console.info(`${[COMMON_COMMAND_STRING_3]}`);
  })
}
```

## isDesktopLyricEnabled<sup>23+</sup>

isDesktopLyricEnabled(): Promise\<boolean>

查询是否启用桌面歌词功能。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<boolean> | Promise对象。返回true表示启用桌面歌词功能；返回false表示不启用桌面歌词功能。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |
| 6600111  | The desktop lyrics feature is not supported. |

```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(async () => {
          let tag: string = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          let currentAVSession: avSession.AVSession = await avSession.createAVSession(context, tag, "audio");
          console.info(`Succeeded in creating AV session, sessionId: ${currentAVSession.sessionId}`);
          let controller: avSession.AVSessionController = await currentAVSession.getController();
          let enabled: boolean = await controller.isDesktopLyricEnabled()
          console.info(`desktop lyric enabled:${enabled}`)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## onDesktopLyricEnabled<sup>23+</sup>

onDesktopLyricEnabled(callback: Callback\<boolean>): void

桌面歌词功能启用状态变更的事件监听。使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                   | 必填 | 说明                            |
| ------ | ---------------------- | ---- | -------------------------------- |
| callback   | Callback\<boolean> | 是   | 回调函数。返回true表示桌面歌词功能启用；返回false表示桌面歌词功能未启用。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**
```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(async () => {
          let tag: string = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          let currentAVSession: avSession.AVSession = await avSession.createAVSession(context, tag, "audio");
          console.info(`Succeeded in creating AV session, sessionId: ${currentAVSession.sessionId}`);
          let controller: avSession.AVSessionController = await currentAVSession.getController();
          controller.onDesktopLyricEnabled((enabled: boolean) => {
            console.info(`desktop lyric enabled state : ${enabled}`);
          })
          console.info('Succeeded in setting onDesktopLyricEnabled.');
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## offDesktopLyricEnabled<sup>23+</sup>

offDesktopLyricEnabled(callback?: Callback\<boolean>): void

注销桌面歌词启用状态变更事件监听。使用callback异步回调。

注销后将不再对该事件进行监听。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                   | 必填 | 说明                            |
| ------ | ---------------------- | ---- | -------------------------------- |
| callback   | Callback\<boolean> | 否   | 回调函数。当事件监听取消成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有桌面歌词功能启用状态变更事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**
```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(async () => {
          let tag: string = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          let currentAVSession: avSession.AVSession = await avSession.createAVSession(context, tag, "audio");
          console.info(`Succeeded in creating AV session, sessionId: ${currentAVSession.sessionId}`);
          let controller: avSession.AVSessionController = await currentAVSession.getController();
          controller.offDesktopLyricEnabled();
          console.info('Succeeded in setting offDesktopLyricEnabled.');
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## setDesktopLyricVisible<sup>23+</sup>

setDesktopLyricVisible(visible: boolean): Promise\<void>

设置当前会话桌面歌词的显示状态。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| ------ | ------ | ---- | ---------- |
| visible | boolean | 是   | 是否显示桌面歌词。true表示显示；false表示不显示。 |

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<void> |  Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |
| 6600110  | The desktop lyrics feature of this application is not enabled. |
| 6600111  | The desktop lyrics feature is not supported. |

**示例：**

```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(async () => {
          let tag: string = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          let currentAVSession: avSession.AVSession = await avSession.createAVSession(context, tag, "audio");
          console.info(`Succeeded in creating AV session, sessionId: ${currentAVSession.sessionId}`);
          let controller: avSession.AVSessionController = await currentAVSession.getController();
          await controller.setDesktopLyricVisible(true);
          console.info('Succeeded in setting desktop lyric visible.');
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## isDesktopLyricVisible<sup>23+</sup>

isDesktopLyricVisible(): Promise\<boolean>

查询当前会话桌面歌词的显示状态。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<boolean> | Promise对象。返回true表示显示桌面歌词；返回false表示不显示桌面歌词。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |
| 6600110  | The desktop lyrics feature of this application is not enabled. |
| 6600111  | The desktop lyrics feature is not supported. |

**示例：**
```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(async () => {
          let tag: string = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          let currentAVSession: avSession.AVSession = await avSession.createAVSession(context, tag, "audio");
          console.info(`Succeeded in creating AV session, sessionId: ${currentAVSession.sessionId}`);
          let controller: avSession.AVSessionController = await currentAVSession.getController();
          let visible: boolean = await controller.isDesktopLyricVisible();
          console.info(`isDesktopLyricVisible: ${visible}`);
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## onDesktopLyricVisibilityChanged<sup>23+</sup>

onDesktopLyricVisibilityChanged(callback: Callback\<boolean>): void

注册显示桌面歌词状态变更的事件监听。使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                   | 必填 | 说明                            |
| ------ | ---------------------- | ---- | -------------------------------- |
| callback   | Callback\<boolean> | 是   | 回调函数。返回true表示开启显示桌面歌词状态；返回false表示关闭显示桌面歌词状态。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**
```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(async () => {
          let tag: string = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          let currentAVSession: avSession.AVSession = await avSession.createAVSession(context, tag, "audio");
          console.info(`Succeeded in creating AV session, sessionId: ${currentAVSession.sessionId}`);
          let controller: avSession.AVSessionController = await currentAVSession.getController();
          controller.onDesktopLyricVisibilityChanged((visible: boolean) => {
            console.info(`desktop lyric visible state: ${visible}`);
          });
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## offDesktopLyricVisibilityChanged<sup>23+</sup>

offDesktopLyricVisibilityChanged(callback?: Callback\<boolean>): void

注销显示桌面歌词状态变更事件监听。使用callback异步回调。

注销后将不再对该事件进行监听。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                   | 必填 | 说明                            |
| ------ | ---------------------- | ---- | -------------------------------- |
| callback   | Callback\<boolean> | 否   | 回调函数。当事件监听取消成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有显示桌面歌词状态变更事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**
```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(async () => {
          let tag: string = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          let currentAVSession: avSession.AVSession = await avSession.createAVSession(context, tag, "audio");
          console.info(`Succeeded in creating AV session, sessionId: ${currentAVSession.sessionId}`);
          let controller: avSession.AVSessionController = await currentAVSession.getController();
          controller.offDesktopLyricVisibilityChanged();
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## setDesktopLyricState<sup>23+</sup>

setDesktopLyricState(state: DesktopLyricState): Promise\<void>

设置当前会话桌面歌词状态。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| ------ | ------ | ---- | ---------- |
| state | [DesktopLyricState](./arkts-apis-avsession-i.md#desktoplyricstate23) | 是   | 桌面歌词状态。 |

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<void> |  Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |
| 6600110  | The desktop lyrics feature of this application is not enabled. |
| 6600111  | The desktop lyrics feature is not supported. |

**示例：**

```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(async () => {
          let tag: string = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          let currentAVSession: avSession.AVSession = await avSession.createAVSession(context, tag, "audio");
          console.info(`Succeeded in creating AV session, sessionId: ${currentAVSession.sessionId}`);
          let controller: avSession.AVSessionController = await currentAVSession.getController();
          let state: avSession.DesktopLyricState = {
            isLocked: true,
          };
          await controller.setDesktopLyricState(state);
          console.info('Succeeded in setting desktop lyric state.');
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## getDesktopLyricState<sup>23+</sup>

getDesktopLyricState(): Promise\<DesktopLyricState>

获取当前会话桌面歌词状态。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<[DesktopLyricState](./arkts-apis-avsession-i.md#desktoplyricstate23)> |  Promise对象。返回桌面歌词状态。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |
| 6600110  | The desktop lyrics feature of this application is not enabled. |
| 6600111  | The desktop lyrics feature is not supported. |

**示例：**

```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(async () => {
          let tag: string = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          let currentAVSession: avSession.AVSession = await avSession.createAVSession(context, tag, "audio");
          console.info(`Succeeded in creating AV session, sessionId: ${currentAVSession.sessionId}`);
          let controller: avSession.AVSessionController = await currentAVSession.getController();
          let state: avSession.DesktopLyricState = await controller.getDesktopLyricState();
          console.info(`getDesktopLyricState: ${state.isLocked}`);
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## onDesktopLyricStateChanged<sup>23+</sup>

onDesktopLyricStateChanged(callback: Callback\<DesktopLyricState>): void

注册桌面歌词状态变更的事件监听。使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                   | 必填 | 说明                            |
| ------ | ---------------------- | ---- | -------------------------------- |
| callback   | Callback\<[DesktopLyricState](./arkts-apis-avsession-i.md#desktoplyricstate23)> | 是   | 回调函数。返回桌面歌词状态。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**
```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(async () => {
          let tag: string = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          let currentAVSession: avSession.AVSession = await avSession.createAVSession(context, tag, "audio");
          console.info(`Succeeded in creating AV session, sessionId: ${currentAVSession.sessionId}`);
          let controller: avSession.AVSessionController = await currentAVSession.getController();
          controller.onDesktopLyricStateChanged((state: avSession.DesktopLyricState) => {
            console.info(`desktop lyric isLocked : ${state.isLocked}`);
          })
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## offDesktopLyricStateChanged<sup>23+</sup>

offDesktopLyricStateChanged(callback?: Callback\<DesktopLyricState>): void

注销桌面歌词状态变更事件监听。使用callback异步回调。

注销后将不再对该事件进行监听。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                   | 必填 | 说明                            |
| ------ | ---------------------- | ---- | -------------------------------- |
| callback   | Callback\<[DesktopLyricState](./arkts-apis-avsession-i.md#desktoplyricstate23)> | 否   | 回调函数。当事件监听取消成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有桌面歌词状态变更事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**
```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(async () => {
          let tag: string = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          let currentAVSession: avSession.AVSession = await avSession.createAVSession(context, tag, "audio");
          console.info(`CreateAVSession : SUCCESS :sessionId = ${currentAVSession.sessionId}`);
          let controller: avSession.AVSessionController = await currentAVSession.getController();
          controller.offDesktopLyricStateChanged();
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## on('metadataChange')<sup>10+</sup>

on(type: 'metadataChange', filter: Array\<keyof AVMetadata> | 'all', callback: (data: AVMetadata) => void)

注册元数据变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onMetadataChange](#onmetadatachange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 事件回调类型，支持事件`'metadataChange'`：当元数据变化时，触发该事件。 |
| filter   | Array\<keyof&nbsp;[AVMetadata](arkts-apis-avsession-i.md#avmetadata10)\>&nbsp;&#124;&nbsp;'all' | 是   | 'all' 表示关注元数据所有字段变化；Array<keyof&nbsp;[AVMetadata](arkts-apis-avsession-i.md#avmetadata10)\> 表示关注Array中的字段变化。 |
| callback | (data: [AVMetadata](arkts-apis-avsession-i.md#avmetadata10)) => void | 是   | 回调函数，参数data是变化后的元数据。                         |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 401 | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|
| 6600101  | Session service exception.|
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.on('metadataChange', 'all', (metadata: avSession.AVMetadata) => {
  console.info(`on metadataChange assetId : ${metadata.assetId}`);
});

avsessionController.on('metadataChange', ['assetId', 'title', 'description'], (metadata: avSession.AVMetadata) => {
  console.info(`on metadataChange assetId : ${metadata.assetId}`);
});
```

## onMetadataChange<sup>23+</sup>

onMetadataChange(filter: Array\<string>, callback: Callback\<AVMetadata>): void

注册元数据变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('metadataChange')](#onmetadatachange10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| filter   | Array\<string> | 是   |  表示关注Array中的字段变化。 |
| callback | Callback<[AVMetadata](arkts-apis-avsession-i.md#avmetadata10)> | 是   | 回调函数，参数是变化后的元数据。                         |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.onMetadataChange(['assetId', 'title', 'description'], (metadata: avSession.AVMetadata) => {
  console.info(`onMetadataChange assetId : ${metadata.assetId}`);
});
```

## onMetadataChangeAll<sup>23+</sup>

onMetadataChangeAll(callback: Callback\<AVMetadata>): void

注册元数据变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('metadataChange')](#onmetadatachange10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback<[AVMetadata](arkts-apis-avsession-i.md#avmetadata10)> | 是   | 回调函数，参数data是变化后的元数据。                         |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.onMetadataChangeAll((metadata: avSession.AVMetadata) => {
  console.info(`onMetadataChangeAll assetId : ${metadata.assetId}`);
});
```

## off('metadataChange')<sup>10+</sup>

off(type: 'metadataChange', callback?: (data: AVMetadata) => void)

注销媒体控制器元数据变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offMetadataChange](#offmetadatachange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                                               | 必填 | 说明                                                    |
| -------- | ------------------------------------------------ | ---- | ------------------------------------------------------ |
| type     | string                                           | 是   | 取消对应的事件监听，支持事件`'metadataChange'`。         |
| callback | (data: [AVMetadata](arkts-apis-avsession-i.md#avmetadata10)) => void        | 否   | 回调函数，参数data是变化后的元数据。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。                         |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 401 | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|
| 6600101  | Session service exception.|
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.off('metadataChange');
```

## offMetadataChange<sup>23+</sup>

offMetadataChange(callback?: Callback\<AVMetadata>): void

注销媒体控制器元数据变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('metadataChange')](#offmetadatachange10)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                               | 必填 | 说明                                                    |
| -------- | ------------------------------------------------ | ---- | ------------------------------------------------------ |
| callback | Callback<[AVMetadata](arkts-apis-avsession-i.md#avmetadata10)>       | 否   | 回调函数，参数data是变化后的元数据。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。                         |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.offMetadataChange();
```

## on('playbackStateChange')<sup>10+</sup>

on(type: 'playbackStateChange', filter: Array\<keyof AVPlaybackState> | 'all', callback: (state: AVPlaybackState) => void)

注册播放状态变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onPlaybackStateChange](#onplaybackstatechange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型       | 必填 | 说明      |
| --------| -----------|-----|------------|
| type     | string    | 是   | 事件回调类型，支持事件`'playbackStateChange'`：当播放状态变化时，触发该事件。 |
| filter   | Array\<keyof&nbsp;[AVPlaybackState](arkts-apis-avsession-i.md#avplaybackstate10)\>&nbsp;&#124;&nbsp;'all' | 是   | 'all' 表示关注播放状态所有字段变化；Array<keyof&nbsp;[AVPlaybackState](arkts-apis-avsession-i.md#avplaybackstate10)\> 表示关注Array中的字段变化。 |
| callback | (state: [AVPlaybackState](arkts-apis-avsession-i.md#avplaybackstate10)) => void       | 是   | 回调函数，参数state是变化后的播放状态。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 401 | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.on('playbackStateChange', 'all', (playbackState: avSession.AVPlaybackState) => {
  console.info(`on playbackStateChange state : ${playbackState.state}`);
});

avsessionController.on('playbackStateChange', ['state', 'speed', 'loopMode'], (playbackState: avSession.AVPlaybackState) => {
  console.info(`on playbackStateChange state : ${playbackState.state}`);
});
```

## onPlaybackStateChange<sup>23+</sup>

onPlaybackStateChange(filter: Array\<string>, callback: Callback\<AVPlaybackState>): void

注册播放状态变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('playbackStateChange')](#onplaybackstatechange10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型       | 必填 | 说明      |
| --------| -----------|-----|------------|
| filter   | Array\<string\>| 是   | Array\<string\> 表示关注Array中的字段变化。 |
| callback | Callback<[AVPlaybackState](arkts-apis-avsession-i.md#avplaybackstate10)>       | 是   | 回调函数，参数state是变化后的播放状态。|

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.onPlaybackStateChange(['state', 'speed', 'loopMode'], (playbackState: avSession.AVPlaybackState) => {
  console.info(`onPlaybackStateChange state : ${playbackState.state}`);
});
```

## onPlaybackStateChangeAll<sup>23+</sup>

onPlaybackStateChangeAll(callback: Callback\<AVPlaybackState>): void

注册播放状态变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('playbackStateChange')](#onplaybackstatechange10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型       | 必填 | 说明      |
| --------| -----------|-----|------------|
| callback | Callback<[AVPlaybackState](arkts-apis-avsession-i.md#avplaybackstate10)>      | 是   | 回调函数，参数state是变化后的播放状态。|

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.onPlaybackStateChangeAll((playbackState: avSession.AVPlaybackState) => {
  console.info(`onPlaybackStateChangeAll state : ${playbackState.state}`);
});
```

## off('playbackStateChange')<sup>10+</sup>

off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void)

注销媒体控制器播放状态变化的事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offPlaybackStateChange](#offplaybackstatechange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                     |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| type     | string                                                       | 是   | 取消对应的事件监听，支持事件`'playbackStateChange'`。    |
| callback | (state: [AVPlaybackState](arkts-apis-avsession-i.md#avplaybackstate10)) => void         | 否   | 回调函数，参数state是需要更新的播放状态。只包含需要更新的播放状态属性，并不代表当前全量的播放状态。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.off('playbackStateChange');
```

## offPlaybackStateChange<sup>23+</sup>

offPlaybackStateChange(callback?: Callback\<AVPlaybackState>): void

注销媒体控制器播放状态变化的事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('playbackStateChange')](#offplaybackstatechange10)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                     |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| callback | Callback<[AVPlaybackState](arkts-apis-avsession-i.md#avplaybackstate10)>       | 否   | 回调函数，参数state是变化后的播放状态。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。                      |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.offPlaybackStateChange();
```

## on('callMetadataChange')<sup>11+</sup>

on(type: 'callMetadataChange', filter: Array\<keyof CallMetadata> | 'all', callback: Callback\<CallMetadata>): void

注册通话元数据变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onCallMetadataChange](#oncallmetadatachange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名   | 类型       | 必填 | 说明      |
| --------| -----------|-----|------------|
| type     | string    | 是   | 事件回调类型，支持事件`'callMetadataChange'`：当通话元数据变化时，触发该事件。 |
| filter   | Array\<keyof&nbsp;[CallMetadata](arkts-apis-avsession-i.md#callmetadata11)\>&nbsp;&#124;&nbsp;'all' | 是   | 'all' 表示关注通话元数据所有字段变化；Array<keyof&nbsp;[CallMetadata](arkts-apis-avsession-i.md#callmetadata11)\> 表示关注Array中的字段变化。 |
| callback | Callback<[CallMetadata](arkts-apis-avsession-i.md#callmetadata11)\>   | 是   | 回调函数，参数callmetadata是变化后的通话元数据。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.on('callMetadataChange', 'all', (callmetadata: avSession.CallMetadata) => {
  console.info(`on callMetadataChange state : ${callmetadata.name}`);
});

avsessionController.on('callMetadataChange', ['name'], (callmetadata: avSession.CallMetadata) => {
  console.info(`on callMetadataChange state : ${callmetadata.name}`);
});
```

## onCallMetadataChange<sup>23+</sup>

onCallMetadataChange(filter: Array\<string>, callback: Callback\<CallMetadata>): void

注册通话元数据变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('callMetadataChange')](#oncallmetadatachange11)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型       | 必填 | 说明      |
| --------| -----------|-----|------------|
| filter   | Array\<string\> | 是   |  表示关注Array中的字段变化。 |
| callback | Callback<[CallMetadata](arkts-apis-avsession-i.md#callmetadata11)\>   | 是   | 回调函数，参数callmetadata是变化后的通话元数据。|

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.onCallMetadataChange(['name'], (callmetadata: avSession.CallMetadata) => {
  console.info(`onCallMetadataChange state : ${callmetadata.name}`);
});
```

## onCallMetadataChangeAll<sup>23+</sup>

onCallMetadataChangeAll(callback: Callback\<CallMetadata>): void

注册通话元数据变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('callMetadataChange')](#oncallmetadatachange11)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型       | 必填 | 说明      |
| --------| -----------|-----|------------|
| callback | Callback<[CallMetadata](arkts-apis-avsession-i.md#callmetadata11)\>   | 是   | 回调函数，参数callmetadata是变化后的通话元数据。|

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.onCallMetadataChangeAll((callmetadata: avSession.CallMetadata) => {
  console.info(`onCallMetadataChangeAll state : ${callmetadata.name}`);
});
```

## off('callMetadataChange')<sup>11+</sup>

off(type: 'callMetadataChange', callback?: Callback\<CallMetadata>): void

注销设置通话元数据变化的事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offCallMetadataChange](#offcallmetadatachange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                     |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| type     | string                                                       | 是   | 取消对应的事件监听，支持事件`'callMetadataChange'`。    |
| callback | Callback<[CallMetadata](arkts-apis-avsession-i.md#callmetadata11)\>       | 否   | 回调函数，参数calldata是变化后的通话原数据。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。      |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.off('callMetadataChange');
```

## offCallMetadataChange<sup>23+</sup>

offCallMetadataChange(callback?: Callback\<CallMetadata>): void

注销设置通话元数据变化的事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('callMetadataChange')](#offcallmetadatachange11)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                     |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| callback | Callback<[CallMetadata](arkts-apis-avsession-i.md#callmetadata11)\>       | 否   | 回调函数，参数calldata是变化后的通话原数据。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。      |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.offCallMetadataChange();
```

## on('callStateChange')<sup>11+</sup>

on(type: 'callStateChange', filter: Array\<keyof AVCallState> | 'all', callback: Callback\<AVCallState>): void

注册通话状态变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onCallStateChange](#oncallstatechange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名   | 类型       | 必填 | 说明      |
| --------| -----------|-----|------------|
| type     | string    | 是   | 事件回调类型，支持事件`'callStateChange'`：当通话状态变化时，触发该事件。 |
| filter   | Array<keyof&nbsp;[AVCallState](arkts-apis-avsession-i.md#avcallstate11)\>&nbsp;&#124;&nbsp;'all' | 是   | 'all' 表示关注通话状态所有字段变化；Array<keyof&nbsp;[AVCallState](arkts-apis-avsession-i.md#avcallstate11)\> 表示关注Array中的字段变化。 |
| callback | Callback<[AVCallState](arkts-apis-avsession-i.md#avcallstate11)\>       | 是   | 回调函数，参数callstate是变化后的通话状态。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.on('callStateChange', 'all', (callstate: avSession.AVCallState) => {
  console.info(`on callStateChange state : ${callstate.state}`);
});

avsessionController.on('callStateChange', ['state'], (callstate: avSession.AVCallState) => {
  console.info(`on callStateChange state : ${callstate.state}`);
});
```

## onCallStateChange<sup>23+</sup>

onCallStateChange(filter: Array\<string>, callback: Callback\<AVCallState>): void

注册通话状态变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('callStateChange')](#oncallstatechange11)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型       | 必填 | 说明      |
| --------| -----------|-----|------------|
| filter   | Array<string\> | 是   |  表示关注Array中的字段变化。 |
| callback | Callback<[AVCallState](arkts-apis-avsession-i.md#avcallstate11)\>       | 是   | 回调函数，参数callstate是变化后的通话状态。|

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.onCallStateChange(['state'], (callstate: avSession.AVCallState) => {
  console.info(`onCallStateChange state : ${callstate.state}`);
});
```

## onCallStateChangeAll<sup>23+</sup>

onCallStateChangeAll(callback: Callback\<AVCallState>): void

注册通话状态变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('callStateChange')](#oncallstatechange11)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型       | 必填 | 说明      |
| --------| -----------|-----|------------|
| callback | Callback<[AVCallState](arkts-apis-avsession-i.md#avcallstate11)\>       | 是   | 回调函数，参数callstate是变化后的通话状态。|

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.onCallStateChangeAll((callstate: avSession.AVCallState) => {
  console.info(`onCallStateChangeAll state : ${callstate.state}`);
});
```

## off('callStateChange')<sup>11+</sup>

off(type: 'callStateChange', callback?: Callback\<AVCallState>): void

注销设置通话状态变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offCallStateChange](#offcallstatechange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                     |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| type     | string                                                       | 是   | 取消对应的事件监听，支持事件`'callStateChange'`。    |
| callback | Callback<[AVCallState](arkts-apis-avsession-i.md#avcallstate11)\>           | 否   | 回调函数，参数callstate是变化后的通话状态。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。      |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.off('callMetadataChange');
```

## offCallStateChange<sup>23+</sup>

offCallStateChange(callback?: Callback\<AVCallState>): void

注销设置通话状态变化的事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('callStateChange')](#offcallstatechange11)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                     |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| callback | Callback<[AVCallState](arkts-apis-avsession-i.md#avcallstate11)\>           | 否   | 回调函数，参数callstate是变化后的通话状态。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。      |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.offCallStateChange();
```

## on('sessionDestroy')<sup>10+</sup>

on(type: 'sessionDestroy', callback: () => void)

注册会话销毁的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onSessionDestroy](#onsessiondestroy23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型       | 必填 | 说明                                                         |
| -------- | ---------- | ---- | ------------------------------------------------------------ |
| type     | string     | 是   | 事件回调类型，支持事件`'sessionDestroy'`：当检测到会话销毁时，触发该事件。 |
| callback | () => void | 是   | 回调函数。<br>当事件监听注册成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.on('sessionDestroy', () => {
  console.info('on sessionDestroy : SUCCESS ');
});
```

## onSessionDestroy<sup>23+</sup>

onSessionDestroy(callback: NoParamCallback): void

注册会话销毁的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('sessionDestroy')](#onsessiondestroy10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型       | 必填 | 说明                                                         |
| -------- | ---------- | ---- | ------------------------------------------------------------ |
| callback | NoParamCallback | 是   | 回调函数。当事件监听注册成功，err为null，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.onSessionDestroy(() => {
  console.info('onSessionDestroy : SUCCESS ');
});
```

## off('sessionDestroy')<sup>10+</sup>

off(type: 'sessionDestroy', callback?: () => void)

注销媒体控制器取消监听会话的销毁事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offSessionDestroy](#offsessiondestroy23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型       | 必填 | 说明                                                         |
| -------- | ---------- | ---- | ------------------------------------------------------------ |
| type     | string     | 是   | 取消对应的事件监听，支持事件`'sessionDestroy'`。             |
| callback | () => void | 否   | 回调函数。<br>当事件监听取消成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.off('sessionDestroy');
```

## offSessionDestroy<sup>23+</sup>

offSessionDestroy(callback?: NoParamCallback): void

注销媒体控制器会话的销毁事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('sessionDestroy')](#offsessiondestroy10)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型       | 必填 | 说明                                                         |
| -------- | ---------- | ---- | ------------------------------------------------------------ |
| callback | NoParamCallback | 否   | 回调函数。<br>当事件监听取消成功，err为null，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.offSessionDestroy();
```

## on('activeStateChange')<sup>10+</sup>

on(type: 'activeStateChange', callback: (isActive: boolean) => void)

注册会话的激活状态的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onActiveStateChange](#onactivestatechange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                        | 必填 | 说明                                                         |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                      | 是   | 事件回调类型，支持事件`'activeStateChange'`：当检测到会话的激活状态发生改变时，触发该事件。 |
| callback | (isActive: boolean) => void | 是   | 回调函数。参数isActive表示会话是否被激活。true表示被激活，false表示禁用。                   |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ----------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600103  |The session controller does not exist. |

**示例：**

```ts
avsessionController.on('activeStateChange', (isActive: boolean) => {
  console.info(`on activeStateChange : SUCCESS : isActive ${isActive}`);
});
```

## onActiveStateChange<sup>23+</sup>

onActiveStateChange(callback: Callback\<boolean>): void

注册会话的激活状态的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('activeStateChange')](#onactivestatechange10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                        | 必填 | 说明                                                         |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback\<boolean> | 是   | 回调函数。参数isActive表示会话是否被激活。true表示被激活，false表示禁用。                   |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ----------------------------- |
| 6600101  | Session service exception. |
| 6600103  |The session controller does not exist. |

**示例：**

```ts
avsessionController.onActiveStateChange((isActive: boolean) => {
  console.info(`onActiveStateChange : SUCCESS : isActive ${isActive}`);
});
```

## off('activeStateChange')<sup>10+</sup>

off(type: 'activeStateChange', callback?: (isActive: boolean) => void)

注销媒体控制器会话激活状态变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offActiveStateChange](#offactivestatechange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                        | 必填 | 说明                                                      |
| -------- | --------------------------- | ---- | ----------------------------------------------------- |
| type     | string                      | 是   | 取消对应的事件监听，支持事件`'activeStateChange'`。      |
| callback | (isActive: boolean) => void | 否   | 回调函数。参数isActive表示会话是否被激活。true表示被激活，false表示禁用。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。                   |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.off('activeStateChange');
```

## offActiveStateChange<sup>23+</sup>

offActiveStateChange(callback?: Callback\<boolean>): void

注销媒体控制器会话激活状态变化的事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('activeStateChange')](#offactivestatechange10)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                        | 必填 | 说明                                                      |
| -------- | --------------------------- | ---- | ----------------------------------------------------- |
| callback | Callback\<boolean> | 否   | 回调函数。参数isActive表示会话是否被激活。true表示被激活，false表示禁用。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。                   |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.offActiveStateChange();
```

## on('validCommandChange')<sup>10+</sup>

on(type: 'validCommandChange', callback: (commands: Array\<AVControlCommandType>) => void)

注册会话支持的有效命令变化事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onValidCommandChange](#onvalidcommandchange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 事件回调类型，支持事件`'validCommandChange'`：当检测到会话的合法命令发生改变时，触发该事件。 |
| callback | (commands: Array<[AVControlCommandType](arkts-apis-avsession-t.md#avcontrolcommandtype10)\>) => void | 是   | 回调函数。参数commands是有效命令的集合。                     |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.on('validCommandChange', (validCommands: avSession.AVControlCommandType[]) => {
  console.info(`validCommandChange : SUCCESS : size : ${validCommands.length}`);
  console.info(`validCommandChange : SUCCESS : validCommands : ${validCommands.values()}`);
});
```

## onValidCommandChange<sup>23+</sup>

onValidCommandChange(callback: Callback<Array\<AVControlCommandType>>): void

注册会话支持的有效命令变化事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('validCommandChange')](#onvalidcommandchange10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                     |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------- |
| callback | Callback<Array<[AVControlCommandType](arkts-apis-avsession-t.md#avcontrolcommandtype10)\>> | 是   | 回调函数。参数commands是有效命令的集合。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.onValidCommandChange((validCommands: avSession.AVControlCommandType[]) => {
  console.info(`validCommandChange : SUCCESS : size : ${validCommands.length}`);
  console.info(`validCommandChange : SUCCESS : validCommands : ${validCommands.values()}`);
});
```

## off('validCommandChange')<sup>10+</sup>

off(type: 'validCommandChange', callback?: (commands: Array\<AVControlCommandType>) => void)

注销媒体控制器会话有效命令变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offValidCommandChange](#offvalidcommandchange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                                             | 必填 | 说明                                                         |
| -------- | ------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                           | 是   | 取消对应的事件监听，支持事件`'validCommandChange'`。         |
| callback | (commands: Array\<AVControlCommandType>) => void | 否   | 回调函数。参数commands是有效命令的集合。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息           |
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.off('validCommandChange');
```

## offValidCommandChange<sup>23+</sup>

offValidCommandChange(callback?: Callback<Array\<AVControlCommandType>>): void

注销媒体控制器会话有效命令变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('validCommandChange')](#offvalidcommandchange10)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------------------------------- |
| callback | Callback<Array<[AVControlCommandType](arkts-apis-avsession-t.md#avcontrolcommandtype10)\>> | 否   | 回调函数。参数commands是有效命令的集合。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。          |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息           |
| -------- | ---------------- |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.offValidCommandChange();
```


## on('outputDeviceChange')<sup>10+</sup>

on(type: 'outputDeviceChange', callback: (state: ConnectionState, device: OutputDeviceInfo) => void): void

注册播放设备变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onOutputDeviceChange](#onoutputdevicechange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                                  | 是   | 事件回调类型，支持事件为`'outputDeviceChange'`：当播放设备变化时，触发该事件）。 |
| callback | (state: [ConnectionState](arkts-apis-avsession-e.md#connectionstate10), device: [OutputDeviceInfo](arkts-apis-avsession-i.md#outputdeviceinfo10)) => void | 是   | 回调函数，参数device是设备相关信息。                         |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ----------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.on('outputDeviceChange', (state: avSession.ConnectionState, device: avSession.OutputDeviceInfo) => {
  console.info(`on outputDeviceChange state: ${state}, device : ${device}`);
});
```

## onOutputDeviceChange<sup>23+</sup>

onOutputDeviceChange(callback: ConnectionEvent): void

注册播放设备变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('outputDeviceChange')](#onoutputdevicechange10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型            | 必填 | 说明                                 |
| -------- | --------------- | ---- | ------------------------------------ |
| callback | ConnectionEvent | 是   | 回调函数，参数device是设备相关信息。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ----------------------- |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.onOutputDeviceChange((state: avSession.ConnectionState, device: avSession.OutputDeviceInfo) => {
  console.info(`onOutputDeviceChange state: ${state}, device : ${device}`);
});
```

## off('outputDeviceChange')<sup>10+</sup>

off(type: 'outputDeviceChange', callback?: (state: ConnectionState, device: OutputDeviceInfo) => void): void

注销监听分布式设备变化事件监听。使用callback异步回调。

指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offOutputDeviceChange](#offoutputdevicechange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                                                    | 必填 | 说明                                                      |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------ |
| type     | string                                                  | 是   | 取消对应的事件监听，支持事件`'outputDeviceChange'`。      |
| callback | (state: [ConnectionState](arkts-apis-avsession-e.md#connectionstate10), device: [OutputDeviceInfo](arkts-apis-avsession-i.md#outputdeviceinfo10)) => void | 否   | 回调函数，参数device是设备相关信息。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。                         |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID  | 错误信息          |
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.off('outputDeviceChange');
```

## offOutputDeviceChange<sup>23+</sup>

offOutputDeviceChange(callback?: ConnectionEvent): void

注销媒体控制器分布式设备变化的事件监听。使用Callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('outputDeviceChange')](#offoutputdevicechange10)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型            | 必填 | 说明                                                         |
| -------- | --------------- | ---- | ------------------------------------------------------------ |
| callback | ConnectionEvent | 否   | 回调函数，参数device是设备相关信息。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID  | 错误信息          |
| -------- | ---------------- |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.offOutputDeviceChange();
```

## on('sessionEvent')<sup>10+</sup>

on(type: 'sessionEvent', callback: (sessionEvent: string, args: {[key: string]: Object}) => void): void

注册媒体控制器设置会话自定义事件变化的监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onSessionEvent](#onsessionevent23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 事件回调类型，支持事件`'sessionEvent'`：当会话事件变化时，触发该事件。 |
| callback | (sessionEvent: string, args: {[key: string]: Object}) => void | 是   | 回调函数，sessionEvent为变化的会话事件名，args为事件的参数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600103  | The session controller does not exist. |

**示例：**

```ts
import { avSession } from '@kit.AVSessionKit';

let tag: string = "createNewSession";
let sessionId: string = "";
let controller:avSession.AVSessionController | undefined = undefined;
avSession.createAVSession(context, tag, "audio").then(async (data:avSession.AVSession)=> {
  currentAVSession = data;
  sessionId = currentAVSession.sessionId;
  controller = await currentAVSession.getController();
  console.info('CreateAVSession : SUCCESS :sessionid = ${sessionid}');
});
if (controller !== undefined) {
  (controller as avSession.AVSessionController).on('sessionEvent', (sessionEvent, args) => {
    console.info(`OnSessionEvent, sessionEvent is ${sessionEvent}, args: ${JSON.stringify(args)}`);
  });
}
```

## onSessionEvent<sup>23+</sup>

onSessionEvent(callback: EventProcess): void

注册媒体控制器设置会话自定义事件变化的监听器。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('sessionEvent')](#onsessionevent10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型         | 必填 | 说明                                                         |
| -------- | ------------ | ---- | ------------------------------------------------------------ |
| callback | EventProcess | 是   | 回调函数，sessionEvent为变化的会话事件名，args为事件的参数。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
import { avSession } from '@kit.AVSessionKit';

let tag: string = "createNewSession";
let sessionId: string = "";
let controller:avSession.AVSessionController | undefined = undefined;
avSession.createAVSession(context, tag, "audio").then(async (data:avSession.AVSession)=> {
  currentAVSession = data;
  sessionId = currentAVSession.sessionId;
  controller = await currentAVSession.getController();
  console.info('CreateAVSession : SUCCESS :sessionid = ${sessionid}');
});
if (controller !== undefined) {
  (controller as avSession.AVSessionController).onSessionEvent((sessionEvent, args) => {
    console.info(`OnSessionEvent, sessionEvent is ${sessionEvent}, args: ${JSON.stringify(args)}`);
  });
}
```

## off('sessionEvent')<sup>10+</sup>

off(type: 'sessionEvent', callback?: (sessionEvent: string, args: {[key: string]: Object}) => void): void

媒体控制器取消监听会话事件的变化通知。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offSessionEvent](#offsessionevent23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 取消对应的事件监听，支持事件`'sessionEvent'`。               |
| callback | (sessionEvent: string, args: {[key: string]: Object}) => void | 否   | 回调函数，参数sessionEvent是变化的事件名，args为事件的参数。<br>该参数为可选参数，若不填写该参数，则认为取消所有对sessionEvent事件的监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.off('sessionEvent');
```

## offSessionEvent<sup>23+</sup>

offSessionEvent(callback?: EventProcess): void

媒体控制器取消监听会话事件的变化通知。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('sessionEvent')](#offsessionevent10)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型         | 必填 | 说明                                                         |
| -------- | ------------ | ---- | ------------------------------------------------------------ |
| callback | EventProcess | 否   | 回调函数，参数event是变化的事件名，args为事件的参数。<br>该参数为可选参数，若不填写该参数，则认为取消所有对sessionEvent事件的监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.offSessionEvent();
```

## on('queueItemsChange')<sup>10+</sup>

on(type: 'queueItemsChange', callback: (items: Array<[AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10)\>) => void): void

注册媒体控制器会话自定义播放列表变化的监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onQueueItemsChange](#onqueueitemschange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                                                   | 必填 | 说明                                                                         |
| -------- | ----------------------------------------------------- | ---- | ---------------------------------------------------------------------------- |
| type     | string                                                | 是   | 事件回调类型，支持事件`'queueItemsChange'`：当session修改播放列表时，触发该事件。 |
| callback | (items: Array<[AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10)\>) => void  | 是   | 回调函数，items为变化的播放列表。                            |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.on('queueItemsChange', (items: avSession.AVQueueItem[]) => {
  console.info(`OnQueueItemsChange, items length is ${items.length}`);
});
```

## onQueueItemsChange<sup>23+</sup>

onQueueItemsChange(callback: Callback<Array<[AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10)\>>): void

注册媒体控制器会话自定义播放列表变化的监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('queueItemsChange')](#onqueueitemschange10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                   | 必填 | 说明                                                                         |
| -------- | ----------------------------------------------------- | ---- | ---------------------------------------------------------------------------- |
| callback | Callback<Array<[AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10)\>>  | 是   | 回调函数，items为变化的播放列表。                            |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.onQueueItemsChange((items: avSession.AVQueueItem[]) => {
  console.info(`OnQueueItemsChange, items length is ${items.length}`);
});
```

## off('queueItemsChange')<sup>10+</sup>

off(type: 'queueItemsChange', callback?: (items: Array<[AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10)\>) => void): void

注销媒体控制器播放列表变化的事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offQueueItemsChange](#offqueueitemschange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名    | 类型                                                 | 必填 | 说明                                                                                                |
| -------- | ---------------------------------------------------- | ---- | --------------------------------------------------------------------------------------------------- |
| type     | string                                               | 是   | 取消对应的事件监听，支持事件`'queueItemsChange'`。                                                     |
| callback | (items: Array<[AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10)\>) => void | 否   | 回调函数，参数items是变化的播放列表。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.off('queueItemsChange');
```

## offQueueItemsChange<sup>23+</sup>

offQueueItemsChange(callback?: Callback<Array<[AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10)\>>): void

注销媒体控制器播放列表变化的事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('queueItemsChange')](#offqueueitemschange10)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                                                 | 必填 | 说明                                                                                                |
| -------- | ---------------------------------------------------- | ---- | --------------------------------------------------------------------------------------------------- |
| callback | Callback<Array<[AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10)\>> | 否   | 回调函数，参数items是变化的播放列表。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.offQueueItemsChange();
```

## on('queueTitleChange')<sup>10+</sup>

on(type: 'queueTitleChange', callback: (title: string) => void): void

注册媒体控制器会话自定义播放列表的名称变化的监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onQueueTitleChange](#onqueuetitlechange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                     | 必填 | 说明                                                                             |
| -------- | ----------------------- | ---- | ------------------------------------------------------------------------------- |
| type     | string                  | 是   | 事件回调类型，支持事件`'queueTitleChange'`：当session修改播放列表名称时，触发该事件。 |
| callback | (title: string) => void | 是   | 回调函数，title为变化的播放列表名称。                                |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.on('queueTitleChange', (title: string) => {
  console.info(`queueTitleChange, title is ${title}`);
});
```

## onQueueTitleChange<sup>23+</sup>

onQueueTitleChange(callback: Callback\<string>): void

注册媒体控制器会话自定义播放列表的名称变化的监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('queueTitleChange')](#onqueuetitlechange10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                     | 必填 | 说明                                                                             |
| -------- | ----------------------- | ---- | ------------------------------------------------------------------------------- |
| callback | Callback\<string> | 是   | 回调函数，title为变化的播放列表名称。                                |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.onQueueTitleChange((title: string) => {
  console.info(`queueTitleChange, title is ${title}`);
});
```

## off('queueTitleChange')<sup>10+</sup>

off(type: 'queueTitleChange', callback?: (title: string) => void): void

注销媒体控制器播放列表名称变化的事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offQueueTitleChange](#offqueuetitlechange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名    | 类型                    | 必填 | 说明                                                                                                    |
| -------- | ----------------------- | ---- | ------------------------------------------------------------------------------------------------------- |
| type     | string                  | 是   | 取消对应的事件监听，支持事件`'queueTitleChange'`。                                                         |
| callback | (title: string) => void | 否   | 回调函数，参数items是变化的播放列表名称。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.off('queueTitleChange');
```

## offQueueTitleChange<sup>23+</sup>

offQueueTitleChange(callback?: Callback\<string>): void

注销媒体控制器播放列表名称变化的事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('queueTitleChange')](#offqueuetitlechange10)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                    | 必填 | 说明                                                                                                    |
| -------- | ----------------------- | ---- | ------------------------------------------------------------------------------------------------------- |
| callback | Callback\<string> | 否   | 回调函数，参数items是变化的播放列表名称。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.offQueueTitleChange();
```

## on('extrasChange')<sup>10+</sup>

on(type: 'extrasChange', callback: (extras: {[key: string]: Object}) => void): void

注册媒体控制器自定义媒体数据包事件变化的监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onExtrasChange](#onextraschange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 事件回调类型，支持事件`'extrasChange'`：当媒体提供方设置自定义媒体数据包时，触发该事件。 |
| callback | (extras: {[key: string]: Object}) => void | 是   | 回调函数，extras为媒体提供方新设置的自定义媒体数据包，该自定义媒体数据包与dispatchSessionEvent方法设置的数据包完全一致。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600103  | The session controller does not exist. |

**示例：**

```ts
import { avSession } from '@kit.AVSessionKit';

let tag: string = "createNewSession";
let sessionId: string = "";
let controller:avSession.AVSessionController | undefined = undefined;
avSession.createAVSession(context, tag, "audio").then(async (data:avSession.AVSession)=> {
  currentAVSession = data;
  sessionId = currentAVSession.sessionId;
  controller = await currentAVSession.getController();
  console.info('CreateAVSession : SUCCESS :sessionid = ${sessionid}');
});
if (controller !== undefined) {
  (controller as avSession.AVSessionController).on('extrasChange', (extras) => {
    console.info(`Caught extrasChange event,the new extra is: ${JSON.stringify(extras)}`);
  });
}
```

## onExtrasChange<sup>23+</sup>

onExtrasChange(callback: Callback\<Record<string, Object>>): void

注册媒体控制器自定义媒体数据包事件变化的监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('extrasChange')](#onextraschange10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback<Record<string, Object>> | 是   | 回调函数，extras为媒体提供方新设置的自定义媒体数据包，该自定义媒体数据包与dispatchSessionEvent方法设置的数据包完全一致。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
import { avSession } from '@kit.AVSessionKit';

let tag: string = "createNewSession";
let sessionId: string = "";
let controller:avSession.AVSessionController | undefined = undefined;
avSession.createAVSession(context, tag, "audio").then(async (data:avSession.AVSession)=> {
  currentAVSession = data;
  sessionId = currentAVSession.sessionId;
  controller = await currentAVSession.getController();
  console.info('CreateAVSession : SUCCESS :sessionid = ${sessionid}');
});
if (controller !== undefined) {
  (controller as avSession.AVSessionController).onExtrasChange((extras) => {
    console.info(`Caught extrasChange event,the new extra is: ${JSON.stringify(extras)}`);
  });
}
```

## off('extrasChange')<sup>10+</sup>

off(type: 'extrasChange', callback?: (extras: {[key: string]: Object}) => void): void

注销媒体控制器自定义媒体数据包变化事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offExtrasChange](#offextraschange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名    | 类型                    | 必填 | 说明                                                                                                    |
| -------- | ----------------------- | ---- | ------------------------------------------------------------------------------------------------------- |
| type     | string                  | 是   | 取消对应的事件监听，支持事件`'extrasChange'`。                                                         |
| callback | (extras: {[key: string]: Object}) => void | 否   | 注册事件监听时的回调函数。<br>该参数为可选参数，若不填写该参数，则认为取消会话所有与此事件相关的监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ----------------                       |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.off('extrasChange');
```

## offExtrasChange<sup>23+</sup>

offExtrasChange(callback?: Callback<Record<string, Object>>): void

注销媒体控制器自定义媒体数据包变化事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('extrasChange')](#offextraschange10)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                    | 必填 | 说明                                                                                                    |
| -------- | ----------------------- | ---- | ------------------------------------------------------------------------------------------------------- |
| callback | Callback<Record<string, Object>> | 否   | 注册事件监听时的回调函数。<br>该参数为可选参数，若不填写该参数，则认为取消会话所有与此事件相关的监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ----------------                       |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.offExtrasChange();
```

## on('customDataChange')<sup>20+</sup>

on(type: 'customDataChange', callback: Callback\<Record\<string, Object>>): void

注册从远程设备发送的自定义数据的监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onCustomDataChange](#oncustomdatachange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                           | 是   | 事件回调类型，支持事件'customDataChange'，当媒体提供方发送自定义数据时，触发该事件。 |
| callback | Callback\<Record\<string, Object>> | 是   | 回调函数，用于接收自定义数据。                               |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息                               |
| -------- | -------------------------------------- |
| 6600101  | Session service exception.             |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
currentAVSession.on('customDataChange', (callback) => {
    console.info(`Caught customDataChange event,the new callback is: ${JSON.stringify(callback)}`);
});
```

## onCustomDataChange<sup>23+</sup>

onCustomDataChange(callback: Callback\<Record\<string, Object>>): void

注册从远程设备发送的自定义数据的监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('customDataChange')](#oncustomdatachange20)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                    | 必填 | 说明                                                                                                    |
| -------- | ----------------------- | ---- | ------------------------------------------------------------------------------------------------------- |
| callback | Callback\<Record\<string, Object>> | 是   | 回调函数，用于接收自定义数据。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ----------------                       |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
monitorCustomDataChange(controller: avSession.AVSessionController | undefined) {
  controller!.onCustomDataChange((data: Record<string, Object>) => {
    console.info(`on_customDataChange Successfully ${data}`);
  });
}
```

## off('customDataChange')<sup>20+</sup>

off(type: 'customDataChange', callback?: Callback\<Record\<string, Object>>): void

注销自定义数据监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offCustomDataChange](#offcustomdatachange23)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                           | 是   | 取消对应的事件监听，支持的事件是'customDataChange'。         |
| callback | Callback\<Record\<string, Object>> | 否   | 注册事件监听时的回调函数。该参数为可选参数，若不填写该参数，则认为取消会话所有与此事件相关的监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息                               |
| -------- | -------------------------------------- |
| 6600101  | Session service exception.             |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
currentAVSession.off('customDataChange');
```

## offCustomDataChange<sup>23+</sup>

offCustomDataChange(callback?: Callback\<Record\<string, Object>>): void

注销自定义数据监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('customDataChange')](#offcustomdatachange20)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                    | 必填 | 说明                                                                                                    |
| -------- | ----------------------- | ---- | ------------------------------------------------------------------------------------------------------- |
| callback | Callback\<Record\<string, Object>> | 否   | 注销自定义数据的监听器。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ----------------                       |
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
controller!.offCustomDataChange();
```

## getAVPlaybackStateSync<sup>10+</sup>

getAVPlaybackStateSync(): AVPlaybackState;

使用同步方法获取当前会话的播放状态。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                                        | 说明                                                         |
| --------- | ------------------------------------------------------------ |
| [AVPlaybackState](arkts-apis-avsession-i.md#avplaybackstate10)  | 当前会话的播放状态。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
let playbackState: avSession.AVPlaybackState = avsessionController.getAVPlaybackStateSync();
```


## getAVMetadataSync<sup>10+</sup>

getAVMetadataSync(): AVMetadata

使用同步方法获取会话元数据。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                | 说明                          |
| ----------------------------------- | ----------------------------- |
| [AVMetadata](arkts-apis-avsession-i.md#avmetadata10) | 会话元数据。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
let metaData: avSession.AVMetadata = avsessionController.getAVMetadataSync();
```


## getAVCallState<sup>11+</sup>

getAVCallState(): Promise\<AVCallState>

获取通话状态数据。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                | 说明                          |
| ----------------------------------- | ----------------------------- |
| Promise<[AVCallState](arkts-apis-avsession-i.md#avcallstate11)\> | Promise对象，返回通话状态。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.getAVCallState().then((callstate: avSession.AVCallState) => {
  console.info(`Succeeded in getting AV call state: ${callstate.state}`);
});
```

## getAVCallState<sup>11+</sup>

getAVCallState(callback: AsyncCallback\<AVCallState>): void

获取通话状态数据。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                      | 必填 | 说明                       |
| -------- | ----------------------------------------- | ---- | -------------------------- |
| callback | AsyncCallback<[AVCallState](arkts-apis-avsession-i.md#avcallstate11)\> | 是   | 回调函数，返回通话状态。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.getAVCallState((callstate: avSession.AVCallState) => {
  console.info(`Succeeded in getting AV call state: ${callstate.state}`);
});
```

## getCallMetadata<sup>11+</sup>

getCallMetadata(): Promise\<CallMetadata>

获取通话会话的元数据。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                | 说明                          |
| ----------------------------------- | ----------------------------- |
| Promise<[CallMetadata](arkts-apis-avsession-i.md#callmetadata11)\> | Promise对象，返回会话元数据。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.getCallMetadata().then((calldata: avSession.CallMetadata) => {
  console.info(`Succeeded in getting call metadata, name: ${calldata.name}`);
});
```

## getCallMetadata<sup>11+</sup>

getCallMetadata(callback: AsyncCallback\<CallMetadata>): void

获取通话会话的元数据。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                      | 必填 | 说明                       |
| -------- | ----------------------------------------- | ---- | -------------------------- |
| callback | AsyncCallback<[CallMetadata](arkts-apis-avsession-i.md#callmetadata11)\> | 是   | 回调函数，返回会话元数据。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avsessionController.getCallMetadata((calldata: avSession.CallMetadata) => {
  console.info(`Succeeded in getting call metadata, name: ${calldata.name}`);
});
```

## getAVQueueTitleSync<sup>10+</sup>

getAVQueueTitleSync(): string

使用同步方法获取当前会话播放列表的名称。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型             | 说明                           |
| ---------------- | ----------------------------- |
| string | 当前会话播放列表名称。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
let currentQueueTitle: string = avsessionController.getAVQueueTitleSync();
```


## getAVQueueItemsSync<sup>10+</sup>

getAVQueueItemsSync(): Array\<AVQueueItem\>

使用同步方法获取当前会话播放列表相关信息。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                          | 说明                           |
| --------------------------------------------- | ----------------------------- |
| Array<[AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10)\> | 当前会话播放列表队列。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
let currentQueueItems: Array<avSession.AVQueueItem> = avsessionController.getAVQueueItemsSync();
```

## getOutputDeviceSync<sup>10+</sup>

getOutputDeviceSync(): OutputDeviceInfo

使用同步方法获取当前输出设备信息。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                            | 说明                              |
| ----------------------------------------------- | --------------------------------- |
| [OutputDeviceInfo](arkts-apis-avsession-i.md#outputdeviceinfo10) | 当前输出设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.|
| 6600103  | The session controller does not exist. |

**示例：**

```ts
let currentOutputDevice: avSession.OutputDeviceInfo = avsessionController.getOutputDeviceSync();
```

## isActiveSync<sup>10+</sup>

isActiveSync(): boolean

使用同步方法判断会话是否被激活。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型              | 说明                                                         |
| ----------------- | ------------------------------------------------------------ |
| boolean | 会话是否为激活状态，true表示被激活，false表示禁用。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
let isActive: boolean = avsessionController.isActiveSync();
```

## getValidCommandsSync<sup>10+</sup>

getValidCommandsSync(): Array\<AVControlCommandType\>

使用同步方法获取会话支持的有效命令。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                                         | 说明                              |
| ------------------------------------------------------------ | --------------------------------- |
| Array<[AVControlCommandType](arkts-apis-avsession-t.md#avcontrolcommandtype10)\> | 会话支持的有效命令的集合。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
let validCommands: Array<avSession.AVControlCommandType> = avsessionController.getValidCommandsSync();
```

## getSupportedPlaySpeeds

getSupportedPlaySpeeds(): Promise\<Array\<double>>

获取应用支持的播放倍速列表。使用Promise异步回调。

该列表通过[setSupportedPlaySpeeds](arkts-apis-avsession-AVSession.md#setsupportedplayspeeds)接口设置。如果应用未设置或者设置为空列表，则返回空列表。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<Array\<double>> | Promise对象。返回支持的播放倍速列表。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avcontroller.getSupportedPlaySpeeds().then((speeds: double[]) => {
  console.info(`Succeeded in getting supported play speeds, size: ${speeds.length}`);
});
```

## getSupportedLoopModes

getSupportedLoopModes(): Promise\<Array\<LoopMode>>

获取应用支持的循环模式列表。使用Promise异步回调。

该列表通过[setSupportedLoopModes](arkts-apis-avsession-AVSession.md#setsupportedloopmodes)接口设置。如果应用未设置或者设置为空列表，则返回空列表。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<Array\<[LoopMode](arkts-apis-avsession-e.md#loopmode10)>> | Promise对象。返回支持的循环模式列表。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avcontroller.getSupportedLoopModes().then((loopModes: avSession.LoopMode[]) => {
  console.info(`Succeeded in getting supported loop modes, size: ${loopModes.length}`);
});
```

## getMediaCenterControlType

getMediaCenterControlType(): Promise\<Array\<AVMediaCenterControlType>>

获取应用通过[setMediaCenterControlType](arkts-apis-avsession-AVSession.md#setmediacentercontroltype)接口设置优先显示的控制类型列表。使用Promise异步回调。

如果应用未设置或者设置为空列表，则返回空列表。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<Array\<[AVMediaCenterControlType](arkts-apis-avsession-t.md#avmediacentercontroltype)>> | Promise对象。返回应用希望优先显示的控制类型列表。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avcontroller.getMediaCenterControlType().then((types: avSession.AVMediaCenterControlType[]) => {
  console.info(`Succeeded in getting media center control types, size: ${types.length}`);
});
```

## onMediaCenterControlTypeChanged

onMediaCenterControlTypeChanged(callback: Callback\<Array\<AVMediaCenterControlType>>): void

注册控制类型列表变化的监听事件。使用callback异步回调。

其中控制类型列表由应用通过[setMediaCenterControlType](arkts-apis-avsession-AVSession.md#setmediacentercontroltype)接口设置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型                   | 必填 | 说明                            |
| ------ | ---------------------- | ---- | -------------------------------- |
| callback   | Callback\<Array\<[AVMediaCenterControlType](arkts-apis-avsession-t.md#avmediacentercontroltype)>> | 是   | 回调函数。返回变化后的控制类型列表。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avcontroller.onMediaCenterControlTypeChanged((types: avSession.AVMediaCenterControlType[]) => {
  console.info(`Media center control types changed, size: ${types.length}`);
});
```

## offMediaCenterControlTypeChanged

offMediaCenterControlTypeChanged(callback?: Callback\<Array\<AVMediaCenterControlType>>): void

取消控制类型列表变化的监听事件。

取消后将不再对该事件进行监听。其中控制类型列表由应用通过[setMediaCenterControlType](arkts-apis-avsession-AVSession.md#setmediacentercontroltype)接口设置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型                   | 必填 | 说明                            |
| ------ | ---------------------- | ---- | -------------------------------- |
| callback   | Callback\<Array\<[AVMediaCenterControlType](arkts-apis-avsession-t.md#avmediacentercontroltype)>> | 否   | 回调函数。该参数为可选参数，若不填写该参数，则认为对所有控制类型列表变化事件取消监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avcontroller.offMediaCenterControlTypeChanged();
```

## onSupportedPlaySpeedsChange

onSupportedPlaySpeedsChange(callback: Callback\<Array\<double>>): void

注册支持的播放倍速列表变化的监听事件。使用callback异步回调。

其中播放倍速列表由应用通过[setSupportedPlaySpeeds](arkts-apis-avsession-AVSession.md#setsupportedplayspeeds)接口设置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型                   | 必填 | 说明                            |
| ------ | ---------------------- | ---- | -------------------------------- |
| callback  | Callback\<Array\<double>> | 是   | 回调函数。返回变化后支持的播放倍速列表。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avcontroller.onSupportedPlaySpeedsChange((speeds: double[]) => {
  console.info(`Supported play speeds changed, size: ${speeds.length}`);
});
```

## offSupportedPlaySpeedsChange

offSupportedPlaySpeedsChange(callback?: Callback\<Array\<double>>): void

取消支持的播放倍速列表变化事件监听。

取消后将不再对该事件进行监听。其中播放倍速列表由应用通过[setSupportedPlaySpeeds](arkts-apis-avsession-AVSession.md#setsupportedplayspeeds)接口设置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型                   | 必填 | 说明                            |
| ------ | ---------------------- | ---- | -------------------------------- |
| callback   | Callback\<Array\<double>> | 否   | 回调函数。该参数为可选参数，若不填写该参数，则认为对所有支持的播放倍速列表变化事件取消监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avcontroller.offSupportedPlaySpeedsChange();
```

## onSupportedLoopModesChange

onSupportedLoopModesChange(callback: Callback\<Array\<LoopMode>>): void

注册支持的循环模式列表变化的监听事件。使用callback异步回调。

其中循环模式列表由应用通过[setSupportedLoopModes](arkts-apis-avsession-AVSession.md#setsupportedloopmodes)接口设置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型                   | 必填 | 说明                            |
| ------ | ---------------------- | ---- | -------------------------------- |
| callback   | Callback\<Array\<[LoopMode](arkts-apis-avsession-e.md#loopmode10)>> | 是   | 回调函数。返回变化后支持的循环模式列表。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avcontroller.onSupportedLoopModesChange((loopModes: avSession.LoopMode[]) => {
  console.info(`Supported loop modes changed, size: ${loopModes.length}`);
});
```

## offSupportedLoopModesChange

offSupportedLoopModesChange(callback?: Callback\<Array\<LoopMode>>): void

取消支持的循环模式列表变化事件监听。

取消后将不再对该事件进行监听。其中循环模式列表由应用通过[setSupportedLoopModes](arkts-apis-avsession-AVSession.md#setsupportedloopmodes)接口设置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型                   | 必填 | 说明                            |
| ------ | ---------------------- | ---- | -------------------------------- |
| callback   | Callback\<Array\<[LoopMode](arkts-apis-avsession-e.md#loopmode10)>> | 否   | 回调函数。该参数为可选参数，若不填写该参数，则认为对所有支持的循环模式列表变化事件取消监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**示例：**

```ts
avcontroller.offSupportedLoopModesChange();
```
