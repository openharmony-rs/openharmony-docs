# CustomCommandEvent

```TypeScript
type CustomCommandEvent = (command: string, args: string) => Promise<OperResult>
```

带有事件和参数的通用处理函数。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-type CustomCommandEvent = (command: string, args: string) => Promise<OperResult>--><!--Device-avMusicTemplate-type CustomCommandEvent = (command: string, args: string) => Promise<OperResult>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | string | 是 | 请求事件。 |
| args | string | 是 | 请求事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[OperResult](arkts-avsession-avmusictemplate-operresult-i.md)&gt; | Promise用于返回OperResult。 |
