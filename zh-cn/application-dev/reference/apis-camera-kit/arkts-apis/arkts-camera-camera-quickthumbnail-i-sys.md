# QuickThumbnail（系统接口）

Quick thumbnail object

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface QuickThumbnail--><!--Device-camera-interface QuickThumbnail-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## release

```TypeScript
release(): Promise<void>
```

Release quick thumbnail object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-QuickThumbnail-release(): Promise<void>--><!--Device-QuickThumbnail-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## captureId

```TypeScript
readonly captureId: int
```

capture id.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-QuickThumbnail-readonly captureId: int--><!--Device-QuickThumbnail-readonly captureId: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## thumbnailImage

```TypeScript
thumbnailImage: image.PixelMap
```

Thumbnail image.

**类型：** image.PixelMap

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-QuickThumbnail-thumbnailImage: image.PixelMap--><!--Device-QuickThumbnail-thumbnailImage: image.PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

