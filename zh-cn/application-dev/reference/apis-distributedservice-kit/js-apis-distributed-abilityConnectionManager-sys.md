# @ohos.distributedsched.abilityConnectionManager (应用多端协同管理)(系统接口)
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @hu-zhiqiong-->

abilityConnectionManager模块提供了应用协同接口管理能力，支持在设备间建立协同会话并实现跨设备数据传输与实时音视频流传输。该模块适用于协同办公、跨设备屏幕共享、多屏互动等场景，解决了应用在不同设备间无缝协作的问题，打破了单一设备的使用边界，让用户可以在多设备之间顺畅切换，提升工作效率和用户体验。设备组网成功（需登录同账号、双端打开蓝牙）后，系统应用和三方应用可以跨设备拉起同应用的一个[UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md)，拉起并连接成功后可实现跨设备数据传输，包括字符串、[ArrayBuffer](../../arkts-utils/arraybuffer-object.md)字节流、图片、传输流。协同会话用于管理设备间的连接状态和数据通道，传输流用于实现音视频数据的实时传输。协同会话通过跨设备连接接口创建，创建成功后会返回会话ID用于后续操作。

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

注册collaborateEvent事件的回调监听，用于接收协同事件的异步通知。需与off('collaborateEvent')方法配合使用，在不需要接收事件时，应调用off('collaborateEvent')取消监听以释放资源。

**使用场景**：跨设备拉起应用时，监听协同会话的状态变化（如对方设备接收/拒绝协同请求），以更新本端UI状态或处理协同流程。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                    | 必填   | 说明    |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | 是    |   表示事件回调类型，支持的事件类型为'collaborateEvent'，当协同状态发生变化时触发该事件。   |
| sessionId | number  | 是    | 表示创建的协同会话ID。    |
| callback | Callback&lt;[CollaborateEventInfo](#collaborateeventinfo)&gt; | 是    | 表示注册的回调函数，callback返回协同事件的信息。    |

**错误码：**

以下错误码的详细原因和处理步骤请参考[通用错误码](../errorcode-universal.md)。

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
  // 注册collaborateEvent事件监听
  abilityConnectionManager.on('collaborateEvent', sessionId, (callbackInfo) => {
    hilog.info(0x0000, 'testTag', 'session collaborateEvent, eventType is', callbackInfo.eventType);
  });
  ```

## abilityConnectionManager.on('receiveImage')

on(type:&nbsp;'receiveImage',&nbsp;sessionId:&nbsp;number,&nbsp;callback:&nbsp;Callback&lt;EventCallbackInfo&gt;):&nbsp;void

注册receiveImage事件的回调监听，用于接收图片传输事件的异步通知。需与off('receiveImage')方法配合使用，在不需要接收图片时，应调用off('receiveImage')取消监听以释放资源。

**使用场景**：远程视频通话、跨设备图片分享、屏幕共享等需要接收对端发送图片数据时，监听图片接收事件并处理。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                    | 必填   | 说明    |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | 是    |   表示事件回调类型，支持的事件类型为'receiveImage'，当接收到对端设备发送的图片时触发该事件。   |
| sessionId | number  | 是    | 表示创建的协同会话ID。    |
| callback | Callback&lt;[EventCallbackInfo](#eventcallbackinfo)&gt; | 是    | 表示注册的回调函数，用于接收图片接收事件信息。    |

**错误码：**

以下错误码的详细原因和处理步骤请参考[通用错误码](../errorcode-universal.md)。

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
  abilityConnectionManager.on('receiveImage', sessionId, (callbackInfo) => {
    hilog.info(0x0000, 'testTag', 'session receiveImage, sessionId is', callbackInfo.sessionId);
  });
  ```

## abilityConnectionManager.off('collaborateEvent')

off(type:&nbsp;'collaborateEvent',&nbsp;sessionId:&nbsp;number,&nbsp;callback?:&nbsp;Callback&lt;CollaborateEventInfo&gt;):&nbsp;void

取消collaborateEvent事件的回调监听。需与on('collaborateEvent')方法配合使用，在不需要接收协同事件或组件销毁时，应调用此方法取消监听以释放资源。

**使用场景**：协同会话结束、页面销毁或不再需要监听协同状态变化时，及时取消监听以释放资源。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                    | 必填   | 说明    |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | 是    |   表示事件回调类型，支持的事件类型为'collaborateEvent'。    |
| sessionId | number  | 是    | 表示创建的协同会话ID。    |
| callback | Callback&lt;[CollaborateEventInfo](#collaborateeventinfo)&gt; | 否    | 表示注册的回调函数。如果传入该参数，则取消该callback的监听。如果未传入该参数，则取消所有'collaborateEvent'事件监听。    |

**错误码：**

以下错误码的详细原因和处理步骤请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';

  // sessionId需通过协同会话创建接口获取
  let sessionId = 100;
  // 取消collaborateEvent事件监听
  abilityConnectionManager.off('collaborateEvent', sessionId);
  ```

## abilityConnectionManager.off('receiveImage')

off(type:&nbsp;'receiveImage',&nbsp;sessionId:&nbsp;number,&nbsp;callback?:&nbsp;Callback&lt;EventCallbackInfo&gt;):&nbsp;void

取消receiveImage事件的回调监听。需与on('receiveImage')方法配合使用，在不需要接收图片或组件销毁时，应调用此方法取消监听以释放资源。

**使用场景**：不再需要接收图片传输事件（如协同会话结束、页面销毁）时，及时取消监听以释放资源。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                    | 必填   | 说明    |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | 是    |   表示事件回调类型，支持的事件类型为'receiveImage'。    |
| sessionId | number  | 是    | 表示创建的协同会话ID。    |
| callback | Callback&lt;[EventCallbackInfo](#eventcallbackinfo)&gt; | 否    | 表示注册的回调函数。如果传入该参数，则取消该callback的监听。如果未传入该参数，则取消所有'receiveImage'事件监听。    |

**错误码：**

以下错误码的详细原因和处理步骤请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';

  // sessionId需通过协同会话创建接口获取
  let sessionId = 100;
  // 取消receiveImage事件监听
  abilityConnectionManager.off('receiveImage', sessionId);
  ```

## abilityConnectionManager.sendImage

sendImage(sessionId:&nbsp;number,&nbsp;image:&nbsp;image.PixelMap,&nbsp;quality?:&nbsp;number):&nbsp;Promise&lt;void&gt;

应用连接成功并创建传输流后，设备A或设备B可向对端设备发送图片。图片会根据指定的压缩质量进行编码后，通过传输流通道发送至对端设备。发送成功后，对端设备可通过注册的回调接收图片，使用Promise异步回调。业务结束后应及时销毁传输流，否则会增加系统功耗。

**使用场景**：跨设备视频通话中发送视频帧、远程协作时发送截图、跨设备图片共享等需要向对端发送图片数据的场景。

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
| Promise&lt;void&gt; | 无返回值的Promise对象。resolve表示图片发送成功，reject表示图片发送失败或出错。 |

**错误码：**

以下错误码的详细原因和处理步骤请参考[通用错误码](../errorcode-universal.md)。

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
    // 打开图片选择器，让用户选择图片
    photoPicker.select(photoSelectOptions).then((photoSelectResult) => {
      if (!photoSelectResult) {
        hilog.error(0x0000, 'testTag', 'photoSelectResult = null');
        return;
      }

      // 以只读方式打开图片文件
      let file = fileIo.openSync(photoSelectResult.photoUris[0], fileIo.OpenMode.READ_ONLY);
      hilog.info(0x0000, 'testTag', 'file.fd:' + file.fd);

      // 示例中sessionId为模拟值，实际需通过abilityConnectionManager.connectAbility等接口创建协同会话后获取
      let sessionId = 100;
      // 根据文件描述符创建图片源对象
      let imageSourceApi: image.ImageSource = image.createImageSource(file.fd);
      if (imageSourceApi) {
        // 将图片源转换为像素映射对象
        imageSourceApi.createPixelMap().then((pixelMap) => {
          // 发送图片到对端设备
          abilityConnectionManager.sendImage(sessionId, pixelMap).then(() => {
            hilog.info(0x0000, 'testTag', 'sendImage success');
          }).catch((err: BusinessError) => {
            hilog.error(0x0000, 'testTag', `sendImage failed with error. Code: ${err.code}, message: ${err.message}`);
          });
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

**使用场景**：跨设备视频通话、屏幕共享、远程协作等需要实时传输音视频数据时，创建传输流通道。

**调用顺序：**
1. 调用createStream()创建传输流，获取streamId
2. （视频流可选）调用getSurfaceId()获取surfaceId
3. （视频流可选）调用setSurfaceId()绑定Surface
4. 调用startStream()启动传输流
5. 使用完毕后调用stopStream()停止传输流
6. 最后调用destroyStream()销毁传输流

**配对调用：** createStream()需与destroyStream()配对使用，业务结束后必须调用destroyStream()释放资源。

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

以下错误码的详细原因和处理步骤请参考[通用错误码](../errorcode-universal.md)和[分布式设备管理错误码](./errorcode-device-manager.md)。

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
  // 创建传输流，配置名称为'receive'，角色为SOURCE（发送流）
  abilityConnectionManager.createStream(sessionId, {name: 'receive', role: 0}).then(async (streamId) => {
    // 配置Surface参数
    let surfaceParam: abilityConnectionManager.SurfaceParam = {
      width: 640,
      height: 480,
      format: 1
    }
    // 获取Surface唯一标识符
    let surfaceId = abilityConnectionManager.getSurfaceId(streamId, surfaceParam);
    hilog.info(0x0000, 'testTag', 'surfaceId is ' + surfaceId);
    // 将SurfaceID存储到全局状态管理中，供后续UI组件使用
    AppStorage.setOrCreate<string>('surfaceId', surfaceId);
    // 启动传输流
    abilityConnectionManager.startStream(streamId);
  })
  ```

## abilityConnectionManager.setSurfaceId

setSurfaceId(streamId:&nbsp;number,&nbsp;surfaceId:&nbsp;string,&nbsp;param:&nbsp;SurfaceParam):&nbsp;void

设置传输流与Surface的绑定关系。Surface用于承载音视频数据的显示或采集，绑定后传输流的音视频数据将直接渲染到Surface上或从Surface采集数据。

**使用场景**：跨设备视频通话中，将接收端的视频流绑定到Surface进行显示；或发送端将Surface采集的视频流传输到对端。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                      | 必填   | 说明    |
| --------- | --------------------------------------- | ---- | ----- |
| streamId | number | 是    | 表示传输流ID，需通过createStream接口创建传输流后获取。 |
| surfaceId | string | 是    | 表示Surface的唯一标识符，需通过getSurfaceId接口获取。 |
| param | [SurfaceParam](#surfaceparam) | 是    | 表示Surface的配置参数，包括编码宽度、高度、像素格式等。配置后Surface将按照指定参数进行视频帧的编码和渲染。需在流启动前完成绑定。 |

**错误码：**

以下错误码的详细原因和处理步骤请参考[通用错误码](../errorcode-universal.md)。

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
  abilityConnectionManager.createStream(sessionId, {name: 'receive', role: 0}).then(async (streamId) => {
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

**使用场景**：跨设备视频通话中，获取Surface ID并传递给XComponent组件，实现视频流的显示。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                      | 必填   | 说明    |
| --------- | --------------------------------------- | ---- | ----- |
| streamId | number | 是    | 表示传输流ID，需通过createStream接口创建传输流后获取。 |
| param | [SurfaceParam](#surfaceparam) | 是    | 表示Surface的配置参数。需在流启动前完成Surface绑定。 |

**返回值：**

| 类型                  | 说明               |
| ------------------- | ---------------- |
| string | Surface的唯一标识符，可用于后续setSurfaceId等操作。 |

**错误码：**

以下错误码的详细原因和处理步骤请参考[通用错误码](../errorcode-universal.md)。

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
  abilityConnectionManager.createStream(sessionId, {name: 'receive', role: 0}).then(async (streamId) => {
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

**使用场景**：视频通话过程中动态调整视频分辨率（如网络状况变化时降低分辨率以保证流畅度）或修改视频格式时，调用此接口更新配置。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                      | 必填   | 说明    |
| --------- | --------------------------------------- | ---- | ----- |
| streamId | number | 是    | 表示传输流ID，需通过createStream接口创建传输流后获取。 |
| param | [SurfaceParam](#surfaceparam) | 是    | 表示Surface的配置参数。 |

**错误码：**

以下错误码的详细原因和处理步骤请参考[通用错误码](../errorcode-universal.md)。

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
  abilityConnectionManager.createStream(sessionId, {name: 'receive', role: 0}).then(async (streamId) => {
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

发送图片和视频流等业务结束后，创建传输流的应用应及时销毁传输流，否则会增加系统功耗。需与createStream()方法配对使用，在业务结束后必须调用此方法销毁传输流以释放资源。

**使用场景**：跨设备视频通话结束、屏幕共享关闭、远程协作完成等业务场景结束后，及时销毁传输流以释放资源。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                      | 必填   | 说明    |
| --------- | --------------------------------------- | ---- | ----- |
| streamId | number | 是    | 表示传输流ID，需通过createStream接口创建传输流后获取。 |

**错误码：**

以下错误码的详细原因和处理步骤请参考[通用错误码](../errorcode-universal.md)。

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

启动指定传输流，使传输流开始发送或接收视频数据。启动前需确保传输流已完成Surface绑定，否则无法正常启动。需与stopStream()方法配对使用，使用完毕后应调用stopStream()停止传输流，最后调用destroyStream()销毁传输流以释放资源。

**使用场景**：跨设备视频通话建立后，接收端和发送端均调用此接口启动视频流的传输。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                      | 必填   | 说明    |
| --------- | --------------------------------------- | ---- | ----- |
| streamId | number | 是    | 表示传输流ID，需通过createStream接口创建传输流后获取。 |

**错误码：**

以下错误码的详细原因和处理步骤请参考[通用错误码](../errorcode-universal.md)和[分布式设备管理错误码](./errorcode-device-manager.md)。

| 错误码ID | 错误信息 | 说明 |
| ------- | -------------------------------- | -------------------------------- |
| 202      | Not system App.| |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.| |
| 32300002      | The stream at the receive end is not started. | 接收端的传输流未启动，请先启动接收端流后再启动发送端流；或传输流未完成Surface绑定，请先调用setSurfaceId进行绑定。 |

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

停止指定传输流，使传输流停止发送或接收视频数据。需与startStream()方法配对使用，在不需要传输数据时应调用此方法停止传输流，最后调用destroyStream()销毁传输流以释放资源。

**使用场景**：视频通话暂停、用户关闭摄像头、切换前后摄像头等需要临时停止视频传输时调用。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**系统API**：此接口为系统接口。

**参数：**

| 参数名       | 类型                                      | 必填   | 说明    |
| --------- | --------------------------------------- | ---- | ----- |
| streamId | number | 是    | 表示传输流ID，需通过createStream接口创建传输流后获取。 |

**错误码：**

以下错误码的详细原因和处理步骤请参考[通用错误码](../errorcode-universal.md)。

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
| format | [VideoPixelFormat](#videopixelformat) | 否    | 是   | 表示视频像素格式，此选项必须在发送端配置。NV12适合大多数场景，NV21适合Android平台兼容场景。不同格式对压缩效率和视频质量有影响，建议根据实际需求选择。必须在流启动前设置，流启动后到停止前均无法更新。不传入时默认为NV21。 |
| rotation | number | 否    | 是   | 表示视频的旋转角度（取值范围为{0, 90, 180, 270}，默认值为0）。0表示不旋转，90表示向右旋转90度（适合竖屏视频），180表示旋转180度，270表示向左旋转90度。不传入时默认为0。旋转操作可能影响编码性能，建议在需要时使用。 |
| flip | [FlipOptions](#flipoptions) | 否    | 是   | 表示视频是否反转。HORIZONTAL表示水平翻转（适合镜像场景），VERTICAL表示垂直翻转。不传入时不进行翻转。翻转操作可能影响编码性能，建议在需要时使用。 |

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
| image  | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | 否   | 是   |   表示接收的图片。不传入该参数时表示未接收到图片或图片信息不可用。 |

## CollaborateEventInfo

协同事件信息。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

| 名称       | 类型   | 只读   | 可选   | 说明      |
| -------- | ------ | ---- | ---- | ------- |
| eventType | [CollaborateEventType](#collaborateeventtype) | 否   | 否 | 表示协同事件的类型。 |
| eventMsg | string | 否   | 是   | 表示协同事件的消息内容。 |

## CollaborateEventType

协同事件类型的枚举。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

| 名称|  值 | 说明 |
|-------|-------|-------|
| SEND_FAILURE | 0 |表示任务发送失败。|
| COLOR_SPACE_CONVERSION_FAILURE | 1 |表示色彩空间转换失败。|

## StartOptionParams

启动选项参数的枚举。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

| 名称|  值 | 说明 |
|-------|-------|-------|
| START_IN_BACKGROUND | 1 |表示在拉起对端应用时，不显示UI界面，仅启动应用进程。|
