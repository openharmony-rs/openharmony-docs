# Types
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_gyH0B0hP-->
<!--Designer: @ccfriend-->
<!--Tester: @chen-gong1-->
<!--Adviser: @w_Machine_cc-->

> **NOTE**
>
> - The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This module applies only to cars running API version 23 or later.

## NoParamAsyncCallback

type NoParamAsyncCallback = () => Promise&lt;void&gt;

Defines an asynchronous callback function type that takes no parameters. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

## QueryMainTabsEvent

type QueryMainTabsEvent = () => Promise<MediaTab[]>

Defines the main tab query event. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Return value**

| Type                                                        | Description                               |
| ------------------------------------------------------------ | ----------------------------------- |
| Promise<[MediaTab](arkts-apis-avMusicTemplate-i.md#mediatab)[]> | Promise used to return a media tab collection.|

## QueryMediaTabContentEvent

type QueryMediaTabContentEvent = (tabId: string) => Promise&lt;MediaTabContent&gt;

Defines the media tab content query event. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name| Type  | Mandatory| Description        |
| ------ | ------ | ---- | ------------ |
| tabId  | string | Yes  | ID of the tab.|

**Return value**

| Type                                                        | Description                             |
| ------------------------------------------------------------ | --------------------------------- |
| Promise<[MediaTabContent](arkts-apis-avMusicTemplate-i.md#mediatabcontent)> | Promise used to return the media tab content.|

## QueryMediaEntityEvent

type QueryMediaEntityEvent = (params: QueryMediaEntityParam) => Promise&lt;PageMediaEntity&gt;

Defines the media entity query event. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name| Type                                                                                      | Mandatory| Description                |
| ------ |------------------------------------------------------------------------------------------| ---- | -------------------- |
| params | [QueryMediaEntityParam](arkts-apis-avMusicTemplate-i.md#querymediaentityparam) | Yes  | Parameters for querying a media instance.|

**Return value**

| Type                                                        | Description                                     |
| ------------------------------------------------------------ | ----------------------------------------- |
| Promise<[PageMediaEntity](arkts-apis-avMusicTemplate-i.md#pagemediaentity)> | Promise used to return the media entity pagination object.|

## QueryCompilationEvent

type QueryCompilationEvent = (compilationId: string, pageIndex: number) => Promise&lt;PageMediaEntity&gt;

Defines the compilation query event. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name       | Type  | Mandatory| Description        |
| ------------- | ------ | ---- | ------------ |
| compilationId | string | Yes  | ID of the compilation.  |
| pageIndex     | number    | Yes  | Page index.|

**Return value**

| Type                                                        | Description                                     |
| ------------------------------------------------------------ | ----------------------------------------- |
| Promise<[PageMediaEntity](arkts-apis-avMusicTemplate-i.md#pagemediaentity)> | Promise used to return the compilation media entity object.|

## QueryPlaylistEvent

type QueryPlaylistEvent = (pageIndex: number, sort: Sort) => Promise&lt;PageMediaEntity&gt;

Defines the playlist query event. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name   | Type                                                    | Mandatory| Description          |
| --------- | ------------------------------------------------------ | ---- | -------------- |
| pageIndex | number                                                    | Yes  | Page index.  |
| sort      | [Sort](arkts-apis-avMusicTemplate-e.md#sort) | Yes  | Enumeration value of sorting.|

**Return value**

| Type                                                        | Description                                       |
| ------------------------------------------------------------ | ------------------------------------------- |
| Promise<[PageMediaEntity](arkts-apis-avMusicTemplate-i.md#pagemediaentity)> | Promise used to return the playlist pagination object.|

## QueryCurrentSingleEvent

type QueryCurrentSingleEvent = () => Promise&lt;Single&gt;

Defines the current single track query event. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Return value**

| Type                                                        | Description                         |
| ------------------------------------------------------------ | ----------------------------- |
| Promise<[Single](arkts-apis-avMusicTemplate-i.md#single)> | Promise used to return the **Single** object.|

## QueryCompilationByKeywordEvent

type QueryCompilationByKeywordEvent = (keyword: string) => Promise&lt;Compilation[]&gt;

Defines the event of querying compilations by keyword. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name | Type  | Mandatory| Description                  |
| ------- | ------ | ---- | ---------------------- |
| keyword | string | Yes  | Keyword used to search for compilations.|

**Return value**

| Type                                                        | Description                                     |
| ------------------------------------------------------------ | ----------------------------------------- |
| Promise<[Compilation](arkts-apis-avMusicTemplate-i.md#compilation)[]> | Promise used to return the array of compilations related to the keyword.|

## QueryMediaEntityByKeywordEvent

type QueryMediaEntityByKeywordEvent = (keyword: string, searchType: EntityType, pageIndex: number) => Promise&lt;PageMediaEntity&gt;

Defines the event of querying media entities by keyword. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name    | Type                                                                | Mandatory| Description                  |
| ---------- |--------------------------------------------------------------------| ---- | ---------------------- |
| keyword    | string                                                             | Yes  | Keyword used to search for media.|
| searchType | [EntityType](arkts-apis-avMusicTemplate-e.md#entitytype) | Yes  | Type of the media resource to be searched for.|
| pageIndex  | number                                                                | Yes  | Page index. The value starts from 0. |

**Return value**

| Type                                                        | Description                                             |
| ------------------------------------------------------------ | ------------------------------------------------- |
| Promise<[PageMediaEntity](arkts-apis-avMusicTemplate-i.md#pagemediaentity)> | Promise used to return the media entity pagination object related to the keyword.|

## QueryRecommendMediaEntityListEvent

type QueryRecommendMediaEntityListEvent = () => Promise&lt;MediaEntity[]&gt;

Defines the event of querying the recommended media entity list. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Return value**

| Type                                                        | Description                                   |
| ------------------------------------------------------------ | --------------------------------------- |
| Promise<[MediaEntity](arkts-apis-avMusicTemplate-i.md#mediaentity)[]> | Promise used to return the array of recommended media instances.|

## QueryHotWordsEvent

type QueryHotWordsEvent = () => Promise&lt;string[]&gt;

Defines the hot word query event. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Return value**

| Type             | Description                         |
| ----------------- | ----------------------------- |
| Promise<string[]> | Promise used to return the array of hot words.|

## QuerySearchHistoryEvent

type QuerySearchHistoryEvent = () => Promise&lt;string[]&gt;

Defines the search history query event. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Return value**

| Type             | Description                             |
| ----------------- | --------------------------------- |
| Promise<string[]> | Promise used to return the array of search history.|

## ClearSearchHistoryEvent

type ClearSearchHistoryEvent = () => Promise&lt;OperResult&gt;

Defines the event of clearing search history. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Return value**

| Type                                                        | Description                                           |
| ------------------------------------------------------------ | ----------------------------------------------- |
| Promise<[OperResult](arkts-apis-avMusicTemplate-i.md#operresult)> | Promise used to return the result of clearing the search history.|

## LoginEvent

type LoginEvent = (controlType: LoginType, id?: string) => Promise&lt;QrCodeInfo[]&gt;

Defines the login event. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name     | Type                   | Mandatory| Description      |
| ----------- | ----------------------- | ---- | ---------- |
| controlType | [LoginType](#logintype) | Yes  | Login type.|
| id          | string                  | No  | QR code ID.|

**Return value**

| Type                                                        | Description                               |
| ------------------------------------------------------------ | ----------------------------------- |
| Promise<[QrCodeInfo](arkts-apis-avMusicTemplate-i.md#qrcodeinfo)[]> | Promise used to return the array of QR code information.|

## LoginType

type LoginType = 'queryLoginInfo' | 'refreshLoginInfo' | 'cancel' | 'logout'

Defines the login type. The value of this type can be any of the following strings.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Type              | Description          |
| ------------------ | -------------- |
| 'queryLoginInfo'   | Query login information.|
| 'refreshLoginInfo' | Refresh login information.|
| 'cancel'           | Cancel.        |
| 'logout'           | Logout.    |

## RequestDialogInfoEvent

type RequestDialogInfoEvent = (actionType: DialogActionType, actionInfo?: DialogActionInfo) => Promise&lt;DialogInfo&gt;

Defines the dialog box information request event. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name    | Type                                                        | Mandatory| Description                  |
| ---------- | ------------------------------------------------------------ | ---- | ---------------------- |
| actionType | [DialogActionType](#dialogactiontype)                        | Yes  | Dialog box type.          |
| actionInfo | [DialogActionInfo](arkts-apis-avMusicTemplate-i.md#dialogactioninfo) | No  | Information about the dialog box action result.|

**Return value**

| Type                                                        | Description                         |
| ------------------------------------------------------------ | ----------------------------- |
| Promise<[DialogInfo](arkts-apis-avMusicTemplate-i.md#dialoginfo)> | Promise used to return the dialog box information.|

## DialogActionType

type DialogActionType = 'open' | 'close' | 'refresh'

Defines the dialog box action type. You can use the strings listed in the following table.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Type     | Description  |
| --------- | ------ |
| 'open'    | Open.|
| 'close'   | Close.|
| 'refresh' | Refresh.|

## HandleMemberPurchaseEvent

type HandleMemberPurchaseEvent = (info: MemberPurchaseInfo) => Promise&lt;DialogInfo&gt;

Defines the membership purchase handling event. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name| Type                                                        | Mandatory| Description            |
| ------ | ------------------------------------------------------------ | ---- | ---------------- |
| info   | [MemberPurchaseInfo](arkts-apis-avMusicTemplate-i.md#memberpurchaseinfo) | Yes  | Membership purchase information.|

**Return value**

| Type                                                        | Description                         |
| ------------------------------------------------------------ | ----------------------------- |
| Promise<[DialogInfo](arkts-apis-avMusicTemplate-i.md#dialoginfo)> | Promise used to return the dialog box information.|

## QueryMemberPurchaseEvent

type QueryMemberPurchaseEvent = (memberPurchaseType: MemberPurchaseType) => Promise&lt;MemberPurchaseInfo[]&gt;

Defines the membership purchase query event. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name            | Type                                                        | Mandatory| Description            |
| ------------------ | ------------------------------------------------------------ | ---- | ---------------- |
| memberPurchaseType | [MemberPurchaseType](arkts-apis-avMusicTemplate-e.md#memberpurchasetype) | Yes  | Type of the membership purchase.|

**Return value**

| Type                                                        | Description                                 |
| ------------------------------------------------------------ | ------------------------------------- |
| Promise<[MemberPurchaseInfo](arkts-apis-avMusicTemplate-i.md#memberpurchaseinfo)[]> | Promise used to return the array of membership purchase information.|

## QueryCustomContentEvent

type QueryCustomContentEvent = (queryType: CustomType[]) => Promise&lt;CustomElement&gt;

Defines the content query event. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name   | Type                         | Mandatory| Description                                       |
| --------- | --------------------------- | ---- | ------------------------------------------- |
| queryType | [CustomType](#customtype)[] | Yes  | Custom type, which contains the user information, tab configuration, code build options, and system settings.|

**Return value**

| Type                                                        | Description                                   |
| ------------------------------------------------------------ | --------------------------------------- |
| Promise<[CustomElement](arkts-apis-avMusicTemplate-i.md#customelement)> | Promise used to return the custom elements of the home page.|

## CustomType

type CustomType = 'USER_INFO' | 'TAB' | 'COMPILATION' | 'SETTINGS'

Defines the custom type. You can use the strings listed in the following table.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Type         | Description      |
| ------------- | ---------- |
| 'USER_INFO'   | User information.|
| 'TAB'         | Tab.  |
| 'COMPILATION' | Compilation.    |
| 'SETTINGS'    | Settings.    |

## DownloadMediaEntityEvent

type DownloadMediaEntityEvent = (controlType: DownloadControlType, mediaEntity: MediaEntity) => Promise&lt;OperResult&gt;

Defines the media entity download event. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name     | Type                                                        | Mandatory| Description                                      |
| ----------- | ---------------------------------------------------------- | ---- | ------------------------------------------ |
| controlType | [DownloadControlType](#downloadcontroltype)                | Yes  | Control type, which can be user information, tab, compilation, or settings.|
| mediaEntity | [MediaEntity](arkts-apis-avMusicTemplate-i.md#mediaentity) | Yes  | Media instance.                                |

**Return value**

| Type                                                        | Description                                         |
| ------------------------------------------------------------ | --------------------------------------------- |
| Promise<[OperResult](arkts-apis-avMusicTemplate-i.md#operresult)> | Promise used to return the result of downloading the media entity.|

## DownloadControlType

type DownloadControlType = 'startDownload' | 'deleteDownload' | 'resumeDownload' | 'pauseDownload'

Defines the download control types, including starting, resuming, pausing, and deleting a download. You can use the strings listed in the following table.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Type            | Description      |
| ---------------- | ---------- |
| 'startDownload'  | Starts a download.|
| 'deleteDownload' | Deletes a download.|
| 'resumeDownload' | Resumes a download.|
| 'pauseDownload'  | Pauses a download.|

## SettingsChangeEvent

type SettingsChangeEvent = (settingItem: SettingItem) => Promise&lt;SettingItem&gt;

Defines the settings change event. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name     | Type                                                        | Mandatory| Description    |
| ----------- | ------------------------------------------------------------ | ---- | -------- |
| settingItem | [SettingItem](arkts-apis-avMusicTemplate-i.md#settingitem) | Yes  | Setting item.|

**Return value**

| Type                                                        | Description                             |
| ------------------------------------------------------------ | --------------------------------- |
| Promise<[SettingItem](arkts-apis-avMusicTemplate-i.md#settingitem)> | Promise used to return the changed settings.|

## ProblemAndAdviceEvent

type ProblemAndAdviceEvent = (advice: string) => Promise&lt;OperResult&gt;

Defines the problem and advice event. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| advice | string | Yes  | Content of the problem or advice.|

**Return value**

| Type                                                        | Description                                       |
| ------------------------------------------------------------ | ------------------------------------------- |
| Promise<[OperResult](arkts-apis-avMusicTemplate-i.md#operresult)> | Promise used to return the result of the problem or advice.|

## PlayForSearchEvent

type PlayForSearchEvent = (command: SearchPlayInfoType, args: SearchPlayInfo) => Promise&lt;OperResult&gt;

Defines the search and playback event. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name | Type                                                        | Mandatory| Description            |
| ------- | ------------------------------------------------------------ | ---- | ---------------- |
| command | [SearchPlayInfoType](arkts-apis-avMusicTemplate-e.md#searchplayinfotype) | Yes  | Type of the search and playback information.|
| args    | [SearchPlayInfo](arkts-apis-avMusicTemplate-i.md#searchplayinfo) | Yes  | Search and playback information.      |

**Return value**

| Type                                                        | Description                                 |
| ------------------------------------------------------------ | ------------------------------------- |
| Promise<[OperResult](arkts-apis-avMusicTemplate-i.md#operresult)> | Promise used to return the result of the search and playback operation.|

## ExecuteActionEvent

type ExecuteActionEvent = (actionType: string, params: string) => Promise&lt;string&gt;

Defines the action execution event. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name    | Type  | Mandatory| Description      |
| ---------- | ------ | ---- | ---------- |
| actionType | string | Yes  | Action type.|
| params     | string | Yes  | Parameter information.|

**Return value**

| Type                 | Description                                 |
| --------------------- | ------------------------------------- |
| Promise&lt;string&gt; | Promise used to return the result of action execution.|

## PlayMediaEntityEvent

type PlayMediaEntityEvent = (mediaEntity: MediaEntity) => Promise&lt;void&gt;

Defines the media entity playback event. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name     | Type                                                        | Mandatory| Description                |
| ----------- | ------------------------------------------------------------ | ---- | -------------------- |
| mediaEntity | [MediaEntity](arkts-apis-avMusicTemplate-i.md#mediaentity) | Yes  | Media entity to be played.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

## FavoriteMediaEntityEvent

type FavoriteMediaEntityEvent = (actionType: MediaFavoriteType, mediaEntity: MediaEntity) => Promise&lt;OperResult&gt;

Defines the event of adding a media entity to favorites. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name     | Type                                                       | Mandatory| Description      |
| ----------- | ---------------------------------------------------------- | ---- | ---------- |
| actionType  | [MediaFavoriteType](#mediafavoritetype)                   | Yes  | Action type.|
| mediaEntity | [MediaEntity](arkts-apis-avMusicTemplate-i.md#mediaentity) | Yes  | Media instance.|

**Return value**

| Type                     | Description                                         |
| ------------------------- | --------------------------------------------- |
| Promise&lt;OperResult&gt; | Promise used to return the result of adding the media entity to favorites.|

## MediaFavoriteType

type MediaFavoriteType = 'addFavorite' | 'removeFavorite'

Defines the media favorites type. You can use the strings listed in the following table.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Type            | Description      |
| ---------------- | ---------- |
| 'addFavorite'    | Adds an item to favorites.|
| 'removeFavorite' | Removes an item from favorites.|

## DialogControlType

type DialogControlType = 'open' | 'close' | 'refresh' | 'toast'

Defines the dialog box control type. You can use the strings listed in the following table.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Type     | Description  |
| --------- | ------ |
| 'open'    | Open.|
| 'close'   | Close.|
| 'refresh' | Refresh.|
| 'toast'   | Toast.|

## ActionType

type ActionType = 'add' | 'remove'

Defines the action type. You can use the strings listed in the following table.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Type    | Description  |
| -------- | ------ |
| 'add'    | Add.|
| 'remove' | Remove.|

## ReportDialogCommandEvent

type ReportDialogCommandEvent = (type: DialogControlType, buttonInfo: DialogInfo) => void

Defines the dialog box command reporting event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name    | Type                                                        | Mandatory| Description            |
| ---------- | ------------------------------------------------------------ | ---- | ---------------- |
| type       | [DialogControlType](#dialogcontroltype)                      | Yes  | Dialog box control type.|
| buttonInfo | [DialogInfo](arkts-apis-avMusicTemplate-i.md#dialoginfo) | Yes  | Dialog box information.    |

## ReportTabContentEvent

type ReportTabContentEvent = (tabId: string, tabContent: MediaTabContent) => void

Defines the tab content reporting event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name    | Type                                                        | Mandatory| Description          |
| ---------- | ------------------------------------------------------------ | ---- | -------------- |
| tabId      | string                                                       | Yes  | ID of the tab.  |
| tabContent | [MediaTabContent](arkts-apis-avMusicTemplate-i.md#mediatabcontent) | Yes  | Content of the tab.|

## ReportCustomElementsChangeEvent

type ReportCustomElementsChangeEvent = (actionType: ActionType, customType: CustomType, customElement: CustomElement) => void

Defines the event of reporting custom element changes.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name       | Type                                                     | Mandatory| Description        |
| ------------- | ------------------------------------------------------- | ---- | ------------ |
| actionType    | [ActionType](#actiontype)                               | Yes  | Action type.  |
| customType    | [CustomType](#customtype)                               | Yes  | Custom type.|
| customElement | [CustomElement](arkts-apis-avMusicTemplate-i.md#customelement) | Yes  | Custom element.|

## ReportExecuteActionEvent

type ReportExecuteActionEvent = (actionType: string, params: string) => void

Defines the action execution reporting event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name    | Type  | Mandatory| Description            |
| ---------- | ------ | ---- | ---------------- |
| actionType | string | Yes  | Action type.      |
| params     | string | Yes  | Information about the action execution.|

## ReportExecuteAbilityEvent

type ReportExecuteAbilityEvent = (want: WantAgent) => void

Defines the event of notifying the audio template controller to launch the specified media application UI.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name| Type                                                        | Mandatory| Description              |
| ------ | ------------------------------------------------------------ | ---- | ------------------ |
| want   | [WantAgent](../apis-ability-kit/js-apis-app-ability-wantAgent.md#wantagent) | Yes  | Launch information of the media application page.|
