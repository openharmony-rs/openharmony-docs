# Filter

过滤条件。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-agent-interface Filter--><!--Device-agent-interface Filter-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## action

```TypeScript
action?: Action
```

任务操作选项。 - UPLOAD表示上传任务。 - DOWNLOAD表示下载任务。 - 如果未填写，则查询所有任务。

**类型：** Action

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-Filter-action?: Action--><!--Device-Filter-action?: Action-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## after

```TypeScript
after?: long
```

开始的Unix时间戳（毫秒），默认值为调用时刻减24小时。

**类型：** long

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-Filter-after?: long--><!--Device-Filter-after?: long-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## before

```TypeScript
before?: long
```

结束的Unix时间戳（毫秒），默认为调用时刻。

**类型：** long

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-Filter-before?: long--><!--Device-Filter-before?: long-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## mode

```TypeScript
mode?: Mode
```

任务模式。 - FOREGROUND表示前台任务。 - BACKGROUND表示后台任务。 - 如果未填写，则查询所有任务。

**类型：** Mode

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-Filter-mode?: Mode--><!--Device-Filter-mode?: Mode-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## state

```TypeScript
state?: State
```

指定任务的状态。如果未填写，则查询所有任务。

**类型：** State

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-Filter-state?: State--><!--Device-Filter-state?: State-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

