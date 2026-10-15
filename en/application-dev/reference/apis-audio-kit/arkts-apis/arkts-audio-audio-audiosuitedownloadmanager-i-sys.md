# AudioSuiteDownloadManager (System API)

```TypeScript
interface AudioSuiteDownloadManager
```

Provides audio suite download management capabilities, including starting, pausing, canceling downloads, querying status, and uninstalling features.

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

Cancels the download of a specified feature. It should be called when the feature state is [DOWNLOADING](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#downloading) or DOWNLOAD_PAUSE. After this function is called, the state changes to [VERSION_CHECK_SUCCEEDED](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#version_check_succeeded).

If the interface is invoked when the interface is not in the valid state, the interface directly returns and retains the original state.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteDownloadManager-cancelDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>--><!--Device-AudioSuiteDownloadManager-cancelDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | Yes | Types of the features to cancel.<br>The maximum length is 5. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. The value of featureTypes is invalid. |
| 6800302 | System service process terminated. |

## getFeatureStatus

```TypeScript
getFeatureStatus(featureTypes: Array<AudioSuiteFeatureType>): Promise<AudioSuiteFeatureStatusInfoArray>
```

Obtains the status of a specified feature. This API uses a promise to return the result.

This interface is used only to query the local installation status of a feature and is not connected to the network.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteDownloadManager-getFeatureStatus(featureTypes: Array<AudioSuiteFeatureType>): Promise<AudioSuiteFeatureStatusInfoArray>--><!--Device-AudioSuiteDownloadManager-getFeatureStatus(featureTypes: Array<AudioSuiteFeatureType>): Promise<AudioSuiteFeatureStatusInfoArray>-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | Yes | Types of the features to query.<br>The maximum length is 5. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AudioSuiteFeatureStatusInfoArray](arkts-audio-audio-audiosuitefeaturestatusinfoarray-t-sys.md)&gt; | Promise used to return the feature status array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. The value of featureTypes is invalid. |
| 6800302 | System service process terminated. |

## getNewVersionInfo

```TypeScript
getNewVersionInfo(featureTypes: Array<AudioSuiteFeatureType>): Promise<Array<AudioSuiteFeatureVersionInfo>>
```

Obtains the latest version information of a specified feature. This API uses a promise to return the result.

This interface queries information through the network.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteDownloadManager-getNewVersionInfo(featureTypes: Array<AudioSuiteFeatureType>): Promise<Array<AudioSuiteFeatureVersionInfo>>--><!--Device-AudioSuiteDownloadManager-getNewVersionInfo(featureTypes: Array<AudioSuiteFeatureType>): Promise<Array<AudioSuiteFeatureVersionInfo>>-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | Yes | Types of the features to query.<br>The maximum length is 5. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AudioSuiteFeatureVersionInfo](arkts-audio-audio-audiosuitefeatureversioninfo-i-sys.md)&gt;&gt; | Promise used to return the version info array. Each element corresponds to the feature at the same index in featureTypes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. The value of featureTypes is invalid. |
| 6800302 | System service process terminated. |
| 6800501 | Required network conditions not met. The current network status is unavailable. |

## isFeatureInstalled

```TypeScript
isFeatureInstalled(featureTypes: Array<AudioSuiteFeatureType>): Promise<Array<boolean>>
```

Obtains whether a specified feature has been installed. This API uses a promise to return the result.

This interface is used only to query the local installation status of a feature and is not connected to the network.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteDownloadManager-isFeatureInstalled(featureTypes: Array<AudioSuiteFeatureType>): Promise<Array<boolean>>--><!--Device-AudioSuiteDownloadManager-isFeatureInstalled(featureTypes: Array<AudioSuiteFeatureType>): Promise<Array<boolean>>-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | Yes | Types of the features to query.<br>The maximum length is 5. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;boolean&gt;&gt; | Promise used to return the install status array. Each element corresponds to the feature at the same index in featureTypes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. The value of featureTypes is invalid. |
| 6800302 | System service process terminated. |

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
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSuiteFeatureStatusInfoArray](arkts-audio-audio-audiosuitefeaturestatusinfoarray-t-sys.md)&gt; | No | Callback to be unsubscribed.<br>If the callback parameter is not transferred, all subscriptions are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| 6800302 | System service process terminated. |

