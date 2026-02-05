# 分布式相机开发指南
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedHardware-->
<!--Owner: @hobbycao-->
<!--Designer: @saga_2025-->
<!--Tester: @wei-guoqing1-->
<!--Adviser: @w_Machine_cc-->

## 简介

  OpenHarmony分布式相机通过打破硬件边界，实现了跨设备的摄像头能力协同。当搭载OpenHarmony系统的设备A与设备B完成组网后，设备A的应用可实时调用设备B的摄像头资源，获取对方影像（预览流/拍照流/录像流），且支持分辨率调节、参数同步等深度控制。这一功能在以下场景中具有突破性应用价值，例如：
  - 多视角协同创作
  - 远程专家协作
  - 沉浸式安防系统
  - 分布式影音交互


### 基本概念

  在进行分布式相机开发前，建议开发者查看下列章节，了解相关功能操作：
  - [跨设备连接UIAbility开发指南](abilityconnectmanager-guidelines.md)
  - [相机管理](../media/camera/camera-device-management.md)
  - [申请相机开发的权限](../media/camera/camera-preparation.md)
  - [会话管理](../media/camera/camera-session-management.md)
  - [拍照](../media/camera/camera-shooting.md)
  - [录像](../media/camera/camera-recording.md)


## 环境准备

### 环境要求

  设备A和设备B之间需要组网成功，并通过分布式硬件管理框架上线设备。


