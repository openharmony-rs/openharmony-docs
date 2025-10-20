# Distributed Camera Development
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedHardware-->
<!--Owner: @hobbycao-->
<!--Designer: @saga_2025-->
<!--Tester: @wei-guoqing1-->
<!--Adviser: @w_Machine_cc-->

## Overview

  OpenHarmony distributed camera implements collaboration across devices by breaking hardware boundaries. For example, after devices A and B running OpenHarmony are networked, the application on device A can call the camera resources of device B in real time to obtain images (preview stream, photo stream, or video stream) from device B. In addition, in-depth controls such as resolution adjustment and settings synchronization are supported on device A. Distributed camera achieves the following breakthroughs:
  - Collaborative creation with multiple users
  - Remote collaboration with experts
  - Immersive security system
  - Distributed audio and video interaction


### Basic Concepts

  Before started, you are advised to read the following topics to have a basic understanding of related functions:
  - [UIAbility Connection Development](abilityconnectmanager-guidelines.md)
  - [Camera Device Management (ArkTS)](../media/camera/camera-device-management.md)
  - [Camera Development Preparations](../media/camera/camera-preparation.md)
  - [Camera Session Management (ArkTS)](../media/camera/camera-session-management.md)
  - [Photo Capture (ArkTS)](../media/camera/camera-shooting.md)
  - [Video Recording (ArkTS)](../media/camera/camera-recording.md)


## Preparing the Environment

### Environment Requirements

  Device A and device B are successfully networked and placed online through the distributed hardware management framework.


