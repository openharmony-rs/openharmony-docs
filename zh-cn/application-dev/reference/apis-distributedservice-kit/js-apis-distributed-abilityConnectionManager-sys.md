# @ohos.distributedsched.abilityConnectionManager (应用多端协同管理)(系统接口)
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @hu-zhiqiong-->

abilityConnectionManager模块提供了应用协同接口管理能力。设备组网成功（需登录同账号、双端打开蓝牙）后，系统应用和三方应用可以跨设备拉起同应用的一个[UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md)，拉起并连接成功后可实现跨设备数据传输，包括字符串、[ArrayBuffer](../../arkts-utils/arraybuffer-object.md)字节流、图片、传输流。协同会话用于管理设备间的连接状态和数据通道，传输流用于实现音视频数据的实时传输。

> **说明：**
>
> 本模块首批接口从API version 18开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块为系统接口。
> 本模块接口仅可在Stage模型下使用。

## 导入模块

```js
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## abilityConnectionManager.on('collaborateEvent')

on(type:&nbsp;'collaborateEvent',&nbsp;sessionId:&nbsp;number,&nbsp;callback:&nbsp;Callback&lt;CollaborateEventInfo&gt;):&nbsp;void

注册collaborateEvent事件的回调监听，用于接收协同事件的异步通知。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                    | 必填   | 说明    |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | 是    |   表示事件回调类型，支持的事件类型为'collaborateEvent'，完成`collaborateEvent()`调用，触发该事件。   |
| sessionId | number  | 是    | 表示创建的协同会话ID。    |
| callback | Callback&lt;[CollaborateEventInfo](#collaborateeventinfo)&gt; | 是    | 表示注册的回调函数，callback返回协同事件的信息。    |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  // 定义协同会话ID
  let sessionId = 100;
  // 注册collaborateEvent事件监听
  abilityConnectionManager.on("collaborateEvent", sessionId, (callbackInfo) => {
    hilog.info(0x0000, 'testTag', 'session collaborateEvent, eventType is', callbackInfo.eventType);
  });
  ```

## abilityConnectionManager.on('receiveImage')

on(type:&nbsp;'receiveImage',&nbsp;sessionId:&nbsp;number,&nbsp;callback:&nbsp;Callback&lt;EventCallbackInfo&gt;):&nbsp;void

