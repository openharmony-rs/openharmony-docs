# Enums
> **说明：**
>
> 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## AVMusicTemplateType<sup>23+</sup>

音频模板类型的枚举。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称    | 值         | 说明     |
| ------- | ---------- | -------- |
| DEFAULT | 'smartCar' | 智选车。 |

## EntityType<sup>23+</sup>

媒体资源类型的枚举。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称          | 值   | 说明         |
| ------------- | ---- | ------------ |
| UNKNOWN       | 0    | 未知的类型。 |
| SINGLE        | 1    | 单曲类型。   |
| SINGER        | 2    | 歌手类型。   |
| ALBUM         | 3    | 专辑类型     |
| RANKING       | 4    | 排行榜类型。 |
| BANNER        | 5    | 海报类型。   |
| RADIO_STATION | 6    | 电台类型。   |

## PlaybackState<sup>23+</sup>

媒体资源的播放状态的枚举。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称                     | 值   | 说明       |
| ------------------------ | ---- | ---------- |
| PLAYBACK_STATE_PREPARE   | 0    | 准备状态。 |
| PLAYBACK_STATE_PLAY      | 1    | 播放中。   |
| PLAYBACK_STATE_PAUSE     | 2    | 暂停状态。 |
| PLAYBACK_STATE_STOP      | 3    | 停止状态   |
| PLAYBACK_STATE_COMPLETED | 4    | 播放完成。 |
| PLAYBACK_STATE_ERROR     | 5    | 错误状态。 |
| PLAYBACK_STATE_BUFFERING | 6    | 缓冲状态。 |

## Sort<sup>23+</sup>

排序类型的枚举。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称          | 值   | 说明   |
| ------------- | ---- | ------ |
| NONE          | 0    | 无。   |
| ORDER         | 1    | 正序。 |
| REVERSE_ORDER | 2    | 倒序。 |

## SettingType<sup>23+</sup>

设置类型的枚举。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称   | 值   | 说明                                             |
| ------ | ---- | ------------------------------------------------ |
| SWITCH | 0    | 开关，这种设置类型用于控制功能的开启或关闭状态。 |
| LIST   | 1    | 列表，这种设置类型用于从多个选项中选择一个选项。 |
| JUMP   | 2    | 跳转，这种设置用于跳转到另一个界面。             |

## DialogType<sup>23+</sup>

弹框类型的枚举。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称     | 值   | 说明       |
| -------- | ---- | ---------- |
| NORMAL   | 0    | 正常弹框。 |
| INTERNET | 1    | 联网弹框。 |
| FLOW     | 2    | 流程弹框。 |
| PAID     | 3    | 付费弹框。 |
| VIP      | 4    | VIP弹框。  |
| LOGIN    | 5    | 登录弹框。 |
| ERROR    | 6    | 错误弹框。 |
| UNKNOWN  | 7    | 未知弹框。 |

## ButtonType<sup>23+</sup>

按钮类型的枚举。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称      | 值   | 说明       |
| --------- | ---- | ---------- |
| NORMAL    | 0    | 正常按钮。 |
| EMPHASIZE | 1    | 强调按钮。 |

## MemberPurchaseType<sup>23+</sup>

会员购买类型的枚举。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称   | 值       | 说明   |
| ------ | -------- | ------ |
| NORMAL | 'normal' | 常规。 |
| BANNER | 'banner' | 横幅。 |

## SearchPlayInfoType<sup>23+</sup>

搜播信息类型的枚举。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称       | 值          | 说明       |
| ---------- | ----------- | ---------- |
| PLAY_MUSIC | 'playMusic' | 播放音乐。 |
| PLAY_VIDEO | 'playVideo' | 播放视频。 |

## DownloadStatus<sup>23+</sup>

下载状态类型的枚举。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称             | 值   | 说明       |
| ---------------- | ---- | ---------- |
| DOWNLOAD_SUCCESS | 0    | 下载成功。 |
| DOWNLOADING      | 1    | 下载中。   |
| DOWNLOAD_FAIL    | 2    | 下载失败。 |