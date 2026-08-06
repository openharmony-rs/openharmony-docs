# EventInfo（系统接口）

事件信息对象，用于接收升级事件通知时传递的事件详情。包含eventId(事件ID，标识具体事件类型)和taskBody(任务数据，包含任务状态和进度)字段。 使用场景：在注册事件监听(on方法)后，事件发生时回调函数会接收到EventInfo对象，通过解析eventId和taskBody可获知升级任务的实时状态和进度，用于实时监控升级流程。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-update-export interface EventInfo--><!--Device-update-export interface EventInfo-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## eventId

```TypeScript
eventId: EventId
```

事件ID，用于标识具体的升级事件类型。通过eventId可判断当前发生的具体事件(如EVENT\_DOWNLOAD\_START表示开始下载、EVENT\_UPGRADE\_SUCCESS表示升级成功等)，从而采取相应处理。 常见事件类型包括下载事件(EVENT\_DOWNLOAD\_START等)、升级事件(EVENT\_UPGRADE\_START等)、完成事件(EVENT\_UPGRADE\_SUCCESS、EVENT\_UPGRADE\_FAIL)。建议在 事件回调中根据eventId执行不同的业务逻辑。

**类型：** EventId

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-EventInfo-eventId: EventId--><!--Device-EventInfo-eventId: EventId-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## taskBody

```TypeScript
taskBody: TaskBody
```

任务数据。

**类型：** TaskBody

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-EventInfo-taskBody: TaskBody--><!--Device-EventInfo-taskBody: TaskBody-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

