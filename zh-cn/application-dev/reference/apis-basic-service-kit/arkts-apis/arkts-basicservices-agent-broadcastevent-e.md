# BroadcastEvent

定义自定义系统事件。用户可以使用公共事件接口获取该事件。

上传下载SA具有'ohos.permission.SEND_TASK_COMPLETE_EVENT'权限，用户可以配置事件的metadata指向的二级配置文件来拦截其他事件发送者。

调用CommonEventData类型传输公共事件相关数据，成员的内容填写和 [CommonEventData](arkts-basicservices-commoneventdata-commoneventdata-i.md) 介绍的有所区别，其中CommonEventData.code表示任务的状态，目前为0x40 COMPLETE或0x41 FAILED；CommonEventData.data表示任务的taskId。

<!--Del-->

请参考[静态订阅公共事件](../../../../basic-services/common-event/common-event-static-subscription-sys.md)以获取事件配置信息和二级配置文件的配置方式。<!--DelEnd-->

**起始版本：** 11

<!--Device-agent-enum BroadcastEvent--><!--Device-agent-enum BroadcastEvent-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## COMPLETE

```TypeScript
COMPLETE = 'ohos.request.event.COMPLETE'
```

表示自定义系统事件完成。在任务结束后会触发该事件，根据任务的成功或失败，事件的code返回0x40或者0x41。

**起始版本：** 11

<!--Device-BroadcastEvent-COMPLETE = 'ohos.request.event.COMPLETE'--><!--Device-BroadcastEvent-COMPLETE = 'ohos.request.event.COMPLETE'-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

