# Progress

任务进度的数据结构。

**起始版本：** 10

<!--Device-agent-interface Progress--><!--Device-agent-interface Progress-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## 导入模块

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## extras

```TypeScript
readonly extras?: object
```

交互的额外内容，例如：来自服务器的响应的header和body。默认值为空。

**类型：** object

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Progress-readonly extras?: object--><!--Device-Progress-readonly extras?: object-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## index

```TypeScript
readonly index: number
```

任务中当前正在处理的文件索引。

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Progress-readonly index: int--><!--Device-Progress-readonly index: int-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## processed

```TypeScript
readonly processed: number
```

任务中当前文件的已处理数据大小，单位为字节（B）。

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Progress-readonly processed: long--><!--Device-Progress-readonly processed: long-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## sizes

```TypeScript
readonly sizes: Array<number>
```

任务中文件的大小，单位为字节（B）。在下载过程中，若服务器使用chunk方式传输导致无法从请求头中获取文件总大小时，sizes为 -1。

**类型：** Array<number>

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Progress-readonly sizes: Array<long>--><!--Device-Progress-readonly sizes: Array<long>-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## state

```TypeScript
readonly state: State
```

任务当前的状态。

**类型：** State

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Progress-readonly state: State--><!--Device-Progress-readonly state: State-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

