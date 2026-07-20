# @ohos.multimedia.avMusicTemplate

> **说明：**  
>  
> - 本模块仅适用于API version 23及以上版本的Car设备。

**起始版本：** 23

<!--Device-unnamed-declare namespace avMusicTemplate--><!--Device-unnamed-declare namespace avMusicTemplate-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## 导入模块

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createAVMusicTemplate](arkts-avsession-avmusictemplate-createavmusictemplate-f.md#createavmusictemplate) | 创建音频模板，返回音频模板实例。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createAVMusicTemplateController](arkts-avsession-avmusictemplate-createavmusictemplatecontroller-f-sys.md#createavmusictemplatecontroller) | 创建音频模板控制器，返回音频模板控制器对象。 |
| [getAllAVMusicTemplateDescriptors](arkts-avsession-avmusictemplate-getallavmusictemplatedescriptors-f-sys.md#getallavmusictemplatedescriptors) | 获取所有的音频模板描述，返回音频模板描述的集合。 |
| [offAVMusicTemplateCreate](arkts-avsession-avmusictemplate-offavmusictemplatecreate-f-sys.md#offavmusictemplatecreate) | 注销音频模板创建监听。 |
| [offAVMusicTemplateDestroy](arkts-avsession-avmusictemplate-offavmusictemplatedestroy-f-sys.md#offavmusictemplatedestroy) | 注销音频模板销毁监听。 |
| [onAVMusicTemplateCreate](arkts-avsession-avmusictemplate-onavmusictemplatecreate-f-sys.md#onavmusictemplatecreate) | 注册音频模板创建的监听。使用callback异步回调。 |
| [onAVMusicTemplateDestroy](arkts-avsession-avmusictemplate-onavmusictemplatedestroy-f-sys.md#onavmusictemplatedestroy) | 注册音频模板销毁监听。使用callback异步回调。 |
<!--DelEnd-->

### 类

| 名称 | 说明 |
| --- | --- |
| [AVMusicTemplate](arkts-avsession-avmusictemplate-avmusictemplate-c.md) | 调用[avMusicTemplate.createAVMusicTemplate](arkts-avsession-avmusictemplate-createavmusictemplate-f.md#createavmusictemplate-1)获取实例后，可获取其ID，启动音频模板界面，并配置数据获取方法。随后，同步数据给模板控制方，以完成后续操作。 |
| [AVMusicTemplateController](arkts-avsession-avmusictemplate-avmusictemplatecontroller-c.md) | 音频模板控制器，可以获得音频模板控制器唯一的标识，用于与接入音频模板的媒体应用数据交互。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Album](arkts-avsession-avmusictemplate-album-i.md) | 专辑的定义。继承自[MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md)。 |
| [Banner](arkts-avsession-avmusictemplate-banner-i.md) | 海报的定义。继承自[MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md)。 |
| [Compilation](arkts-avsession-avmusictemplate-compilation-i.md) | 合集的定义。继承自[OperResult](arkts-avsession-avmusictemplate-operresult-i.md)。 |
| [CustomElement](arkts-avsession-avmusictemplate-customelement-i.md) | “我的主页”自定义元素的定义。继承自[OperResult](arkts-avsession-avmusictemplate-operresult-i.md)。 |
| [DialogActionInfo](arkts-avsession-avmusictemplate-dialogactioninfo-i.md) | 对话框动作信息的定义。 |
| [DialogButtonInfo](arkts-avsession-avmusictemplate-dialogbuttoninfo-i.md) | 对话框按钮信息的定义。 |
| [DialogInfo](arkts-avsession-avmusictemplate-dialoginfo-i.md) | 对话框信息的定义。 |
| [EpisodeRange](arkts-avsession-avmusictemplate-episoderange-i.md) | 剧集的范围的定义。 |
| [FavoriteData](arkts-avsession-avmusictemplate-favoritedata-i.md) | 收藏/订阅的定义。 |
| [MediaElement](arkts-avsession-avmusictemplate-mediaelement-i.md) | 媒体元素Singer/Radio/Banner结构体定义 |
| [MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md) | 媒体实例的定义。继承自[OperResult](arkts-avsession-avmusictemplate-operresult-i.md)。 |
| [MediaTab](arkts-avsession-avmusictemplate-mediatab-i.md) | 媒体标签页的定义。 |
| [MediaTabContent](arkts-avsession-avmusictemplate-mediatabcontent-i.md) | 媒体标签页内容的定义。继承自[OperResult](arkts-avsession-avmusictemplate-operresult-i.md)。 |
| [MemberPurchaseInfo](arkts-avsession-avmusictemplate-memberpurchaseinfo-i.md) | 会员购买信息的定义。 |
| [OperResult](arkts-avsession-avmusictemplate-operresult-i.md) | 操作结果的定义。 |
| [PageMediaEntity](arkts-avsession-avmusictemplate-pagemediaentity-i.md) | 标签页媒体的定义。继承自[OperResult](arkts-avsession-avmusictemplate-operresult-i.md)。 |
| [PlayInfo](arkts-avsession-avmusictemplate-playinfo-i.md) | 播放信息的定义。 |
| [QrCodeInfo](arkts-avsession-avmusictemplate-qrcodeinfo-i.md) | 二维码信息的定义。 |
| [QueryMediaEntityParam](arkts-avsession-avmusictemplate-querymediaentityparam-i.md) | 查询媒体实例参数的定义。 |
| [Ranking](arkts-avsession-avmusictemplate-ranking-i.md) | 排行榜的定义。继承自[MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md)。 |
| [SearchPlayInfo](arkts-avsession-avmusictemplate-searchplayinfo-i.md) | 搜播信息的定义。 |
| [SearchPlayMusicInfo](arkts-avsession-avmusictemplate-searchplaymusicinfo-i.md) | 搜播的音频信息的定义。 |
| [SearchPlayMusicItem](arkts-avsession-avmusictemplate-searchplaymusicitem-i.md) | 搜播的音频项目的定义。 |
| [SearchPlayVideoInfo](arkts-avsession-avmusictemplate-searchplayvideoinfo-i.md) | 搜播的视频信息的定义。 |
| [SettingContent](arkts-avsession-avmusictemplate-settingcontent-i.md) | 设置内容的定义（音频模板里有定义设置页面，设置内容用于设置页的填充）。 |
| [SettingItem](arkts-avsession-avmusictemplate-settingitem-i.md) | 设置项的定义。 |
| [Single](arkts-avsession-avmusictemplate-single-i.md) | 单曲的定义。继承自[MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md)。 |
| [UserInfo](arkts-avsession-avmusictemplate-userinfo-i.md) | 用户信息的定义。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AVMusicTemplateDescriptor](arkts-avsession-avmusictemplate-avmusictemplatedescriptor-i-sys.md) | 音频模板描述。包含音频模板唯一标识，应用的包名和用户ID。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AVMusicTemplateErrorCode](arkts-avsession-avmusictemplate-avmusictemplateerrorcode-e.md) | 表示错误码类型的枚举。 |
| [AVMusicTemplateType](arkts-avsession-avmusictemplate-avmusictemplatetype-e.md) | 表示音频模板类型的枚举。 |
| [ButtonType](arkts-avsession-avmusictemplate-buttontype-e.md) | 表示按钮类型的枚举。 |
| [DialogType](arkts-avsession-avmusictemplate-dialogtype-e.md) | 表示对话框类型的枚举。 |
| [DownloadStatus](arkts-avsession-avmusictemplate-downloadstatus-e.md) | 表示下载状态类型的枚举。 |
| [EntityType](arkts-avsession-avmusictemplate-entitytype-e.md) | 表示媒体资源类型的枚举。 |
| [MemberPurchaseType](arkts-avsession-avmusictemplate-memberpurchasetype-e.md) | 表示会员购买类型的枚举。 |
| [PlaybackState](arkts-avsession-avmusictemplate-playbackstate-e.md) | 表示媒体资源的播放状态的枚举。 |
| [SearchPlayInfoType](arkts-avsession-avmusictemplate-searchplayinfotype-e.md) | 表示搜播信息类型的枚举。 |
| [SettingType](arkts-avsession-avmusictemplate-settingtype-e.md) | 表示设置类型的枚举。 |
| [Sort](arkts-avsession-avmusictemplate-sort-e.md) | 表示查询到的列表数据排序类型的枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ActionType](arkts-avsession-avmusictemplate-actiontype-t.md) | 操作类型的定义。该类型可取的值为下表字符串。 |
| [ClearSearchHistoryEvent](arkts-avsession-avmusictemplate-clearsearchhistoryevent-t.md) | 清除搜索历史事件。使用Promise异步回调。 |
| [CustomType](arkts-avsession-avmusictemplate-customtype-t.md) | 自定义类型。该类型可取的值为下表字符串。 |
| [DialogActionType](arkts-avsession-avmusictemplate-dialogactiontype-t.md) | 对话框操作类型。该类型可取的值为下表字符串。 |
| [DialogControlType](arkts-avsession-avmusictemplate-dialogcontroltype-t.md) | 对话框控制类型的定义。该类型可取的值为下表字符串。 |
| [DownloadControlType](arkts-avsession-avmusictemplate-downloadcontroltype-t.md) | 定义下载操作的控制类型，包括开始下载、删除下载、恢复下载和暂停下载。该类型可取的值为下表字符串。 |
| [DownloadMediaEntityEvent](arkts-avsession-avmusictemplate-downloadmediaentityevent-t.md) | 媒体实体下载事件。使用Promise异步回调。 |
| [ExecuteActionEvent](arkts-avsession-avmusictemplate-executeactionevent-t.md) | 执行操作事件。使用Promise异步回调。 |
| [FavoriteMediaEntityEvent](arkts-avsession-avmusictemplate-favoritemediaentityevent-t.md) | 媒体实体收藏事件。使用Promise异步回调。 |
| [HandleMemberPurchaseEvent](arkts-avsession-avmusictemplate-handlememberpurchaseevent-t.md) | 处理购买会员事件。使用Promise异步回调。 |
| [LoginEvent](arkts-avsession-avmusictemplate-loginevent-t.md) | 登录事件。使用Promise异步回调。 |
| [LoginType](arkts-avsession-avmusictemplate-logintype-t.md) | 登录的类型。该类型可取的值为下表字符串。 |
| [MediaFavoriteType](arkts-avsession-avmusictemplate-mediafavoritetype-t.md) | 媒体收藏类型的定义。该类型可取的值为下表字符串。 |
| [NoParamAsyncCallback](arkts-avsession-avmusictemplate-noparamasynccallback-t.md) | 定义无参数的异步回调函数类型。使用Promise异步回调。 |
| [PlayForSearchEvent](arkts-avsession-avmusictemplate-playforsearchevent-t.md) | 搜播事件。使用Promise异步回调。 |
| [PlayMediaEntityEvent](arkts-avsession-avmusictemplate-playmediaentityevent-t.md) | 媒体实体播放事件。使用Promise异步回调。 |
| [ProblemAndAdviceEvent](arkts-avsession-avmusictemplate-problemandadviceevent-t.md) | 问题和建议事件。使用Promise异步回调。 |
| [QueryCompilationByKeywordEvent](arkts-avsession-avmusictemplate-querycompilationbykeywordevent-t.md) | 按关键字查询合集的事件。使用Promise异步回调。 |
| [QueryCompilationEvent](arkts-avsession-avmusictemplate-querycompilationevent-t.md) | 合集查询事件。使用Promise异步回调。 |
| [QueryCurrentSingleEvent](arkts-avsession-avmusictemplate-querycurrentsingleevent-t.md) | 当前单曲查询事件。使用Promise异步回调。 |
| [QueryCustomContentEvent](arkts-avsession-avmusictemplate-querycustomcontentevent-t.md) | 自定义内容查询事件。使用Promise异步回调。 |
| [QueryHotWordsEvent](arkts-avsession-avmusictemplate-queryhotwordsevent-t.md) | 热词查询事件。使用Promise异步回调。 |
| [QueryMainTabsEvent](arkts-avsession-avmusictemplate-querymaintabsevent-t.md) | 主标签页查询事件。使用Promise异步回调。 |
| [QueryMediaEntityByKeywordEvent](arkts-avsession-avmusictemplate-querymediaentitybykeywordevent-t.md) | 通过关键字查询媒体数据的回调事件 |
| [QueryMediaEntityEvent](arkts-avsession-avmusictemplate-querymediaentityevent-t.md) | 媒体实体查询事件。使用Promise异步回调。 |
| [QueryMediaTabContentEvent](arkts-avsession-avmusictemplate-querymediatabcontentevent-t.md) | 媒体标签页内容查询事件。使用Promise异步回调。 |
| [QueryMemberPurchaseEvent](arkts-avsession-avmusictemplate-querymemberpurchaseevent-t.md) | 购买会员查询事件。使用Promise异步回调。 |
| [QueryPlaylistEvent](arkts-avsession-avmusictemplate-queryplaylistevent-t.md) | 播放列表查询事件。使用Promise异步回调。 |
| [QueryRecommendMediaEntityListEvent](arkts-avsession-avmusictemplate-queryrecommendmediaentitylistevent-t.md) | 推荐媒体实体列表查询事件。使用Promise异步回调。 |
| [QuerySearchHistoryEvent](arkts-avsession-avmusictemplate-querysearchhistoryevent-t.md) | 搜索历史查询事件。使用Promise异步回调。 |
| [ReportCustomElementsChangeEvent](arkts-avsession-avmusictemplate-reportcustomelementschangeevent-t.md) | 上报自定义元素变更信息的回调事件 |
| [ReportDialogCommandEvent](arkts-avsession-avmusictemplate-reportdialogcommandevent-t.md) | 对话框命令上报事件。 |
| [ReportExecuteAbilityEvent](arkts-avsession-avmusictemplate-reportexecuteabilityevent-t.md) | 通知音频模板控制方拉起指定媒体应用界面事件。 |
| [ReportExecuteActionEvent](arkts-avsession-avmusictemplate-reportexecuteactionevent-t.md) | 执行动作上报事件。 |
| [ReportTabContentEvent](arkts-avsession-avmusictemplate-reporttabcontentevent-t.md) | 标签页内容上报事件。 |
| [RequestDialogInfoEvent](arkts-avsession-avmusictemplate-requestdialoginfoevent-t.md) | 对话框信息请求事件。使用Promise异步回调。 |
| [SettingsChangeEvent](arkts-avsession-avmusictemplate-settingschangeevent-t.md) | 设置变更事件类型。使用Promise异步回调。 |

