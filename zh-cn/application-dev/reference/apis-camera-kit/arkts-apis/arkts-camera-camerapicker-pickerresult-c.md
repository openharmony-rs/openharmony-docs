# PickerResult

相机选择器的处理结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cameraPicker-class PickerResult--><!--Device-cameraPicker-class PickerResult-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## mediaType

```TypeScript
mediaType: PickerMediaType
```

返回的媒体类型。

**类型：** [PickerMediaType](arkts-camera-camerapicker-pickermediatype-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PickerResult-mediaType: PickerMediaType--><!--Device-PickerResult-mediaType: PickerMediaType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## resultCode

```TypeScript
resultCode: int
```

处理的结果，成功返回0，失败返回-1。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PickerResult-resultCode: int--><!--Device-PickerResult-resultCode: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## resultUri

```TypeScript
resultUri: string
```

返回的uri地址。若saveUri为空，resultUri为公共媒体路径。若saveUri不为空且具备写权限，resultUri与saveUri相同。若saveUri不为空且不具备写权限，则无法获取到resultUri。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PickerResult-resultUri: string--><!--Device-PickerResult-resultUri: string-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

