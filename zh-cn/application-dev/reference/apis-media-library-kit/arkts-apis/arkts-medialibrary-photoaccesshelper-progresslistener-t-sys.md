# ProgressListener（系统接口）

```TypeScript
type ProgressListener = (progress: Progress) => void
```

表示复制操作进度的监听类型。 进度回调可以表示复制操作的大小进度和复制操作的文件数量进度。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-photoAccessHelper-type ProgressListener = (progress: Progress) => void--><!--Device-photoAccessHelper-type ProgressListener = (progress: Progress) => void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| progress | Progress | 是 | 进度信息。 |

