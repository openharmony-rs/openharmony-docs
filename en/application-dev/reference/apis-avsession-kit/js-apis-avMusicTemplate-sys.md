# @ohos.multimedia.avMusicTemplate (Audio Template) (System API)
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_gyH0B0hP-->
<!--Designer: @ccfriend-->
<!--Tester: @chen-gong1-->
<!--Adviser: @w_Machine_cc-->

This module provides APIs for controlling the audio template. You can use these APIs to query data from media applications that use the audio template, display pages in a unified style, and deliver page operation instructions.

This module provides the following features:

[AVMusicTemplateDescriptor](#avmusictemplatedescriptor): Audio template descriptor, including the unique ID of the audio template, bundle name of the application, and user ID.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.multimedia.avMusicTemplate (Audio Template)](arkts-apis-avMusicTemplate.md).
> - This module applies only to cars running API version 23 or later.

## Modules to Import

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## avMusicTemplate.createAVMusicTemplateController

createAVMusicTemplateController(sessionId: string): AVMusicTemplateController

Creates an audio template controller and returns the audio template controller object.

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**Required permissions:** ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name   | Type  | Mandatory| Description                         |
| --------- | ------ | ---- | ----------------------------- |
| sessionId | string | Yes  | Unique session ID of the **AVSession** object.|

**Return value**

| Type                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [AVMusicTemplateController](arkts-apis-avMusicTemplate-AVMusicTemplateController.md) | Audio template controller, which can be used to obtain the unique ID of the audio template controller and exchange data with the media application accessing the audio template.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verify failed.                                    |
| 202      | Not System App.                                              |
| 801      | Capability not supported.function createAVMusicTemplateController can not work correctly due to limited device capabilities. |
| 35000002 | Failed to create the AVMusicTemplate controller.             |
| 35000005 | AVMusicTemplate does not exist.                              |

**Example:**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
  private currentBundleName: string | undefined = undefined;
  private templateCreateCallback: Callback<avMusicTemplate.AVMusicTemplateDescriptor> =
    (descriptor: avMusicTemplate.AVMusicTemplateDescriptor) => {
      if (this.isInvalid(descriptor)) {
        console.warn(TAG, 'templateCreateCallback: descriptor is invalid');
        return;
      }
      console.info(TAG, `templateCreateCallback, bundleName: ${descriptor.bundleName}`);
      this.createController(descriptor.sessionId, descriptor.bundleName);
    };
  private templateDestroyCallback: Callback<avMusicTemplate.AVMusicTemplateDescriptor> =
    (descriptor: avMusicTemplate.AVMusicTemplateDescriptor) => {
      if (this.isInvalid(descriptor)) {
        console.warn(TAG, 'templateDestroyCallback: descriptor is invalid');
        return;
      }
      if (this.isStringEmpty(this.currentBundleName)) {
        console.warn(TAG, 'templateDestroyCallback: current bundleName is empty');
        return;
      }
      if (this.currentBundleName !== descriptor.bundleName) {
        console.warn(TAG, 'templateDestroyCallback: not current bundleName');
        return;
      }
      this.unregisterListener();
      this.destroyController();
    };

  /**
   * Create a template using getAllAVMusicTemplateDescriptors.
   */
  public createAvMusicTemplateController(bundleName: string) {
    if (this.isStringEmpty(bundleName)) {
      console.warn(TAG, 'createAvMusicTemplateController: bundleName is empty');
      return;
    }
    this.currentBundleName = bundleName;
    try {
      // This method requires the ohos.permission.MANAGE_MEDIA_RESOURCES permission.
      let descriptors: avMusicTemplate.AVMusicTemplateDescriptor[] = avMusicTemplate.getAllAVMusicTemplateDescriptors();
      if (this.isEmptyArray(descriptors)) {
        console.info(TAG, 'createAvMusicTemplateController: descriptors is empty');
        return;
      }
      for (let descriptor of descriptors) {
        if (descriptor === null || descriptor === undefined) {
          console.warn(TAG, 'createAvMusicTemplateController: descriptor is invalid continue');
          continue;
        }
        if (this.currentBundleName === descriptor.bundleName) {
          this.createController(descriptor.sessionId, descriptor.bundleName);
          return;
        }
      }
    } catch (e) {
      console.error(TAG, `getAllAVMusicTemplateDescriptors failed, errCode: ${e?.code}`);
    }
  };

  private isInvalid<T>(obj: T): boolean {
    return obj === undefined || obj === null;
  }

  private isStringEmpty(str: string | undefined): boolean {
    return str === undefined || str === null || str.trim().length === 0;
  }

  private isEmptyArray<T>(array: T[]): boolean {
    return this.isInvalid(array) || array.length <= 0;
  }

  /**
   * Register a template listener.
   */
  public registerAVMusicTemplateListener() {
    try {
      // This method requires the ohos.permission.MANAGE_MEDIA_RESOURCES permission.
      avMusicTemplate.onAVMusicTemplateCreate(this.templateCreateCallback);

      // This method requires the ohos.permission.MANAGE_MEDIA_RESOURCES permission.
      avMusicTemplate.onAVMusicTemplateDestroy(this.templateDestroyCallback);
    } catch (e) {
      console.error(TAG, `registerAVMusicTemplateListener: errCode: ${e?.code}`);
    }
  }

  private createController(sessionId: string, bundleName: string) {
    if (this.currentBundleName === null || this.currentBundleName === undefined) {
      console.warn(TAG, 'createController: sessionId is invalid');
      return;
    }
    if (sessionId === null || sessionId === undefined) {
      console.warn(TAG, 'createController: sessionId is invalid');
      return;
    }
    if (bundleName === null || bundleName === undefined) {
      console.warn(TAG, 'createController: bundleName is invalid');
      return;
    }
    if (this.currentBundleName !== bundleName) {
      console.warn(TAG, 'createController: not current bundleName');
      return;
    }
    if (this.controller != undefined) {
      console.warn(TAG, 'createController: controller not undefined');
      return;
    }
    try {
      this.controller = avMusicTemplate.createAVMusicTemplateController(sessionId);
      console.info('Succeeded in creating controller.');
    } catch (e) {
      console.error(TAG, `createController: errCode: ${e?.code}`);
    }
  }

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    // Unregister the listener for user information changes.
    this.controller?.offUserInfoChange();

    // Unregister the listener for dialog box command changes.
    this.controller?.offDialogCommandChange();

    // Unregister the listener for the current single track changes.
    this.controller?.offCurrentSingleChange();

    // Unregister the listener for media entity changes.
    this.controller?.offMediaEntitiesChange();

    // Unregister the listener for tab content changes.
    this.controller?.offTabContentChange();

    // Unregister the listener for playlist changes.
    this.controller?.offPlaylistChange();

    // Unregister the listener for media download status changes.
    this.controller?.offDownloadMediaEntityStatusChange();

    // Unregister the listener for custom element changes.
    this.controller?.offCustomElementsChange();

    // Unregister the listener for setting changes.
    this.controller?.offSettingsChange();

    // Unregister the listener for reported actions.
    this.controller?.offReportExecuteAction();

    // Unregister the listener for the information about the media center starting the specified third-party application screen.
    this.controller?.offExtensionAbilityChange();
  }

  /**
   * Destroy the controller.
   */
  public destroyController() {
    console.info(TAG, 'destroyController')
    this.controller?.destroy();
    this.controller = undefined;
    this.currentBundleName = undefined;
  }

  /**
   * Unregister the template listener.
   */
  public unregisterAVMusicTemplateListener() {
    try {
      avMusicTemplate.offAVMusicTemplateCreate();
      avMusicTemplate.offAVMusicTemplateDestroy();
    } catch (e) {
      console.error(TAG, `unregisterAVMusicTemplateListener: errCode: ${e?.code}`);
    }
  }
}
```

## avMusicTemplate.getAllAVMusicTemplateDescriptors

getAllAVMusicTemplateDescriptors(userId?: number): AVMusicTemplateDescriptor[]

Obtains all audio template descriptors and returns a collection of audio template descriptors.

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**Required permissions:** ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | -------- |
| userId | number  | No  | User ID. The value is subject to the user input and can be empty.|

**Return value**

| Type                                                     | Description                |
| --------------------------------------------------------- | -------------------- |
| [AVMusicTemplateDescriptor](#avmusictemplatedescriptor)[] | Collection of audio template descriptors.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verify failed.                                    |
| 202      | Not System App.                                              |
| 801      | Capability not supported.function getAllAVMusicTemplateDescriptors can not work correctly due to limited device capabilities. |

**Example:**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private currentBundleName: string | undefined = undefined;

  /**
   * Create a template.
   */
  public createAvMusicTemplateController(bundleName: string) {
    if (this.isStringEmpty(bundleName)) {
      console.warn(TAG, 'createAvMusicTemplateController: bundleName is empty');
      return;
    }
    this.currentBundleName = bundleName;
    try {
      // This method requires the ohos.permission.MANAGE_MEDIA_RESOURCES permission.
      let descriptors: avMusicTemplate.AVMusicTemplateDescriptor[] = avMusicTemplate.getAllAVMusicTemplateDescriptors();
    } catch (e) {
      console.error(TAG, `getAllAVMusicTemplateDescriptors failed, errCode: ${e?.code}`);
    }
  };

  private isStringEmpty(str: string | undefined): boolean {
    return str === undefined || str === null || str.trim().length === 0;
  }
}
```

