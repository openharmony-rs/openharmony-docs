# 分段式拍照(ArkTS)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

分段式拍照是相机的重要功能之一，即应用下发拍照任务后，系统将分多阶段上报不同质量的图片。

- 在第一阶段，系统快速上报轻量处理的图片，轻量处理的图片比全质量图低，出图速度快。应用通过回调会收到一个[PhotoAsset](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAsset.md)对象，通过该对象可调用媒体库接口，读取图片或落盘图片。
- 在第二阶段，相机框架会根据应用的请求图片诉求或在相机进入后台时，进行图像增强处理得到全质量图，并将处理好的图片传回给媒体库，替换轻量处理的图片。

通过分段式拍照，优化了系统的拍照响应时延，从而提升用户体验。

应用开发分段式拍照主要分为以下步骤：

- 通过PhotoOutput，监听photoAssetAvailable回调，获取[photoAccessHelper](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper.md)的PhotoAsset对象。
- 通过PhotoAsset对象，调用媒体库相关接口，读取或落盘图片。

> **说明：**
> 
> - 分段式拍照能力由**设备**和**模式**决定，不同的设备支持的模式各异，对应分段式能力也有所差异，因此应用在切换设备或模式后分段式能力可能会发生变化。
> - 应用无需主动使能分段式拍照能力，相机框架会在配流期间判断设备和模式是否支持分段式，如果支持会使能该功能。

## 开发步骤

详细的API说明请参考[@ohos.multimedia.camera (相机管理)](../../reference/apis-camera-kit/arkts-apis-camera.md)。

1. 导入依赖，需要导入相机框架、媒体库、图片相关领域依赖。

   ```ts
   import { camera } from '@kit.CameraKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { photoAccessHelper } from '@kit.MediaLibraryKit';
   ```

