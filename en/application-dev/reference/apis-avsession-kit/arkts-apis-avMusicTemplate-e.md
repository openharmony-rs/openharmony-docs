# Enums
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

## AVMusicTemplateType

Enumerates the audio template types.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name   | Value        | Description                                                        |
| ------- | ---------- | ------------------------------------------------------------ |
| DEFAULT | 'smartCar' | Default value of the audio template type.<br>It identifies the service type of the current audio template. You can change the value based on your service requirements when creating a template.|

## EntityType

Enumerates the media resource types.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name         | Value  | Description                |
| ------------- | ---- | -------------------- |
| UNKNOWN       | 0    | Unknown type.|
| SINGLE        | 1    | Single type.          |
| SINGER        | 2    | Singer type.          |
| ALBUM         | 3    | Album Type          |
| RANKING       | 4    | Ranking type.        |
| BANNER        | 5    | Poster type.          |
| RADIO_STATION | 6    | Radio type.          |

## PlaybackState

Enumerates the playback states of media resources.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name                    | Value  | Description                                                        |
| ------------------------ | ---- | ------------------------------------------------------------ |
| PLAYBACK_STATE_PREPARE   | 0    | Preparing.<br>The media file is being loaded or buffered, and is not ready for playback.|
| PLAYBACK_STATE_PLAY      | 1    | Playing.                                              |
| PLAYBACK_STATE_PAUSE     | 2    | Paused.                                                  |
| PLAYBACK_STATE_STOP      | 3    | Stopped.                                                  |
| PLAYBACK_STATE_COMPLETED | 4    | Completed.                                              |
| PLAYBACK_STATE_ERROR     | 5    | Playback error.                                              |
| PLAYBACK_STATE_BUFFERING | 6    | Buffering.                                                  |

## Sort

Enumerates the sorting types of the queried list data.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name         | Value  | Description       |
| ------------- | ---- |-----------|
| NONE          | 0    | Default value, which is ascending order.|
| ORDER         | 1    | Ascending order      |
| REVERSE_ORDER | 2    | Reverse order.      |

## SettingType

Enumerates the setting types.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name  | Value  | Description                                            |
| ------ | ---- | ------------------------------------------------ |
| SWITCH | 0    | Switch setting, which is used to enable or disable a feature.|
| LIST   | 1    | List setting, which is used to select an option from multiple options.|
| JUMP   | 2    | Jump setting, which is used to jump to another screen.            |

## DialogType

Enumerates the dialog box types.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name    | Value  | Description        |
| -------- | ---- | ------------ |
| NORMAL   | 0    | Common dialog box.|
| INTERNET | 1    | Internet dialog box.|
| FLOW     | 2    | Flow dialog box.|
| PAID     | 3    | Paid dialog box.|
| VIP      | 4    | VIP dialog box. |
| LOGIN    | 5    | Login dialog box.|
| ERROR    | 6    | Error dialog box.|
| UNKNOWN  | 7    | Unknown dialog box.|

## ButtonType

Enumerates the button types.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name     | Value  | Description      |
| --------- | ---- | ---------- |
| NORMAL    | 0    | Normal button.|
| EMPHASIZE | 1    | Emphasized button.|

## MemberPurchaseType

Enumerates the membership purchase types.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name  | Value      | Description     |
| ------ | -------- |---------|
| NORMAL | 'normal' | Normal purchase.  |
| BANNER | 'banner' | Membership promotion poster.|

## SearchPlayInfoType

Enumerates the search playback information types.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name      | Value         | Description      |
| ---------- | ----------- | ---------- |
| PLAY_MUSIC | 'playMusic' | Plays music.|
| PLAY_VIDEO | 'playVideo' | Plays a video.|

## DownloadStatus

Enumerates the download status types.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name            | Value  | Description      |
| ---------------- | ---- | ---------- |
| DOWNLOAD_SUCCESS | 0    | Download successful.|
| DOWNLOADING      | 1    | Downloading.  |
| DOWNLOAD_FAIL    | 2    | Download failed.|

## AVMusicTemplateErrorCode

Enumerates the error code types.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name            | Value  | Description      |
| ---------------- | ---- | ---------- |
| ERR_CODE_CREATE_AV_MUSIC_TEMPLATE_FAILED | 35000001 | Failed to create the audio template.|
| ERR_CODE_CREATE_AV_MUSIC_TEMPLATE_CONTROLLER_FAILED | 35000002 | Failed to create the audio template controller.|
| ERR_CODE_TEMPLATE_LISTENER_NO_EXIT | 35000003 | The template listener is not registered.|
| ERR_CODE_CONTROLLER_CALLBACK_NO_EXIT | 35000004 | The template controller callback is not registered.|
| ERR_CODE_AV_MUSIC_TEMPLATE_NOT_EXIST | 35000005 | The audio template does not exist.|
| ERR_CODE_CONTROLLER_NOT_EXIST | 35000006 | The template controller does not exist.|
| ERR_CODE_CONTROLLER_IS_EXIST | 35000007 | The template controller already exists.|
| ERR_CODE_SERVICE_NOT_EXIST | 35000008 | The audio template management service does not exist.|
| ERR_CODE_SERVICE_EXCEPTION | 35000009 | The audio template management service is abnormal.|
| ERR_CODE_EXCEED_MAX_DATA_SIZE | 35000010 | The data exceeds the maximum transmission capacity.|
| ERR_CODE_WRITE_RESULT_EXCEPTION | 35000011 | Failed to write data. The data is unavailable.|
| ERR_CODE_AV_MUSIC_TEMPLATE_ERROR | 35000012 | The audio template is incorrect.|
