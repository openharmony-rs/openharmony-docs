# ExecuteActionEvent

```TypeScript
type ExecuteActionEvent = (actionType: string, params: string) => Promise<string>
```

执行操作事件。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-type ExecuteActionEvent = (actionType: string, params: string) => Promise<string>--><!--Device-avMusicTemplate-type ExecuteActionEvent = (actionType: string, params: string) => Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| actionType | string | 是 | 动作类型。 |
| params | string | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回执行操作的结果字符串。 |