2. 确定拍照输出流。

   通过[CameraOutputCapability](../../reference/apis-camera-kit/arkts-apis-camera-i.md#cameraoutputcapability)中的photoProfiles属性，可获取当前设备支持的拍照输出流，通过[createPhotoOutput](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#createphotooutput11)方法创建拍照输出流。

   ```ts
   function getPhotoOutput(cameraManager: camera.CameraManager, 
     cameraOutputCapability: camera.CameraOutputCapability): camera.PhotoOutput | undefined {
     let photoProfilesArray: Array<camera.Profile> = cameraOutputCapability.photoProfiles;
     if (photoProfilesArray===null || photoProfilesArray===undefined) {
       console.error("createOutput photoProfilesArray is null!");
       return undefined;
     }
     let photoOutput: camera.PhotoOutput | undefined = undefined;
     try {
      if (photoProfilesArray.length > 0) {
          photoOutput = cameraManager.createPhotoOutput(photoProfilesArray[0]);
      } else {
          console.error("the length of photoProfilesArray<=0!");
          return undefined;
      }
     } catch (error) {
       let err = error as BusinessError;
       console.error(`Failed to createPhotoOutput. error: ${err}`);
     }
     return photoOutput;
   }
   ```

3. 设置拍照photoAssetAvailable的回调。

   > **注意：**
   >
   > 如果已经注册了photoAssetAvailable回调，并且在Session开始之后又注册了photoAvailable回调，photoAssetAvailable和photoAvailable同时注册，会导致流被重启，仅photoAssetAvailable生效。
   >
   > 不建议开发者同时注册[photoAvailable](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#onphotoavailable11)和[photoAssetAvailable](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#onphotoassetavailable12)。

   ```ts
   function getPhotoAccessHelper(context: Context): photoAccessHelper.PhotoAccessHelper {
     let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
     return phAccessHelper;
   }

   function onPhotoOutputPhotoAssetAvailable(photoOutput: camera.PhotoOutput, context: Context): void {
     photoOutput.on('photoAssetAvailable', (err: BusinessError, photoAsset: photoAccessHelper.PhotoAsset) => {
       if (err) {
         console.error(`photoAssetAvailable error: ${err}.`);
         return;
       }
       console.info('photoOutPutCallBack photoAssetAvailable');
       // 开发者可通过photoAsset调用媒体库相关接口，自定义处理图片。
       // 处理方式一：调用媒体库落盘接口保存一阶段图，二阶段图就绪后媒体库会主动帮应用替换落盘图片。
       mediaLibSavePhoto(photoAsset, getPhotoAccessHelper(context));
       // 处理方式二：调用媒体库接口请求图片并注册一阶段图或二阶段图buffer回调，自定义使用。
       mediaLibRequestBuffer(photoAsset, context);
     });
   }

   async function mediaLibSavePhoto(photoAsset: photoAccessHelper.PhotoAsset,
     phAccessHelper: photoAccessHelper.PhotoAccessHelper): Promise<void> {
     try {
       let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(photoAsset);
       assetChangeRequest.saveCameraPhoto();
       await phAccessHelper.applyChanges(assetChangeRequest);
       console.info('apply saveCameraPhoto successfully');
     } catch (err) {
       console.error(`apply saveCameraPhoto failed with error: ${err.code}, ${err.message}`);
     }
   }

   class MediaDataHandler implements photoAccessHelper.MediaAssetDataHandler<ArrayBuffer> {
     onDataPrepared(data: ArrayBuffer) {
       if (data === undefined) {
         console.error('Error occurred when preparing data');
         return;
       }
       // 应用获取到图片buffer后可自定义处理。
       console.info('on image data prepared');
     }
   }

   async function mediaLibRequestBuffer(photoAsset: photoAccessHelper.PhotoAsset, context: Context) {
     let requestOptions: photoAccessHelper.RequestOptions = {
       // 按照业务需求配置回图模式。
       // FAST_MODE：仅接收一阶段低质量图回调。
       // HIGH_QUALITY_MODE：仅接收二阶段全质量图回调。
       // BALANCE_MODE：接收一阶段及二阶段图片回调。
       deliveryMode: photoAccessHelper.DeliveryMode.FAST_MODE,
     }
     const handler = new MediaDataHandler();
     await photoAccessHelper.MediaAssetManager.requestImageData(context, photoAsset, requestOptions, handler);
     console.info('requestImageData successfully');
   }
   ```

   落盘图片参考媒体库接口：[saveCameraPhoto](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md#savecameraphoto12)

   请求图片参考媒体库接口：[requestImageData](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAssetManager.md#requestimagedata11) 和 [onDataPrepared](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAssetDataHandler.md#ondataprepared11)

4. 拍照时的会话配置及触发拍照的方式，与普通拍照相同，请参考[拍照](camera-shooting.md)的步骤4-5。

## 状态监听

在相机应用开发过程中，可以随时监听拍照输出流状态，包括拍照流开始、拍照帧的开始与结束、拍照输出流的错误。

- 通过注册固定的captureStartWithInfo回调函数获取监听拍照开始结果，photoOutput创建成功时即可监听，相机设备已经准备开始这次拍照时触发，该事件返回此次拍照的captureId。

  ```ts
  function onPhotoOutputCaptureStart(photoOutput: camera.PhotoOutput): void {
    photoOutput.on('captureStartWithInfo', (err: BusinessError, captureStartInfo: camera.CaptureStartInfo) => {
      if (err !== undefined && err.code !== 0) {
        return;
      }
      console.info(`photo capture started, captureId : ${captureStartInfo.captureId}`);
    });
  }
  ```

- 通过注册固定的captureEnd回调函数获取监听拍照结束结果，photoOutput创建成功时即可监听，该事件返回结果为拍照完全结束后的相关信息[CaptureEndInfo](../../reference/apis-camera-kit/arkts-apis-camera-i.md#captureendinfo)。

  ```ts
  function onPhotoOutputCaptureEnd(photoOutput: camera.PhotoOutput): void {
    photoOutput.on('captureEnd', (err: BusinessError, captureEndInfo: camera.CaptureEndInfo) => {
      if (err !== undefined && err.code !== 0) {
        return;
      }
      console.info(`photo capture end, captureId : ${captureEndInfo.captureId}`);
      console.info(`frameCount : ${captureEndInfo.frameCount}`);
    });
  }
  ```

- 通过注册固定的captureReady回调函数获取监听可拍下一张结果，photoOutput创建成功时即可监听，当下一张可拍时触发，该事件返回结果为下一张可拍的相关信息。

  ```ts
  function onPhotoOutputCaptureReady(photoOutput: camera.PhotoOutput): void {
    photoOutput.on('captureReady', (err: BusinessError) => {
      if (err !== undefined && err.code !== 0) {
        return;
      }
      console.info(`photo capture ready`);
    });
  }
  ```

- 通过注册固定的error回调函数获取监听拍照输出流的错误结果。callback返回拍照输出接口使用错误时的对应错误码，错误码类型参见[CameraErrorCode](../../reference/apis-camera-kit/arkts-apis-camera-e.md#cameraerrorcode)。

  ```ts
  function onPhotoOutputError(photoOutput: camera.PhotoOutput): void {
    photoOutput.on('error', (error: BusinessError) => {
      console.error(`Photo output error code: ${error.code}`);
    });
  }
  ```

## 分段式拍照实践

在开发相机应用时，需要先[申请相关权限](camera-preparation.md)。

当前示例提供完整的分段式拍照流程介绍，方便开发者了解完整的接口调用顺序。

在参考以下示例前，建议开发者查看[分段式拍照(ArkTS)](camera-deferred-capture.md)的具体章节，了解[设备输入](camera-device-input.md)、[会话管理](camera-session-management.md)、[拍照](camera-shooting.md)等单个流程。

### 开发流程

在获取到相机支持的输出流能力后，开始创建拍照流，开发流程如下。

![deferred-capture-development-process](figures/deferred-capture-development-process.png)

### 完整示例

Context获取方式请参考：[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```ts
import { camera } from '@kit.CameraKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { abilityAccessCtrl, Permissions } from '@kit.AbilityKit';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

let photoSession: camera.PhotoSession | undefined = undefined;
let cameraInput: camera.CameraInput | undefined = undefined;
let previewOutput: camera.PreviewOutput | undefined = undefined;
let photoOutput: camera.PhotoOutput | undefined = undefined;

function getPhotoAccessHelper(context: Context): photoAccessHelper.PhotoAccessHelper {
  let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
  return phAccessHelper;
}
   
class MediaDataHandler implements photoAccessHelper.MediaAssetDataHandler<ArrayBuffer> {
  onDataPrepared(data: ArrayBuffer) {
    if (data === undefined) {
      console.error('Error occurred when preparing data');
      return;
    }
    console.info('on image data prepared');
    // 请在获取到拍照buffer后，再释放session，提前释放session，会导致无法正常出图。
    releaseCamSession();
  }
}

async function mediaLibRequestBuffer(photoAsset: photoAccessHelper.PhotoAsset, context: Context) {
  let requestOptions: photoAccessHelper.RequestOptions = {
    deliveryMode: photoAccessHelper.DeliveryMode.FAST_MODE,
  }
  const handler = new MediaDataHandler();
  await photoAccessHelper.MediaAssetManager.requestImageData(context, photoAsset, requestOptions, handler);
  console.info('requestImageData successfully');
}

async function mediaLibSavePhoto(photoAsset: photoAccessHelper.PhotoAsset,
  phAccessHelper: photoAccessHelper.PhotoAccessHelper): Promise<void> {
  try {
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest =
      new photoAccessHelper.MediaAssetChangeRequest(photoAsset);
    assetChangeRequest.saveCameraPhoto();
    await phAccessHelper.applyChanges(assetChangeRequest);
    console.info('apply saveCameraPhoto successfully');
  } catch (err) {
    console.error(`apply saveCameraPhoto failed with error: ${err.code}, ${err.message}`);
  }
}

function setPhotoOutputCb(photoOutput: camera.PhotoOutput, context: Context): void {
  // 监听回调之后，调用photoOutput的capture方法，低质量图上报后触发回调。
  photoOutput.on('photoAssetAvailable', async (err: BusinessError, photoAsset: photoAccessHelper.PhotoAsset): Promise<void> => {
    console.info('getPhotoAsset start');
    console.error(`err: ${err}`);
    if ((err !== undefined && err.code !== 0) || photoAsset === undefined) {
      console.error('getPhotoAsset failed');
      return;
    }
    // 调用媒体库落盘接口保存一阶段低质量图，二阶段真图就绪后媒体库会主动帮应用替换落盘图片。
    await mediaLibSavePhoto(photoAsset, getPhotoAccessHelper(context));
    // 调用媒体库接口注册低质量图或高质量图buffer回调，自定义处理。
    // mediaLibRequestBuffer(photoAsset, context);
  });
}


async function deferredCaptureCase(context: Context, surfaceId: string): Promise<void> {
  // 创建CameraManager对象。
  let cameraManager: camera.CameraManager = camera.getCameraManager(context);
  if (!cameraManager) {
    console.error('camera.getCameraManager error');
    return;
  }
  // 监听相机状态变化。
  cameraManager.on('cameraStatus', (err: BusinessError, cameraStatusInfo: camera.CameraStatusInfo) => {
    if (err !== undefined && err.code !== 0) {
      console.error('cameraStatus with errorCode = ' + err.code);
      return;
    }
    console.info(`camera : ${cameraStatusInfo.camera.cameraId}`);
    console.info(`status: ${cameraStatusInfo.status}`);
  });

  // 获取相机列表。
  let cameraArray: Array<camera.CameraDevice> = cameraManager.getSupportedCameras();
  if (cameraArray.length <= 0) {
    console.error('cameraManager.getSupportedCameras error');
    return;
  }

  for (let index = 0; index < cameraArray.length; index++) {
    console.info('cameraId : ' + cameraArray[index].cameraId); // 获取相机ID。
    console.info('cameraPosition : ' + cameraArray[index].cameraPosition); // 获取相机位置。
    console.info('cameraType : ' + cameraArray[index].cameraType); // 获取相机类型。
    console.info('connectionType : ' + cameraArray[index].connectionType); // 获取相机连接类型。
  }

  // 创建相机输入流。
  try {
    cameraInput = cameraManager.createCameraInput(cameraArray[0]);
  } catch (error) {
    let err = error as BusinessError;
    console.error('Failed to createCameraInput errorCode = ' + err.code);
  }
  if (cameraInput === undefined) {
    return;
  }

  // 监听cameraInput错误信息。
  let cameraDevice: camera.CameraDevice = cameraArray[0];
  cameraInput.on('error', cameraDevice, (error: BusinessError) => {
    console.error(`Camera input error code: ${error.code}`);
  });

  // 打开相机。
  await cameraInput.open();

  // 获取支持的模式类型。
  let sceneModes: Array<camera.SceneMode> = cameraManager.getSupportedSceneModes(cameraArray[0]);
  let isSupportPhotoMode: boolean = sceneModes.indexOf(camera.SceneMode.NORMAL_PHOTO) >= 0;
  if (!isSupportPhotoMode) {
    console.error('photo mode not support');
    return;
  }
  // 获取相机设备支持的输出流能力。
  let cameraOutputCap: camera.CameraOutputCapability =
    cameraManager.getSupportedOutputCapability(cameraArray[0], camera.SceneMode.NORMAL_PHOTO);
  if (!cameraOutputCap) {
    console.error('cameraManager.getSupportedOutputCapability error');
    return;
  }
  console.info('outputCapability: ' + JSON.stringify(cameraOutputCap));

  let previewProfilesArray: Array<camera.Profile> = cameraOutputCap.previewProfiles;
  if (!previewProfilesArray) {
    console.error('createOutput previewProfilesArray == null || undefined');
  }

  let photoProfilesArray: Array<camera.Profile> = cameraOutputCap.photoProfiles;
  if (!photoProfilesArray) {
    console.error('createOutput photoProfilesArray == null || undefined');
  }

  // 创建预览输出流，其中参数surfaceId参考上文XComponent组件，预览流为XComponent组件提供的surface。
  try {
    previewOutput = cameraManager.createPreviewOutput(previewProfilesArray[0], surfaceId);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`Failed to create the PreviewOutput instance. error code: ${err.code}`);
  }
  if (previewOutput === undefined) {
    return;
  }

  // 监听预览输出错误信息。
  previewOutput.on('error', (error: BusinessError) => {
    console.error(`Preview output error code: ${error.code}`);
  });

  // 创建拍照输出流。
  try {
    photoOutput = cameraManager.createPhotoOutput(photoProfilesArray[0]);
  } catch (error) {
    let err = error as BusinessError;
    console.error('Failed to createPhotoOutput errorCode = ' + err.code);
  }
  if (photoOutput === undefined) {
    return;
  }

  // 注册监听photoAssetAvailable回调。
  setPhotoOutputCb(photoOutput, context);

  // 创建会话。
  try {
    photoSession = cameraManager.createSession(camera.SceneMode.NORMAL_PHOTO) as camera.PhotoSession;
  } catch (error) {
    let err = error as BusinessError;
    console.error('Failed to create the session instance. errorCode = ' + err.code);
  }
  if (photoSession === undefined) {
    return;
  }
  // 监听session错误信息。
  photoSession.on('error', (error: BusinessError) => {
    console.error(`Capture session error code: ${error.code}`);
  });

  // 开始配置会话。
  try {
    photoSession.beginConfig();
  } catch (error) {
    let err = error as BusinessError;
    console.error('Failed to beginConfig. errorCode = ' + err.code);
  }

  // 向会话中添加相机输入流。
  try {
    photoSession.addInput(cameraInput);
  } catch (error) {
    let err = error as BusinessError;
    console.error('Failed to addInput. errorCode = ' + err.code);
  }

  // 向会话中添加预览输出流。
  try {
    photoSession.addOutput(previewOutput);
  } catch (error) {
    let err = error as BusinessError;
    console.error('Failed to addOutput(previewOutput). errorCode = ' + err.code);
  }

  // 向会话中添加拍照输出流。
  try {
    photoSession.addOutput(photoOutput);
  } catch (error) {
    let err = error as BusinessError;
    console.error('Failed to addOutput(photoOutput). errorCode = ' + err.code);
  }

  // 提交会话配置。
  await photoSession.commitConfig();

  // 启动会话。
  try {
    await photoSession.start();
  } catch (error) {
    let err = error as BusinessError;
    console.error('Failed to start. errorCode = ', err.code);
  }

  // 判断设备是否支持闪光灯。
  let flashStatus: boolean = false;
  try {
    flashStatus = photoSession.hasFlash();
  } catch (error) {
    let err = error as BusinessError;
    console.error('Failed to hasFlash. errorCode = ' + err.code);
  }
  console.info('Returned with the flash light support status:' + flashStatus);

  if (flashStatus) {
    // 判断是否支持自动闪光灯模式。
    let flashModeStatus: boolean = false;
    try {
      let status: boolean = photoSession.isFlashModeSupported(camera.FlashMode.FLASH_MODE_AUTO);
      flashModeStatus = status;
    } catch (error) {
      let err = error as BusinessError;
      console.error('Failed to check whether the flash mode is supported. errorCode = ' + err.code);
    }
    if (flashModeStatus) {
      // 设置自动闪光灯模式。
      try {
        photoSession.setFlashMode(camera.FlashMode.FLASH_MODE_AUTO);
      } catch (error) {
        let err = error as BusinessError;
        console.error('Failed to set the flash mode. errorCode = ' + err.code);
      }
    }
  }

  // 判断是否支持连续自动变焦模式。
  let focusModeStatus: boolean = false;
  try {
    let status: boolean = photoSession.isFocusModeSupported(camera.FocusMode.FOCUS_MODE_CONTINUOUS_AUTO);
    focusModeStatus = status;
  } catch (error) {
    let err = error as BusinessError;
    console.error('Failed to check whether the focus mode is supported. errorCode = ' + err.code);
  }

  if (focusModeStatus) {
    // 设置连续自动变焦模式。
    try {
      photoSession.setFocusMode(camera.FocusMode.FOCUS_MODE_CONTINUOUS_AUTO);
    } catch (error) {
      let err = error as BusinessError;
      console.error('Failed to set the focus mode. errorCode = ' + err.code);
    }
  }

  // 获取相机支持的可变焦距比范围。
  let zoomRatioRange: Array<number> = [];
  try {
    zoomRatioRange = photoSession.getZoomRatioRange();
  } catch (error) {
    let err = error as BusinessError;
    console.error('Failed to get the zoom ratio range. errorCode = ' + err.code);
  }
  if (zoomRatioRange.length <= 0) {
    return;
  }

  // 设置可变焦距比。
  try {
    photoSession.setZoomRatio(zoomRatioRange[0]);
  } catch (error) {
    let err = error as BusinessError;
    console.error('Failed to set the zoom ratio value. errorCode = ' + err.code);
  }
  let photoCaptureSetting: camera.PhotoCaptureSetting = {
    quality: camera.QualityLevel.QUALITY_LEVEL_HIGH, // 设置图片质量高。
    rotation: camera.ImageRotation.ROTATION_0 // 设置图片旋转角度0。
  }

  // 使用当前拍照设置触发一次拍照。
  photoOutput.capture(photoCaptureSetting, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to capture the photo ${err.message}`);
      return;
    }
    console.info('Callback invoked to indicate the photo capture request success.');
  });
}

async function releaseCamSession() {
  // 停止当前会话。
  try {
    await photoSession?.stop();
  } catch (error) {
    let err = error as BusinessError;
    console.error('Failed to stop, error = ' + err.code);
  }

  // 释放拍照输出流。
  try {
    await photoOutput?.release();
  } catch (error) {
    let err = error as BusinessError;
    console.error('Failed to release photo, error = ' + err.code);
  }

  // 释放预览输出流。
  try {
    await previewOutput?.release();
  } catch (error) {
    let err = error as BusinessError;
    console.error('Failed to release preview, error = ' + err.code);
  }

  // 释放相机输入流。
  try {
    await cameraInput?.close();
  } catch (error) {
    let err = error as BusinessError;
    console.error('Failed to close, error = ' + err.code);
  }

  // 释放会话。
  try {
    await photoSession?.release();
  } catch (error) {
    let err = error as BusinessError;
    console.error('Failed to release session, error = ' + err.code);
  }

  // 会话置空。
  photoSession = undefined;
}

@Entry
@Component
struct Index {
  @State message: string = 'PhotoAssetDemo';
  @State isShow: boolean = false;
  private mXComponentController: XComponentController = new XComponentController();
  private surfaceId = '';
  private uiContext: UIContext = this.getUIContext();
  private context: Context | undefined = this.uiContext.getHostContext();
  private cameraPermission: Permissions = 'ohos.permission.CAMERA'; // 申请权限相关问题可参考本篇开头的申请相关权限文档
  private mXComponentOptions: XComponentOptions = {
    type: XComponentType.SURFACE,
    controller: this.mXComponentController
  }


  async requestPermissionsFn(): Promise<void> {
    let atManager = abilityAccessCtrl.createAtManager();
    if (this.context) {
      let res = await atManager.requestPermissionsFromUser(this.context, [this.cameraPermission]);
      for (let i = 0; i < res.permissions.length; i++) {
        if (this.cameraPermission.toString() === res.permissions[i] && res.authResults[i] === 0) {
          this.isShow = true;
        }
      }
    }
  }

  aboutToAppear(): void {
    this.requestPermissionsFn();
  }

  build() {
    Column() {
      Column() {
        if (this.isShow) {
          XComponent(this.mXComponentOptions)
          .onLoad(async () => {
            console.info('onLoad is called');
            if (this.context) {
              this.surfaceId = this.mXComponentController.getXComponentSurfaceId();
              console.info(`onLoad surfaceId: ${this.surfaceId}`);
              deferredCaptureCase(this.context, this.surfaceId);
            }
          })
          .renderFit(RenderFit.RESIZE_CONTAIN)
        }
      }
      .height('95%')
      .justifyContent(FlexAlign.Center)

      Text(this.message)
        .id('PhotoAssetDemo')
        .fontSize(38)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```