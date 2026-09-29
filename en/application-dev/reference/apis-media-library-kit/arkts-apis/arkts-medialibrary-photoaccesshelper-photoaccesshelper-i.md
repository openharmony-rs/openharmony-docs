# PhotoAccessHelper

```TypeScript
interface PhotoAccessHelper
```

Helper functions to access photos and albums.

**Since:** 10

<!--Device-photoAccessHelper-interface PhotoAccessHelper--><!--Device-photoAccessHelper-interface PhotoAccessHelper-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## applyChanges

```TypeScript
applyChanges(mediaChangeRequest: MediaChangeRequest): Promise<void>
```

Applies media changes. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-PhotoAccessHelper-applyChanges(mediaChangeRequest: MediaChangeRequest): Promise<void>--><!--Device-PhotoAccessHelper-applyChanges(mediaChangeRequest: MediaChangeRequest): Promise<void>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mediaChangeRequest | [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md) | Yes | Request for asset changes or album changes. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The mediaChangeRequest parameter is not a valid MediaChangeRequest object; <br>2.Server returned an error during applyChanges, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs; <br>3.The resource change operation for the current request type is not supported. |

**Examples**

This API depends on the [MediaChangeRequest](arkts-apis-photoAccessHelper-i.md#mediachangerequest) object. For details about the sample code, see the examples of [MediaAssetChangeRequest](arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md) and [MediaAlbumChangeRequest](arkts-apis-photoAccessHelper-MediaAlbumChangeRequest.md).

## checkPhotoUrisReadPermission

```TypeScript
checkPhotoUrisReadPermission(uris: string[]): Promise<Map<string, MediaAssetPermissionState>>
```

Query whether the assets exist and whether the invoker has read permission on the assets without permission.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PhotoAccessHelper-checkPhotoUrisReadPermission(uris: string[]): Promise<Map<string, MediaAssetPermissionState>>--><!--Device-PhotoAccessHelper-checkPhotoUrisReadPermission(uris: string[]): Promise<Map<string, MediaAssetPermissionState>>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uris | string[] | Yes | Asset URI list. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Map&lt;string, [MediaAssetPermissionState](arkts-medialibrary-photoaccesshelper-mediaassetpermissionstate-e.md)&gt;&gt; | Returns whether the assets exist and whether the invoker has read permission on the assets without permission. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Scenario-specific parameters are incorrect. Possible causes are as follows:<br>1. The length of the input parameter queue is greater than 500. <br>2. The input parameter is null or undefined. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs. Possible causes:<br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('checkPhotoUrisReadPermissionDemo');

  try {
    let uris: string[] = [
      'file://fileUriDemo1', // The URI here is an example only.
      'file://fileUriDemo2'
    ];
    let permissionMap: Map<string, photoAccessHelper.MediaAssetPermissionState> =
      await phAccessHelper.checkPhotoUrisReadPermission(uris);
  } catch (err) {
    const error = err as BusinessError;
    console.error(`checkPhotoUrisReadPermission failed, error: ${error.code}, ${error.message}`);
  }
}
```

<a id="createasset-4"></a>

## createAsset

```TypeScript
createAsset(photoType: PhotoType, extension: string, options: CreateOptions, callback: AsyncCallback<string>): void
```

Creates an image or video asset with the specified file type, file name extension, and options. This API uses an asynchronous callback to return the result.

If you do not have the **ohos.permission.WRITE_IMAGEVIDEO** permission, you can create a media asset by using a security component or an authorization pop-up. For details, see [Saving Media Assets](../../../media/medialibrary/photoAccessHelper-savebutton.md).

**Since:** 10

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-PhotoAccessHelper-createAsset(photoType: PhotoType, extension: string, options: CreateOptions, callback: AsyncCallback<string>): void--><!--Device-PhotoAccessHelper-createAsset(photoType: PhotoType, extension: string, options: CreateOptions, callback: AsyncCallback<string>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| photoType | [PhotoType](arkts-medialibrary-photoaccesshelper-phototype-e.md) | Yes | Type of the file to create, which can be **IMAGE** or **VIDEO**. |
| extension | string | Yes | File name extension, for example, **'jpg'**. |
| options | [CreateOptions](arkts-medialibrary-photoaccesshelper-createoptions-i.md) | Yes | Options used for creation. Currently, only **title** is supported, for example, **{title: 'testPhoto'}**. <br>**NOTE:** <br>If a **subtype** option is passed, the configuration does not take effect. Only DEFAULT images can be saved. <br>The file name must not contain any invalid characters, which are:.. \ / : * ? " ' ` &lt; &gt; &#124; { } [ ] |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the URI of the created image or video asset. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 11 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied<br>**Applicable version:** 10 |
| 13900020 | Invalid parameter. Possible causes:<br>1.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs; <br>2.The number of arguments is invalid; <br>3.The argument list is empty; <br>4.The object is not a valid instance; <br>5.PhotoAccessHelper object is not a valid instance obtained through the proper API; <br>6.The callback parameter type does not match, expected AsyncCallback; <br>7.Failed to get the photoType parameter, please check the parameter type; <br>8.The photoType parameter is not a valid number type; <br>9.Invalid file type, must be IMAGE or VIDEO; <br>10.Failed to parse the extension parameter, please check if it is a valid string; <br>11.Failed to get the options parameter type, please check if it is an object; <br>12.Failed to parse CreateOptions, please check the options parameter; <br>13.Server returned an invalid argument error; <br>14.Failed to get the photoType parameter. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The photoType parameter is not a valid PhotoType enum value, must be IMAGE or VIDEO; <br>2.The extension parameter is not a valid string, please check if it is a valid file extension; <br>3.The options parameter is invalid, please check if it is a valid CreateOptions object; <br>4.Failed to create the asset, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetDemo');
  let photoType: photoAccessHelper.PhotoType = photoAccessHelper.PhotoType.IMAGE;
  let extension:string = 'jpg';
  let options: photoAccessHelper.CreateOptions = {
    title: 'testPhoto'
  }
  phAccessHelper.createAsset(photoType, extension, options, (err, uri) => {
    if (uri !== undefined) {
      console.info('createAsset uri' + uri);
      console.info('createAsset successfully');
    } else {
      console.error(`createAsset failed, error: ${err.code}, ${err.message}`);
    }
  });
}
```

<a id="createasset-5"></a>

## createAsset

```TypeScript
createAsset(photoType: PhotoType, extension: string, callback: AsyncCallback<string>): void
```

Creates an image or video asset with the specified file type and file name extension. This API uses an asynchronous callback to return the result.

If you do not have the **ohos.permission.WRITE_IMAGEVIDEO** permission, you can create a media asset by using a security component or an authorization pop-up. For details, see [Saving Media Assets](../../../media/medialibrary/photoAccessHelper-savebutton.md).

**Since:** 10

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-PhotoAccessHelper-createAsset(photoType: PhotoType, extension: string, callback: AsyncCallback<string>): void--><!--Device-PhotoAccessHelper-createAsset(photoType: PhotoType, extension: string, callback: AsyncCallback<string>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| photoType | [PhotoType](arkts-medialibrary-photoaccesshelper-phototype-e.md) | Yes | Type of the file to create, which can be **IMAGE** or **VIDEO**. |
| extension | string | Yes | File name extension, for example, **'jpg'**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the URI of the created image or video asset. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 11 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied<br>**Applicable version:** 10 |
| 13900020 | Invalid parameter. Possible causes:<br>1.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs <br>2.The number of arguments is invalid; <br>3.The argument list is empty; <br>4.The object is not a valid instance; <br>5.PhotoAccessHelper object is not a valid instance obtained through the proper API; <br>6.The callback parameter type does not match, expected AsyncCallback; <br>7.Failed to get the photoType parameter, please check the parameter type; <br>8.The photoType parameter is not a valid number type; <br>9.Invalid file type, must be IMAGE or VIDEO; <br>10.Failed to parse the extension parameter, please check if it is a valid string; <br>11.Failed to get parameter type, please check the parameter; <br>12.Failed to get the photoType parameter; <br>13.Server returned an invalid argument error. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The photoType parameter is not a valid PhotoType enum value, must be IMAGE or VIDEO; <br>2.The extension parameter is not a valid string, please check if it is a valid file extension; <br>3.Failed to create the asset, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetDemo');
  let photoType: photoAccessHelper.PhotoType = photoAccessHelper.PhotoType.IMAGE;
  let extension: string = 'jpg';
  phAccessHelper.createAsset(photoType, extension, (err, uri) => {
    if (uri !== undefined) {
      console.info('createAsset uri' + uri);
      console.info('createAsset successfully');
    } else {
      console.error(`createAsset failed, error: ${err.code}, ${err.message}`);
    }
  });
}
```

<a id="createasset-6"></a>

## createAsset

```TypeScript
createAsset(photoType: PhotoType, extension: string, options?: CreateOptions): Promise<string>
```

Creates an image or video asset with the specified file type, file name extension, and options. This API uses a promise to return the result.

If you do not have the **ohos.permission.WRITE_IMAGEVIDEO** permission, you can create a media asset by using a security component or an authorization pop-up. For details, see [Saving Media Assets](../../../media/medialibrary/photoAccessHelper-savebutton.md).

