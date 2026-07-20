# AVMusicTemplate

调用[avMusicTemplate.createAVMusicTemplate](arkts-avsession-avmusictemplate-createavmusictemplate-f.md#createavmusictemplate-1)获取实例后，可获取其ID，启动音频模板界面，并配置数据获取方法。随后，同步数据给模板控制方，以完成后续操作。

> **说明：**  
>  
> - 本模块仅适用于API version 23及以上版本的Car设备。

**起始版本：** 23

<!--Device-avMusicTemplate-class AVMusicTemplate--><!--Device-avMusicTemplate-class AVMusicTemplate-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## 导入模块

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

<a id="destroy"></a>
## destroy

```TypeScript
destroy(): Promise<void>
```

销毁音频模板实例。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-destroy(): Promise<void>--><!--Device-AVMusicTemplate-destroy(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function destroy can not work correctly due to limited device capabilities. |

<a id="offclearsearchhistory"></a>
## offClearSearchHistory

```TypeScript
offClearSearchHistory(callback?: ClearSearchHistoryEvent): void
```

注销清除搜索历史的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offClearSearchHistory(callback?: ClearSearchHistoryEvent): void--><!--Device-AVMusicTemplate-offClearSearchHistory(callback?: ClearSearchHistoryEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ClearSearchHistoryEvent](arkts-avsession-avmusictemplate-clearsearchhistoryevent-t.md) | 否 | 清除搜索历史的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offClearSearchHistory can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offdownloadmediaentity"></a>
## offDownloadMediaEntity

```TypeScript
offDownloadMediaEntity(callback?: DownloadMediaEntityEvent): void
```

注销下载媒体实体事件的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offDownloadMediaEntity(callback?: DownloadMediaEntityEvent): void--><!--Device-AVMusicTemplate-offDownloadMediaEntity(callback?: DownloadMediaEntityEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [DownloadMediaEntityEvent](arkts-avsession-avmusictemplate-downloadmediaentityevent-t.md) | 否 | 下载媒体实体的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offDownloadMediaEntity can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offexecuteaction"></a>
## offExecuteAction

```TypeScript
offExecuteAction(callback?: ExecuteActionEvent): void
```

注销执行操作事件的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offExecuteAction(callback?: ExecuteActionEvent): void--><!--Device-AVMusicTemplate-offExecuteAction(callback?: ExecuteActionEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ExecuteActionEvent](arkts-avsession-avmusictemplate-executeactionevent-t.md) | 否 | 执行操作的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offExecuteAction can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offfavoritemediaentity"></a>
## offFavoriteMediaEntity

```TypeScript
offFavoriteMediaEntity(callback?: FavoriteMediaEntityEvent): void
```

注销收藏媒体实体事件的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offFavoriteMediaEntity(callback?: FavoriteMediaEntityEvent): void--><!--Device-AVMusicTemplate-offFavoriteMediaEntity(callback?: FavoriteMediaEntityEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [FavoriteMediaEntityEvent](arkts-avsession-avmusictemplate-favoritemediaentityevent-t.md) | 否 | 收藏媒体实体的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offFavoriteMediaEntity can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offhandlememberpurchase"></a>
## offHandleMemberPurchase

```TypeScript
offHandleMemberPurchase(callback?: HandleMemberPurchaseEvent): void
```

注销处理购买会员事件的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offHandleMemberPurchase(callback?: HandleMemberPurchaseEvent): void--><!--Device-AVMusicTemplate-offHandleMemberPurchase(callback?: HandleMemberPurchaseEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [HandleMemberPurchaseEvent](arkts-avsession-avmusictemplate-handlememberpurchaseevent-t.md) | 否 | 处理购买会员的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offHandleMemberPurchase can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offlogin"></a>
## offLogin

```TypeScript
offLogin(callback?: LoginEvent): void
```

注销登录事件的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offLogin(callback?: LoginEvent): void--><!--Device-AVMusicTemplate-offLogin(callback?: LoginEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [LoginEvent](arkts-avsession-avmusictemplate-loginevent-t.md) | 否 | 登录事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offLogin can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offplayforsearch"></a>
## offPlayForSearch

```TypeScript
offPlayForSearch(callback?: PlayForSearchEvent): void
```

注销搜播事件的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offPlayForSearch(callback?: PlayForSearchEvent): void--><!--Device-AVMusicTemplate-offPlayForSearch(callback?: PlayForSearchEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [PlayForSearchEvent](arkts-avsession-avmusictemplate-playforsearchevent-t.md) | 否 | 搜播的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offPlayForSearch can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offplaymediaentity"></a>
## offPlayMediaEntity

```TypeScript
offPlayMediaEntity(callback?: PlayMediaEntityEvent): void
```

注销播放媒体实体事件的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offPlayMediaEntity(callback?: PlayMediaEntityEvent): void--><!--Device-AVMusicTemplate-offPlayMediaEntity(callback?: PlayMediaEntityEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [PlayMediaEntityEvent](arkts-avsession-avmusictemplate-playmediaentityevent-t.md) | 否 | 播放媒体实体的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offPlayMediaEntity can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offproblemandadvice"></a>
## offProblemAndAdvice

```TypeScript
offProblemAndAdvice(callback?: ProblemAndAdviceEvent): void
```

注销问题与建议事件的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offProblemAndAdvice(callback?: ProblemAndAdviceEvent): void--><!--Device-AVMusicTemplate-offProblemAndAdvice(callback?: ProblemAndAdviceEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ProblemAndAdviceEvent](arkts-avsession-avmusictemplate-problemandadviceevent-t.md) | 否 | 处理问题与建议的回调。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offProblemAndAdvice can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offquerycompilation"></a>
## offQueryCompilation

```TypeScript
offQueryCompilation(callback?: QueryCompilationEvent): void
```

注销查询合集的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offQueryCompilation(callback?: QueryCompilationEvent): void--><!--Device-AVMusicTemplate-offQueryCompilation(callback?: QueryCompilationEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryCompilationEvent](arkts-avsession-avmusictemplate-querycompilationevent-t.md) | 否 | 查询合集的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offQueryCompilation can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offquerycompilationbykeyword"></a>
## offQueryCompilationByKeyword

```TypeScript
offQueryCompilationByKeyword(callback?: QueryCompilationByKeywordEvent): void
```

注销按关键字查询合集的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offQueryCompilationByKeyword(callback?: QueryCompilationByKeywordEvent): void--><!--Device-AVMusicTemplate-offQueryCompilationByKeyword(callback?: QueryCompilationByKeywordEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryCompilationByKeywordEvent](arkts-avsession-avmusictemplate-querycompilationbykeywordevent-t.md) | 否 | 按关键字查询合集的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offQueryCompilationByKeyword can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offquerycurrentsingle"></a>
## offQueryCurrentSingle

```TypeScript
offQueryCurrentSingle(callback?: QueryCurrentSingleEvent): void
```

注销查询当前单曲的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offQueryCurrentSingle(callback?: QueryCurrentSingleEvent): void--><!--Device-AVMusicTemplate-offQueryCurrentSingle(callback?: QueryCurrentSingleEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryCurrentSingleEvent](arkts-avsession-avmusictemplate-querycurrentsingleevent-t.md) | 否 | 查询当前单曲的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offQueryCurrentSingle can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offquerycustomcontent"></a>
## offQueryCustomContent

```TypeScript
offQueryCustomContent(callback?: QueryCustomContentEvent): void
```

注销查询自定义内容事件的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offQueryCustomContent(callback?: QueryCustomContentEvent): void--><!--Device-AVMusicTemplate-offQueryCustomContent(callback?: QueryCustomContentEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryCustomContentEvent](arkts-avsession-avmusictemplate-querycustomcontentevent-t.md) | 否 | 查询自定义内容的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offQueryCustomContent can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offqueryhotwords"></a>
## offQueryHotWords

```TypeScript
offQueryHotWords(callback?: QueryHotWordsEvent): void
```

注销查询热词的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offQueryHotWords(callback?: QueryHotWordsEvent): void--><!--Device-AVMusicTemplate-offQueryHotWords(callback?: QueryHotWordsEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryHotWordsEvent](arkts-avsession-avmusictemplate-queryhotwordsevent-t.md) | 否 | 查询热词的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offQueryHotWords can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offquerymaintabs"></a>
## offQueryMainTabs

```TypeScript
offQueryMainTabs(callback?: QueryMainTabsEvent): void
```

注销查询主标签事件监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offQueryMainTabs(callback?: QueryMainTabsEvent): void--><!--Device-AVMusicTemplate-offQueryMainTabs(callback?: QueryMainTabsEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryMainTabsEvent](arkts-avsession-avmusictemplate-querymaintabsevent-t.md) | 否 | 查询主标签事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offQueryMainTabs can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offquerymediaentity"></a>
## offQueryMediaEntity

```TypeScript
offQueryMediaEntity(callback?: QueryMediaEntityEvent): void
```

注销查询媒体实体监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offQueryMediaEntity(callback?: QueryMediaEntityEvent): void--><!--Device-AVMusicTemplate-offQueryMediaEntity(callback?: QueryMediaEntityEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryMediaEntityEvent](arkts-avsession-avmusictemplate-querymediaentityevent-t.md) | 否 | 查询媒体实体的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offQueryMediaEntity can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offquerymediaentitybykeyword"></a>
## offQueryMediaEntityByKeyword

```TypeScript
offQueryMediaEntityByKeyword(callback?: QueryMediaEntityByKeywordEvent): void
```

注销按关键字查询媒体实体的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offQueryMediaEntityByKeyword(callback?: QueryMediaEntityByKeywordEvent): void--><!--Device-AVMusicTemplate-offQueryMediaEntityByKeyword(callback?: QueryMediaEntityByKeywordEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryMediaEntityByKeywordEvent](arkts-avsession-avmusictemplate-querymediaentitybykeywordevent-t.md) | 否 | 按关键字查询媒体实体的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offQueryMediaEntityByKeyword can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offquerymediatabcontent"></a>
## offQueryMediaTabContent

```TypeScript
offQueryMediaTabContent(callback?: QueryMediaTabContentEvent): void
```

取消查询媒体标签内容监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offQueryMediaTabContent(callback?: QueryMediaTabContentEvent): void--><!--Device-AVMusicTemplate-offQueryMediaTabContent(callback?: QueryMediaTabContentEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryMediaTabContentEvent](arkts-avsession-avmusictemplate-querymediatabcontentevent-t.md) | 否 | 查询媒体标签页内容的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offQueryMediaTabContent can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offquerymemberpurchase"></a>
## offQueryMemberPurchase

```TypeScript
offQueryMemberPurchase(callback?: QueryMemberPurchaseEvent): void
```

注销查询购买会员事件的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offQueryMemberPurchase(callback?: QueryMemberPurchaseEvent): void--><!--Device-AVMusicTemplate-offQueryMemberPurchase(callback?: QueryMemberPurchaseEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryMemberPurchaseEvent](arkts-avsession-avmusictemplate-querymemberpurchaseevent-t.md) | 否 | 查询购买会员的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offQueryMemberPurchase can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offqueryplaylist"></a>
## offQueryPlaylist

```TypeScript
offQueryPlaylist(callback?: QueryPlaylistEvent): void
```

注销查询播放列表的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offQueryPlaylist(callback?: QueryPlaylistEvent): void--><!--Device-AVMusicTemplate-offQueryPlaylist(callback?: QueryPlaylistEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryPlaylistEvent](arkts-avsession-avmusictemplate-queryplaylistevent-t.md) | 否 | 查询播放列表的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offQueryPlaylist can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offqueryrecommendmediaentitylist"></a>
## offQueryRecommendMediaEntityList

```TypeScript
offQueryRecommendMediaEntityList(callback?: QueryRecommendMediaEntityListEvent): void
```

注销查询推荐媒体列表的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offQueryRecommendMediaEntityList(callback?: QueryRecommendMediaEntityListEvent): void--><!--Device-AVMusicTemplate-offQueryRecommendMediaEntityList(callback?: QueryRecommendMediaEntityListEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryRecommendMediaEntityListEvent](arkts-avsession-avmusictemplate-queryrecommendmediaentitylistevent-t.md) | 否 | 查询推荐媒体列表的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offQueryRecommendMediaEntityList can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offquerysearchhistory"></a>
## offQuerySearchHistory

```TypeScript
offQuerySearchHistory(callback?: QuerySearchHistoryEvent): void
```

注销查询搜索历史的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offQuerySearchHistory(callback?: QuerySearchHistoryEvent): void--><!--Device-AVMusicTemplate-offQuerySearchHistory(callback?: QuerySearchHistoryEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QuerySearchHistoryEvent](arkts-avsession-avmusictemplate-querysearchhistoryevent-t.md) | 否 | 查询搜索历史的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offQuerySearchHistory can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offrequestdialoginfo"></a>
## offRequestDialogInfo

```TypeScript
offRequestDialogInfo(callback?: RequestDialogInfoEvent): void
```

注销请求对话框信息的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offRequestDialogInfo(callback?: RequestDialogInfoEvent): void--><!--Device-AVMusicTemplate-offRequestDialogInfo(callback?: RequestDialogInfoEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [RequestDialogInfoEvent](arkts-avsession-avmusictemplate-requestdialoginfoevent-t.md) | 否 | 请求对话框信息的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offRequestDialogInfo can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="offsettingschange"></a>
## offSettingsChange

```TypeScript
offSettingsChange(callback?: SettingsChangeEvent): void
```

注销设置改变事件的监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-offSettingsChange(callback?: SettingsChangeEvent): void--><!--Device-AVMusicTemplate-offSettingsChange(callback?: SettingsChangeEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [SettingsChangeEvent](arkts-avsession-avmusictemplate-settingschangeevent-t.md) | 否 | 设置改变的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offSettingsChange can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onclearsearchhistory"></a>
## onClearSearchHistory

```TypeScript
onClearSearchHistory(callback: ClearSearchHistoryEvent): void
```

注册清除搜索历史的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onClearSearchHistory(callback: ClearSearchHistoryEvent): void--><!--Device-AVMusicTemplate-onClearSearchHistory(callback: ClearSearchHistoryEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ClearSearchHistoryEvent](arkts-avsession-avmusictemplate-clearsearchhistoryevent-t.md) | 是 | 回调函数，返回清除搜索历史的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onClearSearchHistory can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="ondownloadmediaentity"></a>
## onDownloadMediaEntity

```TypeScript
onDownloadMediaEntity(callback: DownloadMediaEntityEvent): void
```

注册下载媒体实体事件的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onDownloadMediaEntity(callback: DownloadMediaEntityEvent): void--><!--Device-AVMusicTemplate-onDownloadMediaEntity(callback: DownloadMediaEntityEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [DownloadMediaEntityEvent](arkts-avsession-avmusictemplate-downloadmediaentityevent-t.md) | 是 | 回调函数，返回下载媒体实体的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onDownloadMediaEntity can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onexecuteaction"></a>
## onExecuteAction

```TypeScript
onExecuteAction(callback: ExecuteActionEvent): void
```

注册执行操作事件的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onExecuteAction(callback: ExecuteActionEvent): void--><!--Device-AVMusicTemplate-onExecuteAction(callback: ExecuteActionEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ExecuteActionEvent](arkts-avsession-avmusictemplate-executeactionevent-t.md) | 是 | 回调函数，返回执行操作的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onExecuteAction can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onfavoritemediaentity"></a>
## onFavoriteMediaEntity

```TypeScript
onFavoriteMediaEntity(callback: FavoriteMediaEntityEvent): void
```

注册收藏媒体实体事件的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onFavoriteMediaEntity(callback: FavoriteMediaEntityEvent): void--><!--Device-AVMusicTemplate-onFavoriteMediaEntity(callback: FavoriteMediaEntityEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [FavoriteMediaEntityEvent](arkts-avsession-avmusictemplate-favoritemediaentityevent-t.md) | 是 | 回调函数，返回收藏媒体实体的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onFavoriteMediaEntity can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onhandlememberpurchase"></a>
## onHandleMemberPurchase

```TypeScript
onHandleMemberPurchase(callback: HandleMemberPurchaseEvent): void
```

注册处理购买会员事件的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onHandleMemberPurchase(callback: HandleMemberPurchaseEvent): void--><!--Device-AVMusicTemplate-onHandleMemberPurchase(callback: HandleMemberPurchaseEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [HandleMemberPurchaseEvent](arkts-avsession-avmusictemplate-handlememberpurchaseevent-t.md) | 是 | 回调函数，返回处理购买会员的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onHandleMemberPurchase can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onlogin"></a>
## onLogin

```TypeScript
onLogin(callback: LoginEvent): void
```

注册登录事件的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onLogin(callback: LoginEvent): void--><!--Device-AVMusicTemplate-onLogin(callback: LoginEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [LoginEvent](arkts-avsession-avmusictemplate-loginevent-t.md) | 是 | 回调函数，返回登录事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onLogin can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onplayforsearch"></a>
## onPlayForSearch

```TypeScript
onPlayForSearch(callback: PlayForSearchEvent): void
```

注册搜播事件的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onPlayForSearch(callback: PlayForSearchEvent): void--><!--Device-AVMusicTemplate-onPlayForSearch(callback: PlayForSearchEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [PlayForSearchEvent](arkts-avsession-avmusictemplate-playforsearchevent-t.md) | 是 | 回调函数，返回搜播的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onPlayForSearch can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onplaymediaentity"></a>
## onPlayMediaEntity

```TypeScript
onPlayMediaEntity(callback: PlayMediaEntityEvent): void
```

注册播放媒体实体事件的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onPlayMediaEntity(callback: PlayMediaEntityEvent): void--><!--Device-AVMusicTemplate-onPlayMediaEntity(callback: PlayMediaEntityEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [PlayMediaEntityEvent](arkts-avsession-avmusictemplate-playmediaentityevent-t.md) | 是 | 回调函数，返回播放媒体实体的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onPlayMediaEntity can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onproblemandadvice"></a>
## onProblemAndAdvice

```TypeScript
onProblemAndAdvice(callback: ProblemAndAdviceEvent): void
```

注册问题与建议事件的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onProblemAndAdvice(callback: ProblemAndAdviceEvent): void--><!--Device-AVMusicTemplate-onProblemAndAdvice(callback: ProblemAndAdviceEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ProblemAndAdviceEvent](arkts-avsession-avmusictemplate-problemandadviceevent-t.md) | 是 | 回调函数，返回问题与建议的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onProblemAndAdvice can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onquerycompilation"></a>
## onQueryCompilation

```TypeScript
onQueryCompilation(callback: QueryCompilationEvent): void
```

注册查询合集的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onQueryCompilation(callback: QueryCompilationEvent): void--><!--Device-AVMusicTemplate-onQueryCompilation(callback: QueryCompilationEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryCompilationEvent](arkts-avsession-avmusictemplate-querycompilationevent-t.md) | 是 | 回调函数，返回查询合集的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onQueryCompilation can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onquerycompilationbykeyword"></a>
## onQueryCompilationByKeyword

```TypeScript
onQueryCompilationByKeyword(callback: QueryCompilationByKeywordEvent): void
```

注册按关键字查询合集的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onQueryCompilationByKeyword(callback: QueryCompilationByKeywordEvent): void--><!--Device-AVMusicTemplate-onQueryCompilationByKeyword(callback: QueryCompilationByKeywordEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryCompilationByKeywordEvent](arkts-avsession-avmusictemplate-querycompilationbykeywordevent-t.md) | 是 | 回调函数，返回按关键字查询合集的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onQueryCompilationByKeyword can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onquerycurrentsingle"></a>
## onQueryCurrentSingle

```TypeScript
onQueryCurrentSingle(callback: QueryCurrentSingleEvent): void
```

注册查询当前单曲的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onQueryCurrentSingle(callback: QueryCurrentSingleEvent): void--><!--Device-AVMusicTemplate-onQueryCurrentSingle(callback: QueryCurrentSingleEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryCurrentSingleEvent](arkts-avsession-avmusictemplate-querycurrentsingleevent-t.md) | 是 | 回调函数，返回查询当前单曲的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onQueryCurrentSingle can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onquerycustomcontent"></a>
## onQueryCustomContent

```TypeScript
onQueryCustomContent(callback: QueryCustomContentEvent): void
```

注册查询自定义内容事件的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onQueryCustomContent(callback: QueryCustomContentEvent): void--><!--Device-AVMusicTemplate-onQueryCustomContent(callback: QueryCustomContentEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryCustomContentEvent](arkts-avsession-avmusictemplate-querycustomcontentevent-t.md) | 是 | 回调函数，返回查询自定义内容的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onQueryCustomContent can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onqueryhotwords"></a>
## onQueryHotWords

```TypeScript
onQueryHotWords(callback: QueryHotWordsEvent): void
```

注册查询热词的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onQueryHotWords(callback: QueryHotWordsEvent): void--><!--Device-AVMusicTemplate-onQueryHotWords(callback: QueryHotWordsEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryHotWordsEvent](arkts-avsession-avmusictemplate-queryhotwordsevent-t.md) | 是 | 回调函数，返回查询热词的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onQueryHotWords can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onquerymaintabs"></a>
## onQueryMainTabs

```TypeScript
onQueryMainTabs(callback: QueryMainTabsEvent): void
```

注册查询主标签的事件监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onQueryMainTabs(callback: QueryMainTabsEvent): void--><!--Device-AVMusicTemplate-onQueryMainTabs(callback: QueryMainTabsEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryMainTabsEvent](arkts-avsession-avmusictemplate-querymaintabsevent-t.md) | 是 | 回调函数，返回查询主标签事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onQueryMainTabs can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onquerymediaentity"></a>
## onQueryMediaEntity

```TypeScript
onQueryMediaEntity(callback: QueryMediaEntityEvent): void
```

注册查询媒体实体监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onQueryMediaEntity(callback: QueryMediaEntityEvent): void--><!--Device-AVMusicTemplate-onQueryMediaEntity(callback: QueryMediaEntityEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryMediaEntityEvent](arkts-avsession-avmusictemplate-querymediaentityevent-t.md) | 是 | 回调函数，返回查询媒体实体的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onQueryMediaEntity can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onquerymediaentitybykeyword"></a>
## onQueryMediaEntityByKeyword

```TypeScript
onQueryMediaEntityByKeyword(callback: QueryMediaEntityByKeywordEvent): void
```

注册按关键字查询媒体实体的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onQueryMediaEntityByKeyword(callback: QueryMediaEntityByKeywordEvent): void--><!--Device-AVMusicTemplate-onQueryMediaEntityByKeyword(callback: QueryMediaEntityByKeywordEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryMediaEntityByKeywordEvent](arkts-avsession-avmusictemplate-querymediaentitybykeywordevent-t.md) | 是 | 回调函数，返回按关键字查询媒体实体的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onQueryMediaEntityByKeyword can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onquerymediatabcontent"></a>
## onQueryMediaTabContent

```TypeScript
onQueryMediaTabContent(callback: QueryMediaTabContentEvent): void
```

注册查询媒体标签内容事件监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onQueryMediaTabContent(callback: QueryMediaTabContentEvent): void--><!--Device-AVMusicTemplate-onQueryMediaTabContent(callback: QueryMediaTabContentEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryMediaTabContentEvent](arkts-avsession-avmusictemplate-querymediatabcontentevent-t.md) | 是 | 回调函数，返回查询媒体标签页内容的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onQueryMediaTabContent can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onquerymemberpurchase"></a>
## onQueryMemberPurchase

```TypeScript
onQueryMemberPurchase(callback: QueryMemberPurchaseEvent): void
```

注册查询购买会员事件的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onQueryMemberPurchase(callback: QueryMemberPurchaseEvent): void--><!--Device-AVMusicTemplate-onQueryMemberPurchase(callback: QueryMemberPurchaseEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryMemberPurchaseEvent](arkts-avsession-avmusictemplate-querymemberpurchaseevent-t.md) | 是 | 回调函数，返回查询购买会员的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onQueryMemberPurchase can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onqueryplaylist"></a>
## onQueryPlaylist

```TypeScript
onQueryPlaylist(callback: QueryPlaylistEvent): void
```

注册查询播放列表的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onQueryPlaylist(callback: QueryPlaylistEvent): void--><!--Device-AVMusicTemplate-onQueryPlaylist(callback: QueryPlaylistEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryPlaylistEvent](arkts-avsession-avmusictemplate-queryplaylistevent-t.md) | 是 | 回调函数，返回查询播放列表的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onQueryPlaylist can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onqueryrecommendmediaentitylist"></a>
## onQueryRecommendMediaEntityList

```TypeScript
onQueryRecommendMediaEntityList(callback: QueryRecommendMediaEntityListEvent): void
```

注册查询推荐媒体列表的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onQueryRecommendMediaEntityList(callback: QueryRecommendMediaEntityListEvent): void--><!--Device-AVMusicTemplate-onQueryRecommendMediaEntityList(callback: QueryRecommendMediaEntityListEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QueryRecommendMediaEntityListEvent](arkts-avsession-avmusictemplate-queryrecommendmediaentitylistevent-t.md) | 是 | 回调函数，返回查询推荐媒体列表的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onQueryRecommendMediaEntityList can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onquerysearchhistory"></a>
## onQuerySearchHistory

```TypeScript
onQuerySearchHistory(callback: QuerySearchHistoryEvent): void
```

注册查询搜索历史的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onQuerySearchHistory(callback: QuerySearchHistoryEvent): void--><!--Device-AVMusicTemplate-onQuerySearchHistory(callback: QuerySearchHistoryEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [QuerySearchHistoryEvent](arkts-avsession-avmusictemplate-querysearchhistoryevent-t.md) | 是 | 回调函数，返回查询搜索历史的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onQuerySearchHistory can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onrequestdialoginfo"></a>
## onRequestDialogInfo

```TypeScript
onRequestDialogInfo(callback: RequestDialogInfoEvent): void
```

注册请求对话框信息的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onRequestDialogInfo(callback: RequestDialogInfoEvent): void--><!--Device-AVMusicTemplate-onRequestDialogInfo(callback: RequestDialogInfoEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [RequestDialogInfoEvent](arkts-avsession-avmusictemplate-requestdialoginfoevent-t.md) | 是 | 回调函数，返回请求对话框信息的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onRequestDialogInfo can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="onsettingschange"></a>
## onSettingsChange

```TypeScript
onSettingsChange(callback: SettingsChangeEvent): void
```

注册设置改变事件的监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-onSettingsChange(callback: SettingsChangeEvent): void--><!--Device-AVMusicTemplate-onSettingsChange(callback: SettingsChangeEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [SettingsChangeEvent](arkts-avsession-avmusictemplate-settingschangeevent-t.md) | 是 | 回调函数，返回设置改变的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onSettingsChange can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

<a id="reportexecuteaction"></a>
## reportExecuteAction

```TypeScript
reportExecuteAction(actionType: string, params: string): Promise<void>
```

向音频模板控制方同步执行操作信息。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-reportExecuteAction(actionType: string, params: string): Promise<void>--><!--Device-AVMusicTemplate-reportExecuteAction(actionType: string, params: string): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| actionType | string | 是 | 行为类型。 |
| params | string | 是 | 行为信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function reportExecuteAction can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000011](../errorcode-avmusictemplate.md#35000011-数据写入错误数据无效) | Thr data write error, data is invalid. |

<a id="setcurrentsingle"></a>
## setCurrentSingle

```TypeScript
setCurrentSingle(single: Single): Promise<void>
```

向音频模板控制方同步当前单曲。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-setCurrentSingle(single: Single): Promise<void>--><!--Device-AVMusicTemplate-setCurrentSingle(single: Single): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| single | [Single](arkts-avsession-avmusictemplate-single-i.md) | 是 | 当前单曲。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function setCurrentSingle can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000011](../errorcode-avmusictemplate.md#35000011-数据写入错误数据无效) | Thr data write error, data is invalid. |

<a id="setcustomelements"></a>
## setCustomElements

```TypeScript
setCustomElements(actionType: ActionType, customType: CustomType,
      customElement: CustomElement): Promise<void>
```

上报自定义数据变更信息至媒体中心

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-setCustomElements(actionType: ActionType, customType: CustomType,
      customElement: CustomElement): Promise<void>--><!--Device-AVMusicTemplate-setCustomElements(actionType: ActionType, customType: CustomType,
      customElement: CustomElement): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| actionType | [ActionType](arkts-avsession-avmusictemplate-actiontype-t.md) | 是 | 操作类型 |
| customType | [CustomType](arkts-avsession-avmusictemplate-customtype-t.md) | 是 | 自定义数据的类型 |
| customElement | [CustomElement](arkts-avsession-avmusictemplate-customelement-i.md) | 是 | 自定义数据 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 通过promise'返回上报自定义数据的结果 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function setCustomElements can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000011](../errorcode-avmusictemplate.md#35000011-数据写入错误数据无效) | Thr data write error, data is invalid. |

<a id="setdialogcommand"></a>
## setDialogCommand

```TypeScript
setDialogCommand(type: DialogControlType, dialogInfo: DialogInfo): Promise<void>
```

向音频模板控制方同步对话框命令。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-setDialogCommand(type: DialogControlType, dialogInfo: DialogInfo): Promise<void>--><!--Device-AVMusicTemplate-setDialogCommand(type: DialogControlType, dialogInfo: DialogInfo): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [DialogControlType](arkts-avsession-avmusictemplate-dialogcontroltype-t.md) | 是 | 对话框控制类型。 |
| dialogInfo | [DialogInfo](arkts-avsession-avmusictemplate-dialoginfo-i.md) | 是 | 对话框信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function setDialogCommand can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000011](../errorcode-avmusictemplate.md#35000011-数据写入错误数据无效) | Thr data write error, data is invalid. |

<a id="setdownloadmediaentitystatus"></a>
## setDownloadMediaEntityStatus

```TypeScript
setDownloadMediaEntityStatus(single: MediaEntity): Promise<void>
```

向音频模板控制方同步单曲下载状态信息。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-setDownloadMediaEntityStatus(single: MediaEntity): Promise<void>--><!--Device-AVMusicTemplate-setDownloadMediaEntityStatus(single: MediaEntity): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| single | [MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md) | 是 | 单曲。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function setDownloadMediaEntityStatus can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000011](../errorcode-avmusictemplate.md#35000011-数据写入错误数据无效) | Thr data write error, data is invalid. |

<a id="setextensionability"></a>
## setExtensionAbility

```TypeScript
setExtensionAbility(want: WantAgent): Promise<void>
```

向音频模板控制方同步用于被拉起的Ability。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-setExtensionAbility(want: WantAgent): Promise<void>--><!--Device-AVMusicTemplate-setExtensionAbility(want: WantAgent): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [WantAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent-wantagent-i.md) | 是 | 能力信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000011](../errorcode-avmusictemplate.md#35000011-数据写入错误数据无效) | Thr data write error, data is invalid. |

<a id="setmediaentities"></a>
## setMediaEntities

```TypeScript
setMediaEntities(entities: MediaEntity[]): Promise<void>
```

向音频模板控制方同步媒体资源变更信息。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-setMediaEntities(entities: MediaEntity[]): Promise<void>--><!--Device-AVMusicTemplate-setMediaEntities(entities: MediaEntity[]): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| entities | [MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md)[] | 是 | 媒体实体的数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function setMediaEntities can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000011](../errorcode-avmusictemplate.md#35000011-数据写入错误数据无效) | Thr data write error, data is invalid. |

<a id="setplaylist"></a>
## setPlaylist

```TypeScript
setPlaylist(playlist: PageMediaEntity): Promise<void>
```

向音频模板控制方同步播放列表。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-setPlaylist(playlist: PageMediaEntity): Promise<void>--><!--Device-AVMusicTemplate-setPlaylist(playlist: PageMediaEntity): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| playlist | [PageMediaEntity](arkts-avsession-avmusictemplate-pagemediaentity-i.md) | 是 | 分页媒体实体。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function setPlaylist can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000011](../errorcode-avmusictemplate.md#35000011-数据写入错误数据无效) | Thr data write error, data is invalid. |

<a id="setsettings"></a>
## setSettings

```TypeScript
setSettings(settingItems: SettingItem[]): Promise<void>
```

向音频模板控制方同步设置信息。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-setSettings(settingItems: SettingItem[]): Promise<void>--><!--Device-AVMusicTemplate-setSettings(settingItems: SettingItem[]): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| settingItems | [SettingItem](arkts-avsession-avmusictemplate-settingitem-i.md)[] | 是 | 设置项数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function setSettings can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000011](../errorcode-avmusictemplate.md#35000011-数据写入错误数据无效) | Thr data write error, data is invalid. |

<a id="settabcontent"></a>
## setTabContent

```TypeScript
setTabContent(tabId: string, tabContent: MediaTabContent): Promise<void>
```

向音频模板控制方同步标签页内容信息。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-setTabContent(tabId: string, tabContent: MediaTabContent): Promise<void>--><!--Device-AVMusicTemplate-setTabContent(tabId: string, tabContent: MediaTabContent): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tabId | string | 是 | 标签的ID。 |
| tabContent | [MediaTabContent](arkts-avsession-avmusictemplate-mediatabcontent-i.md) | 是 | 媒体标签页内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function setTabContent can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000011](../errorcode-avmusictemplate.md#35000011-数据写入错误数据无效) | Thr data write error, data is invalid. |

<a id="setuserinfo"></a>
## setUserInfo

```TypeScript
setUserInfo(userInfo: UserInfo): Promise<void>
```

向音频模板控制方同步用户信息。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-setUserInfo(userInfo: UserInfo): Promise<void>--><!--Device-AVMusicTemplate-setUserInfo(userInfo: UserInfo): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userInfo | [UserInfo](../../apis-arkdata/arkts-apis/arkts-arkdata-distributeddata-userinfo-i.md) | 是 | 用户信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function setUserInfo can not work correctly due to limited device capabilities. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000011](../errorcode-avmusictemplate.md#35000011-数据写入错误数据无效) | Thr data write error, data is invalid. |

<a id="starttemplate"></a>
## startTemplate

```TypeScript
startTemplate(): Promise<OperResult>
```

启动音频模板界面。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-startTemplate(): Promise<OperResult>--><!--Device-AVMusicTemplate-startTemplate(): Promise<OperResult>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;OperResult&gt; | Promise对象，返回启动音频模板界面的操作结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |

## sessionId

```TypeScript
sessionId: string
```

音频模板唯一的标识。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-sessionId: string--><!--Device-AVMusicTemplate-sessionId: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## sessionTag

```TypeScript
sessionTag: string
```

音频模板标签。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplate-sessionTag: string--><!--Device-AVMusicTemplate-sessionTag: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

