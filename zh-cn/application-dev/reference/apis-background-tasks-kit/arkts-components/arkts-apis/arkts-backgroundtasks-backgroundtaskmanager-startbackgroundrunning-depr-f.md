# startBackgroundRunning

## 导入模块

```TypeScript
```

## startBackgroundRunning

```TypeScript
function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent, callback: AsyncCallback<void>): void
```

向系统申请长时任务，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md)(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent, callback: AsyncCallback&lt;void&gt;)

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用运行的上下文。<br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md#context)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 |
| bgMode | BackgroundMode | 是 | 向系统申请的后台模式。 |
| wantAgent | [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-depr-t.md) | 是 | 通知参数，用于指定长时任务通知点击后跳转的界面。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，申请长时任务成功时，err为undefined，否则为错误对象。 |

**示例**

```TypeScript
FA模型示例：
```

```TypeScript
Stage模型示例：
```

```TypeScript
FA模型示例（需使用js代码开发）：
```


## startBackgroundRunning

```TypeScript
function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent): Promise<void>
```

向系统申请长时任务，使用promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md)(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent)

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用运行的上下文。<br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md#context)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 |
| bgMode | BackgroundMode | 是 | 向系统申请的后台模式。 |
| wantAgent | [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-depr-t.md) | 是 | 通知参数，用于指定长时任务通知点击跳转的界面。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**示例**

参见 [startBackgroundRunning](#startbackgroundrunning)