**Since:** 10

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-PhotoAccessHelper-createAsset(photoType: PhotoType, extension: string, options?: CreateOptions): Promise<string>--><!--Device-PhotoAccessHelper-createAsset(photoType: PhotoType, extension: string, options?: CreateOptions): Promise<string>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| photoType | [PhotoType](arkts-medialibrary-photoaccesshelper-phototype-e.md) | Yes | Type of the file to create, which can be **IMAGE** or **VIDEO**. |
| extension | string | Yes | File name extension, for example, **'jpg'**. |
| options | [CreateOptions](arkts-medialibrary-photoaccesshelper-createoptions-i.md) | No | Options used for creation. Currently, only **title** is supported, for example, **{title: 'testPhoto'}**. <br>**NOTE:** <br>If a **subtype** option is passed, the configuration does not take effect. Only DEFAULT images can be saved. <br>The file name must not contain any invalid characters, which are:.. \ / : * ? " ' ` &lt; &gt; &#124; { } [ ] |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the URI of the created image or video asset. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 11 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied<br>**Applicable version:** 10 |
| 13900020 | Invalid parameter. Possible causes:<br>1.System internal error, possible causes:1. System internal error. Possible: 1. File system exception; 3. IPC timeout. Please retry and check logs <br>2.The number of arguments is invalid; <br>3.The argument list is empty; <br>4.The object is not a valid instance; <br>5.PhotoAccessHelper object is not a valid instance obtained through the proper API; <br>6.The callback parameter type does not match, expected AsyncCallback; <br>7.Failed to get the photoType parameter, please check the parameter type; <br>8.The photoType parameter is not a valid number type; <br>9.Invalid file type, must be IMAGE or VIDEO; <br>10.Failed to parse the extension parameter, please check if it is a valid string; <br>11.Failed to get the options parameter type, please check if it is an object; <br>12.Failed to parse CreateOptions, please check the options parameter; <br>13.Server returned an invalid argument error; <br>14.Failed to get the photoType parameter. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The photoType parameter is not a valid PhotoType enum value, must be IMAGE or VIDEO; <br>2.The extension parameter is not a valid string, please check if it is a valid file extension; <br>3.The options parameter is invalid, please check if it is a valid CreateOptions object; <br>4.Failed to create the asset, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetDemo');
  try {
    let photoType: photoAccessHelper.PhotoType = photoAccessHelper.PhotoType.IMAGE;
    let extension: string = 'jpg';
    let options: photoAccessHelper.CreateOptions = {
      title: 'testPhoto'
    }
    let uri: string = await phAccessHelper.createAsset(photoType, extension, options);
    console.info('createAsset uri' + uri);
    console.info('createAsset successfully');
  } catch (err) {
    console.error(`createAsset failed, error: ${err.code}, ${err.message}`);
  }
}
```

## createAssetWithShortTermPermission

```TypeScript
createAssetWithShortTermPermission(photoCreationConfig: PhotoCreationConfig): Promise<string>
```

Creates an asset with a temporary permission of the given period. When this API is called by an application for the first time, a dialog box will be displayed for the user to confirm whether to save the asset. If the user agrees to save the asset, the asset instance will be created and the file URI granted with the save permission will be returned. The application can write the asset based on the URI.

Within 5 minutes after the user agrees to save the asset, if the same application calls this API again, the authorized URI can be automatically returned without the need to display the confirmation dialog box. Exiting the application will terminate the authorization, and the user need to re-trigger the dialog box for authorization confirmation when the application is re-launched.

**Since:** 12

**Required permissions:** ohos.permission.SHORT_TERM_WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-createAssetWithShortTermPermission(photoCreationConfig: PhotoCreationConfig): Promise<string>--><!--Device-PhotoAccessHelper-createAssetWithShortTermPermission(photoCreationConfig: PhotoCreationConfig): Promise<string>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| photoCreationConfig | [PhotoCreationConfig](arkts-medialibrary-photoaccesshelper-photocreationconfig-i.md) | Yes | Configuration for saving a media asset (image or video) to the media library, including the file name.<br>**NOTE:** <br>If a **subtype** option is passed, the configuration does not take effect. Only DEFAULT images can be saved. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the URI of the asset saved. The URIs are granted with the permission for the application to write data. If the URIs fail to be generated, a batch creation error code will be returned.<br>The error code **-3006** means that there are invalid characters; **-2004** means that the image type does not match the file name extension; **-203** means that the file operation is abnormal. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { fileIo } from '@kit.CoreFileKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
    console.info('createAssetWithShortTermPermissionDemo.');
    
    try {
        let photoCreationConfig: photoAccessHelper.PhotoCreationConfig = {
            title: '123456', 
            fileNameExtension: 'jpg',
            photoType: photoAccessHelper.PhotoType.IMAGE,
            subtype: photoAccessHelper.PhotoSubtype.DEFAULT, 
        };

        let resultUri: string = await phAccessHelper.createAssetWithShortTermPermission(photoCreationConfig);
        let resultFile: fileIo.File = fileIo.openSync(resultUri, fileIo.OpenMode.READ_WRITE);
        // Use the actual URI and file size.
        let srcFile:  fileIo.File = fileIo.openSync("file://test.jpg", fileIo.OpenMode.READ_ONLY);
        let bufSize: number = 2000000;
        let readSize: number = 0;
        let buf = new ArrayBuffer(bufSize);
        let readLen = fileIo.readSync(srcFile.fd, buf, {
            offset: readSize,
            length: bufSize
        });
        if (readLen > 0) {
            readSize += readLen;
            fileIo.writeSync(resultFile.fd, buf, { length: readLen });
        }
        fileIo.closeSync(srcFile);
        fileIo.closeSync(resultFile);
    } catch (err) {
        console.error('createAssetWithShortTermPermission failed, errCode is ' + err.code + ', errMsg is ' + err.message);
    }
    
}
```

## createAssetWithShortTermPermissionEx

```TypeScript
createAssetWithShortTermPermissionEx(creationSetting: CreationSetting): Promise<string>
```

Displays the dialog box for the first time for the user to confirm whether to save the asset. This API uses a promise to return the result.

> **NOTE:** 
> 
> - After the user agrees to save the asset, the API returns the URI of the created asset that has the save permission. The application can use the URI to write the image or video.
> 
> - Within 5 minutes after the user agrees to save the asset, if the same application calls this API again, the system directly returns the authorized URI for the application to save the image or video without displaying a confirmation dialog box. Exiting the application will terminate the authorization, and the user need to re-trigger the dialog box for authorization confirmation when the application is re-launched.

**Since:** 23

**Required permissions:** ohos.permission.SHORT_TERM_WRITE_IMAGEVIDEO

**Model restriction:** This API can be used only in the stage model.

<!--Device-PhotoAccessHelper-createAssetWithShortTermPermissionEx(creationSetting: CreationSetting): Promise<string>--><!--Device-PhotoAccessHelper-createAssetWithShortTermPermissionEx(creationSetting: CreationSetting): Promise<string>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| creationSetting | [CreationSetting](arkts-medialibrary-photoaccesshelper-creationsetting-i.md) | Yes | Configuration for saving a media asset (image or video) to the media library, including the file name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the URI of the media library file to the application. The application can use the returned URI to write data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.Internal error in dialog, please retry; <br>2.Dialog result missing required parameters, system internal error; <br>3.Dialog operation failed, please retry; <br>4.Callback processing failed, system internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

## createPhotoAsset

```TypeScript
createPhotoAsset(photoType: PhotoType, extension: string, title?: string): Promise<string>
```

Creates an image or video resource with the specified file type, extension, and title. This API uses a promise to return the result.

If you do not have the **ohos.permission.WRITE_IMAGEVIDEO** permission, you can create a media asset by using a security component or an authorization pop-up. For details, see [Saving Media Assets](../../../media/medialibrary/photoAccessHelper-savebutton.md).

**Since:** 23

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-PhotoAccessHelper-createPhotoAsset(photoType: PhotoType, extension: string, title?: string): Promise<string>--><!--Device-PhotoAccessHelper-createPhotoAsset(photoType: PhotoType, extension: string, title?: string): Promise<string>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| photoType | [PhotoType](arkts-medialibrary-photoaccesshelper-phototype-e.md) | Yes | Type of the file to be created. For example, **IMAGE** or **VIDEO**. |
| extension | string | Yes | File name extension. For example, **'jpg'**. |
| title | string | No | Title of the image or video resource. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the URL of the created image or video. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Invalid parameter. Possible causes:<br>1.The number of parameters is invalid, expected 2 or 3 parameters; <br>2.The photoType parameter must be a number; <br>3.The photoType must be IMAGE(1) or VIDEO(2); <br>4.The extension parameter must be a string; <br>5.The extension does not match the photoType; <br>6.The title parameter must be a string (when provided); <br>7.The title contains invalid characters or exceeds the length limit; <br>8.The server returned an invalid argument error. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | MediaLibrary inner fail. Possible causes:<br>1.Server returned an invalid argument error. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createPhotoAssetDemo');
  try {
    let photoType: photoAccessHelper.PhotoType = photoAccessHelper.PhotoType.IMAGE;
    let extension: string = 'jpg';
    let title: string = 'testPhoto';
    let uri: string = await phAccessHelper.createPhotoAsset(photoType, extension, title);
    console.info('createPhotoAsset uri' + uri);
    console.info('createPhotoAsset successfully');
  } catch (err) {
    console.error(`createPhotoAsset failed, error: ${err.code}, ${err.message}`);
  }
}
```

## getAlbumIdByLpath

```TypeScript
getAlbumIdByLpath(lpath: string): Promise<number>
```

Obtains the album ID in the media library based on the album's virtual path. This API uses a promise to return the result.

This API supports the following albums: camera application album, screenshot application album, and screen recording application album.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

<!--Device-PhotoAccessHelper-getAlbumIdByLpath(lpath: string): Promise<int>--><!--Device-PhotoAccessHelper-getAlbumIdByLpath(lpath: string): Promise<int>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| lpath | string | Yes | Virtual path of the album. The value can contain a maximum of 255 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the album ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Invalid parameter. Possible causes:<br>1.The number of parameters is not 1; <br>2.The value is not a string or the string fails to be read; <br>3.The lpath is an empty string or its length exceeds the maximum limit (255); <br>4.The lpath is not in the allowed list of MEDIA_DIRS (excluding /DCIM/Camera, /Pictures/Screenshots, and /Pictures/Screenrecords); <br>5.The IPC call returns a server error code. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | MediaLibrary inner fail. Possible causes:<br>1.System internal error, failed to create boolean value, please retry; <br>2.The IPC call returns a server error code; <br>3.Failed to initialize error Field / Failed to initialize data Field. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getAlbumIdByLpath');

  try {
      let albumId: number = await phAccessHelper.getAlbumIdByLpath('testLpath');
      console.info('requestFile:: albumId: ', albumId);

      console.info('getAlbumIdByLpath completed.');
      console.info(`albumId : ${albumId}`);
    } catch (err) {
      console.error(`getAlbumIdByLpath failed: ${err.code}, ${err.message}`);
    }
}
```

## getAlbums

```TypeScript
getAlbums(
      type: AlbumType,
      subtype: AlbumSubtype,
      options: FetchOptions,
      callback: AsyncCallback<FetchResult<Album>>
    ): void
```

Obtains albums based on the specified options and album type. This API uses an asynchronous callback to return the result.

Before the operation, ensure that the albums to obtain exist.

