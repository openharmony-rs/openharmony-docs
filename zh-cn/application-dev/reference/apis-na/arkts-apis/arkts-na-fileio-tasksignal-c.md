# TaskSignal

拷贝中断信号。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-class TaskSignal--><!--Device-fileIo-class TaskSignal-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## cancel

```TypeScript
cancel(): void
```

取消拷贝任务。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-TaskSignal-cancel(): void--><!--Device-TaskSignal-cancel(): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900012 | Permission denied by the file system |
| 13900010 | Try again |
| 13900043 | No task can be canceled. |

