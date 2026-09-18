# agent(Upload and Download)

The request agent api. Supports "background" and "frontend" tasks as while. Though "background" and "frontend" here do not the same with process's concept. All tasks will be executed at request manager service and recorded. Background tasks is for concurrent transfer, such as caching videos for a later play. Frontend tasks is for instant transfer, such as submitting forms for a consumption bill. Background tasks use notification to tell user tasks' status information. Frontend tasks use callback to tell caller tasks' status information. Background has some automatically restore mechanism. Frontend tasks controlled by caller. Uses `multipart/form-data` in client request for upload. A `Content-Disposition: attachment; filename=&lt;filename&gt;` response from server leads to download. More details, please see the architecture documents of the request subsystem. Only front-end mode is supported in cross-platform scenarios.

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [create](arkts-basicservices-agent-create-f.md) | Creates an upload or download task and adds it to the queue. This API uses an asynchronous callback to return the result. HTTP/HTTPS is supported. |
| [create](arkts-basicservices-agent-create-f.md) | Creates an upload or download task and adds it to the queue. This API uses a promise to return the result. HTTP/ HTTPS is supported. |
| [getTask](arkts-basicservices-agent-gettask-f.md) | Obtains task information based on the task ID. This API uses a promise to return the result. |
| [remove](arkts-basicservices-agent-remove-f.md) | Removes a specified task of the invoker. If the task is being executed, the task is forced to stop. This API uses an asynchronous callback to return the result. After this API is called, the **task** object and its callback function are released. |
| [remove](arkts-basicservices-agent-remove-f.md) | Removes a specified task of the invoker. If the task is being executed, the task is forced to stop. This API uses a promise to return the result. After this API is called, the **task** object and its callback function are released. |
| [show](arkts-basicservices-agent-show-f.md) | Queries the task details based on the task ID. This API uses an asynchronous callback to return the result. |
| [show](arkts-basicservices-agent-show-f.md) | Queries the task details based on the task ID. This API uses a promise to return the result. |
| [touch](arkts-basicservices-agent-touch-f.md) | Queries the task details based on the task ID and token. This API uses an asynchronous callback to return the result. |
| [touch](arkts-basicservices-agent-touch-f.md) | Queries the task details based on the task ID and token. This API uses a promise to return the result. |
| [search](arkts-basicservices-agent-search-f.md) | Searches for task IDs based on [Filter](arkts-basicservices-agent-filter-i.md). The IDs of all tasks from the invoking time to 24 hours ago are searched. This API uses an asynchronous callback to return the result. |
| [search](arkts-basicservices-agent-search-f.md) | Searches for task IDs based on [Filter](arkts-basicservices-agent-filter-i.md). This API uses an asynchronous callback to return the result. |
| [search](arkts-basicservices-agent-search-f.md) | Searches for task IDs based on [Filter](arkts-basicservices-agent-filter-i.md). This API uses a promise to return the result. |
| [createGroup](arkts-basicservices-agent-creategroup-f.md) | Creates a group based on [GroupConfig](arkts-basicservices-agent-groupconfig-i.md). This API uses a promise to return the result. |
| [attachGroup](arkts-basicservices-agent-attachgroup-f.md) | Attaches multiple download task IDs to a specified group ID. This API uses a promise to return the result. |
| [deleteGroup](arkts-basicservices-agent-deletegroup-f.md) | Deletes a specified group. No task ID can be added to the group. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [query](arkts-basicservices-agent-query-f-sys.md) | Queries specified task details. Creates a group based on GroupConfig |
| [query](arkts-basicservices-agent-query-f-sys.md) | Queries specified task details. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [FileSpec](arkts-basicservices-agent-filespec-i.md) | Provides the file information of a table item. |
| [FormItem](arkts-basicservices-agent-formitem-i.md) | Describes the form item of a task. |
| [Notification](arkts-basicservices-agent-notification-i.md) | Describes the custom information of the notification bar. |
| [MinSpeed](arkts-basicservices-agent-minspeed-i.md) | Defines the minimum speed of a task. If the task speed is lower than the preset value for a specified period of time, the task fails. The failure cause is [LOW_SPEED](arkts-basicservices-agent-faults-e.md). |
| [Timeout](arkts-basicservices-agent-timeout-i.md) | Defines the timeout configuration of a task. The task waiting duration is not counted. For details about the waiting reasons, see [WaitingReason&lt;sup&gt;20+&lt;/sup&gt;](arkts-basicservices-agent-waitingreason-e.md). |
| [Config](arkts-basicservices-agent-config-i.md) | Provides the configuration information of an upload or download task. |
| [Progress](arkts-basicservices-agent-progress-i.md) | Describes the data structure of the task progress. |
| [Filter](arkts-basicservices-agent-filter-i.md) | Defines the filter criteria. |
| [TaskInfo](arkts-basicservices-agent-taskinfo-i.md) | Defines the data structure of the task information for query. The fields available vary depending on the query type. |
| [HttpResponse](arkts-basicservices-agent-httpresponse-i.md) | Describes the data structure of the task response header. |
| [Task](arkts-basicservices-agent-task-i.md) | Implements an upload or download task. Before using this API, you must obtain a **Task** object, from a promise through [request.agent.create](arkts-basicservices-agent-create-f.md) or from a callback through [request.agent.create](arkts-basicservices-agent-create-f.md). |
| [GroupConfig](arkts-basicservices-agent-groupconfig-i.md) | Describes group configuration options for download tasks. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [Notification](arkts-basicservices-agent-notification-i-sys.md) | Describes the custom information of the notification bar. |
| [Filter](arkts-basicservices-agent-filter-i-sys.md) | Defines the filter criteria. |
| [TaskInfo](arkts-basicservices-agent-taskinfo-i-sys.md) | Defines the data structure of the task information for query. The fields available vary depending on the query type. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [Action](arkts-basicservices-agent-action-e.md) | Defines action options. |
| [Mode](arkts-basicservices-agent-mode-e.md) | Defines mode options. |
| [Network](arkts-basicservices-agent-network-e.md) | Defines network options. |
| [BroadcastEvent](arkts-basicservices-agent-broadcastevent-e.md) | Defines a custom system event. You can use a common event API to obtain the event. |
| [State](arkts-basicservices-agent-state-e.md) | Defines the current task status. |
| [Faults](arkts-basicservices-agent-faults-e.md) | Defines the cause of a task failure. |
| [WaitingReason](arkts-basicservices-agent-waitingreason-e.md) | Enumerates the reasons why a task is waiting. |

### Constants

| Name | Description |
| --- | --- |
| [VISIBILITY_COMPLETION](arkts-basicservices-agent-con.md#visibility_completion) | ([Notification](arkts-basicservices-agent-notification-i.md) visibility type) Displays completion notifications. |
| [VISIBILITY_PROGRESS](arkts-basicservices-agent-con.md#visibility_progress) | ([Notification](arkts-basicservices-agent-notification-i.md) visibility type) Displays progress notifications. |