**Since:** 10

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-getAlbums(      type: AlbumType,      subtype: AlbumSubtype,      options: FetchOptions,      callback: AsyncCallback<FetchResult<Album>>    ): void--><!--Device-PhotoAccessHelper-getAlbums(      type: AlbumType,      subtype: AlbumSubtype,      options: FetchOptions,      callback: AsyncCallback<FetchResult<Album>>    ): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [AlbumType](arkts-medialibrary-photoaccesshelper-albumtype-e.md) | Yes | Type of the album. |
| subtype | [AlbumSubtype](arkts-medialibrary-photoaccesshelper-albumsubtype-e.md) | Yes | Subtype of the album. |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | Yes | Retrieval options. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FetchResult](arkts-medialibrary-photoaccesshelper-fetchresult-i.md)&lt;[Album](arkts-medialibrary-photoaccesshelper-album-i.md)&gt;&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied<br>**Applicable version:** 10 - 11 |
| 13900020 | Invalid parameter. Possible causes:<br>1.The number of parameters is invalid, expected 0 to 4 parameters; <br>2.The callback parameter must be of type AsyncCallback; <br>3.The type parameter must be a number; <br>4.The type must be a valid AlbumType (USER, SYSTEM, SMART, or SOURCE); <br>5.The subtype parameter must be a number; <br>6.The subtype must be a valid AlbumSubtype; <br>7.The fetchColumns contain invalid column names. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The type parameter is not a valid number, must be a valid AlbumType enum value; <br>2.The subtype parameter is not a valid number, must be a valid AlbumSubtype enum value; <br>3.The FetchOptions parameter is invalid, the predicates contain invalid content or the fetchColumns contain unknown column names; <br>4.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs; <br>5.The query result is empty, the IPC or database query returned no albums (not caused by permission or system app errors). |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  // Obtain the album named newAlbumName.
  console.info('getAlbumsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  predicates.equalTo('album_name', 'newAlbumName');
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, fetchOptions, async (err, fetchResult) => {
    if (err) {
      console.error(`getAlbumsCallback failed with err: ${err.code}, ${err.message}`);
      return;
    }
    if (fetchResult === undefined) {
      console.error('getAlbumsCallback fetchResult is undefined');
      return;
    }
    let album = await fetchResult.getFirstObject();
    console.info('getAlbumsCallback successfully, albumName: ' + album.albumName);
    fetchResult.close();
  });
}
```

<a id="getalbums-1"></a>

## getAlbums

```TypeScript
getAlbums(type: AlbumType, subtype: AlbumSubtype, callback: AsyncCallback<FetchResult<Album>>): void
```

Obtains albums by type. This API uses an asynchronous callback to return the result.

Before the operation, ensure that the albums to obtain exist.

**Since:** 10

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-getAlbums(type: AlbumType, subtype: AlbumSubtype, callback: AsyncCallback<FetchResult<Album>>): void--><!--Device-PhotoAccessHelper-getAlbums(type: AlbumType, subtype: AlbumSubtype, callback: AsyncCallback<FetchResult<Album>>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [AlbumType](arkts-medialibrary-photoaccesshelper-albumtype-e.md) | Yes | Type of the album. |
| subtype | [AlbumSubtype](arkts-medialibrary-photoaccesshelper-albumsubtype-e.md) | Yes | Subtype of the album. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FetchResult](arkts-medialibrary-photoaccesshelper-fetchresult-i.md)&lt;[Album](arkts-medialibrary-photoaccesshelper-album-i.md)&gt;&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied<br>**Applicable version:** 10 - 11 |
| 13900020 | Invalid parameter. Possible causes:<br>1.The number of parameters is invalid, expected 0 to 4 parameters; <br>2.The callback parameter must be of type AsyncCallback; <br>3.The type parameter must be a number; <br>4.The type must be a valid AlbumType (USER, SYSTEM, SMART, or SOURCE); <br>5.The subtype parameter must be a number; <br>6.The subtype must be a valid AlbumSubtype. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The type parameter is not a valid number, must be a valid AlbumType enum value; <br>2.The subtype parameter is not a valid number, must be a valid AlbumSubtype enum value; <br>3.The query result is empty, the IPC or database query returned no albums (not caused by permission or system app errors); <br>4.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  // Obtain the system album VIDEO, which is preset by default.
  console.info('getAlbumsDemo');
  phAccessHelper.getAlbums(photoAccessHelper.AlbumType.SYSTEM, photoAccessHelper.AlbumSubtype.VIDEO, async (err, fetchResult) => {
    if (err) {
      console.error(`getAlbumsCallback failed with err: ${err.code}, ${err.message}`);
      return;
    }
    if (fetchResult === undefined) {
      console.error('getAlbumsCallback fetchResult is undefined');
      return;
    }
    let album: photoAccessHelper.Album = await fetchResult.getFirstObject();
    console.info('getAlbumsCallback successfully, albumUri: ' + album.albumUri);
    fetchResult.close();
  });
}
```

<a id="getalbums-2"></a>

## getAlbums

```TypeScript
getAlbums(type: AlbumType, subtype: AlbumSubtype, options?: FetchOptions): Promise<FetchResult<Album>>
```

Obtains albums based on the specified options and album type. This API uses a promise to return the result.

Before the operation, ensure that the albums to obtain exist.

**Since:** 10

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-getAlbums(type: AlbumType, subtype: AlbumSubtype, options?: FetchOptions): Promise<FetchResult<Album>>--><!--Device-PhotoAccessHelper-getAlbums(type: AlbumType, subtype: AlbumSubtype, options?: FetchOptions): Promise<FetchResult<Album>>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [AlbumType](arkts-medialibrary-photoaccesshelper-albumtype-e.md) | Yes | Type of the album. |
| subtype | [AlbumSubtype](arkts-medialibrary-photoaccesshelper-albumsubtype-e.md) | Yes | Subtype of the album. |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | No | Retrieval options. If this parameter is not specified, the albums are obtained based on the album type by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FetchResult](arkts-medialibrary-photoaccesshelper-fetchresult-i.md)&lt;[Album](arkts-medialibrary-photoaccesshelper-album-i.md)&gt;&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied<br>**Applicable version:** 10 - 11 |
| 13900020 | Invalid parameter. Possible causes:<br>1.The number of parameters is invalid, expected 0 to 4 parameters; <br>2.The callback parameter must be of type AsyncCallback; <br>3.The type parameter must be a number; <br>4.The type must be a valid AlbumType (USER, SYSTEM, SMART, or SOURCE); <br>5.The subtype parameter must be a number; <br>6.The subtype must be a valid AlbumSubtype; <br>7.The fetchColumns contain invalid column names. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The type parameter is not a valid number, must be a valid AlbumType enum value; <br>2.The subtype parameter is not a valid number, must be a valid AlbumSubtype enum value; <br>3.The FetchOptions parameter is invalid, the predicates contain invalid content or the fetchColumns contain unknown column names; <br>4.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs; <br>5.The query result is empty, the IPC or database query returned no albums (not caused by permission or system app errors). |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  // Obtain the album named newAlbumName.
  console.info('getAlbumsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  predicates.equalTo('album_name', 'newAlbumName');
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, fetchOptions).then( async (fetchResult) => {
    if (fetchResult === undefined) {
      console.error('getAlbumsPromise fetchResult is undefined');
      return;
    }
    let album: photoAccessHelper.Album = await fetchResult.getFirstObject();
    console.info('getAlbumsPromise successfully, albumName: ' + album.albumName);
    fetchResult.close();
  }).catch((err: BusinessError) => {
    console.error(`getAlbumsPromise failed with err: ${err.code}, ${err.message}`);
  });
}
```

## getAssets

```TypeScript
getAssets(options: FetchOptions, callback: AsyncCallback<FetchResult<PhotoAsset>>): void
```

Obtains image and video assets. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-getAssets(options: FetchOptions, callback: AsyncCallback<FetchResult<PhotoAsset>>): void--><!--Device-PhotoAccessHelper-getAssets(options: FetchOptions, callback: AsyncCallback<FetchResult<PhotoAsset>>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | Yes | Retrieval options. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FetchResult](arkts-medialibrary-photoaccesshelper-fetchresult-i.md)&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt;&gt; | Yes | Callback function. If files from the album are obtained successfully, **err** is **undefined**, and **data** is the result set of the obtained image and video data ([FetchResult](arkts-medialibrary-file-photoaccesshelper.md)). Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied<br>**Applicable version:** 10 - 11 |
| 13900020 | Invalid parameter. Possible causes:<br>1.Invalid number of arguments; <br>2.The options parameter is null or undefined; <br>3.Parameter parsing failed, please check parameter count and types; <br>4.Object is not a valid object; <br>5.PhotoAccessHelper object is not a valid object. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The FetchOptions parameter is invalid, the predicates property is not a valid data predicates object; <br>2.The predicates in FetchOptions contain invalid content or operations, please check if the predicates are valid; <br>3.The fetchColumns in FetchOptions contain invalid column names, please refer to PhotoKeys for valid column names; <br>4.Database query failed, possible causes: 1. Database exception; 2. IPC timeout. Please retry and check logs; <br>5.Query returned an empty result set. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getAssets');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };

  phAccessHelper.getAssets(fetchOptions, async (err, fetchResult) => {
    if (fetchResult !== undefined) {
      console.info('fetchResult success');
      let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
      if (photoAsset !== undefined) {
        console.info('photoAsset.displayName : ' + photoAsset.displayName);
      }
    } else {
      console.error(`fetchResult fail with error: ${err.code}, ${err.message}`);
    }
  });
}
```

<a id="getassets-1"></a>

## getAssets

```TypeScript
getAssets(options: FetchOptions): Promise<FetchResult<PhotoAsset>>
```