## avMusicTemplate.onAVMusicTemplateCreate

onAVMusicTemplateCreate(callback: Callback&lt;AVMusicTemplateDescriptor&gt;): void

Registers a listener for audio template creation. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**Required permissions:** ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------------------- |
| callback | Callback<[AVMusicTemplateDescriptor](#avmusictemplatedescriptor)> | Yes  | Callback used to return the audio template descriptor. It is used to process the command for creating a session.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verify failed.                                    |
| 202      | Not System App.                                              |
| 801      | Capability not supported.function onAVMusicTemplateCreate can not work correctly due to limited device capabilities. |

**Example:**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private templateCreateCallback: Callback<avMusicTemplate.AVMusicTemplateDescriptor> =
    (descriptor: avMusicTemplate.AVMusicTemplateDescriptor) => {
      if (this.isInvalid(descriptor)) {
        console.warn(TAG, 'templateCreateCallback: descriptor is invalid');
        return;
      }
      console.info(TAG, `templateCreateCallback, bundleName: ${descriptor.bundleName}`);
    };

  private isInvalid<T>(obj: T): boolean {
    return obj === undefined || obj === null;
  }

  /**
   * Register a template listener.
   */
  public registerAVMusicTemplateListener() {
    try {
      // This method requires the ohos.permission.MANAGE_MEDIA_RESOURCES permission.
      avMusicTemplate.onAVMusicTemplateCreate(this.templateCreateCallback);
    } catch (e) {
      console.error(TAG, `registerAVMusicTemplateListener: errCode: ${e?.code}`);
    }
  }
}
```

## avMusicTemplate.offAVMusicTemplateCreate

offAVMusicTemplateCreate(callback?: Callback&lt;AVMusicTemplateDescriptor&gt;): void

Unregisters the listener for audio template creation.

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**Required permissions:** ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback<[AVMusicTemplateDescriptor](#avmusictemplatedescriptor)> | No  | Callback used to return the audio template descriptor. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verify failed.                                    |
| 202      | Not System App.                                              |
| 801      | Capability not supported.function offAVMusicTemplateCreate can not work correctly due to limited device capabilities. |

**Example:**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  /**
   * Unregister the template listener.
   */
  public unregisterAVMusicTemplateListener() {
    try {
      avMusicTemplate.offAVMusicTemplateCreate();
    } catch (e) {
      console.error(TAG, `unregisterAVMusicTemplateListener: errCode: ${e?.code}`);
    }
  }
}
```

