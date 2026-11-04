# @ohos.distributedsched.abilityConnectionManager (Cross-Device Connection Management) (System API)
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=d8aa91dfdf43faa9e70ad015fcfeb24fb0de5ca2 translatedAt=2026-11-03T13:03:28.797Z pushedAt=2026-11-04T08:47:59.658Z nl=1 -->

The **abilityConnectionManager** module provides collaborative app interface management capabilities, supporting the establishment of collaborative sessions between devices and enabling cross-device data transmission and real-time audio/video stream transmission. This module is applicable to scenarios such as collaborative office work, solving the problem of seamless collaboration between applications on different devices, breaking the usage boundary of a single device, and allowing users to switch smoothly between multiple devices to improve work efficiency and user experience. After devices are networked successfully, system applications and third-party applications can start a [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md) of the same application across devices. After the application is started and connected successfully, cross-device data transmission can be implemented, including strings, [ArrayBuffer](../../arkts-utils/arraybuffer-object.md) byte streams, images, and transmission streams.

> **NOTE**
>
> The initial APIs of this module are supported since API version 18. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.
> The APIs of this module can be used only in the stage model.

## Modules to Import

```js
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## abilityConnectionManager.on('collaborateEvent')

on(type:&nbsp;'collaborateEvent',&nbsp;sessionId:&nbsp;number,&nbsp;callback:&nbsp;Callback&lt;CollaborateEventInfo&gt;):&nbsp;void

Registers a callback listener for the **collaborateEvent**. This API uses an asynchronous callback to return the result. This listener must be used in pairs with **off('collaborateEvent')**. When the event is no longer needed, cancel the listener in a timely manner to release resources.

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**System API**: This is a system API.

**Parameters**

| Name      | Type                                   | Mandatory  | Description   |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | Yes    |   Event callback type. The supported event type is **collaborateEvent**, which is triggered when the collaboration state changes.   |
| sessionId | number  | Yes    | ID of the created collaborative session, which is obtained after the collaborative session is created.    |
| callback | Callback&lt;[CollaborateEventInfo](./js-apis-distributed-abilityConnectionManager.md#collaborateeventinfo)&gt; | Yes    | Callback used to return the collaborative event information.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  // Obtain the sessionId through the collaborative session creation API.
  let sessionId = 100;
  // Register the collaborateEvent event listener.
  abilityConnectionManager.on('collaborateEvent', sessionId, (callbackInfo) => {
    hilog.info(0x0000, 'testTag', 'session collaborateEvent, eventType is', callbackInfo.eventType);
  });
  ```

## abilityConnectionManager.on('receiveImage')

on(type:&nbsp;'receiveImage',&nbsp;sessionId:&nbsp;number,&nbsp;callback:&nbsp;Callback&lt;EventCallbackInfo&gt;):&nbsp;void

Registers a callback listener for the receiveImage event to receive asynchronous notifications of image transmission events. This API must be used together with **off('receiveImage')**. When image reception is no longer needed, call **off('receiveImage')** to cancel the listener and release resources.

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**System API**: This is a system API.

**Parameters**