Obtains image and video assets. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-PhotoAccessHelper-getAssets(options: FetchOptions): Promise<FetchResult<PhotoAsset>>--><!--Device-PhotoAccessHelper-getAssets(options: FetchOptions): Promise<FetchResult<PhotoAsset>>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | Yes | Retrieval options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FetchResult](arkts-medialibrary-photoaccesshelper-fetchresult-i.md)&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt;&gt; | Promise used to return the image and video assets obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 20 and later |
| 13900012 | Permission denied<br>**Applicable version:** 10 - 19 |
| 13900020 | Invalid parameter. Possible causes:<br>1.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs <br>2.The number of arguments is invalid; <br>3.The argument list is empty; <br>4.The object is not a valid instance; <br>5.PhotoAccessHelper object is not a valid instance obtained through the proper API; <br>6.The callback parameter type does not match, expected AsyncCallback; <br>7.Invalid ffetchColumns: contains unknown column name. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The FetchOptions parameter is invalid, the predicates property is not a valid data predicates object; <br>2.The predicates in FetchOptions contain invalid content or operations, please check if the predicates are valid; <br>3.The fetchColumns in FetchOptions contain invalid column names, please refer to PhotoKeys for valid column names; <br>4.Database query failed, possible causes: 1. Database exception; 2. IPC timeout. Please retry and check logs; <br>5.Query returned an empty result set. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getAssets');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    if (fetchResult !== undefined) {
      console.info('fetchResult success');
      let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
      if (photoAsset !== undefined) {
        console.info('photoAsset.displayName :' + photoAsset.displayName);
      }
    }
  } catch (err) {
    console.error(`getAssets failed, error: ${err.code}, ${err.message}`);
  }
}
```

## getBurstAssets

```TypeScript
getBurstAssets(burstKey: string, options: FetchOptions): Promise<FetchResult<PhotoAsset>>
```

Obtains burst assets. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-PhotoAccessHelper-getBurstAssets(burstKey: string, options: FetchOptions): Promise<FetchResult<PhotoAsset>>--><!--Device-PhotoAccessHelper-getBurstAssets(burstKey: string, options: FetchOptions): Promise<FetchResult<PhotoAsset>>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| burstKey | string | Yes | Universally Unique Identifier (UUID) of a group of burst photos, that is, **BURST_KEY** of [PhotoKeys](arkts-medialibrary-photoaccesshelper-photokeys-e.md). The string contains 36 bytes. |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | Yes | Retrieval options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FetchResult](arkts-medialibrary-photoaccesshelper-fetchresult-i.md)&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt;&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.Failed to check predicates property; <br>2.Failed to get predicates property; <br>3.The object is not a valid instance; <br>4.The predicates parameter is invalid, not of predicates type; <br>5.Invalid predicate, please check the predicates in FetchOptions content or operation; <br>6.Failed to parse ffetchColumns array; <br>7.Failed to create boolean result; <br>8.Sandbox query failed: internal error; <br>9.File operation failed; <br>10.Failed to parse arguments for getBurstAssets. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getBurstAssets');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  // burstKey is a 36-bit UUID, which can be obtained from photoAccessHelper.PhotoKeys.
  let burstKey: string = "e719d696-09fa-44f8-8e9e-ec3f215aa62a";
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await 
      phAccessHelper.getBurstAssets(burstKey, fetchOptions);
    if (fetchResult !== undefined) {
      console.info('fetchResult success');
      let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
      if (photoAsset !== undefined) {
        console.info('photoAsset.displayName :' + photoAsset.displayName);
      }
    }
  } catch (err) {
    console.error(`getBurstAssets failed, error: ${err.code}, ${err.message}`);
  }
}
```

## getPhotoPickerComponentDefaultAlbumName

```TypeScript
getPhotoPickerComponentDefaultAlbumName(): Promise<string>
```

Obtains the name of the album that the **PhotoPickerComponent** shows by default. The name string is localized to match the current system language. This API uses a promise to return the result.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-PhotoAccessHelper-getPhotoPickerComponentDefaultAlbumName(): Promise<string>--><!--Device-PhotoAccessHelper-getPhotoPickerComponentDefaultAlbumName(): Promise<string>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the name of the default album. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. The IPC request timed out. <br>2. system running error |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import {photoAccessHelper} from '@kit.MediaLibraryKit';

async function example(context: Context) {
  console.info('getPhotoPickerComponentDefaultAlbumNameDemo');
  let phAccessHelper: photoAccessHelper.PhotoAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);

  phAccessHelper.getPhotoPickerComponentDefaultAlbumName().then((defaultAlbumName) => {
    console.info('getPhotoPickerComponentDefaultAlbumName success, defaultAlbumName is ' + defaultAlbumName);
  }).catch((err: BusinessError) => {
    console.error(`getPhotoPickerComponentDefaultAlbumName failed with error: ${err.code}, ${err.message}`);
  });
}
```

## getRecentPhotoInfo

```TypeScript
getRecentPhotoInfo(options?: RecentPhotoOptions): Promise<RecentPhotoInfo>
```

Obtains the information about the recent image or video when the application uses the **RecentPhotoComponent** to view recent images or videos. This API uses a promise to return the result.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-PhotoAccessHelper-getRecentPhotoInfo(options?: RecentPhotoOptions): Promise<RecentPhotoInfo>--><!--Device-PhotoAccessHelper-getRecentPhotoInfo(options?: RecentPhotoOptions): Promise<RecentPhotoInfo>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RecentPhotoOptions](arkts-medialibrary-photoaccesshelper-recentphotooptions-c.md) | No | Options for retrieving the recent image or video. If this parameter is not specified, the latest image is retrieved according to the creation time.<br>If this parameter is specified, it must match the **options** configuration in the **RecentPhotoComponent**. Otherwise, there may be discrepancies where the API finds a recent image or video but the component does not. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RecentPhotoInfo](arkts-medialibrary-photoaccesshelper-recentphotoinfo-c.md)&gt; | Promise used to return the information about the recent image or video. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { photoAccessHelper, PhotoSource, RecentPhotoOptions} from '@kit.MediaLibraryKit';

async function example(context: Context) {
  console.info('getRecentPhotoInfoDemo');
  let phAccessHelper: photoAccessHelper.PhotoAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
  let recentPhotoOptions: RecentPhotoOptions = {
    period: 60 * 60,
    MIMEType: photoAccessHelper.PhotoViewMIMETypes.IMAGE_VIDEO_TYPE,
    photoSource: PhotoSource.ALL
  }

  phAccessHelper.getRecentPhotoInfo(recentPhotoOptions).then((recentPhotoInfo) => {
    console.info('getRecentPhotoInfo success, recentPhotoInfo is ' + JSON.stringify(recentPhotoInfo));
  }).catch((err: BusinessError) => {
    console.error(`getRecentPhotoInfo failed with error: ${err.code}, ${err.message}`);
  });
}
```

## getSupportedPhotoFormats

```TypeScript
getSupportedPhotoFormats(photoType: PhotoType): Promise<Array<string>>
```

Obtains the list of image or video file name extensions supported by the media library.

**Since:** 18

<!--Device-PhotoAccessHelper-getSupportedPhotoFormats(photoType: PhotoType): Promise<Array<string>>--><!--Device-PhotoAccessHelper-getSupportedPhotoFormats(photoType: PhotoType): Promise<Array<string>>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| photoType | [PhotoType](arkts-medialibrary-photoaccesshelper-phototype-e.md) | Yes | Type of the file. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return an array of the supported image or video file name extensions. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.invalid photoType; <br>2.Failed to create string; <br>3.Failed to set element. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, photoTypeNumber: number){
  console.info('getSupportedPhotoFormatsDemo.');

  try {
    let outputText: string;
    if (photoTypeNumber !== photoAccessHelper.PhotoType.IMAGE && photoTypeNumber !== photoAccessHelper.PhotoType.VIDEO) {
      outputText = 'Does not support querying formats other than images or videos';
      return;
    }
    outputText = 'The supported types are:\n';
    let imageFormat  = await phAccessHelper.getSupportedPhotoFormats(photoAccessHelper.PhotoType.IMAGE);
    let result = "";
    for (let i = 0; i < imageFormat.length; i++) {
      result += imageFormat[i];
      if (i !== imageFormat.length - 1) {
        result += ', ';
      }
    }
    outputText += result;
    console.info('getSupportedPhotoFormats success, data is ' + outputText);
  } catch (error) {
    console.error('getSupportedPhotoFormats failed, errCode is', error);
  }
}
```

## off('photoChange')

```TypeScript
off(type: 'photoChange', callback?: Callback<PhotoAssetChangeInfos>): void
```

Unregisters the listener for the **'photoChange'** event to stop monitoring media asset changes. If multiple listeners are registered, you can unregister a specific listener by specifying **callback**. Alternatively, you can unregister all of them without specifying **callback**.

**Since:** 20

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-off(type: 'photoChange', callback?: Callback<PhotoAssetChangeInfos>): void--><!--Device-PhotoAccessHelper-off(type: 'photoChange', callback?: Callback<PhotoAssetChangeInfos>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'photoChange' | Yes | Event type. The value is fixed at **'photoChange'**. After the unregistration is complete, any change to the media assets is no longer returned through the callback. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | No | Exact callback you previously registered with [on('photoChange')](#onphotochange). If this parameter is left unspecified, all listeners for the **'photoChange'** event are unregistered.<br> **NOTE:** <br>Once a specific callback is unregistered, it will not be invoked when a media asset changes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Invalid parameter. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | MediaLibrary inner fail. Possible causes:<br>1.Data service initialization failed, possible causes: 1. Database exception; 2. IPC timeout. Please check if the context is properly initialized and retry <br>2.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback1 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback2 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('offPhotoChangeDemo.');

  try {
    // Register onCallback1.
    phAccessHelper.on('photoChange', onCallback1);
    // Register onCallback2.
    phAccessHelper.on('photoChange', onCallback2);

    // Unregister the listening of onCallback1.
    phAccessHelper.off('photoChange', onCallback1);
  } catch (error) {
    console.error('offPhotoChangeDemo failed, errCode is', error);
  }
}
```

## off('photoAlbumChange')

```TypeScript
off(type: 'photoAlbumChange', callback?: Callback<AlbumChangeInfos>): void
```

Unregisters a listener for the **'photoAlbumChange'** event to stop monitoring album changes. If multiple listeners are registered, you can unregister a specific listener by specifying **callback**. Alternatively, you can unregister all of them without specifying **callback**.