注册receiveImage事件的回调监听，用于接收图片传输事件的异步通知。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                    | 必填   | 说明    |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | 是    |   表示事件回调类型，支持的事件类型为'receiveImage'，完成`sendImage()`调用，触发该事件。   |
| sessionId | number  | 是    | 表示创建的协同会话ID。    |
| callback | Callback&lt;[EventCallbackInfo](#eventcallbackinfo)&gt; | 是    | 表示注册的回调函数，用于接收图片接收事件信息。    |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  // sessionId需通过协同会话创建接口获取
  let sessionId = 100;
  // 注册receiveImage事件监听
  abilityConnectionManager.on("receiveImage", sessionId, (callbackInfo) => {
    hilog.info(0x0000, 'testTag', 'session receiveImage, sessionId is', callbackInfo.sessionId);
  });
  ```

## abilityConnectionManager.off('collaborateEvent')

off(type:&nbsp;'collaborateEvent',&nbsp;sessionId:&nbsp;number,&nbsp;callback?:&nbsp;Callback&lt;CollaborateEventInfo&gt;):&nbsp;void

取消collaborateEvent事件的回调监听。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                    | 必填   | 说明    |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | 是    |   表示事件回调类型，支持的事件类型为'collaborateEvent'。    |
| sessionId | number  | 是    | 表示创建的协同会话ID。    |
| callback | Callback&lt;[CollaborateEventInfo](js-apis-distributed-abilityConnectionManager.md#collaborateeventinfo)&gt; | 否    | 表示注册的回调函数。如果传入该参数，则关闭该监听。如果未传入该参数，则取消所有'collaborateEvent'事件监听。    |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';

  let sessionId = 100;
  // 取消collaborateEvent事件监听
  abilityConnectionManager.off("collaborateEvent", sessionId);
  ```

## abilityConnectionManager.off('receiveImage')

off(type:&nbsp;'receiveImage',&nbsp;sessionId:&nbsp;number,&nbsp;callback?:&nbsp;Callback&lt;EventCallbackInfo&gt;):&nbsp;void

取消receiveImage事件的回调监听。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                    | 必填   | 说明    |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | 是    |   表示事件回调类型，支持的事件类型为'receiveImage'，完成sendImage调用时触发该事件。    |
| sessionId | number  | 是    | 表示创建的协同会话ID。    |
| callback | Callback&lt;[EventCallbackInfo](#eventcallbackinfo)&gt; | 否    | 表示注册的回调函数。如果传入该参数，则关闭该监听。如果未传入该参数，则取消所有'receiveImage'事件监听。    |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';

  let sessionId = 100;
  // 取消receiveImage事件监听
  abilityConnectionManager.off("receiveImage", sessionId);
  ```

## abilityConnectionManager.sendImage

sendImage(sessionId:&nbsp;number,&nbsp;image:&nbsp;image.PixelMap,&nbsp;quality?:&nbsp;number):&nbsp;Promise&lt;void&gt;

应用连接成功并创建传输流后，设备A或设备B可向对端设备发送图片。图片会根据指定的压缩质量进行编码后，通过传输流通道发送至对端设备。发送成功后，对端设备可通过注册的回调接收图片，使用Promise异步回调。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                      | 必填   | 说明    |
| --------- | --------------------------------------- | ---- | ----- |
| sessionId | number | 是    | 表示协同会话ID，需先创建协同会话后获取。 |
| image | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | 是    | 表示图片信息。 |
| quality | number | 否    | 表示图像压缩质量，取值范围为0到100，默认值为30。数值越大，图片压缩质量越好，但文件体积越大；数值越小，压缩质量越低，文件体积越小。0-50适合快速预览场景，51-80适合普通传输场景，81-100适合高质量需求场景。 |

**返回值：**

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | 无返回值的Promise对象。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { photoAccessHelper } from '@kit.MediaLibraryKit';
  import { image } from '@kit.ImageKit';
  import { fileIo } from '@kit.CoreFileKit';

  try {
    let photoSelectOptions = new photoAccessHelper.PhotoSelectOptions();
    photoSelectOptions.MIMEType = photoAccessHelper.PhotoViewMIMETypes.IMAGE_TYPE;
    photoSelectOptions.maxSelectNumber = 5;
    let photoPicker = new photoAccessHelper.PhotoViewPicker();
    photoPicker.select(photoSelectOptions).then((photoSelectResult) => {
      if (!photoSelectResult) {
        hilog.error(0x0000, 'testTag', 'photoSelectResult = null');
        return;
      }

      // 以只读方式打开图片文件
      let file = fileIo.openSync(photoSelectResult.photoUris[0], fileIo.OpenMode.READ_ONLY);
      hilog.info(0x0000, 'testTag', 'file.fd:' + file.fd);

      let sessionId = 100;
      // 创建图片源对象
      let imageSourceApi: image.ImageSource = image.createImageSource(file.fd);
      if (imageSourceApi) {
        imageSourceApi.createPixelMap().then((pixelMap) => {
          // 发送图片到对端设备
          abilityConnectionManager.sendImage(sessionId, pixelMap)
        });
      } else {
        hilog.info(0x0000, 'testTag', 'imageSourceApi is undefined');
      }
    })
  } catch (error) {
    const err = error as BusinessError;
    hilog.error(0x0000, 'testTag', `photoPicker failed with error. Code: ${err.code}, message: ${err.message}`);
  }
  ```

## abilityConnectionManager.createStream

createStream(sessionId:&nbsp;number,&nbsp;param:&nbsp;StreamParam):&nbsp;Promise&lt;number&gt;

应用连接成功后，设备A或设备B可创建传输流用于发送图片和视频流。传输流是基于协同会话创建的数据通道，用于实现跨设备音视频数据的实时传输。创建成功后返回流ID，可用于后续流操作。业务结束后应及时销毁传输流，否则会增加系统功耗。使用Promise异步回调。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                      | 必填   | 说明    |
| --------- | --------------------------------------- | ---- | ----- |
| sessionId | number | 是    | 表示协同会话ID。 |
| param | [StreamParam](#streamparam) | 是    | 表示传输流的配置信息。 |

**返回值：**

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;number&gt; | 返回传输流ID的Promise对象。后续操作传输流的接口（如setSurfaceId、getSurfaceId、startStream、stopStream、destroyStream等）需要使用此ID。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[分布式设备管理错误码](./errorcode-device-manager.md)。

| 错误码ID | 错误信息 | 说明 |
| ------- | -------------------------------- | -------------------------------- |
| 202      | Not system App.| |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.| |
| 32300001      | Only one stream can be created for the current session.| 当前会话只能创建一个传输流，请确保在同一个会话中只调用一次createStream，如需创建新流请先销毁现有流。 |
| 32300003      | Bitrate not supported.| 不支持的比特率，请检查StreamParam中的bitrate参数是否在设备支持的范围内，建议使用默认值80000。 |
| 32300004      | Color space not supported.| 不支持的色彩空间，请检查StreamParam中的colorSpaceConversionTarget参数，确保使用支持的色彩空间类型。 |

**示例：**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  hilog.info(0x0000, 'testTag', 'startStream');
  let sessionId = 100;
  // 创建传输流
  abilityConnectionManager.createStream(sessionId ,{name: 'receive', role: 0}).then(async (streamId) => {
    // 配置Surface参数
    let surfaceParam: abilityConnectionManager.SurfaceParam = {
      width: 640,
      height: 480,
      format: 1
    }
    // 获取Surface唯一标识符
    let surfaceId = abilityConnectionManager.getSurfaceId(streamId, surfaceParam);
    hilog.info(0x0000, 'testTag', 'surfaceId is ' + surfaceId);
    // 将SurfaceID存储到全局状态管理中
    AppStorage.setOrCreate<string>('surfaceId', surfaceId);
    // 启动传输流
    abilityConnectionManager.startStream(streamId);
  })
  ```

## abilityConnectionManager.setSurfaceId

setSurfaceId(streamId:&nbsp;number,&nbsp;surfaceId:&nbsp;string,&nbsp;param:&nbsp;SurfaceParam):&nbsp;void

设置传输流与Surface的绑定关系。Surface用于承载音视频数据的显示或采集，绑定后传输流的音视频数据将直接渲染到Surface上或从Surface采集数据。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                      | 必填   | 说明    |
| --------- | --------------------------------------- | ---- | ----- |
| streamId | number | 是    | 表示传输流ID，需通过createStream接口创建传输流后获取。 |
| surfaceId | string | 是    | 表示Surface的唯一标识符，需通过getSurfaceId接口获取。 |
| param | [SurfaceParam](#surfaceparam) | 是    | 表示Surface的配置参数，包括编码宽度、高度、像素格式等。配置后Surface将按照指定参数进行视频帧的编码和渲染。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  hilog.info(0x0000, 'testTag', 'setSurfaceId');
  let sessionId = 100;
  abilityConnectionManager.createStream(sessionId ,{name: 'receive', role: 0}).then(async (streamId) => {
    let surfaceParam: abilityConnectionManager.SurfaceParam = {
      width: 640,
      height: 480,
      format: 1
    }
    let surfaceId = abilityConnectionManager.getSurfaceId(streamId, surfaceParam);
    // 设置传输流与Surface的绑定关系
    abilityConnectionManager.setSurfaceId(streamId, surfaceId, surfaceParam);
  })
  ```

## abilityConnectionManager.getSurfaceId

getSurfaceId(streamId:&nbsp;number,&nbsp;param:&nbsp;SurfaceParam):&nbsp;string

获取指定传输流绑定的Surface的唯一标识符。Surface ID可用于将Surface与组件关联，实现音视频数据的显示。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                      | 必填   | 说明    |
| --------- | --------------------------------------- | ---- | ----- |
| streamId | number | 是    | 表示传输流ID，需通过createStream接口创建传输流后获取。 |
| param | [SurfaceParam](#surfaceparam) | 是    | 表示Surface的配置参数。 |

**返回值：**

| 类型                  | 说明               |
| ------------------- | ---------------- |
| string | Surface的唯一标识符，可用于后续setSurfaceId等操作。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  hilog.info(0x0000, 'testTag', 'getSurfaceId');
  let sessionId = 100;
  abilityConnectionManager.createStream(sessionId ,{name: 'receive', role: 0}).then(async (streamId) => {
    let surfaceParam: abilityConnectionManager.SurfaceParam = {
      width: 640,
      height: 480,
      format: 1
    }
    let surfaceId = abilityConnectionManager.getSurfaceId(streamId, surfaceParam);
  })
  ```

## abilityConnectionManager.updateSurfaceParam

updateSurfaceParam(streamId:&nbsp;number,&nbsp;param:&nbsp;SurfaceParam):&nbsp;void

更新与传输流绑定的Surface的配置信息，使新的配置参数生效。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                      | 必填   | 说明    |
| --------- | --------------------------------------- | ---- | ----- |
| streamId | number | 是    | 表示传输流ID，需通过createStream接口创建传输流后获取。 |
| param | [SurfaceParam](#surfaceparam) | 是    | 表示Surface的配置参数。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  hilog.info(0x0000, 'testTag', 'updateSurfaceParam');
  let sessionId = 100;
  abilityConnectionManager.createStream(sessionId ,{name: 'receive', role: 0}).then(async (streamId) => {
    let surfaceParam: abilityConnectionManager.SurfaceParam = {
      width: 640,
      height: 480,
      format: 1
    }
    // 更新Surface的配置参数
    abilityConnectionManager.updateSurfaceParam(streamId, surfaceParam);
  })
  ```

## abilityConnectionManager.destroyStream

destroyStream(streamId:&nbsp;number):&nbsp;void

发送图片和视频流等业务结束后，创建传输流的应用应及时销毁传输流，否则会增加系统功耗。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                      | 必填   | 说明    |
| --------- | --------------------------------------- | ---- | ----- |
| streamId | number | 是    | 表示传输流ID，需通过createStream接口创建传输流后获取。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  let sessionId = 100;
  hilog.info(0x0000, 'testTag', 'destroyStream called');
  abilityConnectionManager.createStream(sessionId, {name: 'receive', role: 0}).then((streamId) => {
    // 销毁传输流
    abilityConnectionManager.destroyStream(streamId);
  });
  ```

## abilityConnectionManager.startStream

startStream(streamId:&nbsp;number):&nbsp;void

启动指定传输流，使传输流开始发送或接收视频数据。启动前需确保传输流已完成Surface绑定，否则无法正常启动。业务结束后应及时销毁传输流，否则会增加系统功耗。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                      | 必填   | 说明    |
| --------- | --------------------------------------- | ---- | ----- |
| streamId | number | 是    | 表示传输流ID，需通过createStream接口创建传输流后获取。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[分布式设备管理错误码](./errorcode-device-manager.md)。

| 错误码ID | 错误信息 | 说明 |
| ------- | -------------------------------- | -------------------------------- |
| 202      | Not system App.| |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.| |
| 32300002      | The stream at the receive end is not started. | 接收端的传输流未启动，请先启动接收端流后再启动发送端流。 |

**示例：**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  let sessionId = 100;
  hilog.info(0x0000, 'testTag', 'startStream called');
  abilityConnectionManager.createStream(sessionId, {name: 'receive', role: 0}).then((streamId) => {
    // 启动传输流
    abilityConnectionManager.startStream(streamId);
  });
  ```

## abilityConnectionManager.stopStream

stopStream(streamId:&nbsp;number):&nbsp;void

停止指定传输流，使传输流停止发送或接收视频数据。业务结束后应及时销毁传输流，否则会增加系统功耗。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                      | 必填   | 说明    |
| --------- | --------------------------------------- | ---- | ----- |
| streamId | number | 是    | 表示传输流ID，需通过createStream接口创建传输流后获取。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  let sessionId = 100;
  hilog.info(0x0000, 'testTag', 'stopStream called');
  abilityConnectionManager.createStream(sessionId, {name: 'receive', role: 0}).then((streamId) => {
    // 停止传输流
    abilityConnectionManager.stopStream(streamId);
  });
  ```

## StreamParam

流传输配置的参数。用于配置传输流的传输方式和参数。其中role参数区分发送流（SOURCE）和接收流（SINK），发送流需要配置bitrate和colorSpaceConversionTarget等参数。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

| 名称       | 类型    | 只读 | 可选 | 说明          |
| -------- | ------ | ---- | ---- | ----------- |
| name  | string   | 否    | 否 |   表示流传输的名称（接收端必须与发送端一致）。 |
| role  | [StreamRole](#streamrole)     | 否    | 否   |   表示流传输的方式（可以是接收流或发送流）。bitrate参数仅在role为SOURCE时有效。 |
| bitrate  | number   | 否    | 是   |   表示视频比特率，单位为bps，仅在发送端有效，默认值为80000。取值范围需参考设备支持的比特率范围，超出范围时返回错误码32300003。数值越大，视频清晰度越高，但带宽占用越大；数值越小，视频越模糊，但传输更流畅。 |
| colorSpaceConversionTarget  | [colorSpaceManager.ColorSpace](../apis-arkgraphics2d/js-apis-colorSpaceManager.md#colorspace)     | 否    | 是   |  表示转换的目标色彩空间。设置该参数后，视频流的色彩空间将转换为目标色彩空间，用于适配不同设备的色彩显示需求。不传此参数时不进行色彩空间转换。 |

## SurfaceParam

Surface配置参数。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

| 名称       | 类型   | 只读 | 可选 | 说明      |
| -------- | ------ | ---- | ---- | ------- |
| width | number | 否    | 否   | 表示编码宽度，单位为像素。必须在流启动前设置，流启动后到停止前均无法更新。如需更新需要将流停止后重新配置。 |
| height | number | 否    | 否  | 表示编码高度，单位为像素。必须在流启动前设置，流启动后到停止前均无法更新。如需更新需要将流停止后重新配置。 |
| format | [VideoPixelFormat](#videopixelformat) | 否    | 是   | 表示视频像素格式，此选项必须在发送端配置。NV12适合大多数场景，NV21适合Android平台兼容场景。必须在流启动前设置，流启动后到停止前均无法更新。不传入时默认为NV21。 |
| rotation | number | 否    | 是   | 表示视频的旋转角度（取值范围为{0, 90, 180, 270}，默认值为0）。0表示不旋转，90表示向右旋转90度（适合竖屏视频），180表示旋转180度，270表示向左旋转90度。不传入时默认为0。 |
| flip | [FlipOptions](#flipoptions) | 否    | 是   | 表示视频是否反转。HORIZONTAL表示水平翻转（适合镜像场景），VERTICAL表示垂直翻转。不传入时不进行翻转。 |

## FlipOptions

翻转选项的枚举。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

| 名称|  值 | 说明 |
|-------|-------|-------|
| HORIZONTAL | 0 | 表示水平翻转。 |
| VERTICAL | 1 | 表示垂直翻转。 |

## StreamRole

流传输的方式。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

| 名称|  值 | 说明 |
|-------|-------|-------|
| SOURCE  | 0 | 表示流是发送流。 |
| SINK  | 1 | 表示流是接收流。 |

## VideoPixelFormat

视频像素格式的枚举。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

| 名称|  值 | 说明 |
|-------|-------|-------|
| UNKNOWN   | -1 | 表示未知的像素格式。 |
| NV12  | 0 | 表示NV12，YUV420半平面格式。 |
| NV21  | 1 | 表示NV21，YUV420半平面格式。 |

## ConnectOptions

应用连接时所需的连接选项。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

| 名称          | 类型    | 只读   | 可选   | 说明          |
| ----------- | ------- | ---- | ---- | ----------- |
| needSendStream    | boolean  | 否    | 是    | true表示需要发送流（当本端需要向对端发送视频流时选择），false表示不需要发送流（当本端只接收不发送时选择）。默认值为false。    |
| needReceiveStream    | boolean  | 否    | 是    | true表示需要接收流（当本端需要从对端接收视频流时选择），false表示不需要接收流（当本端只发送不接收时选择）。默认值为false。     |

## EventCallbackInfo

回调方法的接收信息。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

| 名称       | 类型    | 只读  | 可选  | 说明          |
| -------- | ------ | ---- | ---- | ----------- |
| image  | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | 否   | 是   |   表示接收的图片。 |

## StartOptionParams

启动选项参数的枚举。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

| 名称|  值 | 说明 |
|-------|-------|-------|
| START_IN_BACKGROUND | 1 |表示在拉起对端应用时，不显示UI界面，仅启动应用进程。|
