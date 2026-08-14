# FileConflictOptions

定义文件拷贝冲突时的选项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-pasteboard-enum FileConflictOptions--><!--Device-pasteboard-enum FileConflictOptions-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## OVERWRITE

```TypeScript
OVERWRITE = 0
```

目标路径存在同文件名时覆盖。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FileConflictOptions-OVERWRITE = 0--><!--Device-FileConflictOptions-OVERWRITE = 0-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## SKIP

```TypeScript
SKIP = 1
```

目标路径存在同文件名时跳过，若设置SKIP，应用获取到的粘贴数据不包含跳过文件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FileConflictOptions-SKIP = 1--><!--Device-FileConflictOptions-SKIP = 1-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