**Since:** 20

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-off(type: 'photoAlbumChange', callback?: Callback<AlbumChangeInfos>): void--><!--Device-PhotoAccessHelper-off(type: 'photoAlbumChange', callback?: Callback<AlbumChangeInfos>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'photoAlbumChange' | Yes | Event type. The value is fixed at **'photoAlbumChange'**. After the unregistration is complete, any change to the albums is no longer returned through the callback. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | No | Exact callback you previously registered with [on('photoAlbumChange')](#onphotoalbumchange). If this parameter is left unspecified, all listeners for the **'photoAlbumChange'** event are unregistered. <br>**NOTE:** <br>Once a specific callback is unregistered, it will not be invoked when an album changes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Invalid parameter. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | MediaLibrary inner fail. Possible causes:<br>1.Data service initialization failed, possible causes: 1. Database exception; 2. IPC timeout. Please check if the context is properly initialized and retry <br>2.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback1 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback2 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onPhotoAlbumChangeDemo.');

  try {
    // Register onCallback1.
    phAccessHelper.on('photoAlbumChange', onCallback1);
    // Register onCallback2.
    phAccessHelper.on('photoAlbumChange', onCallback2);

    // Unregister the listening of onCallback1.
    phAccessHelper.off('photoAlbumChange', onCallback1);
  } catch (error) {
    console.error('onPhotoAlbumChangeDemo failed, errCode is', error);
  }
}
```

## offMediaLibraryAvailability

```TypeScript
offMediaLibraryAvailability(callback? : Callback<MediaLibraryAvailability>):void
```

Unsubscribes to changes of medialibrary availability.

**Since:** 26.0.0

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**Model restriction:** This API can be used only in the stage model.

<!--Device-PhotoAccessHelper-offMediaLibraryAvailability(callback? : Callback<MediaLibraryAvailability>):void--><!--Device-PhotoAccessHelper-offMediaLibraryAvailability(callback? : Callback<MediaLibraryAvailability>):void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MediaLibraryAvailability](arkts-medialibrary-photoaccesshelper-medialibraryavailability-i.md)&gt; | No | Callback used to return the MediaLibraryAvailability. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs. Possible causes:<br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
class MediaLibraryExample {
  private helper: photoAccessHelper.PhotoAccessHelper;
  private handleMediaLibraryChange?: (changeData: photoAccessHelper.MediaLibraryAvailability) => void;

  constructor(context: common.Context) {
    this.helper = photoAccessHelper.getPhotoAccessHelper(context);
  }

  offMediaLibraryAvailability = async () => {
    try {
      this.helper.onMediaLibraryAvailability(this.handleMediaLibraryChange);
      this.helper.offMediaLibraryAvailability(this.handleMediaLibraryChange);
      console.info('Media library listener unregistered successfully');
    } catch (err) {
      console.error(`offMediaLibraryAvailability failed::${(err as BusinessError).code}, ${(err as BusinessError).message} !`);
    }
  };
}
```

## offSinglePhotoAlbumChange

```TypeScript
offSinglePhotoAlbumChange(album?: Album, callback?: Callback<AlbumChangeInfos>): void
```

Unregisters a listener for a single album. Note the following:

1. If no parameter is specified, all listeners for the single albums are unregistered.
2. If **album** is specified but **callback** is not specified, all callback listeners of the album are unregistered.
3. If both **album** and **callback** are specified, only the specified callback listener is unregistered.

**Since:** 23

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-offSinglePhotoAlbumChange(album?: Album, callback?: Callback<AlbumChangeInfos>): void--><!--Device-PhotoAccessHelper-offSinglePhotoAlbumChange(album?: Album, callback?: Callback<AlbumChangeInfos>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| album | [Album](arkts-medialibrary-photoaccesshelper-album-i.md) | No | Album for which the listener is unregistered. After the unregistration is complete, any change to the album is no longer returned through the callback. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | No | Callback used for the unregistration. If this parameter is not specified, all callbacks of the **album** parameter are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Invalid parameter. Possible causes:<br>1.One or two parameters are required; <br>2.Invalid parameter; <br>3.The first parameter is not an object or the second parameter is not a function; <br>4.Object is not a valid object; <br>5.Album object is not a valid object; <br>6.Ordinary album invalid; <br>7.Failed to create callback reference; <br>8.No observer has ever been registered; <br>9.Observer list is empty. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | MediaLibrary inner fail. Possible causes:<br>1.Data service initialization failed, possible causes: 1. Database exception; 2. IPC timeout. Please check if the context is properly initialized and retry <br>2.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}
let onCallback2 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}
let onCallback3 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback3 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onSinglePhotoChangeDemo.');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();

    if (albumFetchResult.isAfterLast()) {
      console.error('lack of album to be moved into');
      return;
    }
    // Register onCallback1.
    phAccessHelper.onSinglePhotoAlbumChange(album, onCallback1);
    // Register onCallback2.
    phAccessHelper.onSinglePhotoAlbumChange(album, onCallback2);
    // Register onCallback3.
    phAccessHelper.onSinglePhotoAlbumChange(album, onCallback3);

    // Unregister onCallback1.
    phAccessHelper.offSinglePhotoAlbumChange(album, onCallback1);
    // Unregister all callbacks of the album.
    phAccessHelper.offSinglePhotoAlbumChange(album);
    // Unregister all listeners of the singlePhotoAlbumChange type.
    phAccessHelper.offSinglePhotoAlbumChange();
  } catch (error) {
    console.error('offSinglePhotoAlbumChangeDemo failed, errCode is', error);
  }
}
```

## offSinglePhotoChange

```TypeScript
offSinglePhotoChange(asset?: PhotoAsset, callback?: Callback<PhotoAssetChangeInfos>): void
```

Unregisters the listener for a single asset. Note the following:

1. If no parameter is specified, all listeners for the single assets are unregistered.
2. If **asset** is specified but **callback** is not specified,
all callback listeners of the **asset** are unregistered.
3. If both **asset** and **callback** are specified, only the specified callback listener is unregistered.

**Since:** 23

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-offSinglePhotoChange(asset?: PhotoAsset, callback?: Callback<PhotoAssetChangeInfos>): void--><!--Device-PhotoAccessHelper-offSinglePhotoChange(asset?: PhotoAsset, callback?: Callback<PhotoAssetChangeInfos>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| asset | [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) | No | Asset for which the listener is canceled. After the unregistration is complete, any change to the **asset** is no longer returned through the **callback**. If this parameter is not specified, all listeners for a single asset are unregistered. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | No | Callback used for the unregistration. If this parameter is not specified, all callbacks of the **asset** parameter are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Invalid parameter. Possible causes:<br>1.The object is not a valid instance; <br>2.The parameter type is invalid; <br>3.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | MediaLibrary inner fail. Possible causes:<br>1.Data service initialization failed, possible causes: 1. Database exception; 2. IPC timeout. Please check if the context is properly initialized and retry <br>2.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}
let onCallback2 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}
let onCallback3 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback3 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onSinglePhotoChangeDemo.');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOptions);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();

    if (albumFetchResult.isAfterLast()) {
      console.error('lack of album to be moved into');
      return;
    }
    // Register onCallback1.
    phAccessHelper.onSinglePhotoChange(asset, onCallback1);
    // Register onCallback2.
    phAccessHelper.onSinglePhotoChange(asset, onCallback2);
    // Register onCallback3.
    phAccessHelper.onSinglePhotoChange(asset, onCallback3);

    // Unregister onCallback1.
    phAccessHelper.offSinglePhotoChange(asset, onCallback1);
    // Unregister all callbacks of the asset.
    phAccessHelper.offSinglePhotoChange(asset);
    // Unregister all listeners of the singlePhotoAssetChange type.
    phAccessHelper.offSinglePhotoChange();
  } catch (error) {
    console.error('offSinglePhotoChangeDemo failed, errCode is', error);
  }
}
```

## on('photoChange')

```TypeScript
on(type: 'photoChange', callback: Callback<PhotoAssetChangeInfos>): void
```

Registers a listener for the **'photoChange'** event to monitor media asset changes. This API uses a callback to return the result, and it accepts multiple callbacks.