## avMusicTemplate.onAVMusicTemplateDestroy

onAVMusicTemplateDestroy(callback: Callback&lt;AVMusicTemplateDescriptor&gt;): void

Registers a listener for audio template destroy. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**Required permissions:** ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                        |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------- |
| callback | Callback<[AVMusicTemplateDescriptor](#avmusictemplatedescriptor)> | Yes  | Callback used to return the audio template descriptor.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verify failed.                                    |
| 202      | Not System App.                                              |
| 801      | Capability not supported.function onAVMusicTemplateDestroy can not work correctly due to limited device capabilities. |

**Example:**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private templateDestroyCallback: Callback<avMusicTemplate.AVMusicTemplateDescriptor> =
    (descriptor: avMusicTemplate.AVMusicTemplateDescriptor) => {
    };

  /**
   * Register a template listener.
   */
  public registerAVMusicTemplateListener() {
    try {
      // This method requires the ohos.permission.MANAGE_MEDIA_RESOURCES permission.
      avMusicTemplate.onAVMusicTemplateDestroy(this.templateDestroyCallback);
    } catch (e) {
      console.error(TAG, `registerAVMusicTemplateListener: errCode: ${e?.code}`);
    }
  }
}
```

## avMusicTemplate.offAVMusicTemplateDestroy

offAVMusicTemplateDestroy(callback?: Callback&lt;AVMusicTemplateDescriptor&gt;): void

Unregister the listener for audio template destroy.

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**Required permissions:** ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback<[AVMusicTemplateDescriptor](#avmusictemplatedescriptor)> | No  | Callback used to return the audio template descriptor. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verify failed.                                    |
| 202      | Not System App.                                              |
| 801      | Capability not supported.function offAVMusicTemplateDestroy can not work correctly due to limited device capabilities. |

**Example:**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  /**
   * Unregister the template listener.
   */
  public unregisterAVMusicTemplateListener() {
    try {
      avMusicTemplate.offAVMusicTemplateDestroy();
    } catch (e) {
      console.error(TAG, `unregisterAVMusicTemplateListener: errCode: ${e?.code}`);
    }
  }
}
```

## AVMusicTemplateDescriptor

Defines the audio template descriptor. It includes the unique ID of the audio template, bundle name of the application, and user ID.

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name      | Type  | Read-Only| Optional| Description              |
| ---------- | ------ | ---- | ---- | ------------------ |
| sessionId  | string | No  | No  | Unique ID of the audio template.|
| bundleName | string | No  | No  | Bundle name of the application.      |
| userId     | number | No  | No  | User ID.          |
