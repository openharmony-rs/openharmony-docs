# AudioSuiteDownloadManager (System API)

```TypeScript
interface AudioSuiteDownloadManager
```

Provides the capability of downloading and managing the audio editing feature, including starting, pausing, Cancel the download, status query, and uninstallation functions.

**Since:** 26.0.1

<!--Device-audio-interface AudioSuiteDownloadManager--><!--Device-audio-interface AudioSuiteDownloadManager-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## cancelDownload

```TypeScript
cancelDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>
```

Cancel the download of a specified feature. Use Promise asynchronous callbacks. Should be in the characteristic state [DOWNLOADING](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#downloading) or This interface is invoked when DOWNLOAD_PAUTE is invoked, After this function is invoked, the status changes to [VERSION_CHECK_SUCCEEDED](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#version_check_succeeded).

When the feature status is not [DOWNLOADING](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#downloading) or DOWNLOAD_PAUTE This interface is invoked. A success response is returned and the original status remains unchanged.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteDownloadManager-cancelDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>--><!--Device-AudioSuiteDownloadManager-cancelDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | Yes | The type of property to cancel. <br>The maximum length is 5. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise object. No result is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. The value of featureTypes is invalid. |
| [6800302](../errorcode-audio.md#6800302-system-service-process-terminated) | System service process terminated. |

## getFeatureStatus

```TypeScript
getFeatureStatus(featureTypes: Array<AudioSuiteFeatureType>): Promise<AudioSuiteFeatureStatusInfoArray>
```

Obtain the status of a specified feature. Use Promise asynchronous callback.

This interface is used to query the local installation status of a feature and does not depend on the network environment.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteDownloadManager-getFeatureStatus(featureTypes: Array<AudioSuiteFeatureType>): Promise<AudioSuiteFeatureStatusInfoArray>--><!--Device-AudioSuiteDownloadManager-getFeatureStatus(featureTypes: Array<AudioSuiteFeatureType>): Promise<AudioSuiteFeatureStatusInfoArray>-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | Yes | Types of the features to query. <br>The maximum length is 5. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AudioSuiteFeatureStatusInfoArray](arkts-audio-audio-audiosuitefeaturestatusinfoarray-t-sys.md)&gt; | Promise object, which returns an array of attribute states. Each element corresponds to a feature at the same index in featureTypes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. The value of featureTypes is invalid. |
| [6800302](../errorcode-audio.md#6800302-system-service-process-terminated) | System service process terminated. |

## getNewVersionInfo

```TypeScript
getNewVersionInfo(featureTypes: Array<AudioSuiteFeatureType>): Promise<Array<AudioSuiteFeatureVersionInfo>>
```

Obtain the latest version of a specified feature. Use Promise asynchronous callback.

Before calling this API, ensure that the device is connected to an available network.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteDownloadManager-getNewVersionInfo(featureTypes: Array<AudioSuiteFeatureType>): Promise<Array<AudioSuiteFeatureVersionInfo>>--><!--Device-AudioSuiteDownloadManager-getNewVersionInfo(featureTypes: Array<AudioSuiteFeatureType>): Promise<Array<AudioSuiteFeatureVersionInfo>>-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | Yes | Types of the features to query. <br>The maximum length is 5. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AudioSuiteFeatureVersionInfo](arkts-audio-audio-audiosuitefeatureversioninfo-i-sys.md)&gt;&gt; | Promise used to return the version info array. Each element corresponds to the feature at the same index in featureTypes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. The value of featureTypes is invalid. |
| [6800302](../errorcode-audio.md#6800302-system-service-process-terminated) | System service process terminated. |
| [6800501](../errorcode-audio.md#6800501-network-conditions-not-met) | Required network conditions not met. The current network status is unavailable. |

## isFeatureInstalled

```TypeScript
isFeatureInstalled(featureTypes: Array<AudioSuiteFeatureType>): Promise<Array<boolean>>
```

Obtains whether a specified feature has been installed. Use Promise asynchronous callback.

This interface is used to query the local installation status of a feature and does not depend on the network environment.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteDownloadManager-isFeatureInstalled(featureTypes: Array<AudioSuiteFeatureType>): Promise<Array<boolean>>--><!--Device-AudioSuiteDownloadManager-isFeatureInstalled(featureTypes: Array<AudioSuiteFeatureType>): Promise<Array<boolean>>-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | Yes | Types of the features to query. <br>The maximum length is 5. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;boolean&gt;&gt; | Promise used to return the install status array. Each element corresponds to the feature at the same index in featureTypes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. The value of featureTypes is invalid. |
| [6800302](../errorcode-audio.md#6800302-system-service-process-terminated) | System service process terminated. |

## offDownloadStatusChange

```TypeScript
offDownloadStatusChange(callback?: Callback<AudioSuiteFeatureStatusInfoArray>): void
```

Unsubscribe from the download status change event. After you cancel the callback, the system does not trigger the callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteDownloadManager-offDownloadStatusChange(callback?: Callback<AudioSuiteFeatureStatusInfoArray>): void--><!--Device-AudioSuiteDownloadManager-offDownloadStatusChange(callback?: Callback<AudioSuiteFeatureStatusInfoArray>): void-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSuiteFeatureStatusInfoArray](arkts-audio-audio-audiosuitefeaturestatusinfoarray-t-sys.md)&gt; | No | Callback function to be canceled, The default value is null. If this parameter is not set, all callbacks that have been subscribed to in the current process are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [6800302](../errorcode-audio.md#6800302-system-service-process-terminated) | System service process terminated. |

## onDownloadStatusChange

```TypeScript
onDownloadStatusChange(callback: Callback<AudioSuiteFeatureStatusInfoArray>): void
```

Subscribe to download status change events. When the download status or progress of any feature changes, the subscription callback is triggered.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteDownloadManager-onDownloadStatusChange(callback: Callback<AudioSuiteFeatureStatusInfoArray>): void--><!--Device-AudioSuiteDownloadManager-onDownloadStatusChange(callback: Callback<AudioSuiteFeatureStatusInfoArray>): void-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSuiteFeatureStatusInfoArray](arkts-audio-audio-audiosuitefeaturestatusinfoarray-t-sys.md)&gt; | Yes | Callback function, which is used to return the array of changed download status information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [6800302](../errorcode-audio.md#6800302-system-service-process-terminated) | System service process terminated. |

## pauseDownload

```TypeScript
pauseDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>
```

Pause the download of a specified feature. Use Promise asynchronous callback. Should be called after the property state is [DOWNLOADING](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#downloading), After this function is invoked, the status changes to [DOWNLOAD_PAUSED](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#download_paused).

If this interface is invoked when the feature status is not [DOWNLOADING](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#downloading), a success message is returned and the original status remains unchanged.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteDownloadManager-pauseDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>--><!--Device-AudioSuiteDownloadManager-pauseDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | Yes | Types of the features to pause. <br>The maximum length is 5. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise object. No result is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. The value of featureTypes is invalid. |
| [6800302](../errorcode-audio.md#6800302-system-service-process-terminated) | System service process terminated. |

## startBackgroundDownload

```TypeScript
startBackgroundDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>
```

Start the background download feature. Use Promise asynchronous callbacks. If the current network condition is Wi-Fi, the system audio service will directly download the feature. If a non-Wi-Fi network, the system audio service automatically downloads after switching to a Wi-Fi network. It can be called in any [AudioSuiteFeatureStatus](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md) state. After the client process exits, the system audio service continuously listens to the network environment until the task is downloaded successfully.

The interface returns a message after the command is sent. During the download, the download progress can be obtained through the download status change event subscribed by [onDownloadStatusChange](#ondownloadstatuschange).

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteDownloadManager-startBackgroundDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>--><!--Device-AudioSuiteDownloadManager-startBackgroundDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | Yes | The type of feature to download. <br>The maximum length is 5. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise object. No result is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. The value of featureTypes is invalid. |
| [6800302](../errorcode-audio.md#6800302-system-service-process-terminated) | System service process terminated. |

## startDownload

```TypeScript
startDownload(featureTypes: Array<AudioSuiteFeatureType>, networkType: NetworkType): Promise<void>
```

Start downloading features based on the specified network. Use Promise asynchronous callbacks. Invoke [getNewVersionInfo](#getnewversioninfo) to query the new version. The query is successful and the status changes to This interface is invoked after [VERSION_CHECK_SUCCEEDED](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#version_check_succeeded), Alternatively, in the [DOWNLOAD_PAUSED](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#download_paused) state, invoke this interface to continue the download, After this function is invoked, the status changes to [DOWNLOADING](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#downloading). After the download is successful, the system automatically enters the [INSTALLING](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#installing) state.

The interface is returned after the download starts. During the download, you can use the [onDownloadStatusChange](#ondownloadstatuschange) Obtains the download progress of the subscribed download status change event.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteDownloadManager-startDownload(featureTypes: Array<AudioSuiteFeatureType>, networkType: NetworkType): Promise<void>--><!--Device-AudioSuiteDownloadManager-startDownload(featureTypes: Array<AudioSuiteFeatureType>, networkType: NetworkType): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | Yes | Types of the features to download. <br>The maximum length is 5. |
| networkType | [NetworkType](arkts-audio-audio-networktype-e-sys.md) | Yes | Network type for downloading. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. The value of featureTypes is invalid. |
| [6800302](../errorcode-audio.md#6800302-system-service-process-terminated) | System service process terminated. |
| [6800501](../errorcode-audio.md#6800501-network-conditions-not-met) | Required network conditions not met. The current network conditions do not match the type specified by networkType. |
| [6800502](../errorcode-audio.md#6800502-insufficient-storage-space) | Insufficient storage space. |

## uninstallFeature

```TypeScript
uninstallFeature(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>
```

Uninstall downloaded features. Use Promise asynchronous callbacks. Should be called after the property state is [INSTALLATION_SUCCEEDED](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#installation_succeeded), If the status changes to [UNINSTALLING](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#uninstalling), the uninstallation starts.

This interface is invoked when the feature status is not [INSTALLATION_SUCCEEDED](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#installation_succeeded), The interface returns a success message and retains the original status.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteDownloadManager-uninstallFeature(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>--><!--Device-AudioSuiteDownloadManager-uninstallFeature(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | Yes | The property type to unload. <br>The maximum length is 5. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise object. No result is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. The value of featureTypes is invalid. |
| [6800302](../errorcode-audio.md#6800302-system-service-process-terminated) | System service process terminated. |
