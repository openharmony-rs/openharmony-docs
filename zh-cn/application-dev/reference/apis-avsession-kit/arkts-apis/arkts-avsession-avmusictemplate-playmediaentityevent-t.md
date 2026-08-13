# PlayMediaEntityEvent

```TypeScript
type PlayMediaEntityEvent = (mediaEntity: MediaEntity) => Promise<void>
```

媒体实体播放事件。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-type PlayMediaEntityEvent = (mediaEntity: MediaEntity) => Promise<void>--><!--Device-avMusicTemplate-type PlayMediaEntityEvent = (mediaEntity: MediaEntity) => Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mediaEntity | [MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md) | 是 | 需要播放的媒体实体。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

