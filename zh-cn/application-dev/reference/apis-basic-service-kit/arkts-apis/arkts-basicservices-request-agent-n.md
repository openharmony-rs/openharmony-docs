# agent

The request agent api.
Supports "background" and "frontend" tasks as while.
Though "background" and "frontend" here do not the same with process's concept.
All tasks will be executed at request manager service and recorded.
Background tasks is for concurrent transfer, such as caching videos for a later play.
Frontend tasks is for instant transfer, such as submitting forms for a consumption bill.
Background tasks use notification to tell user tasks' status information.
Frontend tasks use callback to tell caller tasks' status information.
Background has some automatically restore mechanism.
Frontend tasks controlled by caller.
Uses `multipart/form-data` in client request for upload.
A `Content-Disposition: attachment; filename=<filename>` response from server leads to download.
More details, please see the architecture documents of the request subsystem.
Only front-end mode is supported in cross-platform scenarios.

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [create](arkts-basicservices-agent-create-f.md#create-1) | 创建需要上传或下载的任务，并将其排入队列。支持HTTP/HTTPS协议，使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../../application-models/uiability-usage.md#获取uiability的上下文信息)。<br/> |
| [create](arkts-basicservices-agent-create-f.md#create-2) | 创建需要上传或下载的任务，并将其排入队列。支持HTTP/HTTPS协议，使用Promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../../application-models/uiability-usage.md#获取uiability的上下文信息)。<br/> |
| [getTask](arkts-basicservices-agent-gettask-f.md#getTask-1) | 根据任务id查询任务。使用Promise异步回调。<br/> |
| [remove](arkts-basicservices-agent-remove-f.md#remove-1) | 移除属于调用方的指定任务，如果正在处理中，该任务将被迫停止。使用callback异步回调。在调用后任务对象和其回调函数会被释放。<br/> |
| [remove](arkts-basicservices-agent-remove-f.md#remove-2) | 移除属于调用方的指定任务，如果正在处理中，该任务将被迫停止。使用Promise异步回调。在调用后任务对象和其回调函数会被释放。<br/> |
| [show](arkts-basicservices-agent-show-f.md#show-1) | 根据任务id查询任务的详细信息。使用callback异步回调。<br/> |
| [show](arkts-basicservices-agent-show-f.md#show-2) | 根据任务id查询任务的详细信息。使用Promise异步回调。<br/> |
| [touch](arkts-basicservices-agent-touch-f.md#touch-1) | 根据任务id和token查询任务的详细信息。使用callback异步回调。<br/> |
| [touch](arkts-basicservices-agent-touch-f.md#touch-2) | 根据任务id和token查询任务的详细信息。使用Promise异步回调。<br/> |
| [search](arkts-basicservices-agent-search-f.md#search-1) | 根据默认[Filter](arkts-basicservices-agent-filter-i.md#Filter)过滤条件查找任务id，即查询调用<br/>时刻至24小时前的所有任务的任务id。使用callback异步回调。<br/> |
| [search](arkts-basicservices-agent-search-f.md#search-2) | 根据[Filter](arkts-basicservices-agent-filter-i.md#Filter)过滤条件查找任务id。使用<br/>callback异步回调。<br/> |
| [search](arkts-basicservices-agent-search-f.md#search-3) | 根据[Filter](arkts-basicservices-agent-filter-i.md#Filter)过滤条件查找任务id。使用<br/>Promise异步回调。<br/> |
| <!--DelRow-->[query](arkts-basicservices-agent-query-f-sys.md#query-1) | Queries specified task details.<br/>Creates a group based on GroupConfig<br/> |
| <!--DelRow-->[query](arkts-basicservices-agent-query-f-sys.md#query-2) | Queries specified task details.<br/> |
| [createGroup](arkts-basicservices-agent-creategroup-f.md#createGroup-1) | 根据[GroupConfig](arkts-basicservices-agent-groupconfig-i.md#GroupConfig)分组条件创建分组<br/>，并返回分组id。使用Promise异步回调。<br/> |
| [attachGroup](arkts-basicservices-agent-attachgroup-f.md#attachGroup-1) | 向指定分组id中绑定多个下载任务id。使用Promise异步回调。<br/><br/>如果任意一个任务id不满足添加条件，则所有列表中的任务都不会添加到分组中。<br/> |
| [deleteGroup](arkts-basicservices-agent-deletegroup-f.md#deleteGroup-1) | 移除指定分组，后续不能再往该分组中添加任务id。使用Promise异步回调。<br/><br/>当分组中的所有任务处于完成、失败或移除状态，并且分组被移除时，显示该分组的完成或失败通知。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [FileSpec](arkts-basicservices-agent-filespec-i.md) | 表单项的文件信息。<br/> |
| [FormItem](arkts-basicservices-agent-formitem-i.md) | 任务的表单项信息。<br/> |
| [Notification](arkts-basicservices-agent-notification-i.md) | 通知栏自定义信息。<br/> |
| <!--DelRow-->[Notification](arkts-basicservices-agent-notification-i-sys.md) | 通知栏自定义信息。<br/> |
| [MinSpeed](arkts-basicservices-agent-minspeed-i.md) | 任务的最低限速配置。若任务速度持续低于设定值并达到指定时长，则任务失败，失败原因为<br/>[LOW_SPEED](arkts-basicservices-agent-faults-e.md#Faults)。<br/> |
| [Timeout](arkts-basicservices-agent-timeout-i.md) | 任务的超时配置。任务处于等待状态的时间不参与计算，上传下载任务会存在以下任务等待的原因:<br/>[WaitingReason&lt;sup&gt;20+&lt;/sup&gt;](arkts-basicservices-agent-waitingreason-e.md#WaitingReason)<br/>。<br/> |
| [Config](arkts-basicservices-agent-config-i.md) | 上传/下载任务的配置信息。<br/> |
| [Progress](arkts-basicservices-agent-progress-i.md) | 任务进度的数据结构。<br/> |
| [Filter](arkts-basicservices-agent-filter-i.md) | 过滤条件。<br/> |
| <!--DelRow-->[Filter](arkts-basicservices-agent-filter-i-sys.md) | 过滤条件。<br/> |
| [TaskInfo](arkts-basicservices-agent-taskinfo-i.md) | 查询结果的任务信息数据结构，提供普通查询和系统查询，两种字段的可见范围不同。<br/> |
| <!--DelRow-->[TaskInfo](arkts-basicservices-agent-taskinfo-i-sys.md) | 查询结果的任务信息数据结构，提供普通查询和系统查询，两种字段的可见范围不同。<br/> |
| [HttpResponse](arkts-basicservices-agent-httpresponse-i.md) | 任务响应头的数据结构。<br/> |
| [Task](arkts-basicservices-agent-task-i.md) | 上传或下载任务。使用该方法前需要先获取Task对象，promise形式通过<br/>[request.agent.create](arkts-basicservices-agent-create-f.md#create-2)获取，<br/>callback形式通过<br/>[request.agent.create](request.agent.create(context: BaseContext, config: Config, callback: AsyncCallback&lt;Task&gt;))获取。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; Task对象及其挂载回调函数会在调用remove方法后释放并被系统自动回收。<br/> |
| [GroupConfig](arkts-basicservices-agent-groupconfig-i.md) | 下载任务分组配置选项。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Action](arkts-basicservices-agent-action-e.md) | 定义操作选项。<br/> |
| [Mode](arkts-basicservices-agent-mode-e.md) | 定义模式选项。<br/><br/>当应用的前台任务切换到后台一段时间后会显示运行失败或暂停，而后台任务不受此操作影响。<br/> |
| [Network](arkts-basicservices-agent-network-e.md) | 定义网络选项。<br/><br/>网络不满足设置条件时，未执行的任务会等待执行，执行中的任务将失败或暂停。<br/> |
| [BroadcastEvent](arkts-basicservices-agent-broadcastevent-e.md) | 定义自定义系统事件。用户可以使用公共事件接口获取该事件。<br/><br/>上传下载SA具有'ohos.permission.SEND_TASK_COMPLETE_EVENT'权限，用户可以配置事件的metadata指向的二级配置文件来拦截其他事件发送者。<br/><br/>调用CommonEventData类型传输公共事件相关数据，成员的内容填写和 [CommonEventData](arkts-basicservices-commoneventdata-i.md#CommonEventData) 介绍的<br/>有所区别，其中CommonEventData.code表示任务的状态，目前为0x40 COMPLETE或0x41 FAILED；CommonEventData.data表示任务的taskId。<br/><br/>&lt;!--Del--&gt;<br/><br/>请参考[静态订阅公共事件](../../../../basic-services/common-event/common-event-static-subscription-sys.md)以获取事件配置信息和二级配置文件的配置方式<br/>。&lt;!--DelEnd--&gt;<br/> |
| [State](arkts-basicservices-agent-state-e.md) | 定义任务当前的状态。<br/> |
| [Faults](arkts-basicservices-agent-faults-e.md) | 定义任务失败的原因。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; API version 12及以下版本，只支持串行的尝试连接域名相关ip，且不支持单个ip的连接时间控制，如果DNS返回的首个ip是阻塞的，可能会导致握手超时，进而引发TIMEOUT错误。<br/> |
| [WaitingReason](arkts-basicservices-agent-waitingreason-e.md) | 枚举，定义任务等待的原因。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |

### 常量

| 名称 | 说明 |
| --- | --- |
| [VISIBILITY_COMPLETION](arkts-basicservices-agent-con.md#VISIBILITY_COMPLETION) | [通知栏](arkts-basicservices-agent-notification-i.md#Notification) 展示类型：显示完成通知<br/> |
| [VISIBILITY_PROGRESS](arkts-basicservices-agent-con.md#VISIBILITY_PROGRESS) | [通知栏](arkts-basicservices-agent-notification-i.md#Notification) 展示类型：显示进度通知<br/> |

