# QueryCompilationByKeywordEvent

```TypeScript
type QueryCompilationByKeywordEvent = (keyword: string) => Promise<Compilation[]>
```

按关键字查询合集的事件。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-type QueryCompilationByKeywordEvent = (keyword: string) => Promise<Compilation[]>--><!--Device-avMusicTemplate-type QueryCompilationByKeywordEvent = (keyword: string) => Promise<Compilation[]>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyword | string | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Compilation[]&gt; | Promise对象，返回与关键字相关的合集数组。  |

