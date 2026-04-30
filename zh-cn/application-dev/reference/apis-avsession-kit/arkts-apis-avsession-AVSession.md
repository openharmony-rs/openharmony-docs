# Interface (AVSession)
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @liao_qian-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

调用[avSession.createAVSession](arkts-apis-avsession-f.md#avsessioncreateavsession10)后，返回会话的实例，可以获得会话ID，完成设置元数据，播放状态信息等操作。

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

**系统能力：** SystemCapability.Multimedia.AVSession.Core

| 名称      | 类型   | 只读 | 可选 | 说明                          |
| :-------- | :----- | :--- | :--- | :---------------------------- |
| sessionId<sup>10+</sup> | string | 是   | 否   | AVSession对象唯一的会话标识。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 10 <br>**ArkTS-Sta起始版本：** 23 |
| sessionType<sup>10+</sup> | [AVSessionType](arkts-apis-avsession-t.md#avsessiontype10) | 是   | 否   | AVSession会话类型。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 10 <br>**ArkTS-Sta起始版本：** 23 |
| sessionTag<sup>22+</sup> | string | 是 | 否 | AVSession会话的自定义标签信息。<br>**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 22 <br>**ArkTS-Sta起始版本：** 24 |

**示例：**

```ts
let sessionId: string = currentAVSession.sessionId;
let sessionType: avSession.AVSessionType = currentAVSession.sessionType;
```


## setAVMetadata<sup>10+</sup>

setAVMetadata(data: AVMetadata): Promise\<void>

设置会话元数据。使用Promise异步回调。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                      | 必填 | 说明         |
| ------ | ------------------------- | ---- | ------------ |
| data   | [AVMetadata](arkts-apis-avsession-i.md#avmetadata10) | 是   | 会话元数据。 |

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<void> | Promise对象。当元数据设置成功，无返回结果，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
let metadata: avSession.AVMetadata = {
  assetId: "121278",
  title: "lose yourself",
  artist: "Eminem",
  author: "ST",
  album: "Slim shady",
  writer: "ST",
  composer: "ST",
  duration: 2222,
  mediaImage: "https://www.example.com/example.jpg",
  subtitle: "8 Mile",
  description: "Rap",
  // LRC中有两类元素：一种是时间标签+歌词，一种是ID标签。
  // 例如：[00:25.44]xxx\r\n[00:26.44]xxx\r\n
  lyric: "lrc格式歌词内容",
  // singleLyricText字段存储单条歌词文本，不包含时间戳。
  // 例如："单条歌词内容"。
  singleLyricText: "单条歌词内容",
  previousAssetId: "121277",
  nextAssetId: "121279"
};
currentAVSession.setAVMetadata(metadata).then(() => {
  console.info('Succeeded in setting AVMetadata.');
});
```

## setAVMetadata<sup>10+</sup>

setAVMetadata(data: AVMetadata, callback: AsyncCallback\<void>): void

设置会话元数据。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                                                         |
| -------- | ---------------------------------------------------- | ---- | ------------------------------------------------------------ |
| data     | [AVMetadata](arkts-apis-avsession-i.md#avmetadata10) | 是   | 会话元数据。                                                 |
| callback | AsyncCallback\<void>                                 | 是   | 回调函数。<br>ArkTS-Dyn：当元数据设置成功，err为undefined，否则返回错误对象。<br>ArkTS-Sta：当元数据设置成功，err为null，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
let metadata: avSession.AVMetadata = {
  assetId: "121278",
  title: "lose yourself",
  artist: "Eminem",
  author: "ST",
  album: "Slim shady",
  writer: "ST",
  composer: "ST",
  duration: 2222,
  mediaImage: "https://www.example.com/example.jpg",
  subtitle: "8 Mile",
  description: "Rap",
  // LRC中有两类元素：一种是时间标签+歌词，一种是ID标签。
  // 例如：[00:25.44]xxx\r\n[00:26.44]xxx\r\n
  lyric: "lrc格式歌词内容",
  // singleLyricText字段存储单条歌词文本，不包含时间戳。
  // 例如："单条歌词内容"。
  singleLyricText: "单条歌词内容",
  previousAssetId: "121277",
  nextAssetId: "121279"
};
currentAVSession.setAVMetadata(metadata, () => {
  console.info('Succeeded in setting AVMetadata.');
});
```

## setCallMetadata<sup>11+</sup>

setCallMetadata(data: CallMetadata): Promise\<void>

设置通话会话元数据。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                      | 必填 | 说明         |
| ------ | ------------------------- | ---- | ------------ |
| data   | [CallMetadata](arkts-apis-avsession-i.md#callmetadata11) | 是   | 通话会话元数据。 |

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<void> | Promise对象。当通话元数据设置成功，无返回结果，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
import { image } from '@kit.ImageKit';
import { resourceManager } from '@kit.LocalizationKit';
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  build() {
    Column() {
      Text('Hello World')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
    }
    .width('100%')
    .height('100%')
  }
}

class CallManager {
  private currentAVSession: avSession.AVSession | null = null;

  async setCallMetadata() {
    try {
      let value = await resourceManager.getSysResourceManager().getRawFileContent('IMAGE_URI');
      let imageSource = await image.createImageSource(value.buffer);
      let imagePixel = await imageSource.createPixelMap({ desiredSize: { width: 150, height: 150 } });
      let calldata: avSession.CallMetadata = {
        name: "xiaoming",
        phoneNumber: "111xxxxxxxx",
        avatar: imagePixel
      };
      await this.currentAVSession?.setCallMetadata(calldata);
      console.info('Succeeded in setting call metadata.');
    }
  }
}
```

## setCallMetadata<sup>11+</sup>

setCallMetadata(data: CallMetadata, callback: AsyncCallback\<void>): void

设置通话会话元数据。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                      | 必填 | 说明                                  |
| -------- | ------------------------- | ---- | ------------------------------------- |
| data     | [CallMetadata](arkts-apis-avsession-i.md#callmetadata11) | 是   | 通话会话元数据。                          |
| callback | AsyncCallback\<void>      | 是   | 回调函数。<br>ArkTS-Dyn：当通话元数据设置成功，err为undefined，否则返回错误对象。<br>ArkTS-Sta：当通话元数据设置成功，err为null，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
import { image } from '@kit.ImageKit';
import { resourceManager } from '@kit.LocalizationKit';
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  build() {
    Column() {
      Text('Hello World')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
    }
    .width('100%')
    .height('100%')
  }
}

class CallManager {
  private currentAVSession: avSession.AVSession | null = null;

  async setCallMetadata() {
    try {
      let value = await resourceManager.getSysResourceManager().getRawFileContent('IMAGE_URI');
      let imageSource = await image.createImageSource(value.buffer);
      let imagePixel = await imageSource.createPixelMap({ desiredSize: { width: 150, height: 150 } });
      let calldata: avSession.CallMetadata = {
        name: "xiaoming",
        phoneNumber: "111xxxxxxxx",
        avatar: imagePixel
      };
      this.currentAVSession?.setCallMetadata(calldata, () => {
        console.info('Succeeded in setting call metadata.');
      });
    }
  }
}
```

## setAVCallState<sup>11+</sup>

setAVCallState(state: AVCallState): Promise\<void>

设置通话状态。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                      | 必填 | 说明         |
| ------ | ------------------------- | ---- | ------------ |
| state   | [AVCallState](arkts-apis-avsession-i.md#avcallstate11) | 是   | 通话状态。 |

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<void> | Promise对象。当通话元数据设置成功，无返回结果，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
let calldata: avSession.AVCallState = {
  state: avSession.CallState.CALL_STATE_ACTIVE,
  muted: false
};
currentAVSession.setAVCallState(calldata).then(() => {
  console.info('Succeeded in setting AVCallState.');
});
```

## setAVCallState<sup>11+</sup>

setAVCallState(state: AVCallState, callback: AsyncCallback\<void>): void

设置通话状态。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                      | 必填 | 说明                                  |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state     | [AVCallState](arkts-apis-avsession-i.md#avcallstate11) | 是   | 通话状态。                          |
| callback | AsyncCallback\<void>      | 是   | 回调函数。<br>ArkTS-Dyn：当通话元数据设置成功，err为undefined，否则返回错误对象。<br>ArkTS-Sta：当通话元数据设置成功，err为null，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
let avcalldata: avSession.AVCallState = {
  state: avSession.CallState.CALL_STATE_ACTIVE,
  muted: false
};
currentAVSession.setAVCallState(avcalldata, () => {
  console.info('Succeeded in setting AVCallState.');
});
```

## setAVPlaybackState<sup>10+</sup>

setAVPlaybackState(state: AVPlaybackState): Promise\<void>

设置会话播放状态。使用Promise异步回调。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                | 必填 | 说明                                           |
| ------ | ----------------------------------- | ---- | ---------------|
| state   | [AVPlaybackState](arkts-apis-avsession-i.md#avplaybackstate10) | 是   | 会话播放状态，包括状态、倍数、循环模式等信息。 |

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<void> | Promise对象。当播放状态设置成功，无返回结果，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
let playbackState: avSession.AVPlaybackState = {
  state:avSession.PlaybackState.PLAYBACK_STATE_PLAY,
  speed: 1.0,
  position:{elapsedTime:10, updateTime:(new Date()).getTime()},
  bufferedTime:1000,
  loopMode:avSession.LoopMode.LOOP_MODE_SINGLE,
  isFavorite:true
};
currentAVSession.setAVPlaybackState(playbackState).then(() => {
  console.info('Succeeded in setting AVPlaybackState.');
});
```

## setAVPlaybackState<sup>10+</sup>

setAVPlaybackState(state: AVPlaybackState, callback: AsyncCallback\<void>): void

设置会话播放状态。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                | 必填 | 说明                                           |
| -------- | ----------------------------------- | ---- | ---------------|
| state     | [AVPlaybackState](arkts-apis-avsession-i.md#avplaybackstate10) | 是   | 会话播放状态，包括状态、倍数、循环模式等信息。 |
| callback | AsyncCallback\<void>                | 是   | 回调函数。<br>ArkTS-Dyn：当播放状态设置成功，err为undefined，否则返回错误对象。<br>ArkTS-Sta：当播放状态设置成功，err为null，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
let PlaybackState: avSession.AVPlaybackState = {
  state:avSession.PlaybackState.PLAYBACK_STATE_PLAY,
  speed: 1.0,
  position:{elapsedTime:10, updateTime:(new Date()).getTime()},
  bufferedTime:1000,
  loopMode:avSession.LoopMode.LOOP_MODE_SINGLE,
  isFavorite:true
};
currentAVSession.setAVPlaybackState(PlaybackState, () => {
  console.info('Succeeded in setting AVPlaybackState.');
});
```

## setLaunchAbility<sup>10+</sup>

setLaunchAbility(ability: WantAgent): Promise\<void>

设置一个WantAgent用于拉起会话的Ability。使用Promise异步回调。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                          | 必填 | 说明     |
| ------- | --------------| ---- | ----------------------------|
| ability | [WantAgent](../apis-ability-kit/js-apis-app-ability-wantAgent.md) | 是   | 应用的相关属性信息，如bundleName，abilityName，deviceId等。 |

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<void> | Promise对象。当Ability设置成功，无返回结果，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
import { wantAgent } from '@kit.AbilityKit';

// WantAgentInfo对象。
let wantAgentInfo: wantAgent.WantAgentInfo = {
  wants: [
    {
      deviceId: "deviceId",
      bundleName: "com.example.myapplication",
      abilityName: "EntryAbility",
      action: "action1",
      entities: ["entity1"],
      type: "MIMETYPE",
      uri: "key = {true,true,false}",
      parameters:
        {
          mykey0: 2222,
          mykey1: [1, 2, 3],
          mykey2: "[1, 2, 3]",
          mykey3: "ssssssssssssssssssssssssss",
          mykey4: [false, true, false],
          mykey5: ["qqqqq", "wwwwww", "aaaaaaaaaaaaaaaaa"],
          mykey6: true
        }
    }
  ],
  operationType: wantAgent.OperationType.START_ABILITIES,
  requestCode: 0,
  wantAgentFlags:[wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
}

wantAgent.getWantAgent(wantAgentInfo).then((agent) => {
  currentAVSession.setLaunchAbility(agent).then(() => {
    console.info('Succeeded in setting launch ability.');
  });
});
```

## setLaunchAbility<sup>10+</sup>

setLaunchAbility(ability: WantAgent, callback: AsyncCallback\<void>): void

设置一个WantAgent用于拉起会话的Ability。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                          | 必填 | 说明     |
| -------- | --------------| ---- | --------- |
| ability  | [WantAgent](../apis-ability-kit/js-apis-app-ability-wantAgent.md) | 是   | 应用的相关属性信息，如bundleName，abilityName，deviceId等。  |
| callback | AsyncCallback\<void>                          | 是   | 回调函数。<br>ArkTS-Dyn：当Ability设置成功，err为undefined，否则返回错误对象。<br>ArkTS-Sta：当Ability设置成功，err为null，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
import { wantAgent } from '@kit.AbilityKit';

// WantAgentInfo对象。
let wantAgentInfo: wantAgent.WantAgentInfo = {
  wants: [
    {
      deviceId: "deviceId",
      bundleName: "com.example.myapplication",
      abilityName: "EntryAbility",
      action: "action1",
      entities: ["entity1"],
      type: "MIMETYPE",
      uri: "key = {true,true,false}",
      parameters:
        {
          mykey0: 2222,
          mykey1: [1, 2, 3],
          mykey2: "[1, 2, 3]",
          mykey3: "ssssssssssssssssssssssssss",
          mykey4: [false, true, false],
          mykey5: ["qqqqq", "wwwwww", "aaaaaaaaaaaaaaaaa"],
          mykey6: true
        }
    }
  ],
  operationType: wantAgent.OperationType.START_ABILITIES,
  requestCode: 0,
  wantAgentFlags:[wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
}

wantAgent.getWantAgent(wantAgentInfo).then((agent) => {
  currentAVSession.setLaunchAbility(agent, () => {
    console.info('Succeeded in setting launch ability.');
  });
});
```

## dispatchSessionEvent<sup>10+</sup>

ArkTS-Dyn: dispatchSessionEvent(event: string, args: {[key: string]: Object}): Promise\<void>

ArkTS-Sta: dispatchSessionEvent(event: string, args: Record<string, Object>): Promise\<void>

媒体提供方设置会话内自定义事件。使用Promise异步回调。

包括事件名和键值对形式的事件内容。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                          | 必填 | 说明     |
| ------- | --------------| ---- | ----------------------------|
| event | string | 是   | 需要设置的会话事件的名称。 |
| args | ArkTS-Dyn: {[key: string]: Object}<br>ArkTS-Sta: Record<string, Object> | 是   | 需要传递的会话事件内容。 |

> **说明：**
> 参数args支持的数据类型有：字符串、数字、布尔、对象、数组和文件描述符等，详细介绍请参见[@ohos.app.ability.Want(Want)](../apis-ability-kit/js-apis-app-ability-want.md)。

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<void> | Promise对象。当事件设置成功，无返回结果，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed.<br>**ArkTS模式：** 该错误码仅适用于ArkTS-Dyn。 |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

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
          .onClick(()=>{
            let currentAVSession: avSession.AVSession | undefined = undefined;
            let tag = "createNewSession";
            let context: Context = this.getUIContext().getHostContext() as Context;

            avSession.createAVSession(context, tag, "audio", (data: avSession.AVSession) => {
              currentAVSession = data;
              let eventName = "dynamic_lyric";
              if (currentAVSession !== undefined) {
                (currentAVSession as avSession.AVSession).dispatchSessionEvent(eventName, {lyric : "This is lyric"}).then(() => {
                  console.info('Succeeded in dispatching session event.');
                })
              }
            });
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

## dispatchSessionEvent<sup>10+</sup>

ArkTS-Dyn: dispatchSessionEvent(event: string, args: {[key: string]: Object}, callback: AsyncCallback\<void>): void

ArkTS-Sta: dispatchSessionEvent(event: string, args: Record<string, Object>, callback: AsyncCallback\<void>): void

媒体提供方设置一个会话内自定义事件。使用callback异步回调。

包括事件名和键值对形式的事件内容。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                          | 必填 | 说明     |
| ------- | --------------| ---- | ----------------------------|
| event | string | 是   | 需要设置的会话事件的名称。 |
| args | ArkTS-Dyn: {[key: string]: Object}<br>ArkTS-Sta: Record<string, Object> | 是   | 需要传递的会话事件内容。 |
| callback | AsyncCallback\<void>                          | 是   | 回调函数。<br>ArkTS-Dyn：当会话事件设置成功，err为undefined，否则返回错误对象。<br>ArkTS-Sta：当会话事件设置成功，err为null，否则返回错误对象。 |

> **说明：**

> 参数args支持的数据类型有：字符串、数字、布尔、对象、数组和文件描述符等，详细介绍请参见[@ohos.app.ability.Want(Want)](../apis-ability-kit/js-apis-app-ability-want.md)。

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed.<br>**ArkTS模式：** 该错误码仅适用于ArkTS-Dyn。 |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

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
          .onClick(()=>{
            let currentAVSession: avSession.AVSession | undefined = undefined;
            let tag = "createNewSession";
            let context: Context = this.getUIContext().getHostContext() as Context;

            avSession.createAVSession(context, tag, "audio", (data: avSession.AVSession) => {
              currentAVSession = data;
              let eventName: string = "dynamic_lyric";
              if (currentAVSession !== undefined) {
                (currentAVSession as avSession.AVSession).dispatchSessionEvent(eventName, {lyric : "This is lyric"}, () => {
                  console.info('Succeeded in dispatching session event.');
                })
              }
            });
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

## setAVQueueTitle<sup>10+</sup>

setAVQueueTitle(title: string): Promise\<void>

设置媒体播放列表名称。使用Promise异步回调。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型   | 必填 | 说明           |
| ------ | ------ | ---- | -------------- |
| title  | string | 是   | 播放列表的名称。 |

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<void> | Promise对象。当播放列表设置成功，无返回结果，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
import { image } from '@kit.ImageKit';
import { resourceManager } from '@kit.LocalizationKit';
import { avSession } from '@kit.AVSessionKit';

interface ExtrasType {
  extras: string;
}

@Entry
@Component
struct Index {
  build() {
    Column() {
    }
  }
}

let currentAVSession: avSession.AVSession;

async function setAVQueueItems() {
  try {
    let value = await resourceManager.getSysResourceManager().getRawFileContent('IMAGE_URI');
    let imageSource = await image.createImageSource(value.buffer);
    let imagePixel = await imageSource.createPixelMap({desiredSize:{width: 150, height: 150}});
    let queueItemDescription_1: avSession.AVMediaDescription = {
      assetId: '001',
      title: 'music_name',
      subtitle: 'music_sub_name',
      description: 'music_description',
      mediaImage : imagePixel,
      extras: {extras:'any'}
    };
    let queueItem_1: avSession.AVQueueItem = {
      itemId: 1,
      description: queueItemDescription_1
    } as avSession.AVQueueItem;
    let queueItemDescription_2: avSession.AVMediaDescription = {
      assetId: '002',
      title: 'music_name',
      subtitle: 'music_sub_name',
      description: 'music_description',
      mediaImage: imagePixel,
      extras: {extras:'any'}
    };
    let queueItem_2: avSession.AVQueueItem = {
      itemId: 2,
      description: queueItemDescription_2
    } as avSession.AVQueueItem;
    let queueItemsArray: avSession.AVQueueItem[] = [queueItem_1, queueItem_2];
    currentAVSession.setAVQueueItems(queueItemsArray).then(() => {
      console.info('Succeeded in setting AVQueueItems.');
    });
  }
}
```

## setAVQueueTitle<sup>10+</sup>

setAVQueueTitle(title: string, callback: AsyncCallback\<void>): void

设置媒体播放列表名称。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                  | 必填 | 说明     |
| -------- | --------------------- | ---- | ----------------------------|
| title    | string                | 是   | 播放列表名称字段。                          |
| callback | AsyncCallback\<void>  | 是   | 回调函数。<br>ArkTS-Dyn：当播放状态设置成功，err为undefined，否则返回错误对象。<br>ArkTS-Sta：当播放状态设置成功，err为null，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
let queueTitle = 'QUEUE_TITLE';
currentAVSession.setAVQueueTitle(queueTitle).then(() => {
  console.info('Succeeded in setting AVQueueTitle.');
});
```

## setExtras<sup>10+</sup>

ArkTS-Dyn: setExtras(extras: {[key: string]: Object}): Promise\<void>

ArkTS-Sta: setExtras(extras: Record<string, Object>): Promise\<void>

媒体提供方设置键值对形式的自定义媒体数据包。使用Promise异步回调。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                          | 必填 | 说明     |
| ------- | --------------| ---- | ----------------------------|
| extras | ArkTS-Dyn: {[key: string]: Object}<br>ArkTS-Sta: Record<string, Object> | 是   | 需要传递的自定义媒体数据包键值对。 |

> **说明：**

> 参数extras支持的数据类型有：字符串、数字、布尔、对象、数组和文件描述符等，详细介绍请参见[@ohos.app.ability.Want(Want)](../apis-ability-kit/js-apis-app-ability-want.md)。

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<void> | Promise对象。当自定义媒体数据包设置成功，无返回结果，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed.<br>**ArkTS模式：** 该错误码仅适用于ArkTS-Dyn。 |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

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
          .onClick(() => {
            let currentAVSession: avSession.AVSession | undefined = undefined;
            let tag = "createNewSession";
            let context: Context = this.getUIContext().getHostContext() as Context;

            avSession.createAVSession(context, tag, "audio", (data: avSession.AVSession) => {
              currentAVSession = data;
              if (currentAVSession !== undefined) {
(currentAVSession as avSession.AVSession).setExtras({extras : "This is custom media packet"}).then(() => {
                  console.info('Succeeded in setting extras.');
                })
              }
            });
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

## setExtras<sup>10+</sup>

ArkTS-Dyn: setExtras(extras: {[key: string]: Object}, callback: AsyncCallback\<void>): void

ArkTS-Sta: setExtras(extras: Record<string, Object>, callback: AsyncCallback\<void>): void

媒体提供方设置键值对形式的自定义媒体数据包。使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                          | 必填 | 说明     |
| ------- | --------------| ---- | ----------------------------|
| extras | ArkTS-Dyn: {[key: string]: Object}<br>ArkTS-Sta: Record<string, Object> | 是   | 需要传递的自定义媒体数据包键值对。 |
| callback | AsyncCallback\<void>                          | 是   | 回调函数。<br>ArkTS-Dyn：当自定义媒体数据包设置成功，err为undefined，否则返回错误对象。<br>ArkTS-Sta：当自定义媒体数据包设置成功，err为null，否则返回错误对象。 |

> **说明：**

> 参数extras支持的数据类型有：字符串、数字、布尔、对象、数组和文件描述符等，详细介绍请参见[@ohos.app.ability.Want(Want)](../apis-ability-kit/js-apis-app-ability-want.md)。

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed.<br>**ArkTS模式：** 该错误码仅适用于ArkTS-Dyn。 |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

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
          .onClick(()=>{
            let currentAVSession: avSession.AVSession | undefined = undefined;
            let tag = "createNewSession";
            let context: Context = this.getUIContext().getHostContext() as Context;

            avSession.createAVSession(context, tag, "audio", (data: avSession.AVSession) => {
              currentAVSession = data;
              if (currentAVSession !== undefined) {
                (currentAVSession as avSession.AVSession).setExtras({extras : "This is custom media packet"}, () => {
                  console.info('Succeeded in setting extras.');
                })
              }
            });
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
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;

          avSession.createAVSession(context, tag, "audio", (err, data: avSession.AVSession) => {
            currentAVSession = data;
          });
          if (currentAVSession !== undefined) {
            (currentAVSession as avSession.AVSession).setDesktopLyricVisible(true).then(() => {
              console.info('setDesktopLyricVisible successfully');
            })
          }
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
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          avSession.createAVSession(context, tag, "audio", (err, data: avSession.AVSession) => {
            currentAVSession = data;
          });
          if (currentAVSession !== undefined) {
            (currentAVSession as avSession.AVSession).isDesktopLyricVisible().then((visible: boolean) => {
              console.info(`isDesktopLyricVisible: ${visible}`);
            })
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## onDesktopLyricVisibilityChanged<sup>23+</sup>

onDesktopLyricVisibilityChanged(callback: Callback\<boolean>): void

显示桌面歌词状态变更的事件监听。使用callback异步回调。

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
| 6600102  | The session does not exist. |

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
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          avSession.createAVSession(context, tag, "audio", (err, data: avSession.AVSession) => {
            currentAVSession = data;
          });
          if (currentAVSession !== undefined) {
            try {
              (currentAVSession as avSession.AVSession).onDesktopLyricVisibilityChanged((visible: boolean) => {
                console.info(`desktop lyric visible state: ${visible}`);
              });
            } catch (err) {
            }
          }
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
| 6600102  | The session does not exist. |

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
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          avSession.createAVSession(context, tag, "audio", (err, data: avSession.AVSession) => {
            currentAVSession = data;
          });
          if (currentAVSession !== undefined) {
            try {
              (currentAVSession as avSession.AVSession).offDesktopLyricVisibilityChanged();
            } catch (err) {
            }
          }
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
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;

          avSession.createAVSession(context, tag, "audio", (err, data: avSession.AVSession) => {
            currentAVSession = data;
          });
          if (currentAVSession !== undefined) {
            let state: avSession.DesktopLyricState = {
              isLocked: true,
            };
            (currentAVSession as avSession.AVSession).setDesktopLyricState(state).then(() => {
              console.info('setDesktopLyricState successfully');
            })
          }
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
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;

          avSession.createAVSession(context, tag, "audio", (err, data: avSession.AVSession) => {
            currentAVSession = data;
          });
          if (currentAVSession !== undefined) {
            (currentAVSession as avSession.AVSession).getDesktopLyricState()
              .then((state: avSession.DesktopLyricState) => {
                console.info(`getDesktopLyricState: ${state.isLocked}`);
              })
              
          }
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
| 6600102  | The session does not exist. |

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
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;

          avSession.createAVSession(context, tag, "audio", (err, data: avSession.AVSession) => {
            currentAVSession = data;
          });
          if (currentAVSession !== undefined) {
            try {
              (currentAVSession as avSession.AVSession).onDesktopLyricStateChanged((state: avSession.DesktopLyricState) => {
                console.info(`desktop lyric isLocked : ${state.isLocked}`);
              })
            } catch (err) {
            }
          }
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
| callback   | Callback\<[DesktopLyricState](./arkts-apis-avsession-i.md#desktoplyricstate23)> | 否   | 回调函数。当事件监听注销成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有桌面歌词状态变更事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

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
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          avSession.createAVSession(context, tag, "audio", (err, data: avSession.AVSession) => {
            currentAVSession = data;
          });
          if (currentAVSession !== undefined) {
            try {
              (currentAVSession as avSession.AVSession).offDesktopLyricStateChanged();
            } catch (err) {
            }
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## sendCustomData<sup>20+</sup>

sendCustomData(data: Record\<string, Object>): Promise\<void>

发送私有数据到远端设备。使用Promise异步回调。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 20开始，该接口支持在原子化服务中使用。

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

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102 | The session does not exist. |

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
          .onClick(()=>{
            let currentAVSession: avSession.AVSession | undefined = undefined;
            let tag = "createNewSession";
            let context: Context = this.getUIContext().getHostContext() as Context;

            avSession.createAVSession(context, tag, "audio", (data: avSession.AVSession) => {
            currentAVSession = data;
            });
            if (currentAVSession !== undefined) {
            (currentAVSession as avSession.AVSession).sendCustomData({customData : "This is custom data"}).then(() => {
                console.info('Succeeded in sending custom data.');
            })
            }
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

## enableDesktopLyric<sup>23+</sup>

enableDesktopLyric(enable: boolean): Promise\<void>

当前会话是否启用桌面歌词功能。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| ------ | ------ | ---- | ---------- |
| enable | boolean | 是   | 是否启用桌面歌词。true表示启用，false表示不启用。 |

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
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;

          avSession.createAVSession(context, tag, "audio", (data: avSession.AVSession) => {
            currentAVSession = data;
          });
          if (currentAVSession !== undefined) {
            (currentAVSession as avSession.AVSession).enableDesktopLyric(true).then(() => {
              console.info('Succeeded in enabling desktop lyric.');
            })
          }
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
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;

          avSession.createAVSession(context, tag, "audio", (data: avSession.AVSession) => {
            currentAVSession = data;
          });
          if (currentAVSession !== undefined) {
            (currentAVSession as avSession.AVSession).setDesktopLyricVisible(true).then(() => {
              console.info('Succeeded in setting desktop lyric visible.');
            })
          }
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
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          avSession.createAVSession(context, tag, "audio", (data: avSession.AVSession) => {
            currentAVSession = data;
          });
          if (currentAVSession !== undefined) {
            (currentAVSession as avSession.AVSession).isDesktopLyricVisible().then((visible: boolean) => {
              console.info(`isDesktopLyricVisible: ${visible}`);
            })
          }
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
| 6600102  | The session does not exist. |

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
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          avSession.createAVSession(context, tag, "audio", (data: avSession.AVSession) => {
            currentAVSession = data;
          });
          if (currentAVSession !== undefined) {
            (currentAVSession as avSession.AVSession).onDesktopLyricVisibilityChanged((visible: boolean) => {
              console.info(`desktop lyric visible state: ${visible}`);
            });
          }
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
| callback   | Callback\<boolean> | 否   | 回调函数。当事件监听注销成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有显示桌面歌词状态变更事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

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
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          avSession.createAVSession(context, tag, "audio", (data: avSession.AVSession) => {
            currentAVSession = data;
          });
          if (currentAVSession !== undefined) {
            (currentAVSession as avSession.AVSession).offDesktopLyricVisibilityChanged();
          }
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
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;

          avSession.createAVSession(context, tag, "audio", (data: avSession.AVSession) => {
            currentAVSession = data;
          });
          if (currentAVSession !== undefined) {
            let state: avSession.DesktopLyricState = {
              isLocked: true,
            };
            (currentAVSession as avSession.AVSession).setDesktopLyricState(state).then(() => {
              console.info('Succeeded in setting desktop lyric state.');
            })
          }
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
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;

          avSession.createAVSession(context, tag, "audio", (data: avSession.AVSession) => {
            currentAVSession = data;
          });
          if (currentAVSession !== undefined) {
            (currentAVSession as avSession.AVSession).getDesktopLyricState()
              .then((state: avSession.DesktopLyricState) => {
                console.info(`getDesktopLyricState: ${state.isLocked}`);
              })
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## onDesktopLyricStateChanged<sup>23+</sup>

onDesktopLyricStateChanged(callback: Callback\<DesktopLyricState>): void

桌面歌词状态变更的事件监听。使用callback异步回调。

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
| 6600102  | The session does not exist. |

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
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;

          avSession.createAVSession(context, tag, "audio", (data: avSession.AVSession) => {
            currentAVSession = data;
          });
          if (currentAVSession !== undefined) {
            (currentAVSession as avSession.AVSession).onDesktopLyricStateChanged((state: avSession.DesktopLyricState) => {
              console.info(`desktop lyric isLocked : ${state.isLocked}`);
            })
          }
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
| 6600102  | The session does not exist. |

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
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          avSession.createAVSession(context, tag, "audio", (data: avSession.AVSession) => {
            currentAVSession = data;
          });
          if (currentAVSession !== undefined) {
            (currentAVSession as avSession.AVSession).offDesktopLyricStateChanged();
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## getController<sup>10+</sup>

getController(): Promise\<AVSessionController>

获取本会话对应的控制器。使用Promise异步回调。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                                 | 说明                          |
| ---------------------| ----------------------------- |
| Promise<[AVSessionController](arkts-apis-avsession-AVSessionController.md)> | Promise对象。返回会话控制器。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

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
        .onClick(async ()=>{
          let context: Context = this.getUIContext().getHostContext() as Context;
          let currentAVSession: avSession.AVSession = await avSession.createAVSession(context, 'SESSION_NAME', 'audio');
          let avSessionController: avSession.AVSessionController;
          currentAVSession.getController().then((avController: avSession.AVSessionController) => {
            avSessionController = avController;
            console.info(`Succeeded in getting controller, sessionid: ${avSessionController.sessionId}`);
          });
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## getController<sup>10+</sup>

getController(callback: AsyncCallback\<AVSessionController>): void

获取本会话相应的控制器。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型     | 必填 | 说明                       |
| -------- | ----------------------------| ---- | -------------------------- |
| callback | AsyncCallback<[AVSessionController](arkts-apis-avsession-AVSessionController.md)\> | 是   | 回调函数。返回会话控制器。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

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
          let context: Context = this.getUIContext().getHostContext() as Context;
          let currentAVSession: avSession.AVSession = await avSession.createAVSession(context, 'SESSION_NAME', 'audio');
          let avsessionController: avSession.AVSessionController;
          currentAVSession.getController((avcontroller: avSession.AVSessionController) => {
            avsessionController = avcontroller;
            console.info(`Succeeded in getting controller, sessionid: ${avsessionController.sessionId}`);
          });
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## getAVCastController<sup>10+</sup>

ArkTS-Dyn: getAVCastController(): Promise\<AVCastController>

ArkTS-Sta: getAVCastController(): Promise<AVCastController | undefined>

设备建立连接后，获取投播控制器。使用Promise异步回调。

如果avsession未处于投播状态，则控制器将返回 null。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型     | 说明     |
| --------- | --------- |
| ArkTS-Dyn: Promise<[AVCastController](arkts-apis-avsession-AVCastController.md)\><br>ArkTS-Sta: Promise<[AVCastController](arkts-apis-avsession-AVCastController.md) \| undefined> | Promise对象。返回投播控制器实例。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | --------------------------------------- |
| 6600102| The session does not exist.           |
| 6600109| The remote connection is not established. |

**示例：**

```ts
let avCastController: avSession.AVCastController;
currentAVSession.getAVCastController().then((avcontroller: avSession.AVCastController) => {
  avCastController = avcontroller;
  console.info('Succeeded in getting AV cast controller.');
});
```

## getAVCastController<sup>10+</sup>

ArkTS-Dyn: getAVCastController(callback: AsyncCallback\<AVCastController>): void

ArkTS-Sta: getAVCastController(callback: AsyncCallback<AVCastController | undefined>): void

设备建立连接后获取投播控制器。使用callback异步回调。

如果 avsession 未处于投播状态，则控制器将返回 null。

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型     | 必填 | 说明     |
| --------- | ----------------------------| ---- | --------- |
| callback  | ArkTS-Dyn: AsyncCallback<[AVCastController](arkts-apis-avsession-AVCastController.md)\><br>ArkTS-Sta: AsyncCallback<[AVCastController](arkts-apis-avsession-AVCastController.md) \| undefined> | 是 | 回调函数，返回投播控制器实例。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息                                  |
| -------- |---------------------------------------|
| 6600102| The session does not exist.           |
| 6600109| The remote connection is not established. |

**示例：**

```ts
let avCastController: avSession.AVCastController;
currentAVSession.getAVCastController((avcontroller: avSession.AVCastController) => {
  avCastController = avcontroller;
  console.info('Succeeded in getting AV cast controller.');
});
```

## getOutputDevice<sup>10+</sup>

getOutputDevice(): Promise\<OutputDeviceInfo>

通过会话获取播放设备信息。使用Promise异步回调。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                           | 说明                              |
| ---------------| --------------------------------- |
| Promise<[OutputDeviceInfo](arkts-apis-avsession-i.md#outputdeviceinfo10)> | Promise对象。返回播放设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.getOutputDevice().then((outputDeviceInfo: avSession.OutputDeviceInfo) => {
  console.info(`Succeeded in getting output device, devices length: ${outputDeviceInfo.devices.length}`);
})
```

## getOutputDevice<sup>10+</sup>

getOutputDevice(callback: AsyncCallback\<OutputDeviceInfo>): void

通过会话获取播放设备相关信息。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                  | 必填 | 说明                           |
| -------- | ----------------------| ---- | ------------------------------ |
| callback | AsyncCallback<[OutputDeviceInfo](arkts-apis-avsession-i.md#outputdeviceinfo10)\> | 是   | 回调函数，返回播放设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.getOutputDevice((outputDeviceInfo: avSession.OutputDeviceInfo) => {
  console.info(`Succeeded in getting output device, devices length: ${outputDeviceInfo.devices.length}`);
});
```

## activate<sup>10+</sup>

activate(): Promise\<void>

激活会话，激活后可正常使用会话。使用Promise异步回调方式。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<void> | Promise对象。当会话激活成功，无返回结果，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |


## activate<sup>10+</sup>

activate(callback: AsyncCallback\<void>): void

激活会话，激活后可正常使用会话。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                 | 必填 | 说明                                                         |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback\<void> | 是   | 回调函数。<br>ArkTS-Dyn：当会话激活成功，err为undefined，否则返回错误对象。<br>ArkTS-Sta：当会话激活成功，err为null，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.activate(() => {
  console.info('Succeeded in activating.');
});
```

## deactivate<sup>10+</sup>

deactivate(): Promise\<void>

禁用当前会话的功能。使用Promise异步回调。

可通过[activate](#activate10)恢复。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<void> | Promise对象。当禁用会话成功，无返回结果，否则返回错误对象。|

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.deactivate().then(() => {
  console.info('Deactivate : SUCCESS ');
});
```

## deactivate<sup>10+</sup>

deactivate(callback: AsyncCallback\<void>): void

禁用当前会话。使用callback异步回调。

禁用当前会话的功能，可通过[activate](#activate10)恢复。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                 | 必填 | 说明                                                         |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback\<void> | 是   | 回调函数。<br>ArkTS-Dyn：当禁用会话成功，err为undefined，否则返回错误对象。<br>ArkTS-Sta：当禁用会话成功，err为null，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.deactivate().then(() => {
  console.info('Succeeded in deactivating.');
});
```

## destroy<sup>10+</sup>

destroy(): Promise\<void>

销毁当前会话，使当前会话完全失效。使用Promise异步回调。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<void> | Promise对象。当会话销毁成功，无返回结果，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.destroy().then(() => {
  console.info('Succeeded in destroying.');
});
```

## destroy<sup>10+</sup>

destroy(callback: AsyncCallback\<void>): void

销毁当前会话，使当前会话完全失效。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                 | 必填 | 说明                                                         |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback\<void> | 是   | 回调函数。<br>ArkTS-Dyn：当会话销毁成功，err为undefined，否则返回错误对象。<br>ArkTS-Sta：当会话销毁成功，err为null，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.destroy(() => {
  console.info('Succeeded in destroying.');
});
```

## on('play')<sup>10+</sup>

on(type: 'play', callback: () => void): void

注册播放命令事件监听。使用callback异步回调。

注册该监听，说明应用支持播放指令。每个播放命令仅支持注册一个回调，如果注册新的回调，将替换前一个回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onPlay](#onplay23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                 | 必填 | 说明     |
| -------- | -------------------- | ---- | --------- |
| type     | string               | 是   | 事件回调类型，支持的事件为`'play'`，当播放命令被发送到会话时，触发该事件回调。 |
| callback | () => void | 是   | 回调函数。<br>当事件监听注册成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.on('play', () => {
  console.info('on play entry');
});
```

## onPlay<sup>23</sup>

onPlay(callback: Callback\<CommandInfo>): void

注册播放命令事件监听。使用callback异步回调。

应用将通过回调接收控制器发送的[CommandInfo](arkts-apis-avsession-i.md#commandinfo22)信息。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('play')](#onplay10)。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                               | 必填 | 说明     |
| -------- |------------------------------------------------------------------| ---- | --------- |
| callback | Callback\<[CommandInfo](arkts-apis-avsession-i.md#commandinfo22)> | 是   | 回调函数。当事件监听注册成功，err为undefined，否则为错误对象。                                        |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.onPlay((info: avSession.CommandInfo) => {
  console.info('on play entry');
});
```

## on('pause')<sup>10+</sup>

on(type: 'pause', callback: () => void): void

注册暂停命令事件监听。使用callback异步回调。

注册该监听，说明应用支持暂停指令。每个播放命令仅支持注册一个回调，如果注册新的回调，将替换前一个回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onPause](#onpause23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                 | 必填 | 说明     |
| -------- | -------------------- | ---- | --------- |
| type     | string               | 是   | 事件回调类型，支持的事件为`'pause'`，当暂停命令被发送到会话时，触发该事件回调。 |
| callback | () => void | 是   | 回调函数。<br>当事件监听注册成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.on('pause', () => {
  console.info('on pause entry');
});
```

## onPause<sup>23+</sup>

onPause(callback: NoParamCallback): void

注册暂停命令事件监听。使用callback异步回调。

注册该监听，说明应用支持暂停指令。每个播放命令仅支持注册一个回调，如果注册新的回调，将替换前一个回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('pause')](#onpause10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                 | 必填 | 说明     |
| -------- | -------------------- | ---- | --------- |
| callback | NoParamCallback | 是   | 回调函数。<br>当事件监听注册成功，err为null，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.onPause(() => {
  console.info('onPause entry');
});
```

## on('stop')<sup>10+</sup>

on(type:'stop', callback: () => void): void

注册停止命令事件监听。使用callback异步回调。

注册该监听，说明应用支持停止指令。每个播放命令仅支持注册一个回调，如果注册新的回调，将替换前一个回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onStop](#onstop23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                 | 必填 | 说明     |
| -------- | -------------------- | ---- | --------- |
| type     | string               | 是   | 事件回调类型，支持的事件是`'stop'`，当停止命令被发送到会话时，触发该事件回调。 |
| callback | () => void | 是   | 回调函数。<br>当事件监听注册成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.on('stop', () => {
  console.info('on stop entry');
});
```

## onStop<sup>23+</sup>

onStop(callback: NoParamCallback): void;

注册停止命令事件监听。使用callback异步回调。

注册该监听，说明应用支持停止指令。每个播放命令仅支持注册一个回调，如果注册新的回调，将替换前一个回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('stop')](#onstop10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                 | 必填 | 说明     |
| -------- | -------------------- | ---- | --------- |
| callback | NoParamCallback | 是   | 回调函数。<br>当事件监听注册成功，err为null，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.onStop(() => {
  console.info('onStop entry');
});
```

## on('playNext')<sup>10+</sup>

on(type:'playNext', callback: () => void): void

注册播放下一首命令事件监听。使用callback异步回调。

注册该监听，说明应用支持下一首指令。每个播放命令仅支持注册一个回调，如果注册新的回调，将替换前一个回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onPlayNext](#onplaynext22)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                 | 必填 | 说明     |
| -------- | -------------------- | ---- | --------- |
| type     | string               | 是   | 事件回调类型，支持的事件是`'playNext'`，当播放下一首命令被发送到会话时，触发该事件回调。 |
| callback | () => void | 是   | 回调函数。<br>当事件监听注册成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.on('playNext', () => {
  console.info('on playNext entry');
});
```

## onPlayNext<sup>22+</sup>

onPlayNext(callback: Callback\<CommandInfo>): void

注册播放下一首命令事件监听。使用callback异步回调。

应用将通过回调接收控制器发送的[CommandInfo](arkts-apis-avsession-i.md#commandinfo22)信息。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23


**参数：**

| 参数名   | 类型       | 必填 | 说明     |
| -------- | ---------- | ---- | --------- |
| callback | Callback\<[CommandInfo](arkts-apis-avsession-i.md#commandinfo22)> | 是   | 回调函数。当事件监听注册成功，err为undefined，否则为错误对象。     |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.onPlayNext((info: avSession.CommandInfo) => {
  console.info('on playNext entry');
});
```

## on('playPrevious')<sup>10+</sup>

on(type:'playPrevious', callback: () => void): void

注册播放上一首命令事件监听。使用callback异步回调。

注册该监听，说明应用支持上一首指令。每个播放命令仅支持注册一个回调，如果注册新的回调，将替换前一个回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onPlayPrevious](#onplayprevious22)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                 | 必填 | 说明     |
| -------- | -------------------- | ---- | --------- |
| type     | string               | 是   | 事件回调类型，支持的事件是`'playPrevious'`，当播放上一首命令被发送到会话时，触发该事件回调。 |
| callback | () => void | 是   | 回调函数。<br>当事件监听注册成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.on('playPrevious', () => {
  console.info('on playPrevious entry');
});
```

## onPlayPrevious<sup>22+</sup>

onPlayPrevious(callback: Callback\<CommandInfo>): void

注册播放上一首命令事件监听。使用callback异步回调。

应用将通过回调接收控制器发送的[CommandInfo](arkts-apis-avsession-i.md#commandinfo22)信息。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                 | 必填 | 说明     |
| -------- | -------------------- | ---- | --------- |
| callback | Callback\<[CommandInfo](arkts-apis-avsession-i.md#commandinfo22)> | 是   | 回调函数。当事件监听注册成功，err为undefined，否则为错误对象。       |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.onPlayPrevious((info: avSession.CommandInfo) => {
  console.info('on playPrevious entry');
});
```

## on('fastForward')<sup>10+</sup>

on(type: 'fastForward', callback: (time?: number) => void): void

注册快进命令事件监听。使用callback异步回调。

注册该监听，说明应用支持快进指令。每个播放命令仅支持注册一个回调，如果注册新的回调，将替换前一个回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onFastForward](#onfastforward22)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                 | 必填 | 说明     |
| -------- | -------------------- | ---- | --------- |
| type     | string               | 是   | 事件回调类型，支持的事件是 `'fastForward'`，当快进命令被发送到会话时，触发该事件回调。 |
| callback | (time?: number) => void | 是   | 回调函数。参数time是时间节点，单位为秒。    |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.on('fastForward', (time?: number) => {
  console.info('on fastForward entry');
});
```

## onFastForward<sup>22+</sup>

ArkTS-Dyn: onFastForward(callback: TwoParamCallback\<number, CommandInfo>): void

ArkTS-Sta: onFastForward(callback: TwoParamCallback\<long, CommandInfo>): void

注册快进命令事件监听。使用callback异步回调。

应用将通过回调接收控制器发送的快进时间参数，以及对应的[CommandInfo](arkts-apis-avsession-i.md#commandinfo22)信息。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                  |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------- |
| callback | ArkTS-Dyn: TwoParamCallback\<number, [CommandInfo](arkts-apis-avsession-i.md#commandinfo22)><br>ArkTS-Sta: TwoParamCallback\<long, [CommandInfo](arkts-apis-avsession-i.md#commandinfo22)> | 是   | 回调函数。用于处理'fastForward'操作。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.onFastForward((time: number, info: avSession.CommandInfo) => {
  console.info('on fastForward entry');
});
```

## on('rewind')<sup>10+</sup>

on(type:'rewind', callback: (time?: number) => void): void

注册快退命令事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onRewind](#onrewind22)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                 | 必填 | 说明     |
| -------- | -------------------- | ---- | --------- |
| type     | string               | 是   | 事件回调类型，支持的事件是`'rewind'`，当快退命令被发送到会话时，触发该事件回调。 |
| callback | (time?: number) => void | 是   | 回调函数。参数time是时间节点，单位为秒。      |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.on('rewind', (time?: number) => {
  console.info('on rewind entry');
});
```

## onRewind<sup>22+</sup>

ArkTS-Dyn: onRewind(callback: TwoParamCallback\<number, CommandInfo>): void

ArkTS-Sta: onRewind(callback: TwoParamCallback\<long, CommandInfo>): void

注册快退命令事件监听。使用callback异步回调。

应用将通过回调接收控制器发送的快退时间参数，以及对应的[CommandInfo](arkts-apis-avsession-i.md#commandinfo22)信息。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                             |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------- |
| callback | ArkTS-Dyn: TwoParamCallback\<number, [CommandInfo](arkts-apis-avsession-i.md#commandinfo22)><br>ArkTS-Sta: TwoParamCallback\<long, [CommandInfo](arkts-apis-avsession-i.md#commandinfo22)> | 是   | 回调函数。用于处理'rewind'操作。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.onRewind((time: number, info: avSession.CommandInfo) => {
  console.info('on rewind entry');
});
```


## on('playWithAssetId')<sup>20+</sup>

on(type:'playWithAssetId', callback: Callback\<string>): void

注册指定资源id进行播放的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onPlayWithAssetId](#onplaywithassetid23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名   | 类型                 | 必填 | 说明     |
| -------- | -------------------- | ---- | --------- |
| type     | string               | 是   | 事件回调类型，支持的事件是`'playWithAssetId'`，当指定资源id进行播放时，触发该事件回调。 |
| callback | Callback\<string> | 是   | 回调函数。参数assetId是媒体id。      |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
let playWithAssetIdCallback = (assetId: string) => {
  console.info(`on playWithAssetId entry,  assetId = ${assetId}`);
}
currentAVSession.on('playWithAssetId', playWithAssetIdCallback);
```

## onPlayWithAssetId<sup>23+</sup>

onPlayWithAssetId(callback: Callback\<string>): void

注册指定资源id进行播放的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('playWithAssetId')](#onplaywithassetid20)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                 | 必填 | 说明     |
| -------- | -------------------- | ---- | --------- |
| callback | Callback\<string> | 是   | 回调函数。参数assetId是媒体id。      |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
let playWithAssetIdCallback = (assetId: string) => {
  console.info(`on playWithAssetId entry,  assetId = ${assetId}`);
}
currentAVSession.onPlayWithAssetId(playWithAssetIdCallback);
```

## off('playWithAssetId')<sup>20+</sup>

off(type: 'playWithAssetId', callback?: Callback\<string>): void

注销指定资源id进行播放的事件监听。使用callback异步回调。

注销后，不再进行该事件回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offPlayWithAssetId](#offplaywithassetid23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| type     | string               | 是   | 关闭对应的事件监听，支持的事件是`'playWithAssetId'`。 |
| callback | Callback\<string> | 否   | 回调函数。当事件监听取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。参数assetId是媒体id。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('playWithAssetId');
```

## offPlayWithAssetId<sup>23+</sup>

offPlayWithAssetId(callback?: Callback\<string>): void

注销指定资源id进行播放的事件监听。使用callback异步回调。

注销后，不再进行该事件回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('playWithAssetId')](#offplaywithassetid20)。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| callback | Callback\<string> | 否   | 回调函数。当事件监听取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。参数assetId是媒体id。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offPlayWithAssetId();
```

## on('seek')<sup>10+</sup>

on(type: 'seek', callback: (time: number) => void): void

设置跳转节点事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onSeek](#onseek23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | --------- |
| type     | string                 | 是   | 事件回调类型，支持事件`'seek'`：当跳转节点命令被发送到会话时，触发该事件。 |
| callback | (time: number) => void | 是   | 回调函数。参数time是时间节点，单位为毫秒。                   |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.on('seek', (time: number) => {
  console.info(`on seek entry time : ${time}`);
});
```

## onSeek<sup>23+</sup>

onSeek(callback: Callback\<long>): void

注册跳转节点事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('seek')](#onseek10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | --------- |
| callback | Callback\<long> | 是   | 回调函数。参数time是时间节点，单位为毫秒。                   |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.onSeek((time: long) => {
  console.info(`onSeek entry time : ${time}`);
});
```

## on('setSpeed')<sup>10+</sup>

on(type: 'setSpeed', callback: (speed: number) => void): void

注册播放速率的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onSetSpeed](#onsetspeed23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                    | 必填 | 说明     |
| -------- | ----------------------- | ---- | --------- |
| type     | string                  | 是   | 事件回调类型，支持事件`'setSpeed'`：当设置播放速率的命令被发送到会话时，触发该事件。 |
| callback | (speed: number) => void | 是   | 回调函数。参数speed是播放倍速。                              |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.on('setSpeed', (speed: number) => {
  console.info(`on setSpeed speed : ${speed}`);
});
```

## onSetSpeed<sup>23+</sup>

onSetSpeed(callback: Callback\<double>): void;

注册播放速率的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('setSpeed')](#onsetspeed10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                    | 必填 | 说明     |
| -------- | ----------------------- | ---- | --------- |
| callback | Callback\<double> | 是   | 回调函数。参数speed是播放倍速。                              |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.onSetSpeed((speed: double) => {
  console.info(`onSetSpeed speed : ${speed}`);
});
```

## on('setLoopMode')<sup>10+</sup>

on(type: 'setLoopMode', callback: (mode: LoopMode) => void): void

注册循环模式的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onSetLoopMode](#onsetloopmode23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名    | 类型                                   | 必填 | 说明  |
| -------- | ------------------------------------- | ---- | ---- |
| type     | string                                | 是   | 事件回调类型，支持事件`'setLoopMode'`：当设置循环模式的命令被发送到会话时，触发该事件。 |
| callback | (mode: [LoopMode](arkts-apis-avsession-e.md#loopmode10)) => void | 是   | 回调函数。参数mode是循环模式。                               |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.on('setLoopMode', (mode: avSession.LoopMode) => {
  console.info(`on setLoopMode mode : ${mode}`);
});
```

## onSetLoopMode<sup>23+</sup>

onSetLoopMode(callback: Callback\<LoopMode>): void

注册循环模式的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('setLoopMode')](#onsetloopmode10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                                   | 必填 | 说明  |
| -------- | ------------------------------------- | ---- | ---- |
| callback | Callback<[LoopMode](arkts-apis-avsession-e.md#loopmode10)> | 是   | 回调函数。参数表示目标循环模式。                               |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.onSetLoopMode((mode: avSession.LoopMode) => {
  console.info(`onSetLoopMode mode : ${mode}`);
});
```

## on('setTargetLoopMode')<sup>18+</sup>

on(type: 'setTargetLoopMode', callback: Callback\<LoopMode>): void

注册目标循环模式的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onSetTargetLoopMode](#onsettargetloopmode23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 18

**参数：**

| 参数名    | 类型                                   | 必填 | 说明  |
| -------- | ------------------------------------- | ---- | ---- |
| type     | string                                | 是   | 事件回调类型，支持事件`'setTargetLoopMode'`。<br>- `'setTargetLoopMode'`：当设置目标循环模式的命令被发送到会话时，触发该事件。 |
| callback | Callback<[LoopMode](arkts-apis-avsession-e.md#loopmode10)> | 是   | 回调函数。参数表示目标循环模式。                               |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.on('setTargetLoopMode', (mode: avSession.LoopMode) => {
  console.info(`on setTargetLoopMode mode : ${mode}`);
});
```

## onSetTargetLoopMode<sup>23+</sup>

onSetTargetLoopMode(callback: Callback\<LoopMode>): void

注册目标循环模式的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('setTargetLoopMode')](#onsettargetloopmode18)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                                   | 必填 | 说明  |
| -------- | ------------------------------------- | ---- | ---- |
| callback | Callback<[LoopMode](arkts-apis-avsession-e.md#loopmode10)> | 是   | 回调函数。参数表示目标循环模式。                               |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.onSetTargetLoopMode((mode: avSession.LoopMode) => {
  console.info(`onSetTargetLoopMode mode : ${mode}`);
});
```

## on('toggleFavorite')<sup>10+</sup>

on(type: 'toggleFavorite', callback: (assetId: string) => void): void

注册是否收藏的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onToggleFavorite](#ontogglefavorite23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                      | 必填 | 说明     |
| -------- | ------------------------- | ---- | --------- |
| type     | string                    | 是   | 事件回调类型，支持事件`'toggleFavorite'`：当是否收藏的命令被发送到会话时，触发该事件。 |
| callback | (assetId: string) => void | 是   | 回调函数。参数assetId是媒体ID。                              |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.on('toggleFavorite', (assetId: string) => {
  console.info(`on toggleFavorite mode : ${assetId}`);
});
```

## onToggleFavorite<sup>23+</sup>

onToggleFavorite(callback: Callback\<string>): void

注册是否收藏的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('toggleFavorite')](#ontogglefavorite10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                      | 必填 | 说明     |
| -------- | ------------------------- | ---- | --------- |
| callback | Callback\<string> | 是   | 回调函数。参数assetId是媒体ID。                              |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.onToggleFavorite((assetId: string) => {
  console.info(`onToggleFavorite mode : ${assetId}`);
});
```

## on('skipToQueueItem')<sup>10+</sup>

on(type: 'skipToQueueItem', callback: (itemId: number) => void): void

注册播放列表其中某项被选中的事件监听。使用callback异步回调。

session端可以选择对这个单项歌曲进行播放。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onSkipToQueueItem](#onskiptoqueueitem23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                      | 必填 | 说明                                   |
| -------- | ------------------------ | ---- | ------------------------------------- |
| type     | string                   | 是   | 事件回调类型，支持事件`'skipToQueueItem'`：当播放列表选中单项的命令被发送到会话时，触发该事件。 |
| callback | (itemId: number) => void | 是   | 回调函数。参数itemId是选中的播放列表项的ID。                                                |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.on('skipToQueueItem', (itemId: number) => {
  console.info(`on skipToQueueItem id : ${itemId}`);
});
```

## onSkipToQueueItem<sup>23+</sup>

onSkipToQueueItem(callback: Callback\<int>): void

注册播放列表其中某项被选中的事件监听。使用callback异步回调。

session端可以选择对这个单项歌曲进行播放。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('skipToQueueItem')](#onskiptoqueueitem10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                      | 必填 | 说明                                   |
| -------- | ------------------------ | ---- | ------------------------------------- |
| callback | Callback\<int> | 是   | 回调函数。参数itemId是选中的播放列表项的ID。                                                |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.onSkipToQueueItem((itemId: int) => {
  console.info(`onSkipToQueueItem id : ${itemId}`);
});
```

## on('handleKeyEvent')<sup>10+</sup>

on(type: 'handleKeyEvent', callback: (event: KeyEvent) => void): void

注册蓝牙/有线等外设接入的按键输入事件的监听。使用callback异步回调。

监听多媒体按键事件中播放、暂停、上下一首、快进、快退的指令。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onHandleKeyEvent](#onhandlekeyevent23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型    | 必填 | 说明     |
| -------- | --------- | ---- | --------- |
| type     | string    | 是   | 事件回调类型，支持事件`'handleKeyEvent'`：当按键事件被发送到会话时，触发该事件。 |
| callback | (event: [KeyEvent](../apis-input-kit/js-apis-keyevent.md)) => void | 是   | 回调函数。参数event是按键事件。                              |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | --------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
import { KeyEvent } from '@kit.InputKit';

currentAVSession.on('handleKeyEvent', (event: KeyEvent) => {
  console.info(`on handleKeyEvent event : ${event}`);
});
```

## onHandleKeyEvent<sup>23+</sup>

onHandleKeyEvent(callback: Callback\<KeyEvent>): void

注册蓝牙/有线等外设接入的按键输入事件的监听。使用callback异步回调。

监听多媒体按键事件中播放、暂停、上下一首、快进、快退的指令。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('handleKeyEvent')](#onhandlekeyevent10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型    | 必填 | 说明     |
| -------- | --------- | ---- | --------- |
| callback | Callback<[KeyEvent](../apis-input-kit/js-apis-keyevent.md)> | 是   | 回调函数。参数event是按键事件。                              |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | --------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
import { KeyEvent } from '@kit.InputKit';

currentAVSession.onHandleKeyEvent((event: KeyEvent) => {
  console.info(`on handleKeyEvent event : ${event}`);
});
```

## on('outputDeviceChange')<sup>10+</sup>

on(type: 'outputDeviceChange', callback: (state: ConnectionState, device: OutputDeviceInfo) => void): void

注册播放设备变化的事件监听。使用callback异步回调。

应用接入[系统投播组件](ohos-multimedia-avcastpicker.md)，当用户通过组件切换设备时，会收到设备切换的回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onOutputDeviceChange](#onoutputdevicechange23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型 | 必填 | 说明     |
| -------- | ------------------------| ---- | --------- |
| type     | string                                                  | 是   | 事件回调类型，支持事件`'outputDeviceChange'`：当播放设备变化时，触发该事件。 |
| callback | (state: [ConnectionState](arkts-apis-avsession-e.md#connectionstate10), device: [OutputDeviceInfo](arkts-apis-avsession-i.md#outputdeviceinfo10)) => void | 是   | 回调函数，参数device是设备相关信息。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。                         |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.on('outputDeviceChange', (state: avSession.ConnectionState, device: avSession.OutputDeviceInfo) => {
  console.info(`on outputDeviceChange device : ${device}`);
});
```

## onOutputDeviceChange<sup>23+</sup>

onOutputDeviceChange(callback: ConnectionEvent): void

注册播放设备变化的事件监听。使用callback异步回调。

应用接入[系统投播组件](ohos-multimedia-avcastpicker.md)，当用户通过组件切换设备时，会收到设备切换的回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('outputDeviceChange')](#onoutputdevicechange10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型 | 必填 | 说明     |
| -------- | ------------------------| ---- | --------- |
| callback | ConnectionEvent | 是   | 回调函数。                         |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.onOutputDeviceChange((state: avSession.ConnectionState, device: avSession.OutputDeviceInfo) => {
  console.info(`onOutputDeviceChange device : ${device}`);
});
```

## on('commonCommand')<sup>10+</sup>

on(type: 'commonCommand', callback: (command: string, args: {[key: string]: Object}) => void): void

注册自定义控制命令变化的监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onCommonCommand](#oncommoncommand23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型  |   必填 | 说明     |
| -------- | --------- | ---- | --------- |
| type     | string    | 是   | 事件回调类型，支持事件`'commonCommand'`：当自定义控制命令变化时，触发该事件。 |
| callback | (command: string, args: {[key: string]: Object}) => void | 是   | 回调函数，command为变化的自定义控制命令名，args为自定义控制命令的参数，参数内容与[sendCommonCommand](arkts-apis-avsession-AVSessionController.md#sendcommoncommand10)方法设置的参数内容完全一致。          |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

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
          .onClick(()=>{
            let currentAVSession: avSession.AVSession | undefined = undefined;
            let tag = "createNewSession";
            let context: Context = this.getUIContext().getHostContext() as Context;

            avSession.createAVSession(context, tag, "audio", (err, data: avSession.AVSession) => {
            currentAVSession = data;
            });
            if (currentAVSession !== undefined) {
            (currentAVSession as avSession.AVSession).on('commonCommand', (commonCommand, args) => {
                console.info(`OnCommonCommand, the command is ${commonCommand}, args: ${JSON.stringify(args)}`);
            });
            }
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

## onCommonCommand<sup>23+</sup>

onCommonCommand(callback: EventProcess): void

注册自定义控制命令变化的监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('commonCommand')](#oncommoncommand10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型  |   必填 | 说明     |
| -------- | --------- | ---- | --------- |
| callback | EventProcess | 是   | 回调函数，event为变化的自定义控制命令名，args为自定义控制命令的参数，参数内容与[sendCommonCommand](arkts-apis-avsession-AVSessionController.md#sendcommoncommand10)方法设置的参数内容完全一致。          |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

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
          .onClick(()=>{
            let currentAVSession: avSession.AVSession | undefined = undefined;
            let tag = "createNewSession";
            let context: Context = this.getUIContext().getHostContext() as Context;

            avSession.createAVSession(context, tag, "audio", (err | null, data: avSession.AVSession | undefined) => {
            currentAVSession = data;
            });
            if (currentAVSession !== undefined) {
            (currentAVSession as avSession.AVSession).onCommonCommand((commonCommand, args) => {
                console.info(`OnCommonCommand, the command is ${commonCommand}, args: ${JSON.stringify(args)}`);
            });
            }
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

## off('play')<sup>10+</sup>

off(type: 'play', callback?: () => void): void

注销会话播放事件监听，关闭后，不再进行该事件回调。

注销回调时，需要更新支持的命令列表。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offPlay](#offplay22)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| type     | string               | 是   | 关闭对应的事件监听，支持的事件是`'play'`。|
| callback | () => void | 否   | 回调函数。<br>当事件监听取消成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('play');
```

## offPlay<sup>22+</sup>

offPlay(callback?: Callback\<CommandInfo>): void

注销会话播放事件监听。使用callback异步回调。

指定callback，注销对应监听；未指定callback，则注销所有事件监听。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| callback | Callback\<[CommandInfo](arkts-apis-avsession-i.md#commandinfo22)> | 否   | 回调函数。当事件监听取消成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。                            |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offPlay();
```

## off('pause')<sup>10+</sup>

off(type: 'pause', callback?: () => void): void

注销会话暂停事件监听，关闭后，不再进行该事件回调。

注销回调时，需要更新支持的命令列表。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offPause](#offpause23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| type     | string               | 是   | 注销对应的事件监听，支持的事件是`'pause'`。 |
| callback | () => void | 否   | 回调函数。<br>当事件监听注销成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('pause');
```

## offPause<sup>23+</sup>

offPause(callback?: NoParamCallback): void

注销会话暂停事件监听，关闭后，不再进行该事件回调。

注销回调时，需要更新支持的命令列表。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('pause')](#offpause10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| callback | NoParamCallback | 否   | 回调函数。<br>当事件监听注销成功，err为null，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offPause();
```

## off('stop')<sup>10+</sup>

off(type: 'stop', callback?: () => void): void

注销会话停止事件监听。

注销回调时，需要更新支持的命令列表。注销后，不再进行该事件回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offStop](#offstop23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| type     | string               | 是   | 注销对应的事件监听，支持的事件是`'stop'`。 |
| callback | () => void | 否   | 回调函数。<br>当事件监听注销成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('stop');
```

## offStop<sup>23+</sup>

offStop(callback?: NoParamCallback): void

注销会话停止事件监听。

注销回调时，需要更新支持的命令列表。关闭后，不再进行该事件回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('stop')](#offstop10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| callback | NoParamCallback | 否   | 回调函数。<br>当事件监听注销成功，err为null，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offStop();
```

## off('playNext')<sup>10+</sup>

off(type: 'playNext', callback?: () => void): void

注销会话播放下一首事件监听。

注销回调时，需要更新支持的命令列表。关闭后，不再进行该事件回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offPlayNext](#offplaynext22)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| type     | string               | 是   | 注销对应的事件监听，支持的事件是 `'playNext'`。 |
| callback | () => void | 否   | 回调函数。<br>当事件监听注销成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('playNext');
```

## offPlayNext<sup>22+</sup>

offPlayNext(callback?: Callback\<CommandInfo>): void

注销会话播放下一首事件监听。使用callback异步回调。

指定callback，注销对应监听；未指定callback，则注销所有事件监听。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型        | 必填 | 说明                   |
| -------- | ---------- | ---- | ---------------------- |
| callback | Callback\<[CommandInfo](arkts-apis-avsession-i.md#commandinfo22)> | 否   | 回调函数。当事件监听注销成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。                            |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offPlayNext();
```

## off('playPrevious')<sup>10+</sup>

off(type: 'playPrevious', callback?: () => void): void

注销会话播放上一首事件监听。

注销回调时，需要更新支持的命令列表。关闭后，不再进行该事件回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offPlayPrevious](#offplayprevious22)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| type     | string               | 是   | 注销对应的事件监听，支持的事件是`'playPrevious'`。 |
| callback | () => void | 否   | 回调函数。<br>当事件监听注销成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('playPrevious');
```

## offPlayPrevious<sup>22+</sup>

offPlayPrevious(callback?: Callback\<CommandInfo>): void

注销会话播放上一首事件监听。使用callback异步回调。

指定callback，注销对应监听；未指定callback，则注销所有事件监听。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型     | 必填 | 说明                   |
| -------- |--------| ---- | ---------------------- |
| callback | Callback\<[CommandInfo](arkts-apis-avsession-i.md#commandinfo22)>  | 否   | 回调函数。当事件监听注销成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。                            |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offPlayPrevious();
```

## off('fastForward')<sup>10+</sup>

off(type: 'fastForward', callback?: () => void): void

注销会话快进事件监听。

注销回调时，需要更新支持的命令列表。关闭后，不再进行该事件回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offFastForward](#offfastforward22)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| type     | string               | 是   | 注销对应的事件监听，支持的事件是`'fastForward'`。 |
| callback | () => void | 否   | 回调函数。<br>当事件监听注销成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('fastForward');
```

## offFastForward<sup>22+</sup>

ArkTS-Dyn: offFastForward(callback?: TwoParamCallback<number, CommandInfo>): void

ArkTS-Sta: offFastForward(callback?: TwoParamCallback<long, CommandInfo>): void

注销会话快进事件监听。

注销回调时，需要更新支持的命令列表。关闭后，不再进行该事件回调。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| callback | ArkTS-Dyn: TwoParamCallback<number, CommandInfo><br>ArkTS-Sta: TwoParamCallback<long, CommandInfo> | 否   | 回调函数。<br>当事件监听注销成功，err为null，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offFastForward();
```

## off('rewind')<sup>10+</sup>

off(type: 'rewind', callback?: () => void): void

注销会话快退事件监听。

关闭后，不再进行该事件回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offRewind](#offrewind22)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| type     | string               | 是   | 注销对应的事件监听，支持的事件是`'rewind'`。 |
| callback | () => void | 否   | 回调函数。<br>当事件监听注销成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('rewind');
```

## offRewind<sup>22+</sup>

ArkTS-Dyn: offRewind(callback?: TwoParamCallback\<number, CommandInfo>): void

ArkTS-Sta: offRewind(callback?: TwoParamCallback\<long, CommandInfo>): void

注销会话快退事件监听。使用callback异步回调。

指定callback，注销对应监听；未指定callback，则注销所有事件监听。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| callback | ArkTS-Dyn: TwoParamCallback\<number, [CommandInfo](arkts-apis-avsession-i.md#commandinfo22)><br>ArkTS-Sta: TwoParamCallback\<long, [CommandInfo](arkts-apis-avsession-i.md#commandinfo22)> | 否   | 回调函数。当事件监听注销成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。                            |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offRewind();
```

## off('seek')<sup>10+</sup>

off(type: 'seek', callback?: (time: number) => void): void

注销跳转节点事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offSeek](#offseek23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 注销对应的事件监听，支持关闭事件`'seek'`。                   |
| callback | (time: number) => void | 否   | 回调函数，参数time是时间节点，单位为毫秒。<br>当事件监听注销成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('seek');
```

## offSeek<sup>23+</sup>

offSeek(callback?: Callback\<long>): void

注销跳转节点事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('seek')](#offseek10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback\<long> | 否   | 回调函数，参数time是时间节点，单位为毫秒。<br>当事件监听注销成功，err为null，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offSeek();
```

## off('setSpeed')<sup>10+</sup>

off(type: 'setSpeed', callback?: (speed: number) => void): void

注销播放速率变化事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offSetSpeed](#offsetspeed23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                      | 必填 | 说明     |
| -------- | ------------------------- | ---- | -------------------------|
| type     | string                    | 是   | 注销对应的事件监听，支持关闭事件`'setSpeed'`。            |
| callback | (speed: number) => void | 否   | 回调函数，参数speed是播放倍速。<br>ArkTS-Dyn：当事件监听注销成功，err为undefined，否则返回错误对象。<br>ArkTS-Sta：当事件监听注销成功，err为null，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('setSpeed');
```

## offSetSpeed<sup>23+</sup>

offSetSpeed(callback?: Callback\<double>): void

注销播放速率变化事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('setSpeed')](#offsetspeed10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback\<double> | 否   | 回调函数，参数speed是播放倍速。<br>当事件监听取消成功，err为null，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offSetSpeed();
```

## off('setLoopMode')<sup>10+</sup>

off(type: 'setLoopMode', callback?: (mode: LoopMode) => void): void

注销循环模式变化事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offSetLoopMode](#offsetloopmode23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                                  | 必填 | 说明     |
| -------- | ------------------------------------- | ---- | ----- |
| type     | string | 是   | 注销对应的事件监听，支持注销事件`'setLoopMode'`。|
| callback | (mode: [LoopMode](arkts-apis-avsession-e.md#loopmode10)) => void | 否   | 回调函数，参数mode是循环模式。<br>当事件监听注销成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('setLoopMode');
```

## offSetLoopMode<sup>23+</sup>

offSetLoopMode(callback?: Callback\<LoopMode>): void

注销循环模式变化事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('setLoopMode')](#offsetloopmode10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                  | 必填 | 说明     |
| -------- | ------------------------------------- | ---- | ----- |
| callback | Callback<[LoopMode](arkts-apis-avsession-e.md#loopmode10)> | 否   | 回调函数，参数mode是循环模式。<br>当事件监听取消成功，err为null，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offSetLoopMode();
```

## off('setTargetLoopMode')<sup>18+</sup>

off(type: 'setTargetLoopMode', callback?: Callback\<LoopMode>): void

注销监听目标循环模式变化事件。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offSetTargetLoopMode](#offsettargetloopmode23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 18

**参数：**

| 参数名   | 类型                                  | 必填 | 说明     |
| -------- | ------------------------------------- | ---- | ----- |
| type     | string | 是   | 注销对应的事件监听，支持关闭事件`'setTargetLoopMode'`。|
| callback | Callback<[LoopMode](arkts-apis-avsession-e.md#loopmode10)> | 否   | 回调函数，参数表示目标循环模式。当事件监听注销成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('setTargetLoopMode');
```

## offSetTargetLoopMode<sup>23+</sup>

offSetTargetLoopMode(callback?: Callback\<LoopMode>): void

注销监听目标循环模式变化事件。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('setTargetLoopMode')](#offsettargetloopmode18)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                  | 必填 | 说明     |
| -------- | ------------------------------------- | ---- | ----- |
| callback | Callback<[LoopMode](arkts-apis-avsession-e.md#loopmode10)> | 否   | 回调函数，参数表示目标循环模式。当事件监听注销成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offSetTargetLoopMode();
```

## off('toggleFavorite')<sup>10+</sup>

off(type: 'toggleFavorite', callback?: (assetId: string) => void): void

注销是否收藏的事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offToggleFavorite](#offtogglefavorite23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                      | 必填 | 说明     |
| -------- | ------------------------- | ---- | -------------------------|
| type     | string                    | 是   | 注销对应的事件监听，支持关闭事件`'toggleFavorite'`。            |
| callback | (assetId: string) => void | 否   | 回调函数，参数assetId是媒体ID。<br>当事件监听注销成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101 | Session service exception. |
| 6600102 | The session does not exist. |

**示例：**

```ts
currentAVSession.off('toggleFavorite');
```

## offToggleFavorite<sup>23+</sup>

offToggleFavorite(callback?: Callback\<string>): void

注销是否收藏的事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('toggleFavorite')](#offtogglefavorite10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                      | 必填 | 说明     |
| -------- | ------------------------- | ---- | -------------------------|
| callback | Callback\<string> | 否   | 回调函数，参数是媒体ID。<br>当事件监听注销成功，err为null，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offToggleFavorite();
```

## off('skipToQueueItem')<sup>10+</sup>

off(type: 'skipToQueueItem', callback?: (itemId: number) => void): void

注销播放列表单项选中的事件监听。使用callback异步回调。

指定callback，可注销对应监听；未指定callback，注销所有事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offSkipToQueueItem](#offskiptoqueueitem23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                      | 必填 | 说明    |
| -------- | ------------------------ | ---- | ----------------------|
| type     | string                   | 是   | 注销对应的事件监听，支持注销事件`'skipToQueueItem'`。    |
| callback | (itemId: number) => void<br> | 否   | 回调函数，参数itemId是播放列表单项ID。<br>当事件监听注销成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为注销所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | --------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('skipToQueueItem');
```

## offSkipToQueueItem<sup>23+</sup>

offSkipToQueueItem(callback?: Callback\<int>): void

注销播放列表单项选中的事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('skipToQueueItem')](#offskiptoqueueitem10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                      | 必填 | 说明    |
| -------- | ------------------------ | ---- | ----------------------|
| callback | Callback\<int> | 否   | 回调函数，参数是播放列表单项ID。<br>当事件监听取消成功，err为null，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | --------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offSkipToQueueItem();
```

## off('handleKeyEvent')<sup>10+</sup>

off(type: 'handleKeyEvent', callback?: (event: KeyEvent) => void): void

注销按键事件监听。使用callback异步回调。

指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offHandleKeyEvent](#offhandlekeyevent23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型  |   必填 | 说明     |
| -------- | --------- | ---- | --------- |
| type     | string    | 是   | 关闭对应的事件监听，支持关闭事件`'handleKeyEvent'`。             |
| callback | (event: [KeyEvent](../apis-input-kit/js-apis-keyevent.md)) => void | 否   | 回调函数，参数event是按键事件。<br>当事件监听取消成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。                              |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('handleKeyEvent');
```

## offHandleKeyEvent<sup>23+</sup>

offHandleKeyEvent(callback?: Callback\<KeyEvent>): void

注销监听按键事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('handleKeyEvent')](#offhandlekeyevent10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型  |   必填 | 说明     |
| -------- | --------- | ---- | --------- |
| callback | Callback<[KeyEvent](../apis-input-kit/js-apis-keyevent.md)> | 否   | 回调函数，参数是按键事件。<br>当事件监听取消成功，err为null，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offHandleKeyEvent();
```


## off('outputDeviceChange')<sup>10+</sup>

off(type: 'outputDeviceChange', callback?: (state: ConnectionState, device: OutputDeviceInfo) => void): void

注销播放设备变化的事件监听。使用callback异步回调。

指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offOutputDeviceChange](#offoutputdevicechange23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型 | 必填 | 说明   |
| -------- | ------------------------| ---- | -----------------------|
| type     | string                                                  | 是   | 关闭对应的事件监听，支持关闭事件`'outputDeviceChange'`。     |
| callback | (state: [ConnectionState](arkts-apis-avsession-e.md#connectionstate10), device: [OutputDeviceInfo](arkts-apis-avsession-i.md#outputdeviceinfo10)) => void | 否   | 回调函数，参数device是设备相关信息。<br>当事件监听取消成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。                        |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('outputDeviceChange');
```

## offOutputDeviceChange<sup>23+</sup>

offOutputDeviceChange(callback?: ConnectionEvent): void

注销监听播放设备变化的事件。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('outputDeviceChange')](#offoutputdevicechange10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型 | 必填 | 说明   |
| -------- | ------------------------| ---- | -----------------------|
| callback | ConnectionEvent | 否   | 回调函数，参数device是设备相关信息。<br>当事件监听取消成功，err为null，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offOutputDeviceChange();
```

## off('commonCommand')<sup>10+</sup>

off(type: 'commonCommand', callback?: (command: string, args: {[key: string]: Object}) => void): void

注销监听自定义控制命令的变化。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offCommonCommand](#offcommoncommand23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型  |   必填 | 说明  |
| -------- | --------- | ---- | ----------------------|
| type     | string    | 是   | 取消对应的事件监听，支持事件`'commonCommand'`。    |
| callback |(command: string, args:{[key: string]: Object}) => void | 否   | 回调函数，参数command是变化的自定义控制命令名，args为自定义控制命令的参数。<br>该参数为可选参数，若不填写该参数，则认为取消所有对command事件的监听。|
**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('commonCommand');
```

## offCommonCommand<sup>23+</sup>

offCommonCommand(callback?: EventProcess): void

注销监听自定义控制命令的变化。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('commonCommand')](#offcommoncommand10)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型  |   必填 | 说明  |
| -------- | --------- | ---- | ----------------------|
| callback | EventProcess | 否   | 回调函数，参数event是变化的自定义控制命令名，args为自定义控制命令的参数。<br>该参数为可选参数，若不填写该参数，则认为取消所有对command事件的监听。                      |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offCommonCommand();
```

## on('answer')<sup>11+</sup>

on(type: 'answer', callback: Callback\<void>): void

注册通话接听的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onAnswer](#onanswer23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名   | 类型   |  必填 | 说明     |
| -------- | --------- | ---- | --------- |
| type     | string    | 是   | 事件回调类型，支持事件`'answer'`：当通话接听时，触发该事件。 |
| callback | Callback\<void>                                               | 是   | 回调函数。                      |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.on('answer', () => {
  console.info('on call answer');
});
```

## onAnswer<sup>23+</sup>

onAnswer(callback: NoParamCallback): void

注册通话接听的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('answer')](#onanswer11)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型   |  必填 | 说明     |
| -------- | --------- | ---- | --------- |
| callback | NoParamCallback                                               | 是   | 回调函数。                      |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.onAnswer(() => {
  console.info('on call answer');
});
```

## off('answer')<sup>11+</sup>

off(type: 'answer', callback?: Callback\<void>): void

注销通话接听事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offAnswer](#offanswer23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| type     | string               | 是   | 关闭对应的事件监听，支持的事件是`'answer'`。 |
| callback | Callback\<void>     | 否   | 回调函数。<br>当事件监听取消成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('answer');
```

## offAnswer<sup>23+</sup>

offAnswer(callback?: NoParamCallback): void

注销通话接听事件的监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('answer')](#offanswer11)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| callback | NoParamCallback     | 否   | 回调函数。<br>当事件监听取消成功，err为null，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offAnswer();
```

## on('hangUp')<sup>11+</sup>

on(type: 'hangUp', callback: Callback\<void>): void

注册通话挂断的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onHangUp](#onhangup23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名   | 类型  |   必填 | 说明     |
| -------- | --------- | ---- | --------- |
| type     | string    | 是   | 事件回调类型，支持事件`'hangUp'`：当通话挂断时，触发该事件。 |
| callback | Callback\<void>                                               | 是   | 回调函数。                                             |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.on('hangUp', () => {
  console.info('on call hangUp');
});
```

## onHangUp<sup>23+</sup>

onHangUp(callback: NoParamCallback): void

注册通话挂断的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('hangUp')](#onhangup11)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型  |   必填 | 说明     |
| -------- | --------- | ---- | --------- |
| callback | NoParamCallback                                               | 是   | 回调函数。                                             |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.onHangUp(() => {
  console.info('on call hangUp');
});
```

## off('hangUp')<sup>11+</sup>

off(type: 'hangUp', callback?: Callback\<void>): void

注销通话挂断事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offHangUp](#offhangup23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| type     | string               | 是   | 关闭对应的事件监听，支持的事件是`'hangUp'`。 |
| callback | Callback\<void>      | 否   | 回调函数。<br>当事件监听取消成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('hangUp');
```

## offHangUp<sup>23+</sup>

offHangUp(callback?: NoParamCallback): void

注销通话挂断事件的监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('hangUp')](#offhangup11)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| callback | NoParamCallback      | 否   | 回调函数。<br>当事件监听取消成功，err为null，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offHangUp();
```

## on('toggleCallMute')<sup>11+</sup>

on(type: 'toggleCallMute', callback: Callback\<void>): void

注册通话静音的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onToggleCallMute](#ontogglecallmute23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名   | 类型  |   必填 | 说明     |
| -------- | --------- | ---- | --------- |
| type     | string    | 是   | 事件回调类型，支持事件`'toggleCallMute'`：当通话静音或解除静音时，触发该事件。 |
| callback | Callback\<void>                                               | 是   | 回调函数。                                             |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.on('toggleCallMute', () => {
  console.info('on call toggleCallMute');
});
```

## onToggleCallMute<sup>23+</sup>

onToggleCallMute(callback: NoParamCallback): void

注册通话静音的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('toggleCallMute')](#ontogglecallmute11)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型  |   必填 | 说明     |
| -------- | --------- | ---- | --------- |
| callback | NoParamCallback                                               | 是   | 回调函数。                                             |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------ |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.onToggleCallMute(() => {
  console.info('on call toggleCallMute');
});
```

## off('toggleCallMute')<sup>11+</sup>

off(type: 'toggleCallMute', callback?: Callback\<void>): void

注销通话静音事件的监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offToggleCallMute](#offtogglecallmute23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| type     | string               | 是   | 关闭对应的事件监听，支持的事件是`'toggleCallMute'`。 |
| callback | Callback\<void>    | 否   | 回调函数。<br>当事件监听取消成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('toggleCallMute');
```

## offToggleCallMute<sup>23+</sup>

offToggleCallMute(callback?: NoParamCallback): void

注销通话静音事件的监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('toggleCallMute')](#offtogglecallmute11)。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| callback | NoParamCallback    | 否   | 回调函数。<br>当事件监听取消成功，err为null，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offToggleCallMute();
```

## on('castDisplayChange')<sup>12+</sup>

on(type: 'castDisplayChange', callback: Callback\<CastDisplayInfo>): void

注册扩展屏投播显示设备变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onCastDisplayChange](#oncastdisplaychange23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.ExtendedDisplayCast

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| type     | string    | 是   | 事件回调类型，支持事件`'castDisplayChange'`：当扩展屏投播显示设备变化时触发事件。 |
| callback | Callback\<[CastDisplayInfo](arkts-apis-avsession-i.md#castdisplayinfo12)\>   | 是   | 回调函数。参数是扩展屏投播显示设备信息。                            |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
let castDisplay: avSession.CastDisplayInfo;
currentAVSession.on('castDisplayChange', (display: avSession.CastDisplayInfo) => {
    if (display.state === avSession.CastDisplayState.STATE_ON) {
        castDisplay = display;
        console.info(`Succeeded in castDisplayChange display : ${display.id} ON`);
    } else if (display.state === avSession.CastDisplayState.STATE_OFF){
        console.info(`Succeeded in castDisplayChange display : ${display.id} OFF`);
});
```

## onCastDisplayChange<sup>23+</sup>

onCastDisplayChange(callback: Callback\<CastDisplayInfo>): void

注册扩展屏投播显示设备变化的事件监听。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('castDisplayChange')](#oncastdisplaychange12)。

**系统能力：** SystemCapability.Multimedia.AVSession.ExtendedDisplayCast

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| callback | Callback<[CastDisplayInfo](arkts-apis-avsession-i.md#castdisplayinfo12)>   | 是   | 回调函数。参数是扩展屏投播显示设备信息。                            |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
let castDisplay: avSession.CastDisplayInfo;
currentAVSession.onCastDisplayChange((display: avSession.CastDisplayInfo) => {
    if (display.state === avSession.CastDisplayState.STATE_ON) {
        castDisplay = display;
        console.info(`Succeeded in castDisplayChange display : ${display.id} ON`);
    } else if (display.state === avSession.CastDisplayState.STATE_OFF){
        console.info(`Succeeded in castDisplayChange display : ${display.id} OFF`);
});
```

## off('castDisplayChange')<sup>12+</sup>

off(type: 'castDisplayChange', callback?: Callback\<CastDisplayInfo>): void

注销扩展屏投播显示设备变化事件监听。关闭后，不再进行该事件回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offCastDisplayChange](#offcastdisplaychange23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.ExtendedDisplayCast

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| type     | string    | 是   | 关闭对应的事件监听，支持的事件是`'castDisplayChange'`。 |
| callback | Callback<[CastDisplayInfo](arkts-apis-avsession-i.md#castdisplayinfo12)> | 否   | 回调函数。<br>当事件监听取消成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.|
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('castDisplayChange');
```

## offCastDisplayChange<sup>23+</sup>

offCastDisplayChange(callback?: Callback\<CastDisplayInfo>): void

注销扩展屏投播显示设备变化事件监听。关闭后，不再进行该事件回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('castDisplayChange')](#offcastdisplaychange12)。

**系统能力：** SystemCapability.Multimedia.AVSession.ExtendedDisplayCast

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| callback | Callback<[CastDisplayInfo](arkts-apis-avsession-i.md#castdisplayinfo12)>  | 否   | 回调函数。<br>当事件监听取消成功，err为null，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600101  | Session service exception |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.offCastDisplayChange();
```

## stopCasting<sup>10+</sup>

stopCasting(callback: AsyncCallback\<void>): void

结束投播。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                  | 必填 | 说明                                  |
| -------- | ------------------------------------- | ---- | ------------------------------------- |
| callback | AsyncCallback\<void> | 是   | 回调函数。<br>ArkTS-Dyn：当命令发送成功，err为undefined，否则返回错误对象。<br>ArkTS-Sta：当命令发送成功，err为null，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600109  | The remote connection is not established. |

**示例：**

```ts
currentAVSession.stopCasting(() => {
  console.info('Succeeded in stopping casting.');
});
```

## stopCasting<sup>10+</sup>

stopCasting(): Promise\<void>

结束投播。使用Promise异步回调。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型           | 说明                          |
| -------------- | ----------------------------- |
| Promise\<void> | Promise对象。当成功结束投播，无返回结果，否则返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 6600109  | The remote connection is not established. |

**示例：**

```ts
currentAVSession.stopCasting().then(() => { 
  console.info('Succeeded in stopping casting.');
});
 ```

## getOutputDeviceSync<sup>10+</sup>

getOutputDeviceSync(): OutputDeviceInfo

使用同步方法获取当前输出设备信息。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                            | 说明                              |
| ----------------| --------------------------------- |
| [OutputDeviceInfo](arkts-apis-avsession-i.md#outputdeviceinfo10) | 当前输出设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID   | 错误信息 |
|---------| --------------------------------------- |
| 6600101 | Session service exception. |
| 6600102 | The session does not exist. |

**示例：**

```ts
let currentOutputDevice: avSession.OutputDeviceInfo = currentAVSession.getOutputDeviceSync();
```

## getAllCastDisplays<sup>12+</sup>

getAllCastDisplays(): Promise<Array\<CastDisplayInfo>>

获取当前系统中所有支持扩展屏投播的显示设备。通过Promise异步回调。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.ExtendedDisplayCast

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                            | 说明                              |
| ----------------| --------------------------------- |
| Promise<Array<[CastDisplayInfo](arkts-apis-avsession-i.md#castdisplayinfo12)>>| Promise对象，返回当前系统中所有支持扩展屏投播的显示设备。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID   | 错误信息 |
|---------| --------------------------------------- |
| 6600101 | Session service exception. |
| 6600102 | The session does not exist. |

**示例：**

```ts
let castDisplay: avSession.CastDisplayInfo;
currentAVSession.getAllCastDisplays().then((data: Array< avSession.CastDisplayInfo >) => {
    if (data.length >= 1) {
       castDisplay = data[0];
     }
    });
```

## on('playFromAssetId')<sup>(deprecated)</sup>

on(type:'playFromAssetId', callback: (assetId: number) => void): void

注册媒体id播放事件监听。使用callback异步回调。

> **说明：**
> 
> 从 API version 11 开始支持，从 API version 20 开始废弃。建议使用[on('playWithAssetId')](#onplaywithassetid20)设置媒体id播放事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名   | 类型                 | 必填 | 说明     |
| -------- | -------------------- | ---- | --------- |
| type     | string               | 是   | 事件回调类型，支持的事件是`'playFromAssetId'`，当媒体id播放时，触发该事件回调。 |
| callback | (assetId: number) => void | 是   | 回调函数。参数assetId是媒体id。      |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.on('playFromAssetId', (assetId: number) => {
  console.info('on playFromAssetId entry');
});
```

## off('playFromAssetId')<sup>(deprecated)</sup>

off(type: 'playFromAssetId', callback?: (assetId: number) => void): void

注销媒体id播放事件监听，关闭后，不再进行该事件回调。

> **说明：**
>
> 从 API version 11 开始支持，从 API version 20 开始废弃。建议使用[off('playWithAssetId')](#offplaywithassetid20)取消媒体id播放事件监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名    | 类型                  | 必填 | 说明                   |
| -------- | -------------------- | ---- | ---------------------- |
| type     | string               | 是   | 关闭对应的事件监听，支持的事件是`'playFromAssetId'`。 |
| callback | (assetId: number) => void | 否   | 回调函数。<br>ArkTS-Dyn：当事件监听取消成功，err为undefined，否则返回错误对象。<br>ArkTS-Sta：当事件监听取消成功，err为null，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。参数assetId是媒体id。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ---------|
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('playFromAssetId');
```

## on('customDataChange')<sup>20+</sup>

on(type: 'customDataChange', callback: Callback\<Record\<string, Object>>): void

注册从远程设备发送的自定义数据的监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onCustomDataChange](#oncustomdatachange23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                           | 是   | 事件回调类型，支持事件'customDataChange'，当媒体提供方发送自定义数据时，触发该事件。 |
| callback | Callback\<Record\<string, Object>> | 是   | 回调函数，用于接收自定义数据。                               |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

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
| 6600102 | The session does not exist. |

**示例：**

```ts
currentAVSession.onCustomDataChange(callback) => {
    console.info(`Caught customDataChange event,the new callback is: ${JSON.stringify(callback)}`);
});
```

## off('customDataChange')<sup>20+</sup>

off(type: 'customDataChange', callback?: Callback\<Record\<string, Object>>): void

注销自定义数据监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offCustomDataChange](#offcustomdatachange23)。

**原子化服务API(仅ArkTS-Dyn)：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                           | 是   | 取消对应的事件监听，支持的事件是'customDataChange'。         |
| callback | Callback\<Record\<string, Object>> | 否   | 注册事件监听时的回调函数。该参数为可选参数，若不填写该参数，则认为取消会话所有与此事件相关的监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**示例：**

```ts
currentAVSession.off('customDataChange');
```

## offCustomDataChange<sup>23+</sup>

offCustomDataChange(callback?: Callback\<Record\<string, Object>>): void

注销自定义数据监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('customDataChange')](#offcustomdatachange20)。

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                    | 必填 | 说明                                                                                                    |
| -------- | ----------------------- | ---- | ------------------------------------------------------------------------------------------------------- |
| callback | Callback\<Record\<string, Object>> | 否 | 注销自定义数据的监听。 |

**错误码：**

以下错误码的详细介绍请参见[媒体会话管理错误码](errorcode-avsession.md)。

| 错误码ID | 错误信息 |
| -------- | ----------------                       |
| 6600101  | Session service exception. |
| 6600102 | The session does not exist. |

**示例：**

```ts
currentAVSession.offCustomDataChange();
```