# TaskState

上传任务的任务信息，是 [on('complete' | 'fail')]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 和 [off('complete' | 'fail')]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 接口的回调参数。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-request-interface TaskState--><!--Device-request-interface TaskState-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## message

```TypeScript
message: string
```

上传任务结果描述信息。

**类型：** string

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-TaskState-message: string--><!--Device-TaskState-message: string-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## path

```TypeScript
path: string
```

文件路径。

**类型：** string

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-TaskState-path: string--><!--Device-TaskState-path: string-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## responseCode

```TypeScript
responseCode: int
```

上传任务返回码。返回0表示上传任务成功，返回其它值表示上传任务失败，具体请参见message参数中的上传任务结果描述信息。 此处推荐使用 [request.agent.create]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_创建上传 任务，并获取标准错误码处理异常分支。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-TaskState-responseCode: int--><!--Device-TaskState-responseCode: int-End-->

**系统能力：** SystemCapability.MiscServices.Upload

