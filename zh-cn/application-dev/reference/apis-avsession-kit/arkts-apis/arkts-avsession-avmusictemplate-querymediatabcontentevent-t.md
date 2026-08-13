# QueryMediaTabContentEvent

```TypeScript
type QueryMediaTabContentEvent = (tabId: string) => Promise<MediaTabContent>
```

媒体标签页内容查询事件。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-type QueryMediaTabContentEvent = (tabId: string) => Promise<MediaTabContent>--><!--Device-avMusicTemplate-type QueryMediaTabContentEvent = (tabId: string) => Promise<MediaTabContent>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tabId | string | 是 | 标签页的ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[MediaTabContent](arkts-avsession-avmusictemplate-mediatabcontent-i.md)&gt; | Promise对象，返回媒体标签页内容。 |

