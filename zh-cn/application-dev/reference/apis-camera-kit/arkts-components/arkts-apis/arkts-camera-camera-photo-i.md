# Photo

```TypeScript
interface Photo
```

全质量图对象。

**起始版本：** 11

<!--Device-camera-interface Photo--><!--Device-camera-interface Photo-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## release

```TypeScript
release(): Promise<void>
```

Releases output resources. This API uses a promise to return the result.

**起始版本：** 11

**原子化服务API（仅ArkTS-Dyn）：** 从API版本19开始，该接口支持在原子化服务中使用。

<!--Device-Photo-release(): Promise<void>--><!--Device-Photo-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**示例**

```TypeScript
async function releasePhoto(photo: camera.Photo): Promise<void> {
  await photo.release();
}
```

## main

```TypeScript
main: image.Image
```

Full-quality image.

**类型：** [image.Image](../../apis-image-kit/arkts-apis/arkts-image-image-image-i.md)

**起始版本：** 11

**原子化服务API（仅ArkTS-Dyn）：** 从API版本19开始，该接口支持在原子化服务中使用。

<!--Device-Photo-main: image.Image--><!--Device-Photo-main: image.Image-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core
