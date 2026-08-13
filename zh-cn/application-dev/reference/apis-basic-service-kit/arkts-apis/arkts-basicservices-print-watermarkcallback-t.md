# WatermarkCallback

```TypeScript
type WatermarkCallback = (jobId: string, fd: int) => void
```

定义用来注册强制水印处理的监听事件时使用的回调类型。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-print-type WatermarkCallback = (jobId: string, fd: int) => void--><!--Device-print-type WatermarkCallback = (jobId: string, fd: int) => void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | 表示当前打印任务的id。 |
| fd | int | 是 | 表示当前文件的文件描述符。 |

