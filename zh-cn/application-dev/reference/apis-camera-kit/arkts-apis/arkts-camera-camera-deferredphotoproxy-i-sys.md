# DeferredPhotoProxy（系统接口）

A class object that functions as a thumbnail proxy.

**起始版本：** 23

<!--Device-camera-interface DeferredPhotoProxy--><!--Device-camera-interface DeferredPhotoProxy-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## getThumbnail

```TypeScript
getThumbnail(): Promise<image.PixelMap>
```

Obtains the PixelMap of a thumbnail. This API uses a promise to return the result.

**起始版本：** 23

<!--Device-DeferredPhotoProxy-getThumbnail(): Promise<image.PixelMap>--><!--Device-DeferredPhotoProxy-getThumbnail(): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | PixelMap of the thumbnail. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';

function getThumbnail(proxyObj: camera.DeferredPhotoProxy): void {
  proxyObj.getThumbnail().then((thumbnail: image.PixelMap) => {
    AppStorage.setOrCreate('proxyThumbnail', thumbnail);
  });
}
```

## release

```TypeScript
release(): Promise<void>
```

Releases depth data output resources. This API uses a promise to return the result.

**起始版本：** 23

<!--Device-DeferredPhotoProxy-release(): Promise<void>--><!--Device-DeferredPhotoProxy-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
async function releaseDeferredPhotoProxy(proxyObj: camera.DeferredPhotoProxy): Promise<void> {
  await proxyObj.release();
}
```

