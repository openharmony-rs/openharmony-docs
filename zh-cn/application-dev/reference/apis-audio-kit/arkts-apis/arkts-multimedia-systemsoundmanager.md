# @ohos.multimedia.systemSoundManager

系统声音管理提供管理系统声音的基础能力，包括对系统音效类型的定义、获取系统音效播放器等。

**起始版本：** 23

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare namespace systemSoundManager--><!--Device-unnamed-declare namespace systemSoundManager-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createCustomizedToneAttrs](arkts-audio-systemsoundmanager-createcustomizedtoneattrs-f.md#createcustomizedtoneattrs) | 创建自定义铃声属性。 |
| [createSystemSoundPlayer](arkts-audio-systemsoundmanager-createsystemsoundplayer-f.md#createsystemsoundplayer) | 创建系统音效播放器对象。使用Promise异步回调。 |
| [getSystemSoundManager](arkts-audio-systemsoundmanager-getsystemsoundmanager-f.md#getsystemsoundmanager) | 获取系统声音管理器。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [SystemSoundManager](arkts-audio-systemsoundmanager-systemsoundmanager-i.md) | 管理系统声音。在调用SystemSoundManager的接口前，需要先 通过[getSystemSoundManager]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_创建实例。 |
| [ToneAttrs](arkts-audio-systemsoundmanager-toneattrs-i.md) | 管理铃声属性。在调用ToneAttrs\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_12+\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_的接口前，需要先通过 [createCustomizedToneAttrs]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_或 [getDefaultRingtoneAttrs]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_、 [getRingtoneAttrList]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_等方法获取实例。 |
| [ToneHapticsAttrs](arkts-audio-systemsoundmanager-tonehapticsattrs-i.md) | 系统铃音的振动属性。在调用ToneHapticsAttrs\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_14+\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_的接口前，需要先通过 [getToneHapticsList]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_或 [getHapticsAttrsSyncedWithTone]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_方法获取实例。 |
| [ToneHapticsSettings](arkts-audio-systemsoundmanager-tonehapticssettings-i.md) | 系统铃音的振动设置。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [MediaType](arkts-audio-systemsoundmanager-mediatype-e.md) | 枚举，媒体类型。 |
| [RingtoneType](arkts-audio-systemsoundmanager-ringtonetype-e.md) | 枚举，铃声类型。 |
| [SystemSoundError](arkts-audio-systemsoundmanager-systemsounderror-e.md) | 枚举，系统声音错误类型。 |
| [SystemSoundType](arkts-audio-systemsoundmanager-systemsoundtype-e.md) | 枚举，表示系统音效类型。 |
| [SystemToneType](arkts-audio-systemsoundmanager-systemtonetype-e.md) | 枚举，系统铃声类型。 |
| [ToneCustomizedType](arkts-audio-systemsoundmanager-tonecustomizedtype-e.md) | 枚举，铃声自定义类型。 |
| [ToneHapticsFeature](arkts-audio-systemsoundmanager-tonehapticsfeature-e.md) | 枚举，系统振动风格定义。 \| 名称 \| 值 \| 说明 \| \| ----------------------------- \| -- \| -------------------- \| \| STANDARD\| 0 \| 标准振动风格。 \| \| GENTLE \| 1 \| 轻柔振动风格。 \| |
| [ToneHapticsMode](arkts-audio-systemsoundmanager-tonehapticsmode-e.md) | 枚举，系统铃音场景的振动模式。 \| 名称 \| 值 \| 说明 \| \| ----------------------------- \| -- \| -------------------- \| \| NONE \| 0 \| 无振动模式。 \| \| SYNC \| 1 \| 与铃音同步模式。 \| \| NON\_\_\_ESCAPED\_UNDERSCORE\_\_\_SYNC \| 2 \| 非同步模式。 \| |
| [ToneHapticsType](arkts-audio-systemsoundmanager-tonehapticstype-e.md) | 枚举，系统铃音的振动类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [RingtoneOptions](arkts-audio-systemsoundmanager-ringtoneoptions-t.md) | 系统铃音播放器配置项。 |
| [RingtonePlayer](arkts-audio-systemsoundmanager-ringtoneplayer-t.md) | 系统铃音播放器对象。 |
| [SystemSoundPlayer](arkts-audio-systemsoundmanager-systemsoundplayer-t.md) | 系统音效播放器对象。 |
| [SystemToneOptions](arkts-audio-systemsoundmanager-systemtoneoptions-t.md) | 系统提示音播放器配置项。 |
| [SystemTonePlayer](arkts-audio-systemsoundmanager-systemtoneplayer-t.md) | 系统提示音播放器对象。 |
| [ToneAttrsArray](arkts-audio-systemsoundmanager-toneattrsarray-t.md) | 铃音属性数组。 |
| [ToneHapticsAttrsArray](arkts-audio-systemsoundmanager-tonehapticsattrsarray-t.md) | 系统铃音的振动属性数组。 |

<!--Del-->
### 常量（系统接口）

| 名称 | 说明 |
| --- | --- |
| [TONE_CATEGORY_ALARM](arkts-audio-systemsoundmanager-con-sys.md#tone_category_alarm) | 闹钟铃声类别。 |
| [TONE_CATEGORY_CONTACTS](arkts-audio-systemsoundmanager-con-sys.md#tone_category_contacts) | 联系人铃声类别。 |
| [TONE_CATEGORY_NOTIFICATION](arkts-audio-systemsoundmanager-con-sys.md#tone_category_notification) | 通知铃声类别。 |
| [TONE_CATEGORY_NOTIFICATION_APP](arkts-audio-systemsoundmanager-con-sys.md#tone_category_notification_app) | 应用级通知铃声类别。 |
| [TONE_CATEGORY_RINGTONE](arkts-audio-systemsoundmanager-con-sys.md#tone_category_ringtone) | 铃声类别。 |
| [TONE_CATEGORY_TEXT_MESSAGE](arkts-audio-systemsoundmanager-con-sys.md#tone_category_text_message) | 短信铃声类别。 |
<!--DelEnd-->

