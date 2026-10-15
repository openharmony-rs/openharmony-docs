# agent（上传下载）

```TypeScript
namespace agent
```

The request agent api. Supports "background" and "frontend" tasks as while. Though "background" and "frontend" here do not the same with process's concept. All tasks will be executed at request manager service and recorded. Background tasks is for concurrent transfer, such as caching videos for a later play. Frontend tasks is for instant transfer, such as submitting forms for a consumption bill. Background tasks use notification to tell user tasks' status information. Frontend tasks use callback to tell caller tasks' status information.Background has some automatically restore mechanism. Frontend tasks controlled by caller. Uses `multipart/form-data` in client request for upload. A `Content-Disposition: attachment; filename=<filename>` response from server leads to download. More details, please see the architecture documents of the request subsystem. Only front-end mode is supported in cross-platform scenarios.

**起始版本：** 10

<!--Device-request-namespace agent--><!--Device-request-namespace agent-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## 导入模块

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [attachGroup](arkts-basicservices-agent-attachgroup-f.md#attachgroup) | 向指定分组id中绑定多个下载任务id。使用Promise异步回调。 |
| [create](arkts-basicservices-agent-create-f.md#create1) | 创建需要上传或下载的任务，并将其排入队列。支持HTTP/HTTPS协议，使用callback异步回调。 |
| [create](arkts-basicservices-agent-create-f.md#create2) | 创建需要上传或下载的任务，并将其排入队列。支持HTTP/HTTPS协议，使用Promise异步回调。 |
| [createGroup](arkts-basicservices-agent-creategroup-f.md#creategroup) | 根据[GroupConfig](arkts-basicservices-agent-groupconfig-i.md)分组条件创建分组，并返回分组id。使用Promise异步回调。 |
| [deleteGroup](arkts-basicservices-agent-deletegroup-f.md#deletegroup) | 移除指定分组，后续不能再往该分组中添加任务id。使用Promise异步回调。 |
| [getTask](arkts-basicservices-agent-gettask-f.md#gettask) | 根据任务id查询任务。使用Promise异步回调。 |
| [remove](arkts-basicservices-agent-remove-f.md#remove1) | 移除属于调用方的指定任务，如果正在处理中，该任务将被迫停止。使用callback异步回调。在调用后任务对象和其回调函数会被释放。 |
| [remove](arkts-basicservices-agent-remove-f.md#remove2) | 移除属于调用方的指定任务，如果正在处理中，该任务将被迫停止。使用Promise异步回调。在调用后任务对象和其回调函数会被释放。 |
| [search](arkts-basicservices-agent-search-f.md#search1) | 根据默认[Filter](arkts-basicservices-agent-filter-i.md)过滤条件查找任务id，即查询调用时刻至24小时前的所有任务的任务id。使用callback异步回调。 |
| [search](arkts-basicservices-agent-search-f.md#search2) | 根据[Filter](arkts-basicservices-agent-filter-i.md)过滤条件查找任务id。使用callback异步回调。 |
| [search](arkts-basicservices-agent-search-f.md#search3) | 根据[Filter](arkts-basicservices-agent-filter-i.md)过滤条件查找任务id。使用Promise异步回调。 |
| [show](arkts-basicservices-agent-show-f.md#show1) | 根据任务id查询任务的详细信息。使用callback异步回调。 |
| [show](arkts-basicservices-agent-show-f.md#show2) | 根据任务id查询任务的详细信息。使用Promise异步回调。 |
| [touch](arkts-basicservices-agent-touch-f.md#touch1) | 根据任务id和token查询任务的详细信息。使用callback异步回调。 |
| [touch](arkts-basicservices-agent-touch-f.md#touch2) | 根据任务id和token查询任务的详细信息。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [query](arkts-basicservices-agent-query-f-sys.md#query1) | Queries specified task details. Creates a group based on GroupConfig |
| [query](arkts-basicservices-agent-query-f-sys.md#query2) | Queries specified task details. |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [Config](arkts-basicservices-agent-config-i.md) | 上传/下载任务的配置信息。 |
| [FileSpec](arkts-basicservices-agent-filespec-i.md) | 表单项的文件信息。 |
| [Filter](arkts-basicservices-agent-filter-i.md) | 过滤条件。 |
| [FormItem](arkts-basicservices-agent-formitem-i.md) | 任务的表单项信息。 |
| [GroupConfig](arkts-basicservices-agent-groupconfig-i.md) | 下载任务分组配置选项。 |
| [HttpResponse](arkts-basicservices-agent-httpresponse-i.md) | 任务响应头的数据结构。 |
| [MinSpeed](arkts-basicservices-agent-minspeed-i.md) | 任务的最低限速配置。若任务速度持续低于设定值并达到指定时长，则任务失败，失败原因为[LOW_SPEED](arkts-basicservices-agent-faults-e.md)。 |
| [Notification](arkts-basicservices-agent-notification-i.md) | 通知栏自定义信息。 |
| [Progress](arkts-basicservices-agent-progress-i.md) | 任务进度的数据结构。 |
| [Task](arkts-basicservices-agent-task-i.md) | 上传或下载任务。使用该方法前需要先获取Task对象，promise形式通过[request.agent.create](arkts-basicservices-agent-create-f.md#create2)获取，callback形式通过[request.agent.create](arkts-basicservices-agent-create-f.md#create1)获取。 |
| [TaskInfo](arkts-basicservices-agent-taskinfo-i.md) | 查询结果的任务信息数据结构，提供普通查询和系统查询，两种字段的可见范围不同。 |
| [Timeout](arkts-basicservices-agent-timeout-i.md) | 任务的超时配置。任务处于等待状态的时间不参与计算，上传下载任务会存在以下任务等待的原因: [WaitingReason<sup>20+</sup>](arkts-basicservices-agent-waitingreason-e.md)。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Filter](arkts-basicservices-agent-filter-i-sys.md) | 过滤条件。 |
| [Notification](arkts-basicservices-agent-notification-i-sys.md) | 通知栏自定义信息。 |
| [TaskInfo](arkts-basicservices-agent-taskinfo-i-sys.md) | 查询结果的任务信息数据结构，提供普通查询和系统查询，两种字段的可见范围不同。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Action](arkts-basicservices-agent-action-e.md) | 定义操作选项。 |
| [BroadcastEvent](arkts-basicservices-agent-broadcastevent-e.md) | 定义自定义系统事件。用户可以使用公共事件接口获取该事件。 |
| [Faults](arkts-basicservices-agent-faults-e.md) | 定义任务失败的原因。 |
| [Mode](arkts-basicservices-agent-mode-e.md) | 定义模式选项。 |
| [Network](arkts-basicservices-agent-network-e.md) | 定义网络选项。 |
| [State](arkts-basicservices-agent-state-e.md) | 定义任务当前的状态。 |
| [WaitingReason](arkts-basicservices-agent-waitingreason-e.md) | 枚举，定义任务等待的原因。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [VISIBILITY_COMPLETION](arkts-basicservices-agent-con.md#visibility_completion) | [通知栏](arkts-basicservices-agent-notification-i.md) 展示类型：显示完成通知 |
| [VISIBILITY_PROGRESS](arkts-basicservices-agent-con.md#visibility_progress) | [通知栏](arkts-basicservices-agent-notification-i.md) 展示类型：显示进度通知 |