## onDownloadStatusChange

```TypeScript
onDownloadStatusChange(callback: Callback<AudioSuiteFeatureStatusInfoArray>): void
```

Subscribes to download status change event. When the download status of any feature module changes, the subscription callback is triggered.

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
| 6800302 | System service process terminated. |

## pauseDownload

```TypeScript
pauseDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>
```

Pauses the download of a specified feature. This function is called after the feature status is [DOWNLOADING](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#downloading). After this function is called, the status changes to DOWNLOAD_PAUSE.

If the interface is invoked when the interface is not in the valid state, the interface directly returns and retains the original state.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteDownloadManager-pauseDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>--><!--Device-AudioSuiteDownloadManager-pauseDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | Yes | Types of the features to pause.<br>The maximum length is 5. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. The value of featureTypes is invalid. |
| 6800302 | System service process terminated. |

## startBackgroundDownload

```TypeScript
startBackgroundDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>
```

Start the background download feature. If the current network condition is Wi-Fi: The feature will be downloaded directly. If it is not a Wi-Fi network, the system audio service automatically downloads after switching to the Wi-Fi network. It can be called in any [AudioSuiteFeatureStatus](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md) state. After the client process exits, the system audio service continuously listens to the network environment until the task is downloaded successfully.

The interface returns a message after sending a command. During the download, you can obtain the download progress through the [onDownloadStatusChange](#ondownloadstatuschange) subscribed download status change event.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteDownloadManager-startBackgroundDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>--><!--Device-AudioSuiteDownloadManager-startBackgroundDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | Yes | Types of the features to download.<br>The maximum length is 5. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. The value of featureTypes is invalid. |
| 6800302 | System service process terminated. |

## startDownload

```TypeScript
startDownload(featureTypes: Array<AudioSuiteFeatureType>, networkType: NetworkType): Promise<void>
```

Start downloading features based on the specified network. This interface must be called after the feature status changes to [VERSION_CHECK_SUCCEEDED](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#version_check_succeeded) after the package search succeeds in invoking [getNewVersionInfo](#getnewversioninfo) is called. After this interface is called, the feature status changes to [DOWNLOADING](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#downloading).

The interface returns after the download starts. During the download, you can obtain the download progress through the [onDownloadStatusChange](#ondownloadstatuschange) subscribed download status change event.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteDownloadManager-startDownload(featureTypes: Array<AudioSuiteFeatureType>, networkType: NetworkType): Promise<void>--><!--Device-AudioSuiteDownloadManager-startDownload(featureTypes: Array<AudioSuiteFeatureType>, networkType: NetworkType): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | Yes | Types of the features to download.<br>The maximum length is 5. |
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
| 6800302 | System service process terminated. |
| 6800501 | Required network conditions not met. The current network conditions do not match the type specified by networkType. |
| 6800502 | Insufficient storage space. |

## uninstallFeature

```TypeScript
uninstallFeature(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>
```

Uninstall the downloaded features. This function should be called after the feature status is [INSTALLATION_SUCCEEDED](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#installation_succeeded). After this function is called, the status changes to [UNINSTALLING](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#uninstalling).

If the interface is invoked when the interface is not in the valid state, the interface directly returns and retains the original state.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteDownloadManager-uninstallFeature(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>--><!--Device-AudioSuiteDownloadManager-uninstallFeature(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | Yes | Types of the features to uninstall.<br>The maximum length is 5. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. The value of featureTypes is invalid. |
| 6800302 | Audio client call audio service error. |
