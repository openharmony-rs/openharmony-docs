# DeferredPhotoProxy（系统接口）

```TypeScript
interface DeferredPhotoProxy
```

作为缩略图代理的类对象。

**起始版本：** 11

<!--Device-camera-interface DeferredPhotoProxy--><!--Device-camera-interface DeferredPhotoProxy-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getThumbnail

```TypeScript
getThumbnail(): Promise<image.PixelMap>
```

获取缩略图的 PixelMap。此接口使用 Promise 返回结果。

**起始版本：** 11

<!--Device-DeferredPhotoProxy-getThumbnail(): Promise<image.PixelMap>--><!--Device-DeferredPhotoProxy-getThumbnail(): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | 缩略图的 PixelMap。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
import { image } from '@kit.ImageKit';

function getThumbnail(proxyObj: camera.DeferredPhotoProxy): void {
  proxyObj.getThumbnail().then((thumbnail: image.PixelMap) => {
    AppStorage.setOrCreate('proxyThumbnail', thumbnail);
  });
}
```

<!--DelEnd-->

## release

```TypeScript
release(): Promise<void>
```

释放深度数据输出资源。此接口使用Promise返回结果。

**起始版本：** 11

<!--Device-DeferredPhotoProxy-release(): Promise<void>--><!--Device-DeferredPhotoProxy-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回值的 Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
async function releaseDeferredPhotoProxy(proxyObj: camera.DeferredPhotoProxy): Promise<void> {
  await proxyObj.release();
}
```

<!--DelEnd-->
