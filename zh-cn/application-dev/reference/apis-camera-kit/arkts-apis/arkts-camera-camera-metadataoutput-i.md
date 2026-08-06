# MetadataOutput

metadata流。继承[CameraOutput]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**继承/实现关系：** MetadataOutput extends [CameraOutput](arkts-camera-camera-cameraoutput-i.md)

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-camera-interface MetadataOutput extends CameraOutput--><!--Device-camera-interface MetadataOutput extends CameraOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## addMetadataObjectTypes

```TypeScript
addMetadataObjectTypes(types: Array<MetadataObjectType>): void
```

新增需要上报的检测对象类型。

**起始版本：** 23

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataOutput-addMetadataObjectTypes(types: Array<MetadataObjectType>): void--><!--Device-MetadataOutput-addMetadataObjectTypes(types: Array<MetadataObjectType>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | Array&lt;MetadataObjectType&gt; | 是 | metadata流类型信息，通过getSupportedOutputCapability接口获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 13 - 22 |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## isLockMetadataObjectTrackingSupported

```TypeScript
isLockMetadataObjectTrackingSupported(): boolean
```

检查设备是否支持锁定元数据对象（如猫脸、狗脸）追踪功能。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataOutput-isLockMetadataObjectTrackingSupported(): boolean--><!--Device-MetadataOutput-isLockMetadataObjectTrackingSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否支持锁定元数据对象追踪功能。true表示支持，false表示不支持。 |

## lockMetadataObjectTracking

```TypeScript
lockMetadataObjectTracking(point: Point): void
```

锁定对特定元数据对象（如猫脸、狗脸）的追踪。 > **说明：** > > - 该功能以point所指向的点所在的对象为追踪对象，如果该点不存在追踪对象，则功能不生效。 > > - 被锁定追踪的对象离开取景范围超过三秒或调用解锁追踪后，锁定追踪自动取消。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataOutput-lockMetadataObjectTracking(point: Point): void--><!--Device-MetadataOutput-lockMetadataObjectTracking(point: Point): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| point | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 锁定元数据对象追踪的点位。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## off('metadataObjectsAvailable')

```TypeScript
off(type: 'metadataObjectsAvailable', callback?: AsyncCallback<Array<MetadataObject>>): void
```

注销监听检测到的metadata对象。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataOutput-off(type: 'metadataObjectsAvailable', callback?: AsyncCallback<Array<MetadataObject>>): void--><!--Device-MetadataOutput-off(type: 'metadataObjectsAvailable', callback?: AsyncCallback<Array<MetadataObject>>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'metadataObjectsAvailable' | 是 | 监听事件，固定为'metadataObjectsAvailable'，metadataOutput创建成功后可监听。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;MetadataObject&gt;&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

注销监听metadata流的错误。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataOutput-off(type: 'error', callback?: ErrorCallback): void--><!--Device-MetadataOutput-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 监听事件，固定为'error'，metadataOutput创建成功后可监听。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## offError

```TypeScript
offError(callback?: ErrorCallback): void
```

Unsubscribes from error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-MetadataOutput-offError(callback?: ErrorCallback): void--><!--Device-MetadataOutput-offError(callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Callback used to get the metadata output errors. |

## offMetadataObjectsAvailable

```TypeScript
offMetadataObjectsAvailable(callback?: AsyncCallback<Array<MetadataObject>>): void
```

Unsubscribes from metadata objects available event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-MetadataOutput-offMetadataObjectsAvailable(callback?: AsyncCallback<Array<MetadataObject>>): void--><!--Device-MetadataOutput-offMetadataObjectsAvailable(callback?: AsyncCallback<Array<MetadataObject>>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;MetadataObject&gt;&gt; | 否 | Callback used to get the available metadata objects. |

## on('metadataObjectsAvailable')

```TypeScript
on(type: 'metadataObjectsAvailable', callback: AsyncCallback<Array<MetadataObject>>): void
```

监听检测到的metadata对象，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataOutput-on(type: 'metadataObjectsAvailable', callback: AsyncCallback<Array<MetadataObject>>): void--><!--Device-MetadataOutput-on(type: 'metadataObjectsAvailable', callback: AsyncCallback<Array<MetadataObject>>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'metadataObjectsAvailable' | 是 | 监听事件，固定为'metadataObjectsAvailable'，metadataOutput创建成功后可监听。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_检测到有效的metadata数据时，触发该事件发生并返回相应的metadata数据。如果输入错误字段，则不会创建有效监听。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;MetadataObject&gt;&gt; | 是 | 回调函数，用于获取metadata数据。 |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

监听metadata流的错误，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataOutput-on(type: 'error', callback: ErrorCallback): void--><!--Device-MetadataOutput-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 监听事件，固定为'error'，metadataOutput创建成功后可监听。metadata接口使用错误时触发该事件并返回对应错误码，比如调用[start]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_，[CameraOutput.release]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_接口时发生错误返回对应错误信息。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调函数，用于获取错误信息。返回错误码，错误码类型[CameraErrorCode]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

## onError

```TypeScript
onError(callback: ErrorCallback): void
```

Subscribes to error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-MetadataOutput-onError(callback: ErrorCallback): void--><!--Device-MetadataOutput-onError(callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Callback used to get the metadata output errors. |

## onMetadataObjectsAvailable

```TypeScript
onMetadataObjectsAvailable(callback: AsyncCallback<Array<MetadataObject>>): void
```

Subscribes to metadata objects available event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-MetadataOutput-onMetadataObjectsAvailable(callback: AsyncCallback<Array<MetadataObject>>): void--><!--Device-MetadataOutput-onMetadataObjectsAvailable(callback: AsyncCallback<Array<MetadataObject>>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;MetadataObject&gt;&gt; | 是 | Callback used to get the available metadata objects. |

## removeMetadataObjectTypes

```TypeScript
removeMetadataObjectTypes(types: Array<MetadataObjectType>): void
```

删除需要上报的检测对象类型。

**起始版本：** 23

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataOutput-removeMetadataObjectTypes(types: Array<MetadataObjectType>): void--><!--Device-MetadataOutput-removeMetadataObjectTypes(types: Array<MetadataObjectType>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | Array&lt;MetadataObjectType&gt; | 是 | metadata流类型信息，通过getSupportedOutputCapability接口获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 13 - 22 |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

开始输出metadata，通过注册回调函数获取结果。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataOutput-start(callback: AsyncCallback<void>): void--><!--Device-MetadataOutput-start(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当开始输出metadata成功，err为undefined，否则为错误对象。错误码类型[CameraErrorCode]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## start

```TypeScript
start(): Promise<void>
```

开始输出metadata。使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataOutput-start(): Promise<void>--><!--Device-MetadataOutput-start(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

停止输出metadata，通过注册回调函数获取结果。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataOutput-stop(callback: AsyncCallback<void>): void--><!--Device-MetadataOutput-stop(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当停止输出metadata成功，err为undefined，否则为错误对象。 |

## stop

```TypeScript
stop(): Promise<void>
```

停止输出metadata。使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataOutput-stop(): Promise<void>--><!--Device-MetadataOutput-stop(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

## unlockMetadataObjectTracking

```TypeScript
unlockMetadataObjectTracking(): void
```

解锁元数据对象（如猫脸、狗脸）追踪。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataOutput-unlockMetadataObjectTracking(): void--><!--Device-MetadataOutput-unlockMetadataObjectTracking(): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

