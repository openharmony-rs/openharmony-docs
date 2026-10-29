# AudioSuiteDownloadManager（系统接口）

```TypeScript
interface AudioSuiteDownloadManager
```

提供音频编创特性下载管理能力，包括启动、暂停、取消下载、查询状态、卸载特性功能。

**起始版本：** 26.0.1

<!--Device-audio-interface AudioSuiteDownloadManager--><!--Device-audio-interface AudioSuiteDownloadManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## cancelDownload

```TypeScript
cancelDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>
```

取消下载指定特性。使用Promise异步回调。应在特性状态为[DOWNLOADING](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#downloading)或[DOWNLOAD_PAUSED](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#download_paused)时调用，调用后状态会变为[VERSION_CHECK_SUCCEEDED](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#version_check_succeeded)。

当特性状态不为[DOWNLOADING](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#downloading)或[DOWNLOAD_PAUSED](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#download_paused)时调用本接口，接口会返回成功，保持原有状态不变。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSuiteDownloadManager-cancelDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>--><!--Device-AudioSuiteDownloadManager-cancelDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | 是 | 要取消的特性类型。最大长度为5。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. The value of featureTypes is invalid. |
| [6800302](../errorcode-audio.md#6800302-系统服务进程终止) | System service process terminated. |

## getFeatureStatus

```TypeScript
getFeatureStatus(featureTypes: Array<AudioSuiteFeatureType>): Promise<AudioSuiteFeatureStatusInfoArray>
```

获取指定特性的状态。使用Promise异步回调。

此接口仅基于特性本地安装状态查询，不依赖网络环境。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSuiteDownloadManager-getFeatureStatus(featureTypes: Array<AudioSuiteFeatureType>): Promise<AudioSuiteFeatureStatusInfoArray>--><!--Device-AudioSuiteDownloadManager-getFeatureStatus(featureTypes: Array<AudioSuiteFeatureType>): Promise<AudioSuiteFeatureStatusInfoArray>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | 是 | 要查询的特性类型。最大长度为5。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioSuiteFeatureStatusInfoArray](arkts-audio-audio-audiosuitefeaturestatusinfoarray-t-sys.md)&gt; | Promise对象，返回特性状态数组。每个元素对应于featureTypes中相同索引处的特性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. The value of featureTypes is invalid. |
| [6800302](../errorcode-audio.md#6800302-系统服务进程终止) | System service process terminated. |

## getNewVersionInfo

```TypeScript
getNewVersionInfo(featureTypes: Array<AudioSuiteFeatureType>): Promise<Array<AudioSuiteFeatureVersionInfo>>
```

获取指定特性的最新版本信息。使用Promise异步回调。

调用此接口前，需确保设备已连接可用网络。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSuiteDownloadManager-getNewVersionInfo(featureTypes: Array<AudioSuiteFeatureType>): Promise<Array<AudioSuiteFeatureVersionInfo>>--><!--Device-AudioSuiteDownloadManager-getNewVersionInfo(featureTypes: Array<AudioSuiteFeatureType>): Promise<Array<AudioSuiteFeatureVersionInfo>>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | 是 | 要查询的特性类型。最大长度为5。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[AudioSuiteFeatureVersionInfo](arkts-audio-audio-audiosuitefeatureversioninfo-i-sys.md)&gt;&gt; | Promise对象，返回版本信息数组。每个元素对应于featureTypes中相同索引处的特性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. The value of featureTypes is invalid. |
| [6800302](../errorcode-audio.md#6800302-系统服务进程终止) | System service process terminated. |
| [6800501](../errorcode-audio.md#6800501-网络条件不满足) | Required network conditions not met. The current network status is unavailable. |

## isFeatureInstalled

```TypeScript
isFeatureInstalled(featureTypes: Array<AudioSuiteFeatureType>): Promise<Array<boolean>>
```

获取指定特性是否已安装。使用Promise异步回调。

此接口仅基于特性本地安装状态查询，不依赖网络环境。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSuiteDownloadManager-isFeatureInstalled(featureTypes: Array<AudioSuiteFeatureType>): Promise<Array<boolean>>--><!--Device-AudioSuiteDownloadManager-isFeatureInstalled(featureTypes: Array<AudioSuiteFeatureType>): Promise<Array<boolean>>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | 是 | 要查询的特性类型。最大长度为5。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;boolean&gt;&gt; | Promise对象，返回安装状态数组。每个元素对应于featureTypes中相同索引处的特性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. The value of featureTypes is invalid. |
| [6800302](../errorcode-audio.md#6800302-系统服务进程终止) | System service process terminated. |

## offDownloadStatusChange

```TypeScript
offDownloadStatusChange(callback?: Callback<AudioSuiteFeatureStatusInfoArray>): void
```

取消订阅下载状态变化事件。取消后，系统将不再触发回调。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSuiteDownloadManager-offDownloadStatusChange(callback?: Callback<AudioSuiteFeatureStatusInfoArray>): void--><!--Device-AudioSuiteDownloadManager-offDownloadStatusChange(callback?: Callback<AudioSuiteFeatureStatusInfoArray>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSuiteFeatureStatusInfoArray](arkts-audio-audio-audiosuitefeaturestatusinfoarray-t-sys.md)&gt; | 否 | 需要取消的回调函数，默认值为空。若不设置此参数值，则取消之前在当前进程中订阅的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [6800302](../errorcode-audio.md#6800302-系统服务进程终止) | System service process terminated. |

## onDownloadStatusChange

```TypeScript
onDownloadStatusChange(callback: Callback<AudioSuiteFeatureStatusInfoArray>): void
```

订阅下载状态变化事件。当任一特性的下载状态、下载进度发生变化时，会触发订阅的回调。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSuiteDownloadManager-onDownloadStatusChange(callback: Callback<AudioSuiteFeatureStatusInfoArray>): void--><!--Device-AudioSuiteDownloadManager-onDownloadStatusChange(callback: Callback<AudioSuiteFeatureStatusInfoArray>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSuiteFeatureStatusInfoArray](arkts-audio-audio-audiosuitefeaturestatusinfoarray-t-sys.md)&gt; | 是 | 回调函数，返回变化后的下载状态变化信息数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [6800302](../errorcode-audio.md#6800302-系统服务进程终止) | System service process terminated. |

## pauseDownload

```TypeScript
pauseDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>
```

暂停下载指定特性。使用Promise异步回调。应在特性状态为[DOWNLOADING](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#downloading)后调用，调用后状态会变为[DOWNLOAD_PAUSED](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#download_paused)。

当特性状态不为[DOWNLOADING](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#downloading)时调用本接口，接口会返回成功，保持原有状态不变。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSuiteDownloadManager-pauseDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>--><!--Device-AudioSuiteDownloadManager-pauseDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | 是 | 要暂停的特性类型。最大长度为5。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. The value of featureTypes is invalid. |
| [6800302](../errorcode-audio.md#6800302-系统服务进程终止) | System service process terminated. |

## startBackgroundDownload

```TypeScript
startBackgroundDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>
```

开始后台下载特性。使用Promise异步回调。如果当前网络条件为Wi-Fi网络场景，系统音频服务会直接下载特性；如果非Wi-Fi网络，系统音频服务会在切换到Wi-Fi网络后自动进行下载。可以在任意[AudioSuiteFeatureStatus](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md)状态调用。客户端进程退出后，系统音频服务会持续监听网络环境直到任务下载成功。

接口在发送命令后就返回，下载过程中可以通过[onDownloadStatusChange](#ondownloadstatuschange)订阅的下载状态变化事件获取下载进度。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSuiteDownloadManager-startBackgroundDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>--><!--Device-AudioSuiteDownloadManager-startBackgroundDownload(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | 是 | 要下载的特性类型。最大长度为5。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. The value of featureTypes is invalid. |
| [6800302](../errorcode-audio.md#6800302-系统服务进程终止) | System service process terminated. |

## startDownload

```TypeScript
startDownload(featureTypes: Array<AudioSuiteFeatureType>, networkType: NetworkType): Promise<void>
```

根据指定的网络开始下载特性。使用Promise异步回调。先调用[getNewVersionInfo](#getnewversioninfo)查询新版本；查询成功且状态变为[VERSION_CHECK_SUCCEEDED](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#version_check_succeeded)后调用本接口，或者在[DOWNLOAD_PAUSED](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#download_paused)状态调用本接口继续下载，调用后状态会变为[DOWNLOADING](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#downloading)。下载成功后自动进入[INSTALLING](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#installing)状态。

接口在开始下载后就返回，下载过程中可以通过[onDownloadStatusChange](#ondownloadstatuschange)订阅的下载状态变化事件获取下载进度。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSuiteDownloadManager-startDownload(featureTypes: Array<AudioSuiteFeatureType>, networkType: NetworkType): Promise<void>--><!--Device-AudioSuiteDownloadManager-startDownload(featureTypes: Array<AudioSuiteFeatureType>, networkType: NetworkType): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | 是 | 要下载的特性类型。最大长度为5。 |
| networkType | [NetworkType](arkts-audio-audio-networktype-e-sys.md) | 是 | 下载的网络类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. The value of featureTypes is invalid. |
| [6800302](../errorcode-audio.md#6800302-系统服务进程终止) | System service process terminated. |
| [6800501](../errorcode-audio.md#6800501-网络条件不满足) | Required network conditions not met. The current network conditions do not match the type specified by networkType. |
| [6800502](../errorcode-audio.md#6800502-存储空间不足) | Insufficient storage space. |

## uninstallFeature

```TypeScript
uninstallFeature(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>
```

卸载已下载的特性。使用Promise异步回调。应在特性状态为[INSTALLATION_SUCCEEDED](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#installation_succeeded)后调用，调用后状态会变为[UNINSTALLING](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#uninstalling)则开始卸载。

当特性状态不为[INSTALLATION_SUCCEEDED](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md#installation_succeeded)时调用本接口，接口会返回成功，保持原有状态不变。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSuiteDownloadManager-uninstallFeature(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>--><!--Device-AudioSuiteDownloadManager-uninstallFeature(featureTypes: Array<AudioSuiteFeatureType>): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureTypes | Array&lt;[AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)&gt; | 是 | 要卸载的特性类型。最大长度为5。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. The value of featureTypes is invalid. |
| [6800302](../errorcode-audio.md#6800302-系统服务进程终止) | System service process terminated. |