**Since:** 20

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-on(type: 'photoChange', callback: Callback<PhotoAssetChangeInfos>): void--><!--Device-PhotoAccessHelper-on(type: 'photoChange', callback: Callback<PhotoAssetChangeInfos>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'photoChange' | Yes | Event type. The value is fixed at **'photoChange'**. After the registration is complete, any change to the media assets is returned through the callback. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | Yes | Callback used to return the media asset information after change, which is [PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md). <br>**NOTE:** <br>You can register multiple listeners using this API, and you can call [off('photoChange')](#offphotochange) to unregister all listeners or a specific one. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Invalid parameter. Possible causes:<br>1.Scenario parameter verification failed; <br>2.Invalid parameter. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | MediaLibrary inner fail. Possible causes:<br>1.Data service initialization failed, possible causes: 1. Database exception; 2. IPC timeout. Please check if the context is properly initialized and retry <br>2.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback1 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback2 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onPhotoChangeDemo.');

  try {
    // Register onCallback1.
    phAccessHelper.on('photoChange', onCallback1);
    // Register onCallback2.
    phAccessHelper.on('photoChange', onCallback2);
  } catch (error) {
    console.error('onPhotoChangeDemo failed, errCode is', error);
  }
}
```

## on('photoAlbumChange')

```TypeScript
on(type: 'photoAlbumChange', callback: Callback<AlbumChangeInfos>): void
```

Registers a listener for the **'photoAlbumChange'** event to monitor album changes. This API uses a callback to return the result, and it accepts multiple callbacks.

**Since:** 20

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-on(type: 'photoAlbumChange', callback: Callback<AlbumChangeInfos>): void--><!--Device-PhotoAccessHelper-on(type: 'photoAlbumChange', callback: Callback<AlbumChangeInfos>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'photoAlbumChange' | Yes | Event type. The value is fixed at **'photoAlbumChange'**. After the registration is complete, any change to the albums is returned through the callback. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | Yes | Callback used to return the album information after change, which is [AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md). <br>**NOTE:** <br>You can register multiple listeners using this API, and you can call [off('photoAlbumChange')](#offphotoalbumchange) to unregister all listeners or a specific one. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Invalid parameter. Possible causes:<br>1.Scenario parameter verification failed; <br>2.Invalid parameter. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | MediaLibrary inner fail. Possible causes:<br>1.Data service initialization failed, possible causes: 1. Database exception; 2. IPC timeout. Please check if the context is properly initialized and retry <br>2.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback1 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback2 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onPhotoAlbumChangeDemo.');

  try {
    // Register onCallback1.
    phAccessHelper.on('photoAlbumChange', onCallback1);
    // Register onCallback2.
    phAccessHelper.on('photoAlbumChange', onCallback2);
  } catch (error) {
    console.error('onPhotoAlbumChangeDemo failed, errCode is', error);
  }
}
```

## onMediaLibraryAvailability

```TypeScript
onMediaLibraryAvailability(callback: Callback<MediaLibraryAvailability>): void
```

Subscribes to changes of medialibrary availability.

**Since:** 26.0.0

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**Model restriction:** This API can be used only in the stage model.

<!--Device-PhotoAccessHelper-onMediaLibraryAvailability(callback: Callback<MediaLibraryAvailability>): void--><!--Device-PhotoAccessHelper-onMediaLibraryAvailability(callback: Callback<MediaLibraryAvailability>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MediaLibraryAvailability](arkts-medialibrary-photoaccesshelper-medialibraryavailability-i.md)&gt; | Yes | Callback used to return the MediaLibraryAvailability. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Scenario-specific parameters are incorrect. Possible causes are as follows:<br>1. The input parameter is null or undefined. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs. Possible causes:<br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
class MediaLibraryExample {
  private helper: photoAccessHelper.PhotoAccessHelper;
  private handleMediaLibraryChange?: (changeData: photoAccessHelper.MediaLibraryAvailability) => void;

  constructor(context: common.Context) {
    this.helper = photoAccessHelper.getPhotoAccessHelper(context);
  }

  onMediaLibraryAvailability = async () => {
    try {
      this.handleMediaLibraryChange = (
        changeData: photoAccessHelper.MediaLibraryAvailability
      ) => {
        const availabilityStatus = changeData.availabilityStatus;
        const unavailabilityReason = changeData.unavailabilityReason;
        console.info(`Media library status change: status=${availabilityStatus}, reason=${unavailabilityReason}`);
      };
      this.helper.onMediaLibraryAvailability(this.handleMediaLibraryChange);
      console.info('Media library listener registered successfully');
    } catch (err) {
      console.error(`onMediaLibraryAvailability failed::${(err as BusinessError).code}, ${(err as BusinessError).message} !`);
    }
  };
}
```

## onSinglePhotoAlbumChange

```TypeScript
onSinglePhotoAlbumChange(album: Album, callback: Callback<AlbumChangeInfos>): void
```

Registers a listener for changes of a single common asset. This API uses an asynchronous callback to return the result.

**Since:** 23

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-onSinglePhotoAlbumChange(album: Album, callback: Callback<AlbumChangeInfos>): void--><!--Device-PhotoAccessHelper-onSinglePhotoAlbumChange(album: Album, callback: Callback<AlbumChangeInfos>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| album | [Album](arkts-medialibrary-photoaccesshelper-album-i.md) | Yes | Album to be listened for. After the registration is complete, any change to the albums is returned through the callback. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | Yes | Callback used to return the album information after change, which is [PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md). <br>**NOTE:** <br>This API can be used to register multiple different callbacks. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Invalid parameter. Possible causes:<br>1.One or two parameters are required; <br>2.Invalid parameter; <br>3.Album object is not a valid object; <br>4.The PhotoAsset is not a valid PhotoAsset object; <br>5.Check whether it is a hidden or recycled album; <br>6.Ordinary album invalid; <br>7.Failed to get URI from photo album; <br>8.Registration has reached the limit (&gt;= 50); <br>9.Failed to create a reference for the callback; <br>10.The listener for this resource has been registered with the same callback. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | MediaLibrary inner fail. Possible causes:<br>1.Data service initialization failed, possible causes: 1. Database exception; 2. IPC timeout. Please check if the context is properly initialized and retry <br>2.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}
let onCallback2 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onSinglePhotoAlbumChangeDemo.');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();

    if (albumFetchResult.isAfterLast()) {
      console.error('lack of album to be moved into');
      return;
    }
    // Register onCallback1.
    phAccessHelper.onSinglePhotoAlbumChange(album, onCallback1);
    // Register onCallback2.
    phAccessHelper.onSinglePhotoAlbumChange(album, onCallback2);
  } catch (error) {
    console.error('onSinglePhotoAlbumChangeDemo failed, errCode is', error);
  }
}
```

## onSinglePhotoChange

```TypeScript
onSinglePhotoChange(asset: PhotoAsset, callback: Callback<PhotoAssetChangeInfos>): void
```

Registers a listener for changes of a single common asset. This API uses an asynchronous callback to return the result.

**Since:** 23

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-onSinglePhotoChange(asset: PhotoAsset, callback: Callback<PhotoAssetChangeInfos>): void--><!--Device-PhotoAccessHelper-onSinglePhotoChange(asset: PhotoAsset, callback: Callback<PhotoAssetChangeInfos>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| asset | [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) | Yes | Asset to be listened for. After the registration is complete, any change to the media assets is returned through the callback. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | Yes | Callback used to return the media asset information after change, which is [PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md). <br>**NOTE:** <br>This API can be used to register multiple different callbacks. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Invalid parameter. Possible causes:<br>1.One or two parameters are required; <br>2.3.The first parameter is not an object or the second parameter is not a function; <br>3.The object is not a valid instance to get asset object; <br>4.The PhotoAsset is not a valid PhotoAsset object; <br>5.Check whether it is a hidden or recycled album; <br>6.Check whether it Iis not a MEDIA_TYPE_IMAGE or MEDIA_TYPE_VIDEO; <br>7.Ordinary assets invalid; <br>8.Registration has reached the limit; <br>9.Failed to create a reference for the callback; <br>10.The listener for this resource has been registered with the same callback; <br>11.Failed to get photo asset from parameter; <br>12.Failed to get file asset instance; <br>13.Failed to get fileId from photo asset. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | MediaLibrary inner fail. Possible causes:<br>1.Data service initialization failed, possible causes: 1. Database exception; 2. IPC timeout. Please check if the context is properly initialized and retry <br>2.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}
let onCallback2 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onSinglePhotoChangeDemo.');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOptions);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();

    if (albumFetchResult.isAfterLast()) {
      console.error('lack of album to be moved into');
      return;
    }
    // Register onCallback1.
    phAccessHelper.onSinglePhotoChange(asset, onCallback1);
    // Register onCallback2.
    phAccessHelper.onSinglePhotoChange(asset, onCallback2);
  } catch (error) {
    console.error('onSinglePhotoChangeDemo failed, errCode is', error);
  }
}
```

## registerChange

```TypeScript
registerChange(uri: string, forChildUris: boolean, callback: Callback<ChangeData>): void
```

Registers listening for the specified URI. This API uses a callback to return the result.

**Since:** 10

<!--Device-PhotoAccessHelper-registerChange(uri: string, forChildUris: boolean, callback: Callback<ChangeData>): void--><!--Device-PhotoAccessHelper-registerChange(uri: string, forChildUris: boolean, callback: Callback<ChangeData>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the photo asset, URI of the album, or [DefaultChangeUri](arkts-medialibrary-photoaccesshelper-defaultchangeuri-e.md). |
| forChildUris | boolean | Yes | Whether to perform fuzzy listening.<br> If **uri** is the URI of an album, the value **true** means to listen for the changes of the files in the album; the value **false** means to listen for the changes of the album only. <br>If **uri** is the URI of a photoAsset, there is no difference between **true** and false for **forChildUris**. <br>If **uri** is **DefaultChangeUri**, **forChildUris** must be set to **true**. If **forChildUris** is false, the URI cannot be found and no message can be received. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ChangeData](arkts-medialibrary-photoaccesshelper-changedata-i.md)&gt; | Yes | Callback used to return [ChangeData](arkts-medialibrary-photoaccesshelper-changedata-i.md). **NOTE:**  Multiple callback listeners can be registered for a URI. You can use [unRegisterChange](#unregisterchange) to unregister all listeners for the URI or a specified callback listener. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| 13900020 | Invalid parameter. Possible causes:<br>1.The number of parameters is invalid, expected 3 parameters; <br>2.The uri parameter must be a string; <br>3.The forChildUris parameter must be a boolean; <br>4.The callback parameter must be a function; <br>5.The uri string extraction failed; <br>6.The forChildUris boolean value extraction failed; <br>7.The callback is already registered for this uri, duplicate registration is not allowed; <br>8.The object is not a valid instance. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('registerChangeDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
  let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
  if (photoAsset !== undefined) {
    console.info('photoAsset.displayName : ' + photoAsset.displayName);
  }
  let onCallback1 = (changeData: photoAccessHelper.ChangeData) => {
      console.info('onCallback1 success, changData: ' + JSON.stringify(changeData));
    // file had changed, do something.
  }
  let onCallback2 = (changeData: photoAccessHelper.ChangeData) => {
      console.info('onCallback2 success, changData: ' + JSON.stringify(changeData));
    // file had changed, do something.
  }
  // Register onCallback1.
  phAccessHelper.registerChange(photoAsset.uri, false, onCallback1);
  // Register onCallback2.
  phAccessHelper.registerChange(photoAsset.uri, false, onCallback2);

  await photoAccessHelper.MediaAssetChangeRequest.deleteAssets(context, [photoAsset]);
}
```

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

Releases the **PhotoAccessHelper** instance. This API uses an asynchronous callback to return the result.

Call this API when the APIs of the PhotoAccessHelper instance are no longer used.

**Since:** 10

<!--Device-PhotoAccessHelper-release(callback: AsyncCallback<void>): void--><!--Device-PhotoAccessHelper-release(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid parameter. Possible causes:<br>1.The number of parameters exceeds the maximum limit; <br>2.The current object is invalid; <br>3.The PhotoAccessHelper object is not a valid object. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.PhotoAccessHelper has been released, no need to release again; <br>2.System internal error, possible causes: 1. Database exception; 2. IPC timeout. Please retry and check logs. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('releaseDemo');
  phAccessHelper.release((err) => {
    if (err !== undefined) {
      console.error(`release failed. error: ${err.code}, ${err.message}`);
    } else {
      console.info('release ok.');
    }
  });
}
```

<a id="release-1"></a>

## release

```TypeScript
release(): Promise<void>
```

Releases the **PhotoAccessHelper** instance. This API uses a promise to return the result.

Call this API when the APIs of the PhotoAccessHelper instance are no longer used.

**Since:** 10

<!--Device-PhotoAccessHelper-release(): Promise<void>--><!--Device-PhotoAccessHelper-release(): Promise<void>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid parameter. Possible causes:<br>1.The number of parameters exceeds the maximum limit; <br>2.The current object is invalid; <br>3.The PhotoAccessHelper object is not a valid object. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.PhotoAccessHelper has been released, no need to release again; <br>2.System internal error, possible causes: 1. Database exception; 2. IPC timeout. Please retry and check logs. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('releaseDemo');
  try {
    await phAccessHelper.release();
    console.info('release ok.');
  } catch (err) {
    console.error(`release failed. error: ${err.code}, ${err.message}`);
  }
}
```

