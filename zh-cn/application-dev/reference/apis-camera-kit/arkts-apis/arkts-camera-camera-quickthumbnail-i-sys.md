# QuickThumbnail（系统接口）

```TypeScript
interface QuickThumbnail
```

快速缩略图对象。

**起始版本：** 19

<!--Device-camera-interface QuickThumbnail--><!--Device-camera-interface QuickThumbnail-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## release

```TypeScript
release(): Promise<void>
```

释放快速缩略图对象。

**起始版本：** 19

<!--Device-QuickThumbnail-release(): Promise<void>--><!--Device-QuickThumbnail-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 用于返回结果的 Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

## captureId

```TypeScript
readonly captureId: number
```

拍摄ID。

**类型：** number

**起始版本：** 19

<!--Device-QuickThumbnail-readonly captureId: int--><!--Device-QuickThumbnail-readonly captureId: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## thumbnailImage

```TypeScript
thumbnailImage: image.PixelMap
```

缩略图图像。

**类型：** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**起始版本：** 19

<!--Device-QuickThumbnail-thumbnailImage: image.PixelMap--><!--Device-QuickThumbnail-thumbnailImage: image.PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。
