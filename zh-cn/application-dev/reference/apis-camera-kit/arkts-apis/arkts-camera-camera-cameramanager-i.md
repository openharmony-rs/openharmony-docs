# CameraManager

相机管理器类，使用前需要通过[getCameraManager](arkts-camera-camera-getcameramanager-f.md#getCameraManager)接口获取相机管理实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface CameraManager--><!--Device-camera-interface CameraManager-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## createCameraInput

```TypeScript
createCameraInput(camera: CameraDevice): CameraInput
```

使用CameraDevice对象创建CameraInput实例，同步返回结果。 该接口使用前首先通过[getSupportedCameras](#getSupportedCameras)接口查询当前设备支持的相机设备信息列表，开发者需要根据具体使用场景选 择符合需求的相机设备，然后使用该接口创建CameraInput实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.CAMERA

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-createCameraInput(camera: CameraDevice): CameraInput--><!--Device-CameraManager-createCameraInput(camera: CameraDevice): CameraInput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| camera | [CameraDevice](arkts-camera-camera-cameradevice-i.md) | 是 | CameraDevice对象，通过 [getSupportedCameras](#getSupportedCameras) 接口获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CameraInput](arkts-camera-camera-camerainput-i.md) | 返回CameraInput实例。接口调用失败会返回相应错误码，错误码类型为[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed.<br>**适用版本：** 12+ |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error.<br>**适用版本：** 12+ |

## createCameraInput

```TypeScript
createCameraInput(position: CameraPosition, type: CameraType): CameraInput
```

根据相机位置和类型创建CameraInput实例，同步返回结果。 该接口使用前需要开发者根据应用具体使用场景自行指定相机位置和类型，例如打开前置相机进入自拍功能。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.CAMERA

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-createCameraInput(position: CameraPosition, type: CameraType): CameraInput--><!--Device-CameraManager-createCameraInput(position: CameraPosition, type: CameraType): CameraInput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [CameraPosition](arkts-camera-camera-cameraposition-e.md) | 是 | 相机位置，首先通过 [getSupportedCameras](#getSupportedCameras) 接口获取支持的相机设备对象，然后根据返回的相机设备对象获取设备位置信息。 |
| type | [CameraType](arkts-camera-camera-cameratype-e.md) | 是 | 相机类型，首先通过 [getSupportedCameras](#getSupportedCameras) 接口获取 支持的相机设备对象，然后根据返回的相机设备对象获取设备类型信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CameraInput](arkts-camera-camera-camerainput-i.md) | 返回CameraInput实例。接口调用失败会返回相应错误码，错误码类型为[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed.<br>**适用版本：** 12+ |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error.<br>**适用版本：** 12+ |

## createCaptureSession

```TypeScript
createCaptureSession(): CaptureSession
```

创建CaptureSession实例，同步返回结果。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [createSession](#createSession)

<!--Device-CameraManager-createCaptureSession(): CaptureSession--><!--Device-CameraManager-createCaptureSession(): CaptureSession-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CaptureSession](arkts-camera-camera-capturesession-i.md) | CaptureSession实例。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## createMetadataOutput

```TypeScript
createMetadataOutput(metadataObjectTypes: Array<MetadataObjectType>): MetadataOutput
```

创建metadata流输出对象，同步返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-createMetadataOutput(metadataObjectTypes: Array<MetadataObjectType>): MetadataOutput--><!--Device-CameraManager-createMetadataOutput(metadataObjectTypes: Array<MetadataObjectType>): MetadataOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| metadataObjectTypes | Array&lt;[MetadataObjectType](arkts-camera-camera-metadataobjecttype-e.md)&gt; | 是 | metadata流类型信息，通过 [getSupportedOutputCapability](#getSupportedOutputCapability) 接口获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MetadataOutput](arkts-camera-camera-metadataoutput-i.md) | MetadataOutput实例。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error.<br>**适用版本：** 12+ |

## createPhotoOutput

```TypeScript
createPhotoOutput(profile: Profile, surfaceId: string): PhotoOutput
```

创建拍照输出对象，同步返回结果。 > **说明：** > > - 从API version 10开始支持，从API version 11开始废弃。 > > - 该接口只支持创建JPEG格式的拍照输出对象。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [createPhotoOutput](#createPhotoOutput)(profile?: Profile)

<!--Device-CameraManager-createPhotoOutput(profile: Profile, surfaceId: string): PhotoOutput--><!--Device-CameraManager-createPhotoOutput(profile: Profile, surfaceId: string): PhotoOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| profile | [Profile](arkts-camera-camera-profile-i.md) | 是 | 支持的拍照配置信息，通过 [getSupportedOutputCapability](#getSupportedOutputCapability) 接口获取。 |
| surfaceId | string | 是 | 从[ImageReceiver](../../apis-image-kit/arkts-apis/arkts-image-image-imagereceiver-i.md#ImageReceiver)获取的surfaceId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PhotoOutput](arkts-camera-camera-photooutput-i.md) | PhotoOutput实例。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |

## createPhotoOutput

```TypeScript
createPhotoOutput(profile?: Profile): PhotoOutput
```

创建拍照输出对象，同步返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-createPhotoOutput(profile?: Profile): PhotoOutput--><!--Device-CameraManager-createPhotoOutput(profile?: Profile): PhotoOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| profile | [Profile](arkts-camera-camera-profile-i.md) | 否 | 支持的拍照配置信息，通过 [getSupportedOutputCapability](#getSupportedOutputCapability) 接口获取。 &lt;br&gt;API version 11时，该参数必填；从API version 12开始，如果使用[preconfig](arkts-camera-camera-photosession-i.md#preconfig)进行预配置，传入 profile参数会覆盖preconfig的预配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PhotoOutput](arkts-camera-camera-photooutput-i.md) | PhotoOutput实例。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error.<br>**适用版本：** 12+ |

## createPreviewOutput

```TypeScript
createPreviewOutput(profile: Profile, surfaceId: string): PreviewOutput
```

创建预览输出对象，同步返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-createPreviewOutput(profile: Profile, surfaceId: string): PreviewOutput--><!--Device-CameraManager-createPreviewOutput(profile: Profile, surfaceId: string): PreviewOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| profile | [Profile](arkts-camera-camera-profile-i.md) | 是 | 支持的预览配置信息，通过 [getSupportedOutputCapability](#getSupportedOutputCapability) 接口获取。 |
| surfaceId | string | 是 | 从XComponent或者 [ImageReceiver](../../apis-image-kit/arkts-apis/arkts-image-image-imagereceiver-i.md#ImageReceiver)组件获取的surfaceId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PreviewOutput](arkts-camera-camera-previewoutput-i.md) | PreviewOutput实例。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error.<br>**适用版本：** 12+ |

## createPreviewOutput

```TypeScript
createPreviewOutput(surfaceId: string): PreviewOutput
```

创建无配置信息的预览输出对象，同步返回结果。该接口需配合[preconfig](arkts-camera-camera-photosession-i.md#preconfig)一起使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-createPreviewOutput(surfaceId: string): PreviewOutput--><!--Device-CameraManager-createPreviewOutput(surfaceId: string): PreviewOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | 从XComponent或者 [ImageReceiver](../../apis-image-kit/arkts-apis/arkts-image-image-imagereceiver-i.md#ImageReceiver)组件获取的surfaceId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PreviewOutput](arkts-camera-camera-previewoutput-i.md) | PreviewOutput实例。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## createSession

```TypeScript
createSession<T extends Session>(mode: SceneMode): T
```

创建指定SceneMode的Session实例，同步返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-createSession<T extends Session>(mode: SceneMode): T--><!--Device-CameraManager-createSession<T extends Session>(mode: SceneMode): T-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [SceneMode](arkts-camera-camera-scenemode-e.md) | 是 | 相机支持的模式。如果传入的参数异常（如超出范围、传入null或未定义等），实际接口不会生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Session实例。接口调用失败会返回相应的错误码，错误码类型为[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.<br>**适用版本：** 19+ |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## createVideoOutput

```TypeScript
createVideoOutput(profile: VideoProfile, surfaceId: string): VideoOutput
```

创建录像输出对象，同步返回结果。 在录像模式下，使能SDR或HDR_VIVID拍摄效果时，CameraFormat与ColorSpace必须按照下列表格中的对应关系配置，若不满足表格中CameraFormat与ColorSpace配置，会导致预览异常等问题。 | SDR/HDR拍摄 | CameraFormat | ColorSpace | |--------------------|--------------------------|------------------| | SDR | CAMERA_FORMAT_YUV_420_SP | BT709_LIMIT | | HDR_VIVID | CAMERA_FORMAT_YCRCB_P010&lt;br&gt;CAMERA_FORMAT_YCBCR_P010 | BT2020_HLG_LIMIT&lt;br&gt;BT2020_HLG_FULL |

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-createVideoOutput(profile: VideoProfile, surfaceId: string): VideoOutput--><!--Device-CameraManager-createVideoOutput(profile: VideoProfile, surfaceId: string): VideoOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| profile | [VideoProfile](arkts-camera-camera-videoprofile-i.md) | 是 | 支持的录像配置信息，通过 [getSupportedOutputCapability](#getSupportedOutputCapability) 接口获取。 |
| surfaceId | string | 是 | 从AVRecorder获取的surfaceId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [VideoOutput](arkts-camera-camera-videooutput-i.md) | VideoOutput实例。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error.<br>**适用版本：** 12+ |

## createVideoOutput

```TypeScript
createVideoOutput(surfaceId: string): VideoOutput
```

创建无配置信息的录像输出对象，同步返回结果。该接口需配合[preconfig](arkts-camera-camera-videosession-i.md#preconfig)功能一起使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-createVideoOutput(surfaceId: string): VideoOutput--><!--Device-CameraManager-createVideoOutput(surfaceId: string): VideoOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | 从AVRecorder获取的surfaceId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [VideoOutput](arkts-camera-camera-videooutput-i.md) | VideoOutput实例。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## getCameraConcurrentInfos

```TypeScript
getCameraConcurrentInfos(cameras: Array<CameraDevice>): Array<CameraConcurrentInfo>
```

获取指定相机设备的并发信息。返回空数组表示不支持并发。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-getCameraConcurrentInfos(cameras: Array<CameraDevice>): Array<CameraConcurrentInfo>--><!--Device-CameraManager-getCameraConcurrentInfos(cameras: Array<CameraDevice>): Array<CameraConcurrentInfo>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cameras | Array&lt;[CameraDevice](arkts-camera-camera-cameradevice-i.md)&gt; | 是 | 一组CameraDevice相机设备，并得到与这一组CameraDevice对应的并发信息，推荐设置为由 [getCameraDevice](#getCameraDevice)获取的前置与后置两个用于并发的相机设备。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[CameraConcurrentInfo](arkts-camera-camera-cameraconcurrentinfo-i.md)&gt; | 一组CameraDevice相机设备对象对应的并发信息，与CameraDevice相机设备一一对应。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## getCameraDevice

```TypeScript
getCameraDevice(position: CameraPosition, type: CameraType): CameraDevice
```

根据相机位置和相机类型查询对应相机。 获取指定[CameraPosition](arkts-camera-camera-cameraposition-e.md#CameraPosition)和[CameraType](arkts-camera-camera-cameratype-e.md#CameraType)的相机镜头，如果该接口返回结果为undefined， 表示当前设备未查询到该镜头。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-getCameraDevice(position: CameraPosition, type: CameraType): CameraDevice--><!--Device-CameraManager-getCameraDevice(position: CameraPosition, type: CameraType): CameraDevice-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [CameraPosition](arkts-camera-camera-cameraposition-e.md) | 是 | 需要得到的CameraDevice对象对应的CameraPosition条件。 |
| type | [CameraType](arkts-camera-camera-cameratype-e.md) | 是 | 需要得到的CameraDevice对象对应的CameraType条件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CameraDevice](arkts-camera-camera-cameradevice-i.md) | 根据相机位置和相机类型查询的对应相机。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## getCameraDevices

```TypeScript
getCameraDevices(position: CameraPosition, types: Array<CameraType>, connectType: ConnectionType): Array<CameraDevice>
```

根据相机位置、相机类型数组和连接类型查询符合条件的相机列表。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-getCameraDevices(position: CameraPosition, types: Array<CameraType>, connectType: ConnectionType): Array<CameraDevice>--><!--Device-CameraManager-getCameraDevices(position: CameraPosition, types: Array<CameraType>, connectType: ConnectionType): Array<CameraDevice>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [CameraPosition](arkts-camera-camera-cameraposition-e.md) | 是 | 相机的位置。 |
| types | Array&lt;[CameraType](arkts-camera-camera-cameratype-e.md)&gt; | 是 | 相机类型数组。 |
| connectType | [ConnectionType](arkts-camera-camera-connectiontype-e.md) | 是 | 相机的连接类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[CameraDevice](arkts-camera-camera-cameradevice-i.md)&gt; | 根据相机位置、相机类型数组和连接类型查询符合条件的相机列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## getSupportedCameras

```TypeScript
getSupportedCameras(): Array<CameraDevice>
```

获取支持的基础相机设备对象（如获取CameraType为CAMERA_TYPE_DEFAULT的默认相机），同步返回结果。 如果需要获取额外的相机设备对象（如获取CameraType为CAMERA_TYPE_TELEPHOTO的长焦相机），可通过 [getCameraDevices](#getCameraDevices)接口获取。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-getSupportedCameras(): Array<CameraDevice>--><!--Device-CameraManager-getSupportedCameras(): Array<CameraDevice>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[CameraDevice](arkts-camera-camera-cameradevice-i.md)&gt; | 相机设备列表。 |

## getSupportedFullOutputCapability

```TypeScript
getSupportedFullOutputCapability(camera: CameraDevice, mode: SceneMode): CameraOutputCapability
```

查询指定相机在指定模式下支持的完整输出能力，包括未压缩图（YUV）、HEIF和HDR等能力。 > **说明：** > > 使用YUV，HEIF或HDR等能力前，需要先显式调用此方法确保获取完整输出能力。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-getSupportedFullOutputCapability(camera: CameraDevice, mode: SceneMode): CameraOutputCapability--><!--Device-CameraManager-getSupportedFullOutputCapability(camera: CameraDevice, mode: SceneMode): CameraOutputCapability-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| camera | [CameraDevice](arkts-camera-camera-cameradevice-i.md) | 是 | Camera device. |
| mode | [SceneMode](arkts-camera-camera-scenemode-e.md) | 是 | Scene mode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CameraOutputCapability](arkts-camera-camera-cameraoutputcapability-i.md) | 相机输出能力。 |

## getSupportedOutputCapability

```TypeScript
getSupportedOutputCapability(camera: CameraDevice): CameraOutputCapability
```

查询相机设备支持的输出能力，同步返回结果。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [getSupportedOutputCapability](#getSupportedOutputCapability)(camera: CameraDevice, mode: SceneMode)

<!--Device-CameraManager-getSupportedOutputCapability(camera: CameraDevice): CameraOutputCapability--><!--Device-CameraManager-getSupportedOutputCapability(camera: CameraDevice): CameraOutputCapability-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| camera | [CameraDevice](arkts-camera-camera-cameradevice-i.md) | 是 | Camera device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CameraOutputCapability](arkts-camera-camera-cameraoutputcapability-i.md) | 相机输出能力。 |

## getSupportedOutputCapability

```TypeScript
getSupportedOutputCapability(camera: CameraDevice, mode: SceneMode): CameraOutputCapability
```

查询相机设备在指定模式下支持的输出能力，同步返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-getSupportedOutputCapability(camera: CameraDevice, mode: SceneMode): CameraOutputCapability--><!--Device-CameraManager-getSupportedOutputCapability(camera: CameraDevice, mode: SceneMode): CameraOutputCapability-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| camera | [CameraDevice](arkts-camera-camera-cameradevice-i.md) | 是 | Camera device. |
| mode | [SceneMode](arkts-camera-camera-scenemode-e.md) | 是 | Scene mode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CameraOutputCapability](arkts-camera-camera-cameraoutputcapability-i.md) | 相机输出能力。 |

## getSupportedSceneModes

```TypeScript
getSupportedSceneModes(camera: CameraDevice): Array<SceneMode>
```

获取指定的相机设备对象支持的模式，同步返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-getSupportedSceneModes(camera: CameraDevice): Array<SceneMode>--><!--Device-CameraManager-getSupportedSceneModes(camera: CameraDevice): Array<SceneMode>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| camera | [CameraDevice](arkts-camera-camera-cameradevice-i.md) | 是 | Camera device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[SceneMode](arkts-camera-camera-scenemode-e.md)&gt; | 相机支持的模式列表。 |

## getTorchMode

```TypeScript
getTorchMode(): TorchMode
```

获取当前设备手电筒模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-getTorchMode(): TorchMode--><!--Device-CameraManager-getTorchMode(): TorchMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TorchMode](arkts-camera-camera-torchmode-e.md) | 返回设备当前手电筒模式。 |

## isCameraMuted

```TypeScript
isCameraMuted(): boolean
```

查询当前相机是否禁用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-isCameraMuted(): boolean--><!--Device-CameraManager-isCameraMuted(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示相机被禁用，返回false表示相机未被禁用。 |

## isTorchModeSupported

```TypeScript
isTorchModeSupported(mode: TorchMode): boolean
```

检测是否支持设置的手电筒模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-isTorchModeSupported(mode: TorchMode): boolean--><!--Device-CameraManager-isTorchModeSupported(mode: TorchMode): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [TorchMode](arkts-camera-camera-torchmode-e.md) | 是 | 手电筒模式。传参为null或者undefined，作为0处理，手电筒关闭。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示设备支持设置的手电筒模式，返回false表示设备不支持的手电筒模式。若接口调用失败，返回undefined。 |

## isTorchSupported

```TypeScript
isTorchSupported(): boolean
```

检测设备是否支持手电筒。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-isTorchSupported(): boolean--><!--Device-CameraManager-isTorchSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示设备是否支持手电筒，true表示设备支持手电筒，false表示设备不支持手电。 &lt;br&gt;如果返回false，则[isTorchModeSupported]{ |

## offCameraStatus

```TypeScript
offCameraStatus(callback?: AsyncCallback<CameraStatusInfo>): void
```

Unsubscribes from camera status change event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CameraManager-offCameraStatus(callback?: AsyncCallback<CameraStatusInfo>): void--><!--Device-CameraManager-offCameraStatus(callback?: AsyncCallback<CameraStatusInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[CameraStatusInfo](arkts-camera-camera-camerastatusinfo-i.md)&gt; | 否 | Callback used to get the camera status change. |

## offFoldStatusChange

```TypeScript
offFoldStatusChange(callback?: AsyncCallback<FoldStatusInfo>): void
```

Unsubscribes from fold status change event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CameraManager-offFoldStatusChange(callback?: AsyncCallback<FoldStatusInfo>): void--><!--Device-CameraManager-offFoldStatusChange(callback?: AsyncCallback<FoldStatusInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[FoldStatusInfo](arkts-camera-camera-foldstatusinfo-i.md)&gt; | 否 | Callback used to get the fold status change. |

## offTorchStatusChange

```TypeScript
offTorchStatusChange(callback?: AsyncCallback<TorchStatusInfo>): void
```

Unsubscribes torch status change event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CameraManager-offTorchStatusChange(callback?: AsyncCallback<TorchStatusInfo>): void--><!--Device-CameraManager-offTorchStatusChange(callback?: AsyncCallback<TorchStatusInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[TorchStatusInfo](arkts-camera-camera-torchstatusinfo-i.md)&gt; | 否 | Callback used to return the torch status change |

## off_cameraStatus

```TypeScript
off(type: 'cameraStatus', callback?: AsyncCallback<CameraStatusInfo>): void
```

相机设备状态注销回调，通过注销回调函数取消获取相机的状态变化。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-off(type: 'cameraStatus', callback?: AsyncCallback<CameraStatusInfo>): void--><!--Device-CameraManager-off(type: 'cameraStatus', callback?: AsyncCallback<CameraStatusInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cameraStatus' | 是 | 监听事件，固定为'cameraStatus'。cameraManager对象获取成功后可监听。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[CameraStatusInfo](arkts-camera-camera-camerastatusinfo-i.md)&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off_foldStatusChange

```TypeScript
off(type: 'foldStatusChange', callback?: AsyncCallback<FoldStatusInfo>): void
```

关闭折叠设备折叠状态变化的监听。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-off(type: 'foldStatusChange', callback?: AsyncCallback<FoldStatusInfo>): void--><!--Device-CameraManager-off(type: 'foldStatusChange', callback?: AsyncCallback<FoldStatusInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'foldStatusChange' | 是 | 监听事件，固定为'foldStatusChange'。表示折叠设备折叠状态发生变化。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[FoldStatusInfo](arkts-camera-camera-foldstatusinfo-i.md)&gt; | 否 | 回调函数，返回折叠设备折叠信息。如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有 callback。 |

## off_torchStatusChange

```TypeScript
off(type: 'torchStatusChange', callback?: AsyncCallback<TorchStatusInfo>): void
```

手电筒状态变化注销回调，通过注销回调函数取消获取手电筒状态变化。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-off(type: 'torchStatusChange', callback?: AsyncCallback<TorchStatusInfo>): void--><!--Device-CameraManager-off(type: 'torchStatusChange', callback?: AsyncCallback<TorchStatusInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'torchStatusChange' | 是 | 监听事件，固定为'torchStatusChange'。cameraManager对象获取成功后可监听。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[TorchStatusInfo](arkts-camera-camera-torchstatusinfo-i.md)&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## onCameraStatus

```TypeScript
onCameraStatus(callback: AsyncCallback<CameraStatusInfo>): void
```

Subscribes camera status change event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CameraManager-onCameraStatus(callback: AsyncCallback<CameraStatusInfo>): void--><!--Device-CameraManager-onCameraStatus(callback: AsyncCallback<CameraStatusInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[CameraStatusInfo](arkts-camera-camera-camerastatusinfo-i.md)&gt; | 是 | Callback used to get the camera status change. |

## onFoldStatusChange

```TypeScript
onFoldStatusChange(callback: AsyncCallback<FoldStatusInfo>): void
```

Subscribes fold status change event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CameraManager-onFoldStatusChange(callback: AsyncCallback<FoldStatusInfo>): void--><!--Device-CameraManager-onFoldStatusChange(callback: AsyncCallback<FoldStatusInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[FoldStatusInfo](arkts-camera-camera-foldstatusinfo-i.md)&gt; | 是 | Callback used to get the fold status change. |

## onTorchStatusChange

```TypeScript
onTorchStatusChange(callback: AsyncCallback<TorchStatusInfo>): void
```

Subscribes torch status change event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CameraManager-onTorchStatusChange(callback: AsyncCallback<TorchStatusInfo>): void--><!--Device-CameraManager-onTorchStatusChange(callback: AsyncCallback<TorchStatusInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[TorchStatusInfo](arkts-camera-camera-torchstatusinfo-i.md)&gt; | 是 | Callback used to return the torch status change |

## on_cameraStatus

```TypeScript
on(type: 'cameraStatus', callback: AsyncCallback<CameraStatusInfo>): void
```

相机设备状态回调，通过注册回调函数获取相机的状态变化。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-on(type: 'cameraStatus', callback: AsyncCallback<CameraStatusInfo>): void--><!--Device-CameraManager-on(type: 'cameraStatus', callback: AsyncCallback<CameraStatusInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cameraStatus' | 是 | 监听事件，固定为'cameraStatus'。cameraManager对象获取成功后可监听。目前只支持对设备打开或者关闭会触发该事件并返回对应信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[CameraStatusInfo](arkts-camera-camera-camerastatusinfo-i.md)&gt; | 是 | 回调函数，用于获取镜头状态变化信息。 |

## on_foldStatusChange

```TypeScript
on(type: 'foldStatusChange', callback: AsyncCallback<FoldStatusInfo>): void
```

注册折叠设备折叠状态变化的监听。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-on(type: 'foldStatusChange', callback: AsyncCallback<FoldStatusInfo>): void--><!--Device-CameraManager-on(type: 'foldStatusChange', callback: AsyncCallback<FoldStatusInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'foldStatusChange' | 是 | 监听事件，固定为'foldStatusChange'。表示折叠设备折叠状态发生变化。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[FoldStatusInfo](arkts-camera-camera-foldstatusinfo-i.md)&gt; | 是 | 回调函数。返回折叠设备折叠信息。 |

## on_torchStatusChange

```TypeScript
on(type: 'torchStatusChange', callback: AsyncCallback<TorchStatusInfo>): void
```

手电筒状态变化回调，通过注册回调函数获取手电筒状态变化。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-on(type: 'torchStatusChange', callback: AsyncCallback<TorchStatusInfo>): void--><!--Device-CameraManager-on(type: 'torchStatusChange', callback: AsyncCallback<TorchStatusInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'torchStatusChange' | 是 | 监听事件，固定为'torchStatusChange'。cameraManager对象获取成功后可监听。目前只支持手电筒打开，手电筒关闭，手电筒不可 用，手电筒恢复可用会触发该事件并返回对应信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[TorchStatusInfo](arkts-camera-camera-torchstatusinfo-i.md)&gt; | 是 | 回调函数，用于获取手电筒状态变化信息。 |

## setTorchMode

```TypeScript
setTorchMode(mode: TorchMode): void
```

设置设备手电筒模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraManager-setTorchMode(mode: TorchMode): void--><!--Device-CameraManager-setTorchMode(mode: TorchMode): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [TorchMode](arkts-camera-camera-torchmode-e.md) | 是 | 手电筒模式。传参为null或者undefined，作为0处理，手电筒关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect.<br>**适用版本：** 11 - 17 |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed.<br>**适用版本：** 12+ |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error.<br>**适用版本：** 12+ |

