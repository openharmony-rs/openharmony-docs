# PlayForSearchEvent

```TypeScript
type PlayForSearchEvent = (command: SearchPlayInfoType, args: SearchPlayInfo) => Promise<OperResult>
```

搜播事件。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-type PlayForSearchEvent = (command: SearchPlayInfoType, args: SearchPlayInfo) => Promise<OperResult>--><!--Device-avMusicTemplate-type PlayForSearchEvent = (command: SearchPlayInfoType, args: SearchPlayInfo) => Promise<OperResult>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | [SearchPlayInfoType](arkts-avsession-avmusictemplate-searchplayinfotype-e.md) | 是 |  |
| args | [SearchPlayInfo](arkts-avsession-avmusictemplate-searchplayinfo-i.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;OperResult&gt; | Promise对象，返回搜播的操作结果对象。  |

