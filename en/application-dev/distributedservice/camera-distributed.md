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



**Initiating the Preview Stream and Photo Stream on the Distributed Camera**

**1. Obtain the camera information of a remote device.**

  After the application networking is successful, you can use **getCameraManager()** to obtain the camera manager instance and **getSupportedCameras()** to obtain the supported camera device object.

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


**2. Create a CameraInput instance.**

  After obtaining the **CameraManager** instance and the supported camera device object, call **createCameraInput()** to create a **CameraInput** instance.

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


**3. Obtain the PreviewOutput object.**

  Use **createPreviewOutput()** to create a **PreviewOutput** object.

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



**4. Obtain the PhotoOutput object.**

  Use **createPhotoOutput()** to create a **PhotoOutput** object and **createImageReceiver()** to create an **ImageReceiver** instance.

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


**5. Create a CaptureSession instance.**

Use **createCaptureSession()** to create a **CaptureSession** instance. You can call **beginConfig()** to configure a session, call **addInput()** and **addOutput()** to add **CameraInput()** and **CameraOutput()** to the session, call **commitConfig()** to submit the configuration information, and use a promise to return the result.

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


**6. Start the session.**

  Use **start()** of the **CaptureSession** instance to start the session and use a promise to return the result.

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


**Releasing Distributed Camera Resources**

  After the service collaboration is complete, the collaboration status needs to be ended in a timely manner to release distributed camera resources.

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
