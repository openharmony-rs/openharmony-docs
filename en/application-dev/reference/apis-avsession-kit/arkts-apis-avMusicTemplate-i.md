# Interfaces (Others)
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

## MediaTab

Defines the media tab page.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name         | Type                                                        | Read-Only| Optional| Description                                              |
| ------------- | ------------------------------------------------------------ | ---- | ---- | -------------------------------------------------- |
| tabId         | string                                                       | No  | No  | ID of the tab page.                                    |
| tabName       | string                                                       | No  | No  | Name of the tab page.                                    |
| tabIcon       | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | No  | Yes  | Icon of the tab page (mandatory when a template is accessed on the tab page of the main page).|
| extraDataJson | string                                                       | No  | Yes  | Additional content on the tab page.                              |

## OperResult

Defines the operation result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name     | Type  | Read-Only| Optional| Description      |
| --------- | ------ | ---- | ---- | ---------- |
| errorCode | number   | No  | No  | Error code.  |
| errorMsg  | string | No  | Yes  | Error message.|

## MediaTabContent

Defines the content of the media tab page. It is inherited from [OperResult](#operresult).

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name        | Type                           | Read-Only| Optional| Description                |
| ------------ | ----------------------------- | ---- | ---- | -------------------- |
| tabId        | string                        | No  | No  | ID of the tab page.        |
| compilations | [Compilation](#compilation)[] | No  | No  | Array of page content compilations.|

## Compilation

Defines the compilation. It is inherited from [OperResult](#operresult).

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name           | Type                                                        | Read-Only| Optional| Description                           |
| --------------- | ------------------------------------------------------------ | ---- | ---- |-------------------------------|
| id              | string                                                       | No  | No  | Unique ID of the compilation.                     |
| title           | string                                                       | No  | No  | Title of the compilation.                       |
| hasMoreData     | boolean                                                      | No  | No  | Whether there is more compilation data. **true** means yes; **false** otherwise. No default value.|
| totalSize       | number                                                       | No  | No  | Total number of compilations.                      |
| memberMediaType | [EntityType](arkts-apis-avMusicTemplate-e.md#entitytype) | No  | No  | Media resource type of the compilation.                   |
| topElements     | [MediaEntity](#mediaentity)[]                                  | No  | No  | Content of the collection.                       |

## Banner

Defines the banner. It is inherited from [MediaEntity](#mediaentity).

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name            | Type   | Read-Only| Optional| Description                                |
| ---------------- | ------- | ---- | ---- |------------------------------------|
| isSupportOnePlay | boolean | No  | No  | Whether one-click playback is supported. **true**: yes; **false**: no. No default value.|

## Album

Defines the album. It is inherited from [MediaEntity](#mediaentity).

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name            | Type                         | Read-Only| Optional| Description              |
| ---------------- | ----------------------------- | ---- | ---- | ------------------ |
| singer           | string                        | No  | No  | Singer name.          |
| playCounts       | string                        | No  | No  | Number of playbacks.          |
| favSubscribeData | [FavoriteData](#favoritedata) | No  | No  | Favorite or subscription information.|
| episodeCounts    | string                        | No  | Yes  | Total number of audio files in an album.  |

## Ranking

Defines the ranking. It is inherited from [MediaEntity](#mediaentity).

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name       | Type                           | Read-Only| Optional| Description              |
| ----------- | ----------------------------- | ---- | ---- | ------------------ |
| topElements | [MediaEntity](#mediaentity)[] | No  | No  | Recommended songs in the rank list.|

## MediaEntity

Defines the media instance. It is inherited from [OperResult](#operresult).

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name           | Type                                                        | Read-Only| Optional| Description                   |
| --------------- | ------------------------------------------------------------ | ---- | ---- | ----------------------- |
| mediaId         | string                                                       | No  | No  | ID of the media resource.         |
| mediaType       | [EntityType](arkts-apis-avMusicTemplate-e.md#entitytype) | No  | No  | Type of the media resource.       |
| parentId        | string                                                       | No  | No  | Media resource ID of the parent node.   |
| parentMediaType | [EntityType](arkts-apis-avMusicTemplate-e.md#entitytype) | No  | No  | Media resource type of the parent node. |
| title           | string                                                       | No  | No  | Title of the media resource.       |
| desc            | string                                                       | No  | Yes  | Description of the media resource.       |
| imageUrl        | string                                                       | No  | No  | Cover image URL of the media resource.|
| playState       | [PlaybackState](arkts-apis-avMusicTemplate-e.md#playbackstate) | No  | No  | Playback state of the media resource.   |

## QueryMediaEntityParam

Defines the parameters for querying a media instance.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name         | Type                                                        | Read-Only| Optional| Description                  |
| ------------- | ------------------------------------------------------------ | ---- | ---- | ---------------------- |
| entityId      | string                                                       | No  | No  | ID of the media instance.        |
| pageIndex     | number                                                       | No  | No  | Index of the media tab page.    |
| type          | [EntityType](arkts-apis-avMusicTemplate-e.md#entitytype) | No  | No  | Type of the media resource.        |
| subEntityType | [EntityType](arkts-apis-avMusicTemplate-e.md#entitytype) | No  | Yes  | Media resource type of the child node.|
| sort          | [Sort](arkts-apis-avMusicTemplate-e.md#sort)       | No  | Yes  | Sorting of the queried list data.|
| episodeRange  | [EpisodeRange](#episoderange) | No  | Yes  | Range of episodes to be queried.    |

## EpisodeRange

Defines the episode range.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name | Type| Read-Only| Optional| Description        |
| ----- | ---- | ---- | ---- | ------------ |
| start | number | No  | No  | Start index.|
| end   | number | No  | No  | End index.|

## PageMediaEntity

Defines the media of the tab page. It is inherited from [OperResult](#operresult).

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name           | Type                                                        | Read-Only| Optional| Description                                        |
| --------------- | ------------------------------------------------------------ | ---- | ---- | -------------------------------------------- |
| pageIndex       | number                                                       | No  | No  | Pagination query index.                              |
| pageSize        | number                                                       | No  | No  | Page size.                                |
| hasMoreData     | boolean                                                      | No  | No  | Whether there is a next page. **true** means yes; **false** otherwise. No default value.|
| totalSize       | number                                                       | No  | No  | Total data size.                                |
| memberMediaType | [EntityType](arkts-apis-avMusicTemplate-e.md#entitytype) | No  | No  | Type of the media resource.                              |
| elements        | [MediaEntity](#mediaentity)[] | No  | No  | Data content to be queried. (The corresponding structured data is transferred based on the type.)|
| sort            | [Sort](arkts-apis-avMusicTemplate-e.md#sort)       | No  | Yes  | Data sorting.                                  |
| episodeRange    | [EpisodeRange](#episoderange) | No  | Yes  | Episode range.                                  |

## Single

Defines the single song. It is inherited from [MediaEntity](#mediaentity).

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name            | Type                                                        | Read-Only| Optional| Description                                      |
| ---------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------ |
| isVip            | boolean                                                      | No  | No  | Whether the song is a VIP song. **true**: yes; **false**: no. No default value.|
| singer           | string                                                       | No  | No  | Singer name.                              |
| playInfo         | [PlayInfo](#playinfo) | No  | No  | Information about the song to be played.                            |
| favSubscribeData | [FavoriteData](#favoritedata) | No  | No  | Information about a favorite or subscribed song.                  |
| tags             | string[]                                                     | No  | Yes  | Array of song tags.                      |
| settings         | [SettingItem](#settingitem)[]                                | No  | Yes  | Array of song settings.                        |
| downloadStatus   | [DownloadStatus](arkts-apis-avMusicTemplate-e.md#downloadstatus) | No  | Yes  | Song download status.                            |
| downloadProgress | number                                                       | No  | Yes  | Song download progress.                            |

## PlayInfo

Defines the playback information.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name                  | Type    | Read-Only| Optional| Description                                 |
| ---------------------- | -------- | ---- | ---- |-------------------------------------|
| playCounts             | string   | No  | No  | Number of playback times.                              |
| isSupportNext          | boolean  | No  | No  | Whether the next song is supported. **true**: yes; **false**: no. No default value.|
| isSupportPrev          | boolean  | No  | No  | Whether the previous song is supported. **true**: yes; **false**: no. No default value.|
| isSupportQuickForward  | boolean  | No  | No  | Whether quick-forward is supported. **true**: yes; **false**: no. No default value.|
| isSupportQuickBackward | boolean  | No  | No  | Whether quick-backward is supported. **true**: yes; **false**: no. No default value.|
| quickForwardStep       | number     | No  | No  | Quick-forward step.                          |
| quickBackwardStep      | number     | No  | No  | Quick-backward step.                          |
| isSupportSkipHead      | boolean  | No  | No  | Whether to support skipping the beginning. **true**: yes; **false**: no. No default value.|
| isSupportSkipTail      | boolean  | No  | No  | Whether to support skipping the end. **true**: yes; **false**: no. No default value.|
| isSupportPlayMode      | boolean  | No  | No  | Whether to support switching the playback mode. **true**: yes; **false**: no. No default value.|
| isSupportPlayRate      | boolean  | No  | No  | Whether to support changing the playback rate. **true**: yes; **false**: no. No default value.|
| supportedPlayRate      | string[] | No  | No  | Array of supported playback rates.                       |
| currentPlayRate        | string   | No  | No  | Current playback rate.                           |
| isSupportSoundQuality  | boolean  | No  | No  | Whether to support sound quality. **true**: yes; **false**: no. No default value.|
| isSupportSoundEffect   | boolean  | No  | No  | Whether to support sound effect. **true**: yes; **false**: no. No default value.|
| totalDuration          | number     | No  | No  | Total playback duration.                             |
| currentPlayDuration    | number     | No  | No  | Current playback duration.                           |
| isSupportProgress      | boolean  | No  | No  | Whether to support the progress. **true**: yes; **false**: no. The default value is **true**.|

## FavoriteData

Defines the favorites or subscriptions.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name        | Type   | Read-Only| Optional| Description                                                      |
| ------------ | ------- | ---- | ---- | ---------------------------------------------------------- |
| isSupportFav | boolean | No  | No  | Whether to support favorites or subscriptions. **true**: yes; **false**: no. No default value.|
| isFavorite   | boolean | No  | No  | Whether the content has been favorited or subscribed. **true**: yes; **false**: no. No default value.|
| favCounts    | string  | No  | No  | Number of favorites or subscriptions.                                         |

## SettingItem

Defines the setting item.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name        | Type                                                        | Read-Only| Optional| Description                                                        |
| ------------ | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| id           | string                                                       | No  | No  | Unique ID of the setting item.                                            |
| title        | string                                                       | No  | No  | Title of the setting item.                                              |
| desc         | string                                                       | No  | No  | Description of the setting item.                                              |
| settingType  | [SettingType](arkts-apis-avMusicTemplate-e.md#settingtype) | No  | Yes  | Type of the setting item.                                              |
| settingValue | string \| boolean \| [SettingContent](#settingcontent)[] \| [WantAgent](../apis-ability-kit/js-apis-app-ability-wantAgent.md#wantagent) | No  | Yes  | Value of the setting item.<br>- When **settingType** is **SettingType.SWITCH**, the value is of the boolean type.<br>- When **settingType** is **SettingType.LIST**, the value is a **SettingContent** array.<br>- When **settingType** is **SettingType.JUMP**, the value is of the string type.|
| mediaId      | string                                                       | No  | No  | Media ID associated with the current setting.<br>If the setting is associated with the current media information, set **mediaId**; otherwise, do not set **mediaId**.|

## SettingContent

Defines the setting content. (The audio template defines the setting page, and the setting content is used to fill the setting page.)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name      | Type                                                        | Read-Only| Optional| Description                                               |
| ---------- | ------------------------------------------------------------ | ---- | ---- | --------------------------------------------------- |
| value      | string                                                       | No  | No  | Setting content.                                       |
| isSelected | boolean                                                      | No  | No  | Whether to select the setting content. **true**: yes; **false**: no. No default value.|
| textTags   | string[]                                                     | No  | Yes  | Array of descriptions of the setting content.                             |
| imageTags  | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)[] | No  | Yes  | Array of tag descriptions of the setting content.                         |

## QrCodeInfo

Defines the QR code information.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name       | Type                                                        | Read-Only| Optional| Description                                                        |
| ----------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| id          | string                                                       | No  | No  | Unique ID of the QR code session for user login.<br>When the QR code expires, the MediaUI will use this ID to query and update the new QR code from the media application.|
| price       | string                                                       | No  | No  | Purchase price.                                                  |
| titleName   | string                                                       | No  | No  | Title name.                                                  |
| detailName  | string                                                       | No  | No  | Details name.                                                  |
| tips        | string                                                       | No  | No  | Tip message.                                                  |
| icon        | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | No  | Yes  | Icon of the application associated with the QR code. The icon of the target application should be displayed for the QR code used for application login.|
| content     | string                                                       | No  | No  | Content of the QR code.                                              |
| codeData    | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | No  | Yes  | Image of the QR code.                                                |
| validPeriod | number                                                       | No  | No  | Validity period of the QR code, in seconds.<br>When the QR code expires, it is used to query and obtain a new QR code.|

## DialogActionInfo

Defines the action information of the dialog box.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name        | Type   | Read-Only| Optional| Description                                                       |
| ------------ | ------- | ---- | ---- | ----------------------------------------------------------- |
| dialogId     | string  | No  | No  | Unique ID of the dialog box action.                                   |
| isChecked    | boolean | No  | No  | Whether the check box in the dialog box is selected. **true**: selected; **false**: not selected. No default value.|
| clickedBtnId | string  | No  | No  | ID of the button that a user taps.                                       |

## DialogInfo

Defines the dialog box information.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name       | Type                                                        | Read-Only| Optional| Description                                                        |
| ----------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| dialogId    | string                                                       | No  | No  | Unique ID of the dialog box.                                            |
| dialogType  | [DialogType](arkts-apis-avMusicTemplate-e.md#dialogtype) | No  | No  | Type of the dialog box.                                              |
| title       | string                                                       | No  | Yes  | Title of the dialog box.                                              |
| text        | string                                                       | No  | Yes  | Content of the dialog box.                                              |
| buttons     | [DialogButtonInfo](#dialogbuttoninfo)[] | No  | Yes  | Array of buttons in the dialog box.                                          |
| qrCodes     | [QrCodeInfo](#qrcodeinfo)[]                                  | No  | Yes  | Array of QR codes in the dialog box.<br>If the QR code information is set, the dialog box is identified as a QR code dialog box and the QR code information will be displayed first. A maximum of two QR codes can be set.|
| description | string                                                       | No  | Yes  | Other information about the dialog box.                                          |

## DialogButtonInfo

Defines the dialog box button information.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name      | Type                                                        | Read-Only| Optional| Description        |
| ---------- | ------------------------------------------------------------ | ---- | ---- | ------------ |
| buttonId   | string                                                       | No  | No  | Button ID.  |
| buttonText | string                                                       | No  | No  | Button text.|
| buttonType | [ButtonType](arkts-apis-avMusicTemplate-e.md#buttontype) | No  | No  | Button type.|

## MemberPurchaseInfo

Defines the membership purchase information.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name              | Type                                                        | Read-Only| Optional| Description                       |
| ------------------ | ------------------------------------------------------------ | ---- | ---- |---------------------------|
| id                 | string                                                       | No  | No  | Unique ID of the membership purchase information.             |
| diagramUrl         | string                                                       | No  | No  | URL of the membership purchase diagram. (The diagram must use the 21:9 aspect ratio.)|
| diagramData        | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | No  | Yes  | Membership purchase diagram.                  |
| diagramContent     | string                                                       | No  | No  | Content of the membership purchase diagram.               |
| memberPurchaseType | [MemberPurchaseType](arkts-apis-avMusicTemplate-e.md#memberpurchasetype) | No  | No  | Type of the membership purchase.                  |

## CustomElement

Defines the custom element on the home page. It is inherited from [OperResult](#operresult).

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name              | Type                        | Read-Only| Optional| Description        |
| ------------------ | -------------------------- | ---- | ---- | ------------ |
| userInfo           | [UserInfo](#userinfo)      | No  | Yes  | User information.  |
| tabs               | [MediaTab](#mediatab)[]    | No  | Yes  | Tab information.|
| customCompilations | [Compilation](#compilation)[] | No  | Yes  | Array of compilations.  |
| settings           | [SettingItem](#settingitem)[] | No  | Yes  | Array of setting items.|

## UserInfo

Defines the user information.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name         | Type   | Read-Only| Optional| Description                               |
| ------------- | ------- | ---- | ---- |-----------------------------------|
| userInfoId    | string  | No  | No  | Unique ID of the user.                         |
| nickName      | string  | No  | No  | User nickname.                            |
| profilePicUrl | string  | No  | No  | URL of the user's profile image.                      |
| tips          | string  | No  | No  | Other description about the user.                       |
| isLogin       | boolean | No  | No  | Whether the user has logged in. **true**: yes; **false**: no. No default value.|
| isVip         | boolean | No  | No  | Whether the user is a VIP. **true**: yes; **false**: no. No default value. |

## SearchPlayInfo

Defines the search playback information.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name     | Type                                         | Read-Only| Optional| Description            |
| --------- | ------------------------------------------- | ---- | ---- | ---------------- |
| musicInfo | [SearchPlayMusicInfo](#searchplaymusicinfo) | No  | Yes  | Audio information for search and playback.|
| videoInfo | [SearchPlayVideoInfo](#searchplayvideoinfo) | No  | Yes  | Video information for search and playback.|

## SearchPlayMusicInfo

Defines the audio information for search and playback.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name         | Type                                         | Read-Only| Optional| Description                                               |
| ------------- | --------------------------------------------- | ---- | ---- | --------------------------------------------------- |
| items         | [SearchPlayMusicItem](#searchplaymusicitem)[] | No  | No  | Audio list.                                         |
| displayName   | string                                        | No  | Yes  | Display name of the audio.                                   |
| description   | string                                        | No  | Yes  | Description of the audio.                                     |
| playMusicOnly | boolean                                       | No  | Yes  | Whether to play only audio. **true**: yes; **false**: no. No default value.|
| playMode      | string                                        | No  | Yes  | Playback mode of the audio.                                   |

## SearchPlayMusicItem

Defines the audio project for search and playback.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name      | Type  | Read-Only| Optional| Description            |
| ---------- | ------ | ---- | ---- | ---------------- |
| entityId   | string | No  | No  | Unique ID of the audio.|
| entityName | string | No  | Yes  | Name of the audio.    |

## SearchPlayVideoInfo

Defines the video information for search and playback.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name         | Type  | Read-Only| Optional| Description            |
| ------------- | ------ | ---- | ---- | ---------------- |
| entityId      | string | No  | No  | Unique ID of the video.|
| episodeId     | string | No  | Yes  | Episode ID of the video.  |
| episodeNumber | number   | No  | Yes  | Number of video episodes.    |
| extras        | string | No  | Yes  | Additional information about the video.|
