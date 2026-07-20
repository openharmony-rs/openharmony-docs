# EventId（系统接口）

事件ID。

**起始版本：** 9

<!--Device-update-export enum EventId--><!--Device-update-export enum EventId-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## EVENT_TASK_BASE

```TypeScript
EVENT_TASK_BASE = EventClassify.TASK
```

任务事件。

**起始版本：** 9

<!--Device-EventId-EVENT_TASK_BASE = EventClassify.TASK--><!--Device-EventId-EVENT_TASK_BASE = EventClassify.TASK-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## EVENT_TASK_RECEIVE

```TypeScript
EVENT_TASK_RECEIVE = 0x01000001
```

收到任务。

**起始版本：** 9

<!--Device-EventId-EVENT_TASK_RECEIVE = 0x01000001--><!--Device-EventId-EVENT_TASK_RECEIVE = 0x01000001-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## EVENT_TASK_CANCEL

```TypeScript
EVENT_TASK_CANCEL = 0x01000002
```

取消任务。

**起始版本：** 9

<!--Device-EventId-EVENT_TASK_CANCEL = 0x01000002--><!--Device-EventId-EVENT_TASK_CANCEL = 0x01000002-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## EVENT_DOWNLOAD_WAIT

```TypeScript
EVENT_DOWNLOAD_WAIT = 0x01000003
```

待下载。

**起始版本：** 9

<!--Device-EventId-EVENT_DOWNLOAD_WAIT = 0x01000003--><!--Device-EventId-EVENT_DOWNLOAD_WAIT = 0x01000003-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## EVENT_DOWNLOAD_START

```TypeScript
EVENT_DOWNLOAD_START = 0x01000004
```

开始下载。

**起始版本：** 9

<!--Device-EventId-EVENT_DOWNLOAD_START = 0x01000004--><!--Device-EventId-EVENT_DOWNLOAD_START = 0x01000004-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## EVENT_DOWNLOAD_UPDATE

```TypeScript
EVENT_DOWNLOAD_UPDATE = 0x01000005
```

下载进度更新。

**起始版本：** 9

<!--Device-EventId-EVENT_DOWNLOAD_UPDATE = 0x01000005--><!--Device-EventId-EVENT_DOWNLOAD_UPDATE = 0x01000005-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## EVENT_DOWNLOAD_PAUSE

```TypeScript
EVENT_DOWNLOAD_PAUSE = 0x01000006
```

下载暂停。

**起始版本：** 9

<!--Device-EventId-EVENT_DOWNLOAD_PAUSE = 0x01000006--><!--Device-EventId-EVENT_DOWNLOAD_PAUSE = 0x01000006-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## EVENT_DOWNLOAD_RESUME

```TypeScript
EVENT_DOWNLOAD_RESUME = 0x01000007
```

恢复下载。

**起始版本：** 9

<!--Device-EventId-EVENT_DOWNLOAD_RESUME = 0x01000007--><!--Device-EventId-EVENT_DOWNLOAD_RESUME = 0x01000007-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## EVENT_DOWNLOAD_SUCCESS

```TypeScript
EVENT_DOWNLOAD_SUCCESS = 0x01000008
```

下载成功。

**起始版本：** 9

<!--Device-EventId-EVENT_DOWNLOAD_SUCCESS = 0x01000008--><!--Device-EventId-EVENT_DOWNLOAD_SUCCESS = 0x01000008-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## EVENT_DOWNLOAD_FAIL

```TypeScript
EVENT_DOWNLOAD_FAIL = 0x01000009
```

下载失败。

**起始版本：** 9

<!--Device-EventId-EVENT_DOWNLOAD_FAIL = 0x01000009--><!--Device-EventId-EVENT_DOWNLOAD_FAIL = 0x01000009-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## EVENT_UPGRADE_WAIT

```TypeScript
EVENT_UPGRADE_WAIT = 0x0100000a
```

待升级。

**起始版本：** 9

<!--Device-EventId-EVENT_UPGRADE_WAIT = 0x0100000a--><!--Device-EventId-EVENT_UPGRADE_WAIT = 0x0100000a-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## EVENT_UPGRADE_START

```TypeScript
EVENT_UPGRADE_START = 0x0100000b
```

开始升级。

**起始版本：** 9

<!--Device-EventId-EVENT_UPGRADE_START = 0x0100000b--><!--Device-EventId-EVENT_UPGRADE_START = 0x0100000b-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## EVENT_UPGRADE_UPDATE

```TypeScript
EVENT_UPGRADE_UPDATE = 0x0100000c
```

升级中。

**起始版本：** 9

<!--Device-EventId-EVENT_UPGRADE_UPDATE = 0x0100000c--><!--Device-EventId-EVENT_UPGRADE_UPDATE = 0x0100000c-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## EVENT_APPLY_WAIT

```TypeScript
EVENT_APPLY_WAIT = 0x0100000d
```

待生效。

**起始版本：** 9

<!--Device-EventId-EVENT_APPLY_WAIT = 0x0100000d--><!--Device-EventId-EVENT_APPLY_WAIT = 0x0100000d-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## EVENT_APPLY_START

```TypeScript
EVENT_APPLY_START = 0x0100000e
```

开始生效。

**起始版本：** 9

<!--Device-EventId-EVENT_APPLY_START = 0x0100000e--><!--Device-EventId-EVENT_APPLY_START = 0x0100000e-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## EVENT_UPGRADE_SUCCESS

```TypeScript
EVENT_UPGRADE_SUCCESS = 0x0100000f
```

升级成功。

**起始版本：** 9

<!--Device-EventId-EVENT_UPGRADE_SUCCESS = 0x0100000f--><!--Device-EventId-EVENT_UPGRADE_SUCCESS = 0x0100000f-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## EVENT_UPGRADE_FAIL

```TypeScript
EVENT_UPGRADE_FAIL = 0x01000010
```

升级失败。

**起始版本：** 9

<!--Device-EventId-EVENT_UPGRADE_FAIL = 0x01000010--><!--Device-EventId-EVENT_UPGRADE_FAIL = 0x01000010-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

