# VideoMode

枚举，视频文件的log模式。

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DEFAULT

```TypeScript
DEFAULT = 0
```

默认类型。取值为0表示当前视频非log模式或未判断类型，后续部分视频判断后字段会更新为1，因此不建议使用此字段进行查询。

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## LOG_VIDEO

```TypeScript
LOG_VIDEO = 1
```

log模式视频的文件类型。

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