## requestPhotoUrisReadPermission

```TypeScript
requestPhotoUrisReadPermission(srcFileUris: Array<string>): Promise<Array<string>>
```

<!--RP1--><!--RP1End-->Grants the read permission for unauthorized URIs, returning a list of URIs that have been created and granted the permission.

**Since:** 14

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 14.

<!--Device-PhotoAccessHelper-requestPhotoUrisReadPermission(srcFileUris: Array<string>): Promise<Array<string>>--><!--Device-PhotoAccessHelper-requestPhotoUrisReadPermission(srcFileUris: Array<string>): Promise<Array<string>>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| srcFileUris | Array&lt;string&gt; | Yes | [URIs](../../../file-management/user-file-uri-intro.md#media-file-uri) of the images or videos to be granted with the permission. <br>**NOTE:** <br>Only image and video URIs are supported, and the maximum number of URIs is 100. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the URIs granted with the permission. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.Internal error in dialog, please retry; <br>2.Dialog result missing required parameters, system internal error; <br>3.Dialog operation failed, please retry; <br>4.Callback processing failed, system internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('requestPhotoUrisReadPermissionDemo.');

  try {
    // Obtain the URIs of the images or videos to be granted with the permission.
    let srcFileUris: Array<string> = [
      'file://fileUriDemo1' // The URI here is an example only.
    ];
    let desFileUris: Array<string> = await phAccessHelper.requestPhotoUrisReadPermission(srcFileUris);
    console.info('requestPhotoUrisReadPermission success, data is ' + desFileUris);
  } catch (err) {
    console.error('requestPhotoUrisReadPermission failed, errCode is ' + err.code + ', errMsg is ' + err.message);
  }
}
```

## requestPhotoUrisReadPermissionEx

```TypeScript
requestPhotoUrisReadPermissionEx(srcFileUris: Array<string>): Promise<RequestReadPermissionResult>
```

Grants the read permission for unauthorized URIs. This API uses a promise to return the authorization result.

It contains the list of URIs that have been created and granted the save permission and the list of invalid URIs.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-PhotoAccessHelper-requestPhotoUrisReadPermissionEx(srcFileUris: Array<string>): Promise<RequestReadPermissionResult>--><!--Device-PhotoAccessHelper-requestPhotoUrisReadPermissionEx(srcFileUris: Array<string>): Promise<RequestReadPermissionResult>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| srcFileUris | Array&lt;string&gt; | Yes | [URIs](../../../file-management/user-file-uri-intro.md#media-file-uri) of the images or videos to be granted with the permission. <br>**NOTE:** <br>Only image and video URIs are supported, and the maximum number of URIs is 100. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RequestReadPermissionResult](arkts-medialibrary-photoaccesshelper-requestreadpermissionresult-c.md)&gt; | Promise used to return the list of URIs granted with the permission and the list of invalid URIs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs. Possible causes:<br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out; <br>4. This operation is not supported for assets in shared albums. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
console.info('requestPhotoUrisReadPermissionExDemo.');

  try {
    // Obtain the URIs of the images or videos to be granted with the permission.
    let srcFileUris: Array<string> = [
      'file://fileUriDemo1' // The URI here is an example only.
    ];
    let requestReadPermissionResult: photoAccessHelper.RequestReadPermissionResult = await phAccessHelper.requestPhotoUrisReadPermissionEx(srcFileUris);
    console.info('requestPhotoUrisReadPermissionEx success, data is ' + requestReadPermissionResult);
  } catch (err) {
    console.error('requestPhotoUrisReadPermissionEx failed, errCode is ' + err.code + ', errMsg is ' + err.message);
  }
}
```

<a id="setassetcompatiblecapability-1"></a>

## setAssetCompatibleCapability

```TypeScript
setAssetCompatibleCapability(capability: AssetCompatibleCapability): Promise<void>
```

Sets the asset compatibility capability. The system performs compatibility processing on special assets (such as high-resolution assets). If you want to obtain the original assets, you need to register the compatibility capability with the system.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-PhotoAccessHelper-setAssetCompatibleCapability(capability: AssetCompatibleCapability): Promise<void>--><!--Device-PhotoAccessHelper-setAssetCompatibleCapability(capability: AssetCompatibleCapability): Promise<void>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| capability | [AssetCompatibleCapability](arkts-medialibrary-photoaccesshelper-assetcompatiblecapability-i.md) | Yes | Asset compatibility capability. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Invalid parameter. Possible causes:<br>1.The number of parameters is invalid, expected 1 or 2 parameters; <br>2.The bundleName parameter must be a non-empty string; <br>3.The config parameter must be an object; <br>4.The supportedHighResolution attribute must be a boolean; <br>5.The supportedMimeType attribute must be an array of strings; <br>6.The supportedMimeType array contains unsupported MIME types, only image/jpeg and image/png are supported; <br>7.The supportedMimeTypes array size exceeds the limit (max 2 after deduplication); <br>8.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | MediaLibrary inner fail. Possible causes:<br>1.Parameter is not an array type; <br>2.Failed to get array length; <br>3.Server returned an invalid argument error. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let capability : photoAccessHelper.AssetCompatibleCapability = {
        supportedHighResolution : true,
    };
    await phAccessHelper.setAssetCompatibleCapability(capability);
  } catch (error) {
    console.error('failed to setAssetCompatibleCapability err', error);
  }
}
```

## showAssetsCreationDialog

```TypeScript
showAssetsCreationDialog(srcFileUris: Array<string>, photoCreationConfigs: Array<PhotoCreationConfig>): Promise<Array<string>>
```

Displays a dialog box for the user to confirm whether to save the images or videos. If the user agrees to save the images or videos, this API returns a list of URIs that have been created and granted save permissions (this list is permanent), and the application can use these URIs to write the images or videos. If the user declines to save the images or videos, this API returns an empty list.

The dialog box must display the application name, but this cannot be directly obtained. Therefore, before calling this API, ensure that the **label** and **icon** items are configured in the **abilities** tag in the [module.json5 configuration file](../../../quick-start/module-configuration-file.md). Note that the icon is not affected by the **icon** item in the **abilities** tag and cannot be modified.

> **NOTE:** 
> 
> If the passed URI is a sandbox path, images or videos can be saved but cannot be previewed.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PhotoAccessHelper-showAssetsCreationDialog(srcFileUris: Array<string>, photoCreationConfigs: Array<PhotoCreationConfig>): Promise<Array<string>>--><!--Device-PhotoAccessHelper-showAssetsCreationDialog(srcFileUris: Array<string>, photoCreationConfigs: Array<PhotoCreationConfig>): Promise<Array<string>>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| srcFileUris | Array&lt;string&gt; | Yes | [URIs](../../../file-management/user-file-uri-intro.md#media-file-uri) of the images or videos to be saved to the media library. <br>**NOTE:** <br>- A maximum of 100 images can be saved at a time. <br>- Only image and video URIs are supported. <br>- URIs cannot be manually constructed. You must call APIs to obtain them. For details, see [Obtaining a Media File URI](../../../file-management/user-file-uri-intro.md#obtaining-a-media-file-uri). |
| photoCreationConfigs | Array&lt;[PhotoCreationConfig](arkts-medialibrary-photoaccesshelper-photocreationconfig-i.md)&gt; | Yes | Configuration for saving the images or videos, including the file names. The value must be consistent with that of **srcFileUris**.<br>**NOTE:** <br>If a **subtype** option is passed, the configuration does not take effect. Only DEFAULT images can be saved. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return a URI list. The URIs are granted with the permission for the application to write data. If the URIs fail to be generated, a batch creation error code will be returned.<br>The return values are as follows: <br>- **-3006**: Invalid characters, which are not allowed. <br>-**-2004**: The image type does not match the file name extension. <br>-**-203**: Invalid file operation. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('ShowAssetsCreationDialogDemo.');

  try {
    // Obtain the sandbox URIs of the images or videos to be saved to the media library.
    let srcFileUris: Array<string> = [
      'file://fileUriDemo1' // The URI here is an example only.
    ];
    let photoCreationConfigs: Array<photoAccessHelper.PhotoCreationConfig> = [
      {
        title: 'test2', // Optional.
        fileNameExtension: 'jpg',
        photoType: photoAccessHelper.PhotoType.IMAGE,
        subtype: photoAccessHelper.PhotoSubtype.DEFAULT, // This parameter is optional.
      }
    ];
    let desFileUris: Array<string> = await phAccessHelper.showAssetsCreationDialog(srcFileUris, photoCreationConfigs);
    console.info('showAssetsCreationDialog success, data is ' + desFileUris);
  } catch (err) {
    console.error('showAssetsCreationDialog failed, errCode is ' + err.code + ', errMsg is ' + err.message);
  }
}
```

## showAssetsCreationDialogEx

```TypeScript
showAssetsCreationDialogEx(srcFileUris: Array<string>, creationSettings: Array<CreationSetting>): Promise<Array<string>>
```

Displays a dialog box for the user to confirm whether to save the images or videos. This API uses a promise to return the result.

