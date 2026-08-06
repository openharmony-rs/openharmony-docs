# Photo

全质量图对象。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-camera-interface Photo--><!--Device-camera-interface Photo-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## release

```TypeScript
release(): Promise<void>
```

Releases output resources. This API uses a promise to return the result.

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Photo-release(): Promise<void>--><!--Device-Photo-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

## main

```TypeScript
main: image.Image
```

Full-quality image.

**类型：** image.Image

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Photo-main: image.Image--><!--Device-Photo-main: image.Image-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