### Environment Setup

  1. Install [DevEco Studio](https://developer.huawei.com/consumer/en/download/) 5.0 or later.
  2. Update the public SDK to API version 16 or later.
  3. Connect device A and device B to the PC using USB cables.
  4. Connect device A and device B to the same Wi-Fi, identify each other, and start networking. For details, see [UIAbility Connection Development](abilityconnectmanager-guidelines.md#how-to-develop).


### Environment Verification

  Run the following shell command on the PC:

  ```shell
  hdc shell
  hidumper -s 4700 -a "buscenter -l remote_device_info"
  ```

  If the networking is successful, the number of networking devices is displayed, for example, **remote device num = 1**.


## How to Develop

  OpenHarmony pools cameras on multiple devices to provide users with the capability of using cameras across devices.

### Development Process

  The figure below shows the recommended development process.

  ![Camera Distributed processing](figures/camera-distributed-process.png)
 

### Development Procedure

**Importing the Camera and Multimedia Modules**

   ```ts
  import { camera } from '@kit.CameraKit';
  import { media } from '@kit.MediaKit';
   ```

**Granting the Access Permission to the Application**

  The application should apply for required permissions, which include but are not limited to the following:
  - For accessing the location of an image or a video: ohos.permission.MEDIA_LOCATION
  - For reading files: ohos.permission.READ_MEDIA
  - For writing files: ohos.permission.WRITE_MEDIA
  - For using camera: ohos.permission.CAMERA
  - For multi-device collaboration: ohos.permission.DISTRIBUTED_DATASYNC

  For example, you can call **requestPermissionsFromUser()** to request the corresponding permissions for the UIAbility.
  ```ts
  //EntryAbility.ets
  import { hilog } from '@kit.PerformanceAnalysisKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { abilityAccessCtrl, AbilityConstant, ConfigurationConstant, Permissions,
    UIAbility, Want } from '@kit.AbilityKit';

  export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
      console.info('Sample_VideoRecorder', 'Ability onCreate,requestPermissionsFromUser');
      let permissionNames: Array<Permissions> = ['ohos.permission.MEDIA_LOCATION', 'ohos.permission.READ_MEDIA',
        'ohos.permission.WRITE_MEDIA', 'ohos.permission.CAMERA', 'ohos.permission.MICROPHONE', 'ohos.permission.DISTRIBUTED_DATASYNC'];
      abilityAccessCtrl.createAtManager().requestPermissionsFromUser(this.context, permissionNames).then((data)=> {
        console.info("testTag", data);
      })
        .catch((err : BusinessError) => {
          console.error("testTag", err.message);
        });
    }
  }
  ```


**Initiating the Preview Stream and Photo Stream on the Distributed Camera**

**1. Obtain the camera information of a remote device.**

  After the application networking is successful, you can use **getCameraManager()** to obtain the camera manager instance and **getSupportedCameras()** to obtain the supported camera device object.

  ```ts
  private cameras?: Array<camera.CameraDevice>;
  private cameraManager?: camera.CameraManager;
  private cameraOutputCapability?: camera.CameraOutputCapability;
  private cameraIndex: number = 0;
  private curVideoProfiles?: Array<camera.VideoProfile>;

  initCamera(): void {
    console.info('init remote camera called');
    if (this.cameraManager) {
      console.info('cameraManager already exits');
      return;
    }
    console.info('[camera] case to get cameraManager');
    this.cameraManager = camera.getCameraManager(globalThis.abilityContext);
    if (this.cameraManager) {
      console.info('[camera] case getCameraManager success');
    } else {
      console.error('[camera] case getCameraManager failed');
      return;
    }
    this.cameras = this.cameraManager.getSupportedCameras();
    if (this.cameras) {
      console.info('[camera] case getCameras success, size ', this.cameras.length);
      for (let i = 0; i < this.cameras.length; i++) {
        let came: camera.CameraDevice = this.cameras[i];
        console.info('[came] camera json:', JSON.stringify(came));
        if (came.connectionType == camera.ConnectionType.CAMERA_CONNECTION_REMOTE) {
          this.cameraIndex = i;
          this.cameraOutputCapability = this.cameraManager.getSupportedOutputCapability(came);
          this.curVideoProfiles = this.cameraOutputCapability.videoProfiles;
          console.info('init remote camera done'); // The remote camera is successfully initialized.
          break;
        }
      }
    } else {
      console.error('[camera] case getCameras failed');
    }
  }
  ```

**2. Create a CameraInput instance.**

  After obtaining the **CameraManager** instance and the supported camera device object, call **createCameraInput()** to create a **CameraInput** instance.

  ```ts
  // create camera input
  private cameraInput?: camera.CameraInput;

  async createCameraInput(): Promise<void> {
    console.info('createCameraInput called');
    if (this.cameras && this.cameras.length > 0) {
      let came: camera.CameraDevice = this.cameras[this.cameraIndex];
      console.info('[came]createCameraInput camera json:', JSON.stringify(came));
      this.cameraInput = this.cameraManager?.createCameraInput(came);
      if (this.cameraInput) {
        console.info('[camera] case createCameraInput success');
        await this.cameraInput.open().then(() => {
          console.info('[camera] case cameraInput.open() success');
        }).catch((err: Error) => {
          console.error('[camera] cameraInput.open then.error:', JSON.stringify(err));
        });
      } else {
        console.error('[camera] case createCameraInput failed');
        return;
      }
    }
  }
  ```

**3. Obtain the PreviewOutput object.**

  Use **createPreviewOutput()** to create a **PreviewOutput** object.

  ```ts
  private previewOutput?: camera.PreviewOutput;
  private avProfile: media.AVRecorderProfile = {
    fileFormat: media.ContainerFormatType.CFT_MPEG_4,
  }
  private avConfig: media.AVRecorderConfig = {
    videoSourceType: media.VideoSourceType.VIDEO_SOURCE_TYPE_SURFACE_YUV,
    profile: this.avProfile,
    url: 'fd://',
  }
  private previewProfiles?: Array<camera.Profile>;
  private surfaceId?: string;

  // create camera preview
  async createPreviewOutput(): Promise<void> {
    console.info('createPreviewOutput called');
    if (this.cameraOutputCapability && this.cameraManager) {
      this.previewProfiles = this.cameraOutputCapability.previewProfiles;
      console.info('[camera] this.previewProfiles json ', JSON.stringify(this.previewProfiles));
      if (this.previewProfiles[0].format === camera.CameraFormat.CAMERA_FORMAT_YUV_420_SP) {
        console.info('[camera] case format is VIDEO_SOURCE_TYPE_SURFACE_YUV');
        this.avConfig.videoSourceType = media.VideoSourceType.VIDEO_SOURCE_TYPE_SURFACE_YUV;
      } else {
        console.info('[camera] case format is VIDEO_SOURCE_TYPE_SURFACE_ES');
        this.avConfig.videoSourceType = media.VideoSourceType.VIDEO_SOURCE_TYPE_SURFACE_ES;
      }
      this.previewOutput = this.cameraManager.createPreviewOutput(this.previewProfiles[0], this.surfaceId);
      if (!this.previewOutput) {
        console.error('create previewOutput failed!');
      }
      console.info('createPreviewOutput done');
    }
  }
  ```


**4. Obtain the PhotoOutput object.**

  Use **createPhotoOutput()** to create a **PhotoOutput** object and **createImageReceiver()** to create an **ImageReceiver** instance.

  ```ts
  import { fileIo } from '@kit.CoreFileKit'
  import { image } from '@kit.ImageKit';

  export default class SaveCameraAsset {
    private tag: string
    constructor(tag: string) {
      this.tag = tag;
    }
    public async createImageFd() {
      //...
      return 0;
    }
    public async closeVideoFile() {
      //...
    }
  }
  private photoReceiver?: image.ImageReceiver;
  private photoOutput?: camera.PhotoOutput;
  private mSaveCameraAsset: SaveCameraAsset = new SaveCameraAsset('Sample_VideoRecorder');
  private mFileAssetId?: number;
  private fdPath?: string

  async getImageFileFd(): Promise<void> {
    console.info('getImageFileFd called');
    this.mFileAssetId = await this.mSaveCameraAsset.createImageFd();
    this.fdPath = 'fd://' + this.mFileAssetId.toString();
    this.avConfig.url = this.fdPath;
    console.info('ImageFileFd is: ' + this.fdPath);
    console.info('getImageFileFd done');
  }

  // close file fd
  async closeFd(): Promise<void> {
    console.info('case closeFd called');
    if (this.mSaveCameraAsset) {
      await this.mSaveCameraAsset.closeVideoFile();
      this.mFileAssetId = undefined;
      this.fdPath = undefined;
      console.info('case closeFd done');
    }
  }

  async createPhotoOutput() {
    const photoProfile: camera.Profile = {
      format: camera.CameraFormat.CAMERA_FORMAT_JPEG,
      size: {
        "width": 1280,
        "height": 720
      }
    }
    if (!this.cameraManager) {
      console.error('createPhotoOutput cameraManager is null')
    }
    if (!this.photoReceiver) {
      this.photoReceiver = image.createImageReceiver(photoProfile.size, image.ImageFormat.YCBCR_422_SP, 8)
      this.photoReceiver.on("imageArrival",()=>{
        this.photoReceiver?.readNextImage((err,image)=>{
          if (err || image === undefined) {
            console.error('photoReceiver imageArrival on error')
            return;
          }
          image.getComponent(4, async (err, img) => {
            if (err || img === undefined) {
              console.error('image getComponent on error')
              return;
            }
            await this.getImageFileFd()
            fileIo.write(this.mFileAssetId, img.byteBuffer)
            await this.closeFd()
            await image.release()
            console.info('photoReceiver image.getComponent save success')
          })
        })
      })
        await this.photoReceiver.getReceivingSurfaceId().then((surfaceId: string) => {
          this.photoOutput = this.cameraManager?.createPhotoOutput(photoProfile)
          if (!this.photoOutput) {
            console.error('cameraManager.createPhotoOutput on error')
          }
          console.info('cameraManager.createPhotoOutput success')
          this.photoOutput?.on("captureStart", (err, captureId) => {
            console.info('photoOutput.on captureStart')
          })
        }).catch((err: Error) => {
          console.error('photoReceiver.getReceivingSurfaceId on error:' + err)
        })
      }
    }
  ```

**5. Create a CaptureSession instance.**

Use **createCaptureSession()** to create a **CaptureSession** instance. You can call **beginConfig()** to configure a session, call **addInput()** and **addOutput()** to add **CameraInput()** and **CameraOutput()** to the session, call **commitConfig()** to submit the configuration information, and use a promise to return the result.

  ```ts
  private Session?: camera.Session;

  async failureCallback(error: BusinessError): Promise<void> {
    console.error('case failureCallback called,errMessage is ', JSON.stringify(error));
  }

  async catchCallback(error: BusinessError): Promise<void> {
    console.error('case catchCallback called,errMessage is ', JSON.stringify(error));
  }

  // create camera capture session
  async createCaptureSession(): Promise<void> {
    console.info('createCaptureSession called');
    if (this.cameraManager) {
      this.Session = this.cameraManager.createSession();
      if (!this.Session) {
        console.error('createCaptureSession failed!');
        return;
      }
      try {
        this.Session.beginConfig();
        this.Session.addInput(this.cameraInput);
      } catch (e) {
        console.error('case addInput error:' + JSON.stringify(e));
      }
      try {
        this.Session.addOutput(this.previewOutput);
      } catch (e) {
        console.error('case addOutput error:' + JSON.stringify(e));
      }
      await this.Session.commitConfig().then(() => {
        console.info('captureSession commitConfig success');
      }, this.failureCallback).catch(this.catchCallback);
    }
  }
  ```

**6. Start the session.**

  Use **start()** of the **CaptureSession** instance to start the session and use a promise to return the result.

  ```ts
  // start captureSession
  async startCaptureSession(): Promise<void> {
    console.info('startCaptureSession called');
    if (!this.captureSession) {
      console.error('CaptureSession does not exist!');
      return;
    }

    try {
      await this.captureSession.start();
      console.info('CaptureSession started successfully.');
    } catch (error) {
      console.error('Failed to start CaptureSession:', error);
      if (this.failureCallback) {
        this.failureCallback(error);
      }
    }
  }
  ```

**Releasing Distributed Camera Resources**

  After the service collaboration is complete, the collaboration status needs to be ended in a timely manner to release distributed camera resources.

  ```ts
  private videoOutput?: camera.VideoOutput;
  
  // Release the camera.
  async releaseCameraInput(): Promise<void> {
    console.info('releaseCameraInput called');
    if (this.cameraInput) {
      this.cameraInput = undefined;
    }
    console.info('releaseCameraInput done');
  }

  // Release the preview.
  async releasePreviewOutput(): Promise<void> {
    console.info('releasePreviewOutput called');
    if (this.previewOutput) {
      await this.previewOutput.release().then(() => {
        console.info('[camera] case main previewOutput release called');
      }, this.failureCallback).catch(this.catchCallback);
      this.previewOutput = undefined;
    }
    console.info('releasePreviewOutput done');
  }

  // Release the video output.
  async releaseVideoOutput(): Promise<void> {
    console.info('releaseVideoOutput called');
    if (this.videoOutput) {
      await this.videoOutput.release().then(() => {
        console.info('[camera] case main videoOutput release called');
      }, this.failureCallback).catch(this.catchCallback);
      this.videoOutput = undefined;
    }
    console.info('releaseVideoOutput done');
  }

  // Stop the capture session.
  async stopCaptureSession(): Promise<void> {
    console.info('stopCaptureSession called');
    if (this.captureSession) {
      await this.captureSession.stop().then(() => {
        console.info('[camera] case main captureSession stop success');
      }, this.failureCallback).catch(this.catchCallback);
    }
    console.info('stopCaptureSession done');
  }

  // Release the capture session.
  async releaseCaptureSession(): Promise<void> {
    console.info('releaseCaptureSession called');
    if (this.captureSession) {
      await this.captureSession.release().then(() => {
        console.info('[camera] case main captureSession release success');
      }, this.failureCallback).catch(this.catchCallback);
      this.captureSession = undefined;
    }
    console.info('releaseCaptureSession done');
  }

  // Release the camera resource.
  async releaseCamera(): Promise<void> {
    console.info('releaseCamera called');
    await this.stopCaptureSession();
    await this.releaseCameraInput();
    await this.releasePreviewOutput();
    await this.releaseVideoOutput();
    await this.releaseCaptureSession();
    console.info('releaseCamera done');
  }
  ```

### Debugging and Verification

  After application development is complete, you can install the application on device A and device B. The test procedure is as follows:

  1. Device A starts the distributed camera on device B and initiates a preview. Device A can receive the preview stream.
  2. Device A starts the distributed camera on device B and takes a photo. Device A can receive the photo.

## FAQs


### What should I do if the application on device A cannot start the camera on device B?

**Possible Causes**

  Devices are not networked or are disconnected after networking.

**Solution**

  Enable USB debugging on device A and device B, and use a USB cable to connect the devices to the PC. Run the following shell command on the PC:
   
  ```shell
  hdc shell
  hidumper -s 4700 -a "buscenter -l remote_device_info"
  ```
  If **remote device num = 0** is displayed in the command output, the networking fails. In this case, disable and then enable Wi-Fi, and connect devices to the same Wi-Fi again. If the networking is successful, run the shell command again and the number of networking devices is displayed, for example, **remote device num = 1**.