| Name      | Type                                   | Mandatory  | Description   |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | Yes    | Event callback type. The supported event type is **receiveImage**, which is triggered when an image sent by the peer device is received.   |
| sessionId | number  | Yes    | ID of the created collaborative session, which is obtained after the collaborative session is created.    |
| callback | Callback&lt;[EventCallbackInfo](#eventcallbackinfo)&gt; | Yes    | Callback used to return the image reception event information.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  // Obtain sessionId through the collaborative session creation API.
  let sessionId = 100;
  // Register the receiveImage event listener.
  abilityConnectionManager.on('receiveImage', sessionId, (callbackInfo) => {
    hilog.info(0x0000, 'testTag', 'session receiveImage, sessionId is', callbackInfo.sessionId);
  });
  ```

## abilityConnectionManager.off('collaborateEvent')

off(type:&nbsp;'collaborateEvent',&nbsp;sessionId:&nbsp;number,&nbsp;callback?:&nbsp;Callback&lt;CollaborateEventInfo&gt;):&nbsp;void

Unregisters the callback listener for the **collaborateEvent**. This API must be used together with **on('collaborateEvent')**. When collaboration events are no longer needed or the component is destroyed, call this API to cancel the listener and release resources.

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**System API**: This is a system API.

**Parameters**

| Name      | Type                                   | Mandatory  | Description   |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | Yes   |   Event type, which is **collaborateEvent**.   |
| sessionId | number  | Yes    | ID of the created collaborative session, which is obtained after the collaborative session is created.    |
| callback | Callback&lt;[CollaborateEventInfo](./js-apis-distributed-abilityConnectionManager.md#collaborateeventinfo)&gt; | No    | Callback for the **collaborateEvent**. If this parameter is passed, the listener of this callback is unregistered. If this parameter is not passed, all listeners of the **collaborateEvent** are unregistered.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';

  // Obtain the sessionId through the collaborative session creation API.
  let sessionId = 100;
  // Unsubscribe from the collaborateEvent event.
  abilityConnectionManager.off('collaborateEvent', sessionId);
  ```

## abilityConnectionManager.off('receiveImage')

off(type:&nbsp;'receiveImage',&nbsp;sessionId:&nbsp;number,&nbsp;callback?:&nbsp;Callback&lt;EventCallbackInfo&gt;):&nbsp;void

Unregisters the callback listener for the receiveImage event. This API must be used together with **on('receiveImage')**. When image reception is no longer needed or the component is destroyed, call this API to cancel the listener and release resources.

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**System API**: This is a system API.

**Parameters**

| Name      | Type                                   | Mandatory  | Description   |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | Yes   |   Event type, which is **receiveImage**.   |
| sessionId | number  | Yes    | ID of the created collaborative session, which is obtained after the collaborative session is created.    |
| callback | Callback&lt;[EventCallbackInfo](#eventcallbackinfo)&gt; | No    | Callback for the **receiveImage** event. If this parameter is passed, the listener of this callback is unregistered. If this parameter is not passed, all listeners of the **receiveImage** event are unregistered.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';

  // Obtain the sessionId through the collaborative session creation API.
  let sessionId = 100;
  // Unsubscribe from the receiveImage event.
  abilityConnectionManager.off('receiveImage', sessionId);
  ```

## abilityConnectionManager.sendImage

sendImage(sessionId:&nbsp;number,&nbsp;image:&nbsp;image.PixelMap,&nbsp;quality?:&nbsp;number):&nbsp;Promise&lt;void&gt;

After the application is connected and a transmission stream is created, device A or device B can send an image to the peer device. The image is encoded according to the specified compression quality and then sent to the peer device through the transmission stream channel. After the image is sent successfully, the peer device can receive it through the registered callback. This API uses a Promise to return the result asynchronously. After the service ends, destroy the transmission stream in a timely manner; otherwise, system power consumption will increase. Typical use cases include sending video frames in cross-device video calls, sending screenshots during remote collaboration, and cross-device image sharing, where image data needs to be sent to the peer device.

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**System API**: This is a system API.

**Parameters**

| Name      | Type                                     | Mandatory  | Description   |
| --------- | --------------------------------------- | ---- | ----- |
| sessionId | number | Yes    | ID of the collaborative session, which is obtained after a collaborative session is created. |
| image | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | Yes   | Image information.|
| quality | number | No    | Image compression quality, ranging from 0 to 100, with a default value of 30. |

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**Example**

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
    // Open the image picker for the user to select an image.
    photoPicker.select(photoSelectOptions).then((photoSelectResult) => {
      if (!photoSelectResult) {
        hilog.error(0x0000, 'testTag', 'photoSelectResult = null');
        return;
      }

      // Open the image file in read-only mode.
      let file = fileIo.openSync(photoSelectResult.photoUris[0], fileIo.OpenMode.READ_ONLY);
      hilog.info(0x0000, 'testTag', 'file.fd:' + file.fd);

      // In this example, sessionId is a simulated value. In practice, obtain it after creating a collaborative session through APIs such as abilityConnectionManager.connectAbility.
      let sessionId = 100;
      // Create an image source object based on the file descriptor.
      let imageSourceApi: image.ImageSource = image.createImageSource(file.fd);
      if (imageSourceApi) {
        // Convert the image source into a pixel map object.
        imageSourceApi.createPixelMap().then((pixelMap) => {
          // Send the image to the peer device.
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

After the application connection is established, device A or device B can create a transmission stream to send images and video streams. This API uses a promise to return the result asynchronously. 

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**System API**: This is a system API.

**Parameters**

| Name      | Type                                     | Mandatory  | Description   |
| --------- | --------------------------------------- | ---- | ----- |
| sessionId | number | Yes | ID of the collaborative session, which is obtained after a collaborative session is created. |
| param | [StreamParam](#streamparam) | Yes   | Transport stream configuration.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;number&gt; | Promise used to return the transmission stream ID. This ID is required by the APIs for subsequent operations on the transmission stream, such as setSurfaceId, getSurfaceId, startStream, stopStream, and destroyStream. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Management Error Codes](./errorcode-device-manager.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 32300001      | Only one stream can be created for the current session.|
| 32300003      | Bitrate not supported.|
| 32300004      | Color space not supported.|

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  hilog.info(0x0000, 'testTag', 'startStream');
  let sessionId = 100;
  // Create a transmission stream, configure the name as 'receive', and set the role to SOURCE (sending stream).
  abilityConnectionManager.createStream(sessionId, {name: 'receive', role: 0}).then(async (streamId) => {
    // Configure the Surface parameters.
    let surfaceParam: abilityConnectionManager.SurfaceParam = {
      width: 640,
      height: 480,
      format: 1
    }
    // Obtain the unique identifier of the Surface.
    let surfaceId = abilityConnectionManager.getSurfaceId(streamId, surfaceParam);
    hilog.info(0x0000, 'testTag', 'surfaceId is ' + surfaceId);
    // Store the Surface ID in the global state management for use by subsequent UI components.
    AppStorage.setOrCreate<string>('surfaceId', surfaceId);
    // Start the transmission stream.
    abilityConnectionManager.startStream(streamId);
  })
  ```

## abilityConnectionManager.setSurfaceId

setSurfaceId(streamId:&nbsp;number,&nbsp;surfaceId:&nbsp;string,&nbsp;param:&nbsp;SurfaceParam):&nbsp;void

Sets the binding relationship between a transmission stream and a surface. The surface is used to carry the display or capture of audio and video data. After binding, the audio and video data of the transmission stream is directly rendered to the surface or captured from the surface.

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**System API**: This is a system API.

**Parameters**

| Name      | Type                                     | Mandatory  | Description   |
| --------- | --------------------------------------- | ---- | ----- |
| streamId | number | Yes    | ID of the transmission stream, which is obtained after the stream is created by calling createStream. |
| surfaceId | string | Yes    | Unique identifier of the surface, which is obtained by calling getSurfaceId. |
| param | [SurfaceParam](#surfaceparam) | Yes    | Configuration parameters of the surface, including the encoding width, height, and pixel format. After configuration, the surface encodes and renders video frames based on the specified parameters. The binding must be completed before the stream starts. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**Example**

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
    // Set the binding relationship between the transmission stream and the Surface.
    abilityConnectionManager.setSurfaceId(streamId, surfaceId, surfaceParam);
  })
  ```

## abilityConnectionManager.getSurfaceId

getSurfaceId(streamId:&nbsp;number,&nbsp;param:&nbsp;SurfaceParam):&nbsp;string

Obtains the unique identifier of the Surface bound to the specified transmission stream. The surface ID can be used to associate the surface with a component to display audio and video data.

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**System API**: This is a system API.

**Parameters**

| Name      | Type                                     | Mandatory  | Description   |
| --------- | --------------------------------------- | ---- | ----- |
| streamId | number | Yes | ID of the transmission stream, which is obtained after the stream is created by calling createStream. |
| param | [SurfaceParam](#surfaceparam) | Yes | Configuration parameters of the Surface. The surface must be bound before the stream is started. |

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| string | Unique identifier of the surface, which can be used for subsequent operations such as **setSurfaceId**. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**Example**

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

Updates the configuration information of the surface bound to the transmission stream so that the new configuration parameters take effect.

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**System API**: This is a system API.

**Parameters**

| Name      | Type                                     | Mandatory  | Description   |
| --------- | --------------------------------------- | ---- | ----- |
| streamId | number | Yes | ID of the transmission stream, which is obtained after the stream is created by calling createStream. |
| param | [SurfaceParam](#surfaceparam) | Yes   | Surface configuration.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**Example**

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
    // Update the configuration parameters of the Surface.
    abilityConnectionManager.updateSurfaceParam(streamId, surfaceParam);
  })
  ```

## abilityConnectionManager.destroyStream

destroyStream(streamId:&nbsp;number):&nbsp;void

After services such as sending images and video streams are complete, the application that created the transmission stream should destroy the transmission stream in a timely manner. Otherwise, system power consumption increases. This API must be used together with **createStream()**. After the service is complete, this API must be called to destroy the transmission stream and release resources.

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**System API**: This is a system API.

**Parameters**

| Name      | Type                                     | Mandatory  | Description   |
| --------- | --------------------------------------- | ---- | ----- |
| streamId | number | Yes | ID of the transmission stream, which is obtained after the stream is created by calling createStream. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  let streamId = 100;
  hilog.info(0x0000, 'testTag', 'destroyStream called');
  abilityConnectionManager.destroyStream(streamId);
  ```

## abilityConnectionManager.startStream

startStream(streamId:&nbsp;number):&nbsp;void

Starts a specified transmission stream so that it begins to send or receive video data. Before starting, ensure that the transmission stream has been bound to a Surface; otherwise, it cannot be started properly. This API must be used in pair with **stopStream()**. After use, call **stopStream()** to stop the transmission stream, and finally call **destroyStream()** to destroy the transmission stream and release resources.

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**System API**: This is a system API.

**Parameters**

| Name      | Type                                     | Mandatory  | Description   |
| --------- | --------------------------------------- | ---- | ----- |
| streamId | number | Yes    | ID of the transmission stream, which is obtained after the stream is created by calling createStream. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Management Error Codes](./errorcode-device-manager.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 32300002      | The stream at the receive end is not started. |

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  let streamId = 100;
  hilog.info(0x0000, 'testTag', 'startStream called');
  abilityConnectionManager.startStream(streamId);
  ```

## abilityConnectionManager.stopStream

stopStream(streamId:&nbsp;number):&nbsp;void

Stops a specified transmission stream so that it stops sending or receiving video data. This API must be used in pair with **startStream()**. When data transmission is no longer needed, call this API to stop the transmission stream, and finally call **destroyStream()** to destroy the transmission stream and release resources. Typical use cases include pausing a video call, turning off the camera, and switching between the front and rear cameras, where video transmission needs to be temporarily stopped.

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**System API**: This is a system API.

**Parameters**

| Name      | Type                                     | Mandatory  | Description   |
| --------- | --------------------------------------- | ---- | ----- |
| streamId | number | Yes | ID of the transmission stream, which is obtained after the stream is created by calling createStream. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202      | Not system App.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  let streamId = 100;
  hilog.info(0x0000, 'testTag', 'stopStream called');
  abilityConnectionManager.stopStream(streamId);
  ```

## StreamParam

Defines the parameters for stream transmission configuration. This method can be used to configure the transmission mode and parameters of a transmission stream. The role parameter distinguishes a sending stream (**SOURCE**) from a receiving stream (**SINK**). A sending stream requires parameters such as bitrate and **colorSpaceConversionTarget**.

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**System API**: This is a system API.

| Name      | Type   | Read-Only| Optional| Description         |
| -------- | ------ | ---- | ---- | ----------- |
| name  | string   | No   | No|   Stream name. It must be the same on the TX end and RX end.|
| role  | [StreamRole](#streamrole)     | No    | No   |   Stream transmission mode (receive stream or send stream). The bitrate parameter takes effect only when role is **SOURCE**. |
| bitrate  | number   | No    | Yes   |   Video bitrate, in bps. It takes effect only on the sending end. The default value is 80000. |
| colorSpaceConversionTarget  | [colorSpaceManager.ColorSpace](../apis-arkgraphics2d/js-apis-colorSpaceManager.md#colorspace)     | No    | Yes   |  Target color space for conversion. After this parameter is set, the color space of the video stream is converted to the target color space to adapt to the color display requirements of different devices. If this parameter is not passed, no color space conversion is performed. |

## SurfaceParam

Defines the surface configuration.

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**System API**: This is a system API.

| Name      | Type  | Read-Only| Optional| Description     |
| -------- | ------ | ---- | ---- | ------- |
| width | number | No   | No  | Encoding width. Set this parameter prior to stream transmission. Once stream transmission starts, the setting cannot be updated until the stream transmission ends. If you need to update the setting, stop stream transmission first.|
| height | number | No    | No  | Encoding height. It must be set before the stream starts, and cannot be updated after the stream starts until it stops. To update it, stop the stream and reconfigure it. |
| format | [VideoPixelFormat](#videopixelformat) | No   | Yes  | Video pixel format (valid only at the TX end).|
| rotation | number | No    | Yes   | Rotation angle of the video (value range: {0, 90, 180, 270}, default value: 0). 0 means no rotation, 90 means rotating 90 degrees clockwise (suitable for portrait videos), 180 means rotating 180 degrees, and 270 means rotating 90 degrees counterclockwise. If not passed, the default value 0 is used. |
| flip | [FlipOptions](#flipoptions) | No    | Yes   | Whether the video is flipped. HORIZONTAL means horizontal flip (suitable for mirroring scenarios), and VERTICAL means vertical flip. If not passed, no flip is performed. |

## FlipOptions

Enumerates video flip options.

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**System API**: This is a system API.

| Name|  Value| Description|
|-------|-------|-------|
| HORIZONTAL | 0 | Horizontal flip.|
| VERTICAL | 1 | Vertical flip.|

## StreamRole

Enumerates stream transmission modes.

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**System API**: This is a system API.

| Name|  Value| Description|
|-------|-------|-------|
| SOURCE  | 0 | TX stream.|
| SINK  | 1 | RX stream.|

## VideoPixelFormat

Enumerates video pixel formats.

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**System API**: This is a system API.

| Name|  Value| Description|
|-------|-------|-------|
| UNKNOWN   | -1 | Unknown pixel format.|
| NV12  | 0 | NV12, YUV420 semi-planar format.|
| NV21  | 1 | NV21, YUV420 semi-planar format.|

## ConnectOptions

Defines the connection options for the application.

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name         | Type   | Read-Only  | Optional  | Description         |
| ----------- | ------- | ---- | ---- | ----------- |
| needSendStream    | boolean  | No    | Yes    | Whether to send a stream. The value **true** means that a stream needs to be sent (selected when the local end needs to send a video stream to the peer end), and **false** means that no stream needs to be sent (selected when the local end only receives and does not send). The default value is **false**.    |
| needReceiveStream    | boolean  | No    | Yes    | Whether to receive a stream. The value **true** means that a stream needs to be received (selected when the local end needs to receive a video stream from the peer end), and **false** means that no stream needs to be received (selected when the local end only sends and does not receive). The default value is **false**.     |

## EventCallbackInfo

Defines the event callback information.

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name      | Type   | Read-Only | Optional | Description         |
| -------- | ------ | ---- | ---- | ----------- |
| image  | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | No   | Yes   |   Image received. If this parameter is not passed, no image is received or the image information is unavailable. |

## StartOptionParams

Enumerates application start options.

**Device behavior differences:** When this API is called on wearable that does not support distributed services or on a device managed by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name|  Value| Description|
|-------|-------|-------|
| START_IN_BACKGROUND | 1 |When the peer application is started, the UI is not displayed and only the app process is started.|