### 搭建环境

  1. 安装[DevEco Studio](https://developer.huawei.com/consumer/cn/download/deveco-studio)，要求版本在5.0及以上。
  2. 将public-SDK更新到API 16或以上<!--Del-->，更新SDK的具体操作可参见[更新指南](../tools/openharmony_sdk_upgrade_assistant.md)<!--DelEnd-->。
  3. 用USB线缆将两台调测设备（设备A和设备B）连接到PC。
  4. 打开设备A和设备B的Wifi并连接到同一个接入点上，互相识别，连接并组网。连接组网的具体操作可参见[开发步骤](abilityconnectmanager-guidelines.md#开发步骤)。


### 检验环境是否搭建成功

  PC上执行shell命令：

  ```shell
  hdc shell
  hidumper -s 4700 -a "buscenter -l remote_device_info"
  ```

  组网成功时可显示组网设备数量的信息，如“remote device num = 1”。


## 开发指导

  通过OpenHarmony操作系统，将用户拥有的多个设备相机资源作为一个硬件池，为用户提供跨端使用相机的能力。

### 开发流程

  分布式相机流程图建议如下：

  ![Camera Distributed processing](figures/camera-distributed-process.png)
 

### 开发步骤

**导入相机和多媒体等模块文件**

```ts
import { camera } from '@kit.CameraKit';
import { media } from '@kit.MediaKit';
```

**赋予应用访问权限**

  应用需申请权限，包括但不限于下列权限类型：
  - 图片和视频  ohos.permission.MEDIA_LOCATION
  - 文件读  ohos.permission.READ_MEDIA
  - 文件写  ohos.permission.WRITE_MEDIA
  - 相机  ohos.permission.CAMERA
  - 多设备协同  ohos.permission.DISTRIBUTED_DATASYNC

  例如在UIAbility申请相关的访问权限，通过调用requestPermissionsFromUser()方法添加对应的权限类型。
  <!-- @[request_permissions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/hapAppDcameraSample/entry/src/main/ets/entryability/EntryAbility.ts) -->

``` TypeScript
export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info('Sample_VideoRecorder', 'Ability onCreate,requestPermissionsFromUser');
    let permissionNames: Array<Permissions> = ['ohos.permission.MEDIA_LOCATION', 'ohos.permission.READ_MEDIA',
      'ohos.permission.WRITE_MEDIA', 'ohos.permission.CAMERA', 'ohos.permission.MICROPHONE', 'ohos.permission.DISTRIBUTED_DATASYNC'];
    abilityAccessCtrl.createAtManager().requestPermissionsFromUser(this.context, permissionNames).then((data)=> {
      console.info('testTag', data);
    })
      .catch((err : BusinessError) => {
        console.error('testTag', err.message);
      });
  }
// ···
}
```



**启动分布式相机预览流及拍照流**

**1. 获取远端设备相机信息**

  应用组网成功后，需获取远端设备信息，通过getCameraManager()方法获取相机管理器实例，getSupportedCameras()方法获取支持指定的相机设备对象。

  <!-- @[init_camera](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/hapAppDcameraSample/entry/src/main/ets/recorder/VideoRecorder.ets) -->

``` TypeScript
  async initCamera(): Promise<void> {
    Logger.info(TAG, 'initCamera called');
    if (this.cameraManager) {
      return;
    }
    this.cameraManager = camera.getCameraManager(globalThis.abilityContext);
    this.cameras = this.cameraManager.getSupportedCameras();
    if (this.cameras) {
      this.cameraIndex =
        this.cameras.findIndex(cam => cam.connectionType === camera.ConnectionType.CAMERA_CONNECTION_REMOTE);
      if (this.cameraIndex !== -1) {
        this.cameraOutputCapability = this.cameraManager.getSupportedOutputCapability(this.cameras[this.cameraIndex],
          camera.SceneMode.NORMAL_PHOTO);
      }
    }
  }
```


**2. 创建CameraInput实例**

  获取相机管理器实例和支持指定的相机设备对象后，通过createCameraInput()方法创建CameraInput实例。

  <!-- @[camera_input](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/hapAppDcameraSample/entry/src/main/ets/recorder/VideoRecorder.ets) -->

``` TypeScript
  async createCameraInput(): Promise<void> {
    if (!this.cameras || this.cameraIndex === -1 || !this.cameraManager) {
      Logger.error(TAG, 'createCameraInput failed: prerequisites not met.');
      return;
    }
    const came = this.cameras[this.cameraIndex];
    this.cameraInput = this.cameraManager.createCameraInput(came);

    if (!this.cameraInput) {
      Logger.error(TAG, 'createCameraInput failed: cameraManager.createCameraInput returned undefined.');
      return;
    }
    try {
      await this.cameraInput.open();
      Logger.info(TAG, 'CameraInput opened successfully.');
    } catch (error) {
      const err = error as BusinessError;
      Logger.error(TAG, `cameraInput.open() failed with code: ${err.code}, message: ${err.message}`);
    }
  }
```


**3. 获取预览输出对象**

  通过createPreviewOutput()方法创建预览输出对象。

  <!-- @[create_preview](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/hapAppDcameraSample/entry/src/main/ets/recorder/VideoRecorder.ets) -->

``` TypeScript
  async createPreviewOutput(): Promise<void> {
    // Use optional chaining for a clean prerequisite check
    if (this.cameraOutputCapability?.previewProfiles && this.cameraManager && this.surfaceId) {
      // Select the first available preview profile
      const previewProfile = this.cameraOutputCapability.previewProfiles[0];

      this.previewOutput = this.cameraManager.createPreviewOutput(previewProfile, this.surfaceId);

      // Add a clear check to validate the result of the API call
      if (!this.previewOutput) {
        Logger.error(TAG, 'createPreviewOutput failed: cameraManager.createPreviewOutput returned undefined.');
      } else {
        Logger.info(TAG, 'PreviewOutput created successfully.');
      }
    } else {
      Logger.error(TAG, 'createPreviewOutput failed: prerequisites not met (capability, manager, or surfaceId missing).');
    }
  }
```



**4. 获取拍照输出对象**

  通过createPhotoOutput()方法创建拍照输出对象，通过createImageReceiver()方法创建ImageReceiver实例。

  <!-- @[create_photo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/hapAppDcameraSample/entry/src/main/ets/recorder/VideoRecorder.ets) -->

``` TypeScript
  async createPhotoOutput() {
    if (!this.cameraManager || this.photoReceiver) {
      return;
    }

    const photoProfile: camera.Profile = {
      format: camera.CameraFormat.CAMERA_FORMAT_JPEG,
      size: { 'width': 1280, 'height': 720 }
    };

    try {
      this.photoReceiver = image.createImageReceiver(photoProfile.size, image.ImageFormat.JPEG, 8);
      this.photoReceiver.on('imageArrival', () => {
        (async () => {
          if (!this.photoReceiver) {
            Logger.error(TAG, 'photoReceiver is undefined in imageArrival callback.');
            return;
          }
          let receivedImage: image.Image | undefined = undefined;
          try {
            receivedImage = await this.photoReceiver.readNextImage();
            const component = await receivedImage.getComponent(image.ComponentType.JPEG);
            await this.getImageFileFd();
            await fileIo.write(this.mFileAssetId, component.byteBuffer);
            Logger.info(TAG, 'Photo saved successfully!');
          } catch (e) {
            Logger.error(TAG, `Error processing image: ${JSON.stringify(e)}`);
          } finally {
            if (receivedImage) {
              await receivedImage.release();
            }
            await this.closeFd();
          }
        })();
      });

      const surfaceId = await this.photoReceiver.getReceivingSurfaceId();
      this.photoOutput = this.cameraManager.createPhotoOutput(photoProfile);
    } catch (error) {
      Logger.error(TAG, `createPhotoOutput failed: ${JSON.stringify(error)}`);
    }
  }
  private mSaveCameraAsset: SaveCameraAsset = new SaveCameraAsset(TAG);

  async getImageFileFd(): Promise<void> {
    this.mFileAssetId = await this.mSaveCameraAsset.createImageFd();
  }

  async closeFd(): Promise<void> {
    if (this.mSaveCameraAsset) {
      await this.mSaveCameraAsset.closeImageFile();
    }
    this.mFileAssetId = undefined;
  }
```


**5. 创建CaptureSession实例**

通过createCaptureSession()方法创建CaptureSession实例。调用beginConfig()方法开始配置会话，使用addInput()和addOutput()方法将CameraInput()和CameraOutput()加入到会话，最后调用commitConfig()方法提交配置信息，通过Promise获取结果。

  <!-- @[create_session](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/hapAppDcameraSample/entry/src/main/ets/recorder/VideoRecorder.ets) -->

``` TypeScript
  async createSession(): Promise<void> {
    Logger.info(TAG, 'createSession called');
    if (!this.cameraManager) {
      Logger.error(TAG, 'createSession failed: cameraManager is not initialized.');
      return;
    }
    this.cameraSession = this.cameraManager.createSession(camera.SceneMode.NORMAL_PHOTO);
    if (!this.cameraSession) {
      Logger.error(TAG, 'createSession failed: cameraManager.createSession returned undefined.');
      return;
    }

    try {
      Logger.info(TAG, 'cameraSession beginConfig');
      this.cameraSession.beginConfig();

      if (this.cameraInput) {
        Logger.info(TAG, 'cameraSession addInput: cameraInput');
        this.cameraSession.addInput(this.cameraInput);
      }
      if (this.previewOutput) {
        Logger.info(TAG, 'cameraSession addOutput: previewOutput');
        this.cameraSession.addOutput(this.previewOutput);
      }
      if (this.photoOutput) {
        Logger.info(TAG, 'cameraSession addOutput: photoOutput');
        this.cameraSession.addOutput(this.photoOutput);
      }

      Logger.info(TAG, 'cameraSession commitConfig');
      await this.cameraSession.commitConfig();
      Logger.info(TAG, 'cameraSession commitConfig successfully.');

    } catch (error) {
      const err = error as BusinessError;
      Logger.error(TAG, `cameraSession configuration failed with code: ${err.code}, message: ${err.message}`);
      this.failureCallback(err);
    }
  }
```


**6. 开启会话工作**

  通过CaptureSession实例上的start()方法开始会话工作，通过Promise获取结果。

  <!-- @[start_session](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/hapAppDcameraSample/entry/src/main/ets/recorder/VideoRecorder.ets) -->

``` TypeScript
  async startSession(): Promise<void> {
    Logger.info(TAG, 'startSession called');
    if (!this.cameraSession) {
      Logger.error(TAG, 'startSession failed: captureSession does not exist!');
      return;
    }

    try {
      await this.cameraSession.start();
      Logger.info(TAG, 'cameraSession started successfully.');
    } catch (error) {
      const err = error as BusinessError;
      Logger.error(TAG, `Failed to start session! Code: ${err.code}, Msg: ${err.message}`);
    }
  }
```


**释放分布式相机资源**

  业务协同完毕后需及时结束协同状态，释放分布式相机资源。

  <!-- @[release_camera](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/hapAppDcameraSample/entry/src/main/ets/recorder/VideoRecorder.ets) -->

``` TypeScript
  async releaseCamera(): Promise<void> {
    Logger.info(TAG, '--- STARTING CAMERA RELEASE SEQUENCE ---');

    try {
      // Step 1: Stop and release the session
      if (this.cameraSession) {
        Logger.info(TAG, 'Stopping capture session...');
        await this.cameraSession.stop();
        Logger.info(TAG, 'Releasing capture session...');
        await this.cameraSession.release();
        this.cameraSession = undefined;
      }

      // Step 2: Release the preview output
      if (this.previewOutput) {
        Logger.info(TAG, 'Releasing preview output...');
        await this.previewOutput.release();
        this.previewOutput = undefined;
      }

      // Step 3: Release the photo output and receiver
      if (this.photoOutput) {
        Logger.info(TAG, 'Releasing photo output...');
        await this.photoOutput.release();
        this.photoOutput = undefined;
      }
      if (this.photoReceiver) {
        Logger.info(TAG, 'Releasing photo receiver...');
        await this.photoReceiver.release();
        this.photoReceiver = undefined;
      }

      // Step 4: Close the camera input
      if (this.cameraInput) {
        Logger.info(TAG, 'Closing camera input...');
        await this.cameraInput.close();
        this.cameraInput = undefined;
      }

      Logger.info(TAG, 'All camera resources released.');

    } catch (error) {
      const err = error as BusinessError;
      Logger.error(TAG, `Error during camera release! Code: ${err.code}, Msg: ${err.message}`);
    } finally {
      // Ensure core objects are cleared even if an error occurs
      this.cameraManager = undefined;
      this.cameras = undefined;
      Logger.info(TAG, '--- CAMERA RELEASE SEQUENCE ENDED ---');
    }
  }
```


### 调测验证

  应用侧开发完成后，可在设备A和设备B上安装应用，测试步骤如下：

  1. 设备A拉起设备B上的分布式摄像头并发起预览，设备A能接收到预览流。
  2. 设备A拉起设备B上的分布式摄像头并拍照，设备A能接收到照片。

## 常见问题


### 设备A应用无法拉起设备B摄像头

**可能原因**

  设备间没有相互组网或者组网后中断了连接。

**解决措施**

  设备A和设备B开启USB调试功能，用USB线连接设备和PC。执行shell命令：
   
  ```shell
  hdc shell
  hidumper -s 4700 -a "buscenter -l remote_device_info"
  ```
  回显信息为 “remote device num = 0” 即为组网失败，请禁用再启用Wifi重新接入到同一个接入点上。组网成功后重新执行命令会显示正确组网设备数量的信息，如“remote device num = 1”。