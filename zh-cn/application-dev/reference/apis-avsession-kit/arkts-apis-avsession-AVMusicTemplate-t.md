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

## NoParamAsyncCallback<sup>23+</sup>

type NoParamAsyncCallback = () => Promise&lt;void&gt;

定义无参数的异步回调函数类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

## QueryMainTabsEvent<sup>23+</sup>

type QueryMainTabsEvent = () => Promise<MediaTab[]>

查询主选项卡的事件。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型                                                         | 说明                                |
| ------------------------------------------------------------ | ----------------------------------- |
| Promise<[MediaTab](arkts-apis-avsession-AVMusicTemplate-i.md#MediaTab)[]> | Promise对象。返回媒体标签页的集合。 |

**示例：**

请参考[onQueryMainTabs](./arkts-apis-avsession-AVMusicTemplate.md#onQueryMainTabs23)的示例。

## QueryMediaTabContentEvent<sup>23+</sup>

type QueryMediaTabContentEvent = (tabId: string) => Promise&lt;MediaTabContent&gt;

查询媒体标签页内容的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型   | 必填 | 说明         |
| ------ | ------ | ---- | ------------ |
| tabId  | string | 是   | 标签页的ID。 |

**返回值：**

| 类型                                                         | 说明                              |
| ------------------------------------------------------------ | --------------------------------- |
| Promise<[MediaTabContent](arkts-apis-avsession-AVMusicTemplate-i.md#MediaTabContent)> | Promise对象。返回媒体标签页内容。 |

**示例：**

请参考[onQueryMediaTabContent](./arkts-apis-avsession-AVMusicTemplate.md#onQueryMediaTabContent23)的示例。

## QueryMediaEntityEvent<sup>23+</sup>

type QueryMediaEntityEvent = (params: QueryMediaEntityParam) => Promise&lt;PageMediaEntity&gt;

查询媒体实例的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型                                                         | 必填 | 说明                 |
| ------ | ------------------------------------------------------------ | ---- | -------------------- |
| params | [QueryMediaEntityParam](arkts-apis-avsession-AVMusicTemplate-i.md#QueryMediaEntityParam) | 是   | 查询媒体实例的参数。 |

**返回值：**

| 类型                                                         | 说明                              |
| ------------------------------------------------------------ | --------------------------------- |
| Promise<[PageMediaEntity](arkts-apis-avsession-AVMusicTemplate-i.md#PageMediaEntity)> | Promise对象。返回分页内容的对象。 |

**示例：**

请参考[onQueryMediaEntity](./arkts-apis-avsession-AVMusicTemplate.md#onQueryMediaEntity23)的示例。

## QueryCompilationEvent<sup>23+</sup>

type QueryCompilationEvent = (compilationId: string, pageIndex: int) => Promise&lt;PageMediaEntity&gt;

查询合集的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名        | 类型   | 必填 | 说明         |
| ------------- | ------ | ---- | ------------ |
| compilationId | string | 是   | 合集的ID。   |
| pageIndex     | int    | 是   | 页面的索引。 |

**返回值：**

| 类型                                                         | 说明                              |
| ------------------------------------------------------------ | --------------------------------- |
| Promise<[PageMediaEntity](arkts-apis-avsession-AVMusicTemplate-i.md#PageMediaEntity)> | Promise对象。返回分页内容的对象。 |

**示例：**

请参考[onQueryCompilation](./arkts-apis-avsession-AVMusicTemplate.md#onQueryCompilation23)的示例。

## QueryPlaylistEvent<sup>23+</sup>

type QueryPlaylistEvent = (pageIndex: int, sort: Sort) => Promise&lt;PageMediaEntity&gt;

查询播放列表的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名    | 类型                                                   | 必填 | 说明           |
| --------- | ------------------------------------------------------ | ---- | -------------- |
| pageIndex | int                                                    | 是   | 合集的ID。     |
| sort      | [Sort](arkts-apis-avsession-AVMusicTemplate-e.md#Sort) | 是   | 排序的枚举值。 |

**返回值：**

| 类型                                                         | 说明                              |
| ------------------------------------------------------------ | --------------------------------- |
| Promise<[PageMediaEntity](arkts-apis-avsession-AVMusicTemplate-i.md#PageMediaEntity)> | Promise对象。返回分页内容的对象。 |

**示例：**

请参考[onQueryPlaylist](./arkts-apis-avsession-AVMusicTemplate.md#onQueryPlaylist23)的示例。

## QueryCurrentSingleEvent<sup>23+</sup>

type QueryCurrentSingleEvent = () => Promise&lt;Single&gt;

查询当前单曲的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型                                                         | 说明                              |
| ------------------------------------------------------------ | --------------------------------- |
| Promise<[Single](arkts-apis-avsession-AVMusicTemplate-i.md#Single)> | Promise对象。返回分页内容的对象。 |

**示例：**

请参考[onQueryCurrentSingle](./arkts-apis-avsession-AVMusicTemplate.md#onQueryCurrentSingle23)的示例。

## QueryCompilationByKeywordEvent<sup>23+</sup>

type QueryCompilationByKeywordEvent = (keyword: string) => Promise&lt;Compilation[]&gt;

按关键字查询合集的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名  | 类型   | 必填 | 说明                   |
| ------- | ------ | ---- | ---------------------- |
| keyword | string | 是   | 用于查找合集的关键字。 |

**返回值：**

| 类型                                                         | 说明                          |
| ------------------------------------------------------------ | ----------------------------- |
| Promise<[Compilation](arkts-apis-avsession-AVMusicTemplate-i.md#Compilation)[]> | Promise对象。返回合集的数组。 |

**示例：**

请参考[onQueryCompilationByKeyword](./arkts-apis-avsession-AVMusicTemplate.md#onQueryCompilationByKeyword23)的示例。

## QueryMediaEntityByKeywordEvent<sup>23+</sup>

type QueryMediaEntityByKeywordEvent = (keyword: string, searchType: EntityType, pageIndex: int) => Promise&lt;PageMediaEntity&gt;

按关键字查询媒体实体的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明                   |
| ---------- | ------------------------------------------------------------ | ---- | ---------------------- |
| keyword    | string                                                       | 是   | 用于查找媒体的关键字。 |
| searchType | [EntityType](arkts-apis-avsession-AVMusicTemplate-e.md#EntityType) | 是   | 要搜索的媒体资源类型。 |
| pageIndex  | int                                                          | 是   | 页面的索引。从0开始。  |

**返回值：**

| 类型                                                         | 说明                          |
| ------------------------------------------------------------ | ----------------------------- |
| Promise<[PageMediaEntity](arkts-apis-avsession-AVMusicTemplate-i.md#PageMediaEntity)> | Promise对象。返回分页的实体。 |

**示例：**

请参考[onQueryMediaEntityByKeyword](./arkts-apis-avsession-AVMusicTemplate.md#onQueryMediaEntityByKeyword23)的示例。

## QueryRecommendMediaEntityListEvent<sup>23+</sup>

type QueryRecommendMediaEntityListEvent = () => Promise&lt;MediaEntity[]&gt;

查询推荐媒体实体列表的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型                                                         | 说明                              |
| ------------------------------------------------------------ | --------------------------------- |
| Promise<[MediaEntity](arkts-apis-avsession-AVMusicTemplate-i.md#MediaEntity)[]> | Promise对象。返回媒体实例的数组。 |

**示例：**

请参考[onQueryRecommendMediaEntityList](./arkts-apis-avsession-AVMusicTemplate.md#onQueryRecommendMediaEntityList23)的示例。

## QueryHotWordsEvent<sup>23+</sup>

type QueryHotWordsEvent = () => Promise&lt;string[]&gt;

查询热词的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型              | 说明                          |
| ----------------- | ----------------------------- |
| Promise<string[]> | Promise对象。返回热词的数组。 |

**示例：**

请参考[onQueryHotWords](./arkts-apis-avsession-AVMusicTemplate.md#onQueryHotWords23)的示例。

## QuerySearchHistoryEvent<sup>23+</sup>

type QuerySearchHistoryEvent = () => Promise&lt;string[]&gt;

查询搜索历史的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型              | 说明                              |
| ----------------- | --------------------------------- |
| Promise<string[]> | Promise对象。返回搜索历史的数组。 |

**示例：**

请参考[onQuerySearchHistory](./arkts-apis-avsession-AVMusicTemplate.md#onQuerySearchHistory23)的示例。

## ClearSearchHistoryEvent<sup>23+</sup>

type ClearSearchHistoryEvent = () => Promise&lt;OperResult&gt;

清除搜索历史的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型                                                         | 说明                              |
| ------------------------------------------------------------ | --------------------------------- |
| Promise<[OperResult](arkts-apis-avsession-AVMusicTemplate-i.md#OperResult)> | Promise对象。返回操作结果的对象。 |

**示例：**

请参考[onClearSearchHistory](./arkts-apis-avsession-AVMusicTemplate.md#onClearSearchHistory23)的示例。

## LoginEvent<sup>23+</sup>

type LoginEvent = (controlType: LoginType, id?: string) => Promise&lt;QrCodeInfo[]&gt;

登录的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名      | 类型                       | 必填 | 说明       |
| ----------- | -------------------------- | ---- | ---------- |
| controlType | [LoginType](##LoginType23) | 是   | 登录类型。 |
| id          | string                     | 否   | id。       |

**返回值：**

| 类型                                                         | 说明                                |
| ------------------------------------------------------------ | ----------------------------------- |
| Promise<[QrCodeInfo](arkts-apis-avsession-AVMusicTemplate-i.md##QrCodeInfo23)[]> | Promise对象。返回二维码信息的数组。 |

**示例：**

请参考[onLogin](./arkts-apis-avsession-AVMusicTemplate.md#onLogin23)的示例。

## LoginType<sup>23+</sup>

type LoginType = 'queryLoginInfo' | 'refreshLoginInfo' | 'cancel' | 'logout'

登录的类型。

该类型可取的值为下表字符串。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

| 类型               | 说明           |
| ------------------ | -------------- |
| 'queryLoginInfo'   | 查询登录信息。 |
| 'refreshLoginInfo' | 刷新登录信息。 |
| 'cancel'           | 取消。         |
| 'logout'           | 退出登录。     |

## RequestDialogInfoEvent<sup>23+</sup>

type RequestDialogInfoEvent = (actionType: DialogActionType, actionInfo?: DialogActionInfo) => Promise&lt;DialogInfo&gt;

登录的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明                 |
| ---------- | ------------------------------------------------------------ | ---- | -------------------- |
| actionType | [DialogActionType](##DialogActionType23)                     | 是   | 弹框类型。           |
| actionInfo | [DialogActionInfo](arkts-apis-avsession-AVMusicTemplate-i.md##DialogActionInfo23) | 否   | 弹框动作结果的信息。 |

**返回值：**

| 类型                                                         | 说明                        |
| ------------------------------------------------------------ | --------------------------- |
| Promise<[DialogInfo](arkts-apis-avsession-AVMusicTemplate-i.md##DialogInfo23)> | Promise对象。返回弹框信息。 |

**示例：**

请参考[onRequestDialogInfo](./arkts-apis-avsession-AVMusicTemplate.md#onRequestDialogInfo23)的示例。

## DialogActionType<sup>23+</sup>

type DialogActionType = 'open' | 'close' | 'refresh'

弹框操作类型。

该类型可取的值为下表字符串。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

| 类型      | 说明   |
| --------- | ------ |
| 'open'    | 打开。 |
| 'close'   | 关闭。 |
| 'refresh' | 刷新。 |

## HandleMemberPurchaseEvent<sup>23+</sup>

type HandleMemberPurchaseEvent = (info: MemberPurchaseInfo) => Promise&lt;DialogInfo&gt;

处理购买会员的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型                                                         | 必填 | 说明             |
| ------ | ------------------------------------------------------------ | ---- | ---------------- |
| info   | [MemberPurchaseInfo](arkts-apis-avsession-AVMusicTemplate-i.md##MemberPurchaseInfo23) | 是   | 购买会员的信息。 |

**返回值：**

| 类型                                                         | 说明                        |
| ------------------------------------------------------------ | --------------------------- |
| Promise<[DialogInfo](arkts-apis-avsession-AVMusicTemplate-i.md##DialogInfo23)> | Promise对象。返回弹框信息。 |

**示例：**

请参考[onHandleMemberPurchase](./arkts-apis-avsession-AVMusicTemplate.md#onHandleMemberPurchase23)的示例。

## QueryMemberPurchaseEvent<sup>23+</sup>

type QueryMemberPurchaseEvent = (memberPurchaseType: MemberPurchaseType) => Promise&lt;MemberPurchaseInfo[]&gt;

查询购买会员的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名             | 类型                                                         | 必填 | 说明             |
| ------------------ | ------------------------------------------------------------ | ---- | ---------------- |
| memberPurchaseType | [MemberPurchaseType](arkts-apis-avsession-AVMusicTemplate-e.md##MemberPurchaseType23) | 是   | 购买会员的类型。 |

**返回值：**

| 类型                                                         | 说明                                  |
| ------------------------------------------------------------ | ------------------------------------- |
| Promise<[MemberPurchaseInfo](arkts-apis-avsession-AVMusicTemplate-i.md##MemberPurchaseInfo23)[]> | Promise对象。返回会员购买信息的数组。 |

**示例：**

请参考[onQueryMemberPurchase](./arkts-apis-avsession-AVMusicTemplate.md#onQueryMemberPurchase23)的示例。

## QueryCustomContentEvent<sup>23+</sup>

type QueryCustomContentEvent = (queryType: CustomType[]) => Promise&lt;CustomElement&gt;

查询自定义内容的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名    | 类型                           | 必填 | 说明                                        |
| --------- | ------------------------------ | ---- | ------------------------------------------- |
| queryType | [CustomType](##CustomType23)[] | 是   | 自定义类型：用户信息 ，选项卡，编译，设置。 |

**返回值：**

| 类型                                                         | 说明                                    |
| ------------------------------------------------------------ | --------------------------------------- |
| Promise<[CustomElement](arkts-apis-avsession-AVMusicTemplate-i.md##CustomElement23)> | Promise对象。返回我的页面的自定义元素。 |

**示例：**

请参考[onQueryCustomContent](./arkts-apis-avsession-AVMusicTemplate.md#onQueryCustomContent23)的示例。

## CustomType<sup>23+</sup>

type CustomType = 'USER_INFO' | 'TAB' | 'COMPILATION' | 'SETTINGS'

自定义类型。

该类型可取的值为下表字符串。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

| 类型          | 说明       |
| ------------- | ---------- |
| 'USER_INFO'   | 用户信息。 |
| 'TAB'         | 选项卡。   |
| 'COMPILATION' | 合集。     |
| 'SETTINGS'    | 设置。     |

## DownloadMediaEntityEvent<sup>23+</sup>

type DownloadMediaEntityEvent = (controlType: DownloadControlType, mediaEntity: MediaEntity) => Promise&lt;OperResult&gt;

下载媒体实体的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名      | 类型                                                         | 必填 | 说明                                        |
| ----------- | ------------------------------------------------------------ | ---- | ------------------------------------------- |
| controlType | [DownloadControlType](##DownloadControlType23)               | 是   | 自定义类型：用户信息 ，选项卡，合集，设置。 |
| mediaEntity | [MediaEntity](arkts-apis-avsession-AVMusicTemplate-i.md##MediaEntity23) | 是   | 媒体实例。                                  |

**返回值：**

| 类型                                                         | 说明                            |
| ------------------------------------------------------------ | ------------------------------- |
| Promise<[OperResult](arkts-apis-avsession-AVMusicTemplate-i.md##OperResult23)> | Promise对象。返回操作结果对象。 |

**示例：**

请参考[onDownloadMediaEntity](./arkts-apis-avsession-AVMusicTemplate.md#onDownloadMediaEntity23)的示例。

## DownloadControlType<sup>23+</sup>

type DownloadControlType = 'startDownload' | 'deleteDownload' | 'resumeDownload' | 'pauseDownload'

下载的控制类型的定义。

该类型可取的值为下表字符串。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

| 类型             | 说明       |
| ---------------- | ---------- |
| 'startDownload'  | 开始下载。 |
| 'deleteDownload' | 删除下载。 |
| 'resumeDownload' | 恢复下载。 |
| 'pauseDownload'  | 暂停下载。 |

## SettingsChangeEvent<sup>23+</sup>

type SettingsChangeEvent = (settingItem: SettingItem) => Promise&lt;SettingItem&gt;

设置改变的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名      | 类型                                                         | 必填 | 说明     |
| ----------- | ------------------------------------------------------------ | ---- | -------- |
| settingItem | [SettingItem](arkts-apis-avsession-AVMusicTemplate-i.md##SettingItem23) | 是   | 设置项。 |

**返回值：**

| 类型                                                         | 说明                      |
| ------------------------------------------------------------ | ------------------------- |
| Promise<[SettingItem](arkts-apis-avsession-AVMusicTemplate-i.md##SettingItem23)> | Promise对象。返回设置项。 |

**示例：**

请参考[onSettingsChange](./arkts-apis-avsession-AVMusicTemplate.md#onSettingsChange23)的示例。

## ProblemAndAdviceEvent<sup>23+</sup>

type ProblemAndAdviceEvent = (advice: string) => Promise&lt;OperResult&gt;

问题与建议活动的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型   | 必填 | 说明           |
| ------ | ------ | ---- | -------------- |
| advice | string | 是   | 问题反馈内容。 |

**返回值：**

| 类型                                                         | 说明                            |
| ------------------------------------------------------------ | ------------------------------- |
| Promise<[OperResult](arkts-apis-avsession-AVMusicTemplate-i.md##OperResult23)> | Promise对象。返回操作结果对象。 |

**示例：**

请参考[onProblemAndAdvice](./arkts-apis-avsession-AVMusicTemplate.md#onProblemAndAdvice23)的示例。

## PlayForSearchEvent<sup>23+</sup>

type PlayForSearchEvent = (command: SearchPlayInfoType, args: SearchPlayInfo) => Promise&lt;OperResult&gt;

搜播的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名  | 类型                                                         | 必填 | 说明             |
| ------- | ------------------------------------------------------------ | ---- | ---------------- |
| command | [SearchPlayInfoType](arkts-apis-avsession-AVMusicTemplate-e.md##SearchPlayInfoType23) | 是   | 搜播信息的类型。 |
| args    | [SearchPlayInfo](arkts-apis-avsession-AVMusicTemplate-i.md##SearchPlayInfo23) | 是   | 搜播信息。       |

**返回值：**

| 类型                                                         | 说明                            |
| ------------------------------------------------------------ | ------------------------------- |
| Promise<[OperResult](arkts-apis-avsession-AVMusicTemplate-i.md##OperResult23)> | Promise对象。返回操作结果对象。 |

**示例：**

请参考[onPlayForSearch](./arkts-apis-avsession-AVMusicTemplate.md#onPlayForSearch23)的示例。

## ExecuteActionEvent<sup>23+</sup>

type ExecuteActionEvent = (actionType: string, params: string) => Promise&lt;string&gt;

执行操作的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

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

请参考[onExecuteAction](./arkts-apis-avsession-AVMusicTemplate.md#onExecuteAction23)的示例。

## PlayMediaEntityEvent<sup>23+</sup>

type PlayMediaEntityEvent = (mediaEntity: MediaEntity) => Promise&lt;void&gt;

播放媒体实体的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名      | 类型                                                         | 必填 | 说明       |
| ----------- | ------------------------------------------------------------ | ---- | ---------- |
| mediaEntity | [MediaEntity](arkts-apis-avsession-AVMusicTemplate-i.md##MediaEntity23) | 是   | 媒体实体。 |

**示例：**

请参考[onPlayMediaEntity](./arkts-apis-avsession-AVMusicTemplate.md#onPlayMediaEntity23)的示例。

## FavoriteMediaEntityEvent<sup>23+</sup>

type FavoriteMediaEntityEvent = (actionType: MediaFavoriteType, mediaEntity: MediaEntity) => Promise&lt;OperResult&gt;

收藏媒体实体的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名      | 类型                                                         | 必填 | 说明       |
| ----------- | ------------------------------------------------------------ | ---- | ---------- |
| actionType  | [MediaFavoriteType](##MediaFavoriteType23)                   | 是   | 操作类型。 |
| mediaEntity | [MediaEntity](arkts-apis-avsession-AVMusicTemplate-i.md##MediaEntity23) | 是   | 媒体实体。 |

**返回值：**

| 类型                  | 说明                            |
| --------------------- | ------------------------------- |
| Promise&lt;string&gt; | Promise对象。返回操作结果对象。 |

**示例：**

请参考[onFavoriteMediaEntity](./arkts-apis-avsession-AVMusicTemplate.md#onFavoriteMediaEntity23)的示例。

## MediaFavoriteType<sup>23+</sup>

type MediaFavoriteType = 'addFavorite' | 'removeFavorite'

媒体收藏类型的定义。

该类型可取的值为下表字符串。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

| 类型             | 说明       |
| ---------------- | ---------- |
| 'addFavorite'    | 添加收藏。 |
| 'removeFavorite' | 取消收藏。 |

## DialogControlType<sup>23+</sup>

type DialogControlType = 'open' | 'close' | 'refresh' | 'toast'

弹框控制类型的定义。

该类型可取的值为下表字符串。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

| 类型      | 说明   |
| --------- | ------ |
| 'open'    | 打开。 |
| 'close'   | 关闭。 |
| 'refresh' | 刷新。 |
| 'toast'   | 提示。 |

## ActionType<sup>23+</sup>

type ActionType = 'add' | 'remove'

操作类型的定义。

该类型可取的值为下表字符串。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

| 类型     | 说明   |
| -------- | ------ |
| 'add'    | 添加。 |
| 'remove' | 移除。 |

## ReportDialogCommandEvent<sup>23+</sup>

type ReportDialogCommandEvent = (type: DialogControlType, buttonInfo: DialogInfo) => void

上报弹框命令的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明           |
| ---------- | ------------------------------------------------------------ | ---- | -------------- |
| type       | [DialogControlType](##DialogControlType23)                   | 是   | 弹框控制类型。 |
| buttonInfo | [DialogInfo](arkts-apis-avsession-AVMusicTemplate-i.md##DialogInfo23) | 是   | 弹框信息。     |

**示例：**

请参考[onDialogCommandChange](./arkts-apis-avsession-AVMusicTemplateController.md#onDialogCommandChange23)的示例。

## ReportTabContentEvent<sup>23+</sup>

type ReportTabContentEvent = (tabId: string, tabContent: MediaTabContent) => void

上报标签页内容的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明           |
| ---------- | ------------------------------------------------------------ | ---- | -------------- |
| tabId      | string                                                       | 是   | 标签页的ID。   |
| tabContent | [MediaTabContent](arkts-apis-avsession-AVMusicTemplate-i.md##MediaTabContent23) | 是   | 标签页的内容。 |

**示例：**

请参考[onTabContentChange](./arkts-apis-avsession-AVMusicTemplateController.md#onTabContentChange23)的示例。

## ReportCustomElementsChangeEvent<sup>23+</sup>

type ReportCustomElementsChangeEvent = (actionType: ActionType, customType: CustomType, customElement: CustomElement) => void

上报自定义元素改变的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名        | 类型                                                         | 必填 | 说明         |
| ------------- | ------------------------------------------------------------ | ---- | ------------ |
| actionType    | [ActionType](##ActionType23)                                 | 是   | 操作类型。   |
| customType    | [CustomType](##CustomType23)                                 | 是   | 自定义类型。 |
| customElement | [CustomElement](arkts-apis-avsession-AVMusicTemplate-i.md##CustomElement23) | 是   | 自定义元素。 |

**示例：**

请参考[onCustomElementsChange](./arkts-apis-avsession-AVMusicTemplateController.md#onCustomElementsChange23)的示例。

## ReportExecuteActionEvent<sup>23+</sup>

type ReportExecuteActionEvent = (actionType: string, params: string) => void

上报执行动作的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名     | 类型   | 必填 | 说明             |
| ---------- | ------ | ---- | ---------------- |
| actionType | string | 是   | 操作类型。       |
| params     | string | 是   | 执行动作的信息。 |

**示例：**

请参考[onReportExecuteAction](./arkts-apis-avsession-AVMusicTemplateController.md#onReportExecuteAction23)的示例。

## ReportExecuteAbilityEvent<sup>23+</sup>

type ReportExecuteAbilityEvent = (want: WantAgent) => void

通知音频模板控制方拉起指定三方应用界面的信息的事件类型。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型                                                         | 必填 | 说明               |
| ------ | ------------------------------------------------------------ | ---- | ------------------ |
| want   | [WantAgent](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/js-apis-app-ability-wantAgent.md#WantAgent) | 是   | 三方页面启动信息。 |

**示例：**

请参考[onExtensionAbilityChange](./arkts-apis-avsession-AVMusicTemplateController.md#onExtensionAbilityChange23)的示例。