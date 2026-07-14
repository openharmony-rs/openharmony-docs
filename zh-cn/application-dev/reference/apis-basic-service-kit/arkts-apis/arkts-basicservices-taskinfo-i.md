# TaskInfo

查询结果的任务信息数据结构，提供普通查询和系统查询，两种字段的可见范围不同。

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## action

```TypeScript
readonly action: Action
```

任务操作选项。

- UPLOAD表示上传任务。
- DOWNLOAD表示下载任务。

**类型：** Action

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## ctime

```TypeScript
readonly ctime: number
```

创建任务的Unix时间戳（毫秒），由当前设备的系统生成。

说明：使用
[request.agent.search](arkts-basicservices-search-f.md#search-2)进行
查询时，该值需处于[after,before]区间内才可正常查询到任务id，before和after信息详见
[Filter](arkts-basicservices-filter-i.md)。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## data

```TypeScript
readonly data?: string | Array<FormItem>
```

任务值。

- 通过[request.agent.show](arkts-basicservices-show-f.md#show-2)、
[request.agent.touch](arkts-basicservices-touch-f.md#touch-2)进行查询
。

**类型：** string | Array<FormItem>

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## description

```TypeScript
readonly description: string
```

任务描述。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## extras

```TypeScript
readonly extras?: object
```

任务的额外部分。

**类型：** object

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## faults

```TypeScript
readonly faults: Faults
```

任务的失败原因。

**类型：** Faults

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## gauge

```TypeScript
readonly gauge: boolean
```

后台任务的进度通知策略。

- false：代表仅完成或失败的通知。
- true，发出每个进度已完成或失败的通知。

**类型：** boolean

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## mimeType

```TypeScript
readonly mimeType: string
```

任务配置中的mimetype。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## mode

```TypeScript
readonly mode: Mode
```

任务模式。

- FOREGROUND表示前台任务。
- BACKGROUND表示后台任务。

**类型：** Mode

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## mtime

```TypeScript
readonly mtime: number
```

任务状态改变时的Unix时间戳（毫秒），由当前设备的系统生成。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## priority

```TypeScript
readonly priority: number
```

任务的优先级。前台任务的优先级比后台任务高。任务模式相同的情况下，该配置项的数字越小优先级越高，默认值为0。

**类型：** number

**起始版本：** 11

**系统能力：** SystemCapability.Request.FileTransferAgent

## progress

```TypeScript
readonly progress: Progress
```

任务的过程进度。

**类型：** Progress

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## reason

```TypeScript
readonly reason: string
```

等待/失败/停止/暂停任务的原因。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## retry

```TypeScript
readonly retry: boolean
```

任务的重试开关，仅应用于后台任务。

- true：是
- false：否

**类型：** boolean

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## saveas

```TypeScript
readonly saveas?: string
```

保存下载文件的路径。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## tid

```TypeScript
readonly tid: string
```

任务id。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## title

```TypeScript
readonly title: string
```

任务标题。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## tries

```TypeScript
readonly tries: number
```

任务的尝试次数。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## url

```TypeScript
readonly url?: string
```

任务的url。

- 通过[request.agent.show](arkts-basicservices-show-f.md#show-2)、
[request.agent.touch](arkts-basicservices-touch-f.md#touch-2)进行查询
。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

