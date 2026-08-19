# TaskSignal

拷贝中断信号。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-class TaskSignal--><!--Device-fileIo-class TaskSignal-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
```

## cancel

```TypeScript
cancel(): void
```

取消拷贝任务。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-TaskSignal-cancel(): void--><!--Device-TaskSignal-cancel(): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900012 | Permission denied by the file system |
| 13900010 | Try again |
| 13900043 | No task can be canceled. |

