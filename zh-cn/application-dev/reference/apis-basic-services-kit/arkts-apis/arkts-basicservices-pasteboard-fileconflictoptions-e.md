# FileConflictOptions

定义文件拷贝冲突时的选项。

**起始版本：** 15

**系统能力：** SystemCapability.MiscServices.Pasteboard

## OVERWRITE

```TypeScript
OVERWRITE = 0
```

目标路径存在同文件名时覆盖。

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.MiscServices.Pasteboard

## SKIP

```TypeScript
SKIP = 1
```

目标路径存在同文件名时跳过，若设置SKIP，应用获取到的粘贴数据不包含跳过文件。

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.MiscServices.Pasteboard