> **NOTE:** 
> 
> - If the user agrees, the list of created URIs with the save permission granted is returned. The list is permanently valid and supports image or video writing. If the user rejects, an empty list is returned.
> 
> - The application name and icon need to be displayed in the dialog box. The name and icon need to be configured in the **label** and **icon** items in the **abilities** tag of the [module.json5 configuration file](../../../quick-start/module-configuration-file.md).
> 
> - When the passed URI is a sandbox path, images or videos can be saved properly, but the preview is not displayed.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-PhotoAccessHelper-showAssetsCreationDialogEx(srcFileUris: Array<string>, creationSettings: Array<CreationSetting>): Promise<Array<string>>--><!--Device-PhotoAccessHelper-showAssetsCreationDialogEx(srcFileUris: Array<string>, creationSettings: Array<CreationSetting>): Promise<Array<string>>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| srcFileUris | Array&lt;string&gt; | Yes | [URIs](../../../file-management/user-file-uri-intro.md#media-file-uri) of the images or videos to be saved to the media library. <br>**NOTE:** <br>- A maximum of 100 images can be saved at a time. <br>- Only image and video URIs are supported. <br>- URIs cannot be manually constructed. You must call APIs to obtain them. For details, see [Obtaining a Media File URI](../../../file-management/user-file-uri-intro.md#obtaining-a-media-file-uri). |
| creationSettings | Array&lt;[CreationSetting](arkts-medialibrary-photoaccesshelper-creationsetting-i.md)&gt; | Yes | Configuration for saving images or videos to the media library, including the file name. The URI in this parameter must correspond to that in the **srcFileUris** parameter. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return a URI list. The application can use the returned URI to write data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | MediaLibrary inner fail. Possible causes:<br>1.Internal error in dialog, please retry; <br>2.Dialog result missing required parameters, system internal error; <br>3.Callback processing failed, system internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) { 
  console.info('ShowAssetsCreationDialogExDemo.'); 

  try {
    // Obtain the sandbox URIs of the images or videos to be saved to the media library.
    let srcFileUris: Array<string> = [
      'file://fileUriDemo1' // The URI here is an example only.
    ];
    let photoCreationConfigs: Array<photoAccessHelper.CreationSetting> = [
      {
        title: 'test2', // Optional.
        fileNameExtension: 'jpg',
        photoType: photoAccessHelper.PhotoType.IMAGE
      }
    ];
    let desFileUris: Array<string> = await phAccessHelper.showAssetsCreationDialogEx(srcFileUris, photoCreationConfigs);
    console.info('showAssetsCreationDialogEx success, data is ' + desFileUris);
  } catch (err) {
    console.error('showAssetsCreationDialogEx failed, errCode is ' + err.code + ', errMsg is ' + err.message);
  }
}
```

## showSingleAssetCreationDialogEx

```TypeScript
showSingleAssetCreationDialogEx(srcFileUri: string, creationSetting: CreationSetting, isImageFullyDisplayed: boolean): Promise<string>
```

Displays a dialog box for the user to confirm whether to save an image or video. This API uses a promise to return the result.

> **NOTE:** 
> 
> - If the user agrees to save the images or videos, this API returns a URI that has been created and granted with the save permission (this URI is permanent), and the application can use this URI to write the image or video. If the user declines to save the image or video, this API returns an empty string.
> 
> - The dialog box must display the application name, but this cannot be directly obtained. Therefore, before calling this API, ensure that the **label** and **icon** items are configured in the **abilities** tag in the [module.json5 configuration file](../../../quick-start/module-configuration-file.md). Note that the icon is not affected by the **icon** item in the **abilities** tag and cannot be modified.
> 
> - If the passed URI is a sandbox path, images or videos can be saved but cannot be previewed.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-PhotoAccessHelper-showSingleAssetCreationDialogEx(srcFileUri: string, creationSetting: CreationSetting, isImageFullyDisplayed: boolean): Promise<string>--><!--Device-PhotoAccessHelper-showSingleAssetCreationDialogEx(srcFileUri: string, creationSetting: CreationSetting, isImageFullyDisplayed: boolean): Promise<string>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| srcFileUri | string | Yes | [URIs](../../../file-management/user-file-uri-intro.md#media-file-uri) of the images or videos to be saved to the media library. <br>**NOTE:** <br>- Only one image can be saved at a time. <br>- Only image and video URIs are supported. <br>- URIs cannot be manually constructed. You must call APIs to obtain them. For details, see [Obtaining a Media File URI](../../../file-management/user-file-uri-intro.md#obtaining-a-media-file-uri). |
| creationSetting | [CreationSetting](arkts-medialibrary-photoaccesshelper-creationsetting-i.md) | Yes | Configuration for saving the image or video, including the file name. The value must be consistent with that of **srcFileUri **. |
| isImageFullyDisplayed | boolean | Yes | Whether the image is displayed completely. The value **true** indicates that the image is displayed completely, and **false** indicates the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the URI of the media library file to the application. The URIs are granted with the permission for the application to write data. If the URIs fail to be generated, a batch creation error code will be returned.<br>The return values are as follows: <br>- **-3006**: Invalid characters, which are not allowed. <br>-**-2004**: The image type does not match the file name extension. <br>-**-203**: Invalid file operation. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | MediaLibrary inner fail. Possible causes:<br>1.Internal error in dialog, please retry; <br>2.Dialog result missing required parameters, system internal error; <br>3.Callback processing failed, system internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('ShowSingleAssetCreationDialogExDemo.');

  try {
    // Obtain the sandbox URIs of the images or videos to be saved to the media library.
    let srcFileUri: string = 'file://fileUriDemo1'; // The URI here is an example only.
    let photoCreationConfig: photoAccessHelper.CreationSetting = {
      title: 'test2', // Optional.
      fileNameExtension: 'jpg',
      photoType: photoAccessHelper.PhotoType.IMAGE
    }
    let isImageFullyDisplayed: boolean = true
    let desFileUri: string = await phAccessHelper.showSingleAssetCreationDialogEx(srcFileUri, photoCreationConfig, isImageFullyDisplayed);
    console.info('showSingleAssetCreationDialogEx success, data is ' + desFileUri);
  } catch (err) {
    console.error('showSingleAssetCreationDialogEx failed, errCode is ' + err.code + ', errMsg is ' + err.message);
  }
}
```

## unRegisterChange

```TypeScript
unRegisterChange(uri: string, callback?: Callback<ChangeData>): void
```

Unregisters listening for the specified URI. Multiple callbacks can be registered for a URI for listening. You can use this API to unregister the listening of the specified callbacks or all callbacks.

**Since:** 10

<!--Device-PhotoAccessHelper-unRegisterChange(uri: string, callback?: Callback<ChangeData>): void--><!--Device-PhotoAccessHelper-unRegisterChange(uri: string, callback?: Callback<ChangeData>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the photo asset, URI of the album, or [DefaultChangeUri](arkts-medialibrary-photoaccesshelper-defaultchangeuri-e.md). |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ChangeData](arkts-medialibrary-photoaccesshelper-changedata-i.md)&gt; | No | Callback to unregister. If this parameter is not specified, all the callbacks for listening for the URI will be canceled. **NOTE:**  The specified callback unregistered will not be invoked when the data changes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| 13900020 | Invalid parameter. Possible causes:<br>1.The number of parameters is invalid, expected 1 or 2 parameters; <br>2.The uri parameter must be a string; <br>3.The uri string extraction failed; <br>4.The callback parameter must be a function; <br>5.The object is not a valid instance. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('offDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
  let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
  if (photoAsset !== undefined) {
    console.info('photoAsset.displayName : ' + photoAsset.displayName);
  }
  let onCallback1 = (changeData: photoAccessHelper.ChangeData) => {
    console.info('onCallback1 on');
  }
  let onCallback2 = (changeData: photoAccessHelper.ChangeData) => {
    console.info('onCallback2 on');
  }
  // Register onCallback1.
  phAccessHelper.registerChange(photoAsset.uri, false, onCallback1);
  // Register onCallback2.
  phAccessHelper.registerChange(photoAsset.uri, false, onCallback2);
  // Unregister the listening of onCallback1.
  phAccessHelper.unRegisterChange(photoAsset.uri, onCallback1);
  await photoAccessHelper.MediaAssetChangeRequest.deleteAssets(context, [photoAsset]);
}
```

## createDeleteRequest

```TypeScript
createDeleteRequest(uriList: Array<string>, callback: AsyncCallback<void>): void
```

Creates a dialog box for deleting media files. This API uses an asynchronous callback to return the result. The deleted media files are moved to the trash.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [deleteAssets](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md#deleteassets)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-createDeleteRequest(uriList: Array<string>, callback: AsyncCallback<void>): void--><!--Device-PhotoAccessHelper-createDeleteRequest(uriList: Array<string>, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uriList | Array&lt;string&gt; | Yes | URIs of the media files to delete. A maximum of 300 media files can be deleted. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied. Possible causes:<br>1.Not have ohos.permission.WRITE_IMAGEVIDEO; <br>2.User deny. |
| 13900020 | Invalid parameter. Possible causes:<br>1.The context parameter is invalid, failed to convert to AbilityContext; <br>2.Failed to create the dialog, system internal error, please retry. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The delete operation failed, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs; <br>2.The uriList parameter contains invalid URIs, please check if each URI is a valid file URI obtained from a valid query result; <br>3.The UI extension component reported an error, please retry. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createDeleteRequestDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('asset not exist');
      return;
    }
    phAccessHelper.createDeleteRequest([asset.uri], (err) => {
      if (err === undefined) {
        console.info('createDeleteRequest successfully');
      } else {
        console.error(`createDeleteRequest failed with error: ${err.code}, ${err.message}`);
      }
    });
  } catch (err) {
    console.error(`fetch failed, error: ${err.code}, ${err.message}`);
  }
}
```

<a id="createdeleterequest-1"></a>

## createDeleteRequest

```TypeScript
createDeleteRequest(uriList: Array<string>): Promise<void>
```

Creates a dialog box for deleting media files. This API uses a promise to return the result. The deleted media files are moved to the trash.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [deleteAssets](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md#deleteassets)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-createDeleteRequest(uriList: Array<string>): Promise<void>--><!--Device-PhotoAccessHelper-createDeleteRequest(uriList: Array<string>): Promise<void>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uriList | Array&lt;string&gt; | Yes | URIs of the media files to delete. A maximum of 300 media files can be deleted. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied. Possible causes:<br>1.Not have ohos.permission.WRITE_IMAGEVIDEO; <br>2.User deny. |
| 13900020 | Invalid parameter. Possible causes:<br>1.The context parameter is invalid, failed to convert to AbilityContext; <br>2.Failed to create the dialog, system internal error, please retry. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The delete operation failed, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs; <br>2.The uriList parameter contains invalid URIs, please check if each URI is a valid file URI obtained from a valid query result; <br>3.The UI extension component reported an error, please retry. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createDeleteRequestDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('asset not exist');
      return;
    }
    await phAccessHelper.createDeleteRequest([asset.uri]);
    console.info('createDeleteRequest successfully');
  } catch (err) {
    console.error(`createDeleteRequest failed with error: ${err.code}, ${err.message}`);
  }
}
```
