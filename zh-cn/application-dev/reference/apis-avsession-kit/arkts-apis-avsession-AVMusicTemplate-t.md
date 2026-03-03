# Types
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_gyH0B0hP-->
<!--Designer: @ccfriend-->
<!--Tester: @chen-gong1-->
<!--Adviser: @w_Machine_cc-->



> **说明：**
>
> 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## NoParamAsyncCallback

type NoParamAsyncCallback = () => Promise&lt;void&gt;

定义无参数的异步回调函数类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## QueryMainTabsEvent

type QueryMainTabsEvent = () => Promise<MediaTab[]>

查询主选项卡的事件。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**返回值：**

| 类型                                                                        | 说明                                |
|---------------------------------------------------------------------------| ----------------------------------- |
| Promise<[MediaTab](arkts-apis-avsession-AVMusicTemplate-i.md#mediatab)[]> | Promise对象。返回媒体标签页的集合。 |

**示例：**

请参考[onQueryMainTabs](arkts-apis-avsession-AVMusicTemplate.md#onquerymaintabs)的示例。

## QueryMediaTabContentEvent

type QueryMediaTabContentEvent = (tabId: string) => Promise&lt;MediaTabContent&gt;

查询媒体标签页内容的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型   | 必填 | 说明         |
| ------ | ------ | ---- | ------------ |
| tabId  | string | 是   | 标签页的ID。 |

**返回值：**

| 类型                                                                                    | 说明                              |
|---------------------------------------------------------------------------------------| --------------------------------- |
| Promise<[MediaTabContent](arkts-apis-avsession-AVMusicTemplate-i.md#mediatabcontent)> | Promise对象。返回媒体标签页内容。 |

**示例：**

请参考[onQueryMediaTabContent](arkts-apis-avsession-AVMusicTemplate.md#onquerymediatabcontent)的示例。

## QueryMediaEntityEvent

type QueryMediaEntityEvent = (params: QueryMediaEntityParam) => Promise&lt;PageMediaEntity&gt;

查询媒体实例的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型                                                                                       | 必填 | 说明                 |
| ------ |------------------------------------------------------------------------------------------| ---- | -------------------- |
| params | [QueryMediaEntityParam](arkts-apis-avsession-AVMusicTemplate-i.md#querymediaentityparam) | 是   | 查询媒体实例的参数。 |

**返回值：**

| 类型                                                                                    | 说明                              |
|---------------------------------------------------------------------------------------| --------------------------------- |
| Promise<[PageMediaEntity](arkts-apis-avsession-AVMusicTemplate-i.md#pagemediaentity)> | Promise对象。返回分页内容的对象。 |

**示例：**

请参考[onQueryMediaEntity](arkts-apis-avsession-AVMusicTemplate.md#onquerymediaentity)的示例。

## QueryCompilationEvent

type QueryCompilationEvent = (compilationId: string, pageIndex: int) => Promise&lt;PageMediaEntity&gt;

查询合集的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名        | 类型   | 必填 | 说明         |
| ------------- | ------ | ---- | ------------ |
| compilationId | string | 是   | 合集的ID。   |
| pageIndex     | int    | 是   | 页面的索引。 |

**返回值：**

| 类型                                                                                    | 说明                              |
|---------------------------------------------------------------------------------------| --------------------------------- |
| Promise<[PageMediaEntity](arkts-apis-avsession-AVMusicTemplate-i.md#pagemediaentity)> | Promise对象。返回分页内容的对象。 |

**示例：**

请参考[onQueryCompilation](arkts-apis-avsession-AVMusicTemplate.md#onquerycompilation)的示例。

## QueryPlaylistEvent

type QueryPlaylistEvent = (pageIndex: int, sort: Sort) => Promise&lt;PageMediaEntity&gt;

查询播放列表的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名    | 类型                                                     | 必填 | 说明           |
| --------- | ------------------------------------------------------ | ---- | -------------- |
| pageIndex | int                                                    | 是   | 页面的索引。   |
| sort      | [Sort](arkts-apis-avsession-AVMusicTemplate-e.md#sort) | 是   | 排序的枚举值。 |

**返回值：**

| 类型                                                                                    | 说明                              |
|---------------------------------------------------------------------------------------| --------------------------------- |
| Promise<[PageMediaEntity](arkts-apis-avsession-AVMusicTemplate-i.md#pagemediaentity)> | Promise对象。返回分页内容的对象。 |

**示例：**

请参考[onQueryPlaylist](arkts-apis-avsession-AVMusicTemplate.md#onqueryplaylist)的示例。

## QueryCurrentSingleEvent

type QueryCurrentSingleEvent = () => Promise&lt;Single&gt;

查询当前单曲的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**返回值：**

| 类型                                                         | 说明                          |
| ------------------------------------------------------------ | ----------------------------- |
| Promise<[Single](arkts-apis-avsession-AVMusicTemplate-i.md#single)> | Promise对象。返回Single对象。 |

**示例：**

请参考[onQueryCurrentSingle](arkts-apis-avsession-AVMusicTemplate.md#onquerycurrentsingle)的示例。

## QueryCompilationByKeywordEvent

type QueryCompilationByKeywordEvent = (keyword: string) => Promise&lt;Compilation[]&gt;

按关键字查询合集的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名  | 类型   | 必填 | 说明                   |
| ------- | ------ | ---- | ---------------------- |
| keyword | string | 是   | 用于查找合集的关键字。 |

**返回值：**

| 类型                                                                              | 说明                          |
|---------------------------------------------------------------------------------| ----------------------------- |
| Promise<[Compilation](arkts-apis-avsession-AVMusicTemplate-i.md#compilation)[]> | Promise对象。返回合集的数组。 |

**示例：**

请参考[onQueryCompilationByKeyword](arkts-apis-avsession-AVMusicTemplate.md#onquerycompilationbykeyword)的示例。

## QueryMediaEntityByKeywordEvent

type QueryMediaEntityByKeywordEvent = (keyword: string, searchType: EntityType, pageIndex: int) => Promise&lt;PageMediaEntity&gt;

按关键字查询媒体实体的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名     | 类型                                                                 | 必填 | 说明                   |
| ---------- |--------------------------------------------------------------------| ---- | ---------------------- |
| keyword    | string                                                             | 是   | 用于查找媒体的关键字。 |
| searchType | [EntityType](arkts-apis-avsession-AVMusicTemplate-e.md#entitytype) | 是   | 要搜索的媒体资源类型。 |
| pageIndex  | int                                                                | 是   | 页面的索引。从0开始。  |

**返回值：**

| 类型                                                                                    | 说明                          |
|---------------------------------------------------------------------------------------| ----------------------------- |
| Promise<[PageMediaEntity](arkts-apis-avsession-AVMusicTemplate-i.md#pagemediaentity)> | Promise对象。返回分页的实体。 |

**示例：**

请参考[onQueryMediaEntityByKeyword](arkts-apis-avsession-AVMusicTemplate.md#onquerymediaentitybykeyword)的示例。

## QueryRecommendMediaEntityListEvent

type QueryRecommendMediaEntityListEvent = () => Promise&lt;MediaEntity[]&gt;

查询推荐媒体实体列表的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**返回值：**

| 类型                                                                              | 说明                              |
|---------------------------------------------------------------------------------| --------------------------------- |
| Promise<[MediaEntity](arkts-apis-avsession-AVMusicTemplate-i.md#mediaentity)[]> | Promise对象。返回媒体实例的数组。 |

**示例：**

请参考[onQueryRecommendMediaEntityList](arkts-apis-avsession-AVMusicTemplate.md#onqueryrecommendmediaentitylist)的示例。

## QueryHotWordsEvent

type QueryHotWordsEvent = () => Promise&lt;string[]&gt;

查询热词的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**返回值：**

| 类型              | 说明                          |
| ----------------- | ----------------------------- |
| Promise<string[]> | Promise对象。返回热词的数组。 |

**示例：**

请参考[onQueryHotWords](arkts-apis-avsession-AVMusicTemplate.md#onqueryhotwords)的示例。

## QuerySearchHistoryEvent

type QuerySearchHistoryEvent = () => Promise&lt;string[]&gt;

查询搜索历史的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**返回值：**

| 类型              | 说明                              |
| ----------------- | --------------------------------- |
| Promise<string[]> | Promise对象。返回搜索历史的数组。 |

**示例：**

请参考[onQuerySearchHistory](arkts-apis-avsession-AVMusicTemplate.md#onquerysearchhistory)的示例。

## ClearSearchHistoryEvent

type ClearSearchHistoryEvent = () => Promise&lt;OperResult&gt;

清除搜索历史的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**返回值：**

| 类型                                                                          | 说明                              |
|-----------------------------------------------------------------------------| --------------------------------- |
| Promise<[OperResult](arkts-apis-avsession-AVMusicTemplate-i.md#operresult)> | Promise对象。返回操作结果的对象。 |

**示例：**

请参考[onClearSearchHistory](arkts-apis-avsession-AVMusicTemplate.md#onclearsearchhistory)的示例。

## LoginEvent

type LoginEvent = (controlType: LoginType, id?: string) => Promise&lt;QrCodeInfo[]&gt;

登录的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名      | 类型                      | 必填 | 说明       |
| ----------- | ----------------------- | ---- | ---------- |
| controlType | [LoginType](#logintype) | 是   | 登录类型。 |
| id          | string                  | 否   | id。       |

**返回值：**

| 类型                                                         | 说明                                |
| ------------------------------------------------------------ | ----------------------------------- |
| Promise<[QrCodeInfo](arkts-apis-avsession-AVMusicTemplate-i.md#qrcodeinfo)[]> | Promise对象。返回二维码信息的数组。 |

**示例：**

请参考[onLogin](arkts-apis-avsession-AVMusicTemplate.md#onlogin)的示例。

## LoginType

type LoginType = 'queryLoginInfo' | 'refreshLoginInfo' | 'cancel' | 'logout'

登录的类型。

该类型可取的值为下表字符串。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| 类型               | 说明           |
| ------------------ | -------------- |
| 'queryLoginInfo'   | 查询登录信息。 |
| 'refreshLoginInfo' | 刷新登录信息。 |
| 'cancel'           | 取消。         |
| 'logout'           | 退出登录。     |

## RequestDialogInfoEvent

type RequestDialogInfoEvent = (actionType: DialogActionType, actionInfo?: DialogActionInfo) => Promise&lt;DialogInfo&gt;

请求对话框信息的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名     | 类型                                                        | 必填 | 说明                 |
| ---------- | --------------------------------------------------------- | ---- | -------------------- |
| actionType | [DialogActionType](#dialogactiontype)                     | 是   | 弹框类型。           |
| actionInfo | [DialogActionInfo](arkts-apis-avsession-AVMusicTemplate-i.md#dialogactioninfo) | 否   | 弹框动作结果的信息。 |

**返回值：**

| 类型                                                         | 说明                        |
| ------------------------------------------------------------ | --------------------------- |
| Promise<[DialogInfo](arkts-apis-avsession-AVMusicTemplate-i.md#dialoginfo)> | Promise对象。返回弹框信息。 |

**示例：**

请参考[onRequestDialogInfo](arkts-apis-avsession-AVMusicTemplate.md#onrequestdialoginfo)的示例。

## DialogActionType

type DialogActionType = 'open' | 'close' | 'refresh'

弹框操作类型。

该类型可取的值为下表字符串。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| 类型      | 说明   |
| --------- | ------ |
| 'open'    | 打开。 |
| 'close'   | 关闭。 |
| 'refresh' | 刷新。 |

## HandleMemberPurchaseEvent

type HandleMemberPurchaseEvent = (info: MemberPurchaseInfo) => Promise&lt;DialogInfo&gt;

处理购买会员的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型                                                         | 必填 | 说明             |
| ------ | ------------------------------------------------------------ | ---- | ---------------- |
| info   | [MemberPurchaseInfo](arkts-apis-avsession-AVMusicTemplate-i.md#memberpurchaseinfo) | 是   | 购买会员的信息。 |

**返回值：**

| 类型                                                         | 说明                        |
| ------------------------------------------------------------ | --------------------------- |
| Promise<[DialogInfo](arkts-apis-avsession-AVMusicTemplate-i.md#dialoginfo)> | Promise对象。返回弹框信息。 |

**示例：**

请参考[onHandleMemberPurchase](arkts-apis-avsession-AVMusicTemplate.md#onhandlememberpurchase)的示例。

## QueryMemberPurchaseEvent

type QueryMemberPurchaseEvent = (memberPurchaseType: MemberPurchaseType) => Promise&lt;MemberPurchaseInfo[]&gt;

查询购买会员的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名             | 类型                                                         | 必填 | 说明             |
| ------------------ | ------------------------------------------------------------ | ---- | ---------------- |
| memberPurchaseType | [MemberPurchaseType](arkts-apis-avsession-AVMusicTemplate-e.md#memberpurchasetype) | 是   | 购买会员的类型。 |

**返回值：**

| 类型                                                         | 说明                                  |
| ------------------------------------------------------------ | ------------------------------------- |
| Promise<[MemberPurchaseInfo](arkts-apis-avsession-AVMusicTemplate-i.md#memberpurchaseinfo)[]> | Promise对象。返回会员购买信息的数组。 |

**示例：**

请参考[onQueryMemberPurchase](arkts-apis-avsession-AVMusicTemplate.md#onquerymemberpurchase)的示例。

## QueryCustomContentEvent

type QueryCustomContentEvent = (queryType: CustomType[]) => Promise&lt;CustomElement&gt;

查询自定义内容的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名    | 类型                          | 必填 | 说明                                        |
| --------- | --------------------------- | ---- | ------------------------------------------- |
| queryType | [CustomType](#customtype)[] | 是   | 自定义类型：包含用户基本信息、界面选项卡配置、代码编译选项和系统设置项。 |

**返回值：**

| 类型                                                         | 说明                                    |
| ------------------------------------------------------------ | --------------------------------------- |
| Promise<[CustomElement](arkts-apis-avsession-AVMusicTemplate-i.md#customelement)> | Promise对象。返回我的页面的自定义元素。 |

**示例：**

请参考[onQueryCustomContent](arkts-apis-avsession-AVMusicTemplate.md#onquerycustomcontent)的示例。

## CustomType

type CustomType = 'USER_INFO' | 'TAB' | 'COMPILATION' | 'SETTINGS'

自定义类型。

该类型可取的值为下表字符串。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| 类型          | 说明       |
| ------------- | ---------- |
| 'USER_INFO'   | 用户信息。 |
| 'TAB'         | 选项卡。   |
| 'COMPILATION' | 合集。     |
| 'SETTINGS'    | 设置。     |

## DownloadMediaEntityEvent

type DownloadMediaEntityEvent = (controlType: DownloadControlType, mediaEntity: MediaEntity) => Promise&lt;OperResult&gt;

下载媒体实体的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名      | 类型                                                         | 必填 | 说明                                       |
| ----------- | ---------------------------------------------------------- | ---- | ------------------------------------------ |
| controlType | [DownloadControlType](#downloadcontroltype)                | 是   | controlType的可选项包括：用户信息，选项卡，合集，设置。 |
| mediaEntity | [MediaEntity](arkts-apis-avsession-AVMusicTemplate-i.md#mediaentity) | 是   | 媒体实例。                                 |

**返回值：**

| 类型                                                         | 说明                            |
| ------------------------------------------------------------ | ------------------------------- |
| Promise<[OperResult](arkts-apis-avsession-AVMusicTemplate-i.md#operresult)> | Promise对象。返回操作结果对象。 |

**示例：**

请参考[onDownloadMediaEntity](arkts-apis-avsession-AVMusicTemplate.md#ondownloadmediaentity)的示例。

## DownloadControlType

type DownloadControlType = 'startDownload' | 'deleteDownload' | 'resumeDownload' | 'pauseDownload'

定义下载操作的控制类型，包括开始下载、删除下载、恢复下载和暂停下载。

该类型可取的值为下表字符串。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| 类型             | 说明       |
| ---------------- | ---------- |
| 'startDownload'  | 开始下载。 |
| 'deleteDownload' | 删除下载。 |
| 'resumeDownload' | 恢复下载。 |
| 'pauseDownload'  | 暂停下载。 |

## SettingsChangeEvent

type SettingsChangeEvent = (settingItem: SettingItem) => Promise&lt;SettingItem&gt;

设置改变的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名      | 类型                                                         | 必填 | 说明     |
| ----------- | ------------------------------------------------------------ | ---- | -------- |
| settingItem | [SettingItem](arkts-apis-avsession-AVMusicTemplate-i.md#settingitem) | 是   | 设置项。 |

**返回值：**

| 类型                                                         | 说明                      |
| ------------------------------------------------------------ | ------------------------- |
| Promise<[SettingItem](arkts-apis-avsession-AVMusicTemplate-i.md#settingitem)> | Promise对象。返回设置项。 |

**示例：**

请参考[onSettingsChange](arkts-apis-avsession-AVMusicTemplate.md#onsettingschange)的示例。

## ProblemAndAdviceEvent

type ProblemAndAdviceEvent = (advice: string) => Promise&lt;OperResult&gt;

问题与建议活动的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型   | 必填 | 说明           |
| ------ | ------ | ---- | -------------- |
| advice | string | 是   | 问题反馈内容。 |

**返回值：**

| 类型                                                         | 说明                            |
| ------------------------------------------------------------ | ------------------------------- |
| Promise<[OperResult](arkts-apis-avsession-AVMusicTemplate-i.md#operresult)> | Promise对象。返回操作结果对象。 |

**示例：**

请参考[onProblemAndAdvice](arkts-apis-avsession-AVMusicTemplate.md#onproblemandadvice)的示例。

## PlayForSearchEvent

type PlayForSearchEvent = (command: SearchPlayInfoType, args: SearchPlayInfo) => Promise&lt;OperResult&gt;

搜播的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名  | 类型                                                         | 必填 | 说明             |
| ------- | ------------------------------------------------------------ | ---- | ---------------- |
| command | [SearchPlayInfoType](arkts-apis-avsession-AVMusicTemplate-e.md#searchplayinfotype) | 是   | 搜播信息的类型。 |
| args    | [SearchPlayInfo](arkts-apis-avsession-AVMusicTemplate-i.md#searchplayinfo) | 是   | 搜播信息。       |

**返回值：**

| 类型                                                         | 说明                            |
| ------------------------------------------------------------ | ------------------------------- |
| Promise<[OperResult](arkts-apis-avsession-AVMusicTemplate-i.md#operresult)> | Promise对象。返回操作结果对象。 |

**示例：**

请参考[onPlayForSearch](arkts-apis-avsession-AVMusicTemplate.md#onplayforsearch)的示例。

## ExecuteActionEvent

type ExecuteActionEvent = (actionType: string, params: string) => Promise&lt;string&gt;

执行操作的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名     | 类型   | 必填 | 说明       |
| ---------- | ------ | ---- | ---------- |
| actionType | string | 是   | 动作类型。 |
| params     | string | 是   | 参数信息。 |

**返回值：**

| 类型                  | 说明                            |
| --------------------- | ------------------------------- |
| Promise&lt;string&gt; | Promise对象。返回操作结果对象。 |

**示例：**

请参考[onExecuteAction](arkts-apis-avsession-AVMusicTemplate.md#onexecuteaction)的示例。

## PlayMediaEntityEvent

type PlayMediaEntityEvent = (mediaEntity: MediaEntity) => Promise&lt;void&gt;

播放媒体实体的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名      | 类型                                                         | 必填 | 说明       |
| ----------- | ------------------------------------------------------------ | ---- | ---------- |
| mediaEntity | [MediaEntity](arkts-apis-avsession-AVMusicTemplate-i.md#mediaentity) | 是   | 媒体实体。 |

**示例：**

请参考[onPlayMediaEntity](arkts-apis-avsession-AVMusicTemplate.md#onplaymediaentity)的示例。

## FavoriteMediaEntityEvent

type FavoriteMediaEntityEvent = (actionType: MediaFavoriteType, mediaEntity: MediaEntity) => Promise&lt;OperResult&gt;

收藏媒体实体的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名      | 类型                                                        | 必填 | 说明       |
| ----------- | ---------------------------------------------------------- | ---- | ---------- |
| actionType  | [MediaFavoriteType](#mediafavoritetype)                   | 是   | 操作类型。 |
| mediaEntity | [MediaEntity](arkts-apis-avsession-AVMusicTemplate-i.md#mediaentity) | 是   | 媒体实体。 |

**返回值：**

| 类型                  | 说明                            |
| --------------------- | ------------------------------- |
| Promise&lt;string&gt; | Promise对象。返回操作结果对象。 |

**示例：**

请参考[onFavoriteMediaEntity](arkts-apis-avsession-AVMusicTemplate.md#onfavoritemediaentity)的示例。

## MediaFavoriteType

type MediaFavoriteType = 'addFavorite' | 'removeFavorite'

媒体收藏类型的定义。

该类型可取的值为下表字符串。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| 类型             | 说明       |
| ---------------- | ---------- |
| 'addFavorite'    | 添加收藏。 |
| 'removeFavorite' | 取消收藏。 |

## DialogControlType

type DialogControlType = 'open' | 'close' | 'refresh' | 'toast'

弹框控制类型的定义。

该类型可取的值为下表字符串。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| 类型      | 说明   |
| --------- | ------ |
| 'open'    | 打开。 |
| 'close'   | 关闭。 |
| 'refresh' | 刷新。 |
| 'toast'   | 提示。 |

## ActionType

type ActionType = 'add' | 'remove'

操作类型的定义。

该类型可取的值为下表字符串。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| 类型     | 说明   |
| -------- | ------ |
| 'add'    | 添加。 |
| 'remove' | 移除。 |

## ReportDialogCommandEvent

type ReportDialogCommandEvent = (type: DialogControlType, buttonInfo: DialogInfo) => void

上报弹框命令的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名     | 类型                                                        | 必填 | 说明           |
| ---------- | --------------------------------------------------------- | ---- | -------------- |
| type       | [DialogControlType](#dialogcontroltype)                   | 是   | 弹框控制类型。 |
| buttonInfo | [DialogInfo](arkts-apis-avsession-AVMusicTemplate-i.md#dialoginfo) | 是   | 弹框信息。     |

**示例：**

请参考[onDialogCommandChange](arkts-apis-avsession-AVMusicTemplateController.md#ondialogcommandchange)的示例。

## ReportTabContentEvent

type ReportTabContentEvent = (tabId: string, tabContent: MediaTabContent) => void

上报标签页内容的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明           |
| ---------- | ------------------------------------------------------------ | ---- | -------------- |
| tabId      | string                                                       | 是   | 标签页的ID。   |
| tabContent | [MediaTabContent](arkts-apis-avsession-AVMusicTemplate-i.md#mediatabcontent) | 是   | 标签页的内容。 |

**示例：**

请参考[onTabContentChange](arkts-apis-avsession-AVMusicTemplateController.md#ontabcontentchange)的示例。

## ReportCustomElementsChangeEvent

type ReportCustomElementsChangeEvent = (actionType: ActionType, customType: CustomType, customElement: CustomElement) => void

上报自定义元素改变的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名        | 类型                                                      | 必填 | 说明         |
| ------------- | ------------------------------------------------------- | ---- | ------------ |
| actionType    | [ActionType](#actiontype)                               | 是   | 操作类型。   |
| customType    | [CustomType](#customtype)                               | 是   | 自定义类型。 |
| customElement | [CustomElement](arkts-apis-avsession-AVMusicTemplate-i.md#customelement) | 是   | 自定义元素。 |

**示例：**

请参考[onCustomElementsChange](arkts-apis-avsession-AVMusicTemplateController.md#oncustomelementschange)的示例。

## ReportExecuteActionEvent

type ReportExecuteActionEvent = (actionType: string, params: string) => void

上报执行动作的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名     | 类型   | 必填 | 说明             |
| ---------- | ------ | ---- | ---------------- |
| actionType | string | 是   | 操作类型。       |
| params     | string | 是   | 执行动作的信息。 |

**示例：**

请参考[onReportExecuteAction](arkts-apis-avsession-AVMusicTemplateController.md#onreportexecuteaction)的示例。

## ReportExecuteAbilityEvent

type ReportExecuteAbilityEvent = (want: WantAgent) => void

通知音频模板控制方拉起指定三方应用界面的信息的事件类型。



**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型                                                         | 必填 | 说明               |
| ------ | ------------------------------------------------------------ | ---- | ------------------ |
| want   | [WantAgent](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/js-apis-app-ability-wantAgent.md#WantAgent) | 是   | 三方页面启动信息。 |

**示例：**

请参考[onExtensionAbilityChange](arkts-apis-avsession-AVMusicTemplateController.md#onextensionabilitychange)的示例。