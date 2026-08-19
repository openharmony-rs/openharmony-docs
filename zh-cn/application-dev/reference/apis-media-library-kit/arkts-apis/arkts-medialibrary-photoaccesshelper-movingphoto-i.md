# MovingPhoto

动态照片对象。 > **说明：** > > - 本Interface首批接口从API version 12开始支持。

**起始版本：** 23

<!--Device-photoAccessHelper-interface MovingPhoto--><!--Device-photoAccessHelper-interface MovingPhoto-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## getUri

```TypeScript
getUri(): string
```

获取动态照片的uri。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MovingPhoto-getUri(): string--><!--Device-MovingPhoto-getUri(): string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 动态照片的uri。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 14000011 | System inner fail |

## getUri

```TypeScript
getUri(): string | null
```

Obtains the URI of this moving photo.

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-MovingPhoto-getUri(): string | null--><!--Device-MovingPhoto-getUri(): string | null-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns uri of the moving photo, if the operation fails, returns null |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## requestContent

```TypeScript
requestContent(imageFileUri: string, videoFileUri: string): Promise<void>
```

同时请求动态照片的图片内容和视频内容，并写入参数指定的对应的uri中。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-MovingPhoto-requestContent(imageFileUri: string, videoFileUri: string): Promise<void>--><!--Device-MovingPhoto-requestContent(imageFileUri: string, videoFileUri: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| imageFileUri | string | 是 | 待写入动态照片图片内容的uri。示例imageFileUri为："file://com.example.temptest/data/storage/el2/ base/haps/ImageFile.jpg"。 |
| videoFileUri | string | 是 | 待写入动态照片视频内容的uri。示例videoFileUri为："file://com.example.temptest/data/storage/el2/ base/haps/VideoFile.mp4"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | System inner fail. Possible causes: <br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## requestContent

```TypeScript
requestContent(resourceType: ResourceType, fileUri: string): Promise<void>
```

请求指定资源类型的动态照片内容，并写入参数指定的uri中。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-MovingPhoto-requestContent(resourceType: ResourceType, fileUri: string): Promise<void>--><!--Device-MovingPhoto-requestContent(resourceType: ResourceType, fileUri: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceType | ResourceType | 是 | 所请求动态照片内容的资源类型。 |
| fileUri | string | 是 | 待写入动态照片内容的uri。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | System inner fail. Possible causes: <br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## requestContent

```TypeScript
requestContent(resourceType: ResourceType): Promise<ArrayBuffer>
```

请求指定资源类型的动态照片内容，以ArrayBuffer的形式返回。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-MovingPhoto-requestContent(resourceType: ResourceType): Promise<ArrayBuffer>--><!--Device-MovingPhoto-requestContent(resourceType: ResourceType): Promise<ArrayBuffer>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceType | ResourceType | 是 | 所请求动态照片内容的资源类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise对象，返回包含所请求文件内容的ArrayBuffer。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | System inner fail. Possible causes: <br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

