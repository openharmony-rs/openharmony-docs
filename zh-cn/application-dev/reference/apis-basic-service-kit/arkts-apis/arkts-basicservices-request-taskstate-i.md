# TaskState

上传任务的任务信息，是[on('complete' | 'fail')](request.UploadTask.on(type: 'complete' | 'fail', callback: Callback&lt;Array<TaskState>&gt;))和[off('complete' | 'fail')](request.UploadTask.off(type: 'complete' | 'fail', callback?: Callback&lt;Array<TaskState>&gt;))接口的回调参数。

**起始版本：** 9

<!--Device-request-interface TaskState--><!--Device-request-interface TaskState-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## 导入模块

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## message

```TypeScript
message: string
```

上传任务结果描述信息。

**类型：** string

**起始版本：** 9

<!--Device-TaskState-message: string--><!--Device-TaskState-message: string-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## path

```TypeScript
path: string
```

文件路径。

**类型：** string

**起始版本：** 9

<!--Device-TaskState-path: string--><!--Device-TaskState-path: string-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## responseCode

```TypeScript
responseCode: number
```

上传任务返回码。返回0表示上传任务成功，返回其它值表示上传任务失败，具体请参见message参数中的上传任务结果描述信息。

此处推荐使用[request.agent.create](arkts-basicservices-agent-create-f.md#create)创建上传任务，并获取标准错误码处理异常分支。

**类型：** number

**起始版本：** 9

<!--Device-TaskState-responseCode: int--><!--Device-TaskState-responseCode: int-End-->

**系统能力：** SystemCapability.MiscServices.Upload

