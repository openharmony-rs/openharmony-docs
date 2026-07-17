# @ohos.multimedia.systemSoundManager

系统声音管理提供管理系统声音的基础能力，包括对系统音效类型的定义、获取系统音效播放器等。

**起始版本：** 23

<!--Device-unnamed-declare namespace systemSoundManager--><!--Device-unnamed-declare namespace systemSoundManager-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { systemSoundManager } from '@kit.AudioKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createCustomizedToneAttrs](arkts-audio-systemsoundmanager-createcustomizedtoneattrs-f-sys.md#createcustomizedtoneattrs-1) | 创建自定义铃声属性。 |
| [createSystemSoundPlayer](arkts-audio-systemsoundmanager-createsystemsoundplayer-f.md#createsystemsoundplayer-1) | 创建系统音效播放器对象。使用Promise异步回调。 |
| [getSystemSoundManager](arkts-audio-systemsoundmanager-getsystemsoundmanager-f-sys.md#getsystemsoundmanager-1) | 获取系统声音管理器。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SystemSoundManager](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md) | 管理系统声音。在调用SystemSoundManager的接口前，需要先通过[getSystemSoundManager](arkts-audio-systemsoundmanager-getsystemsoundmanager-f-sys.md#getsystemsoundmanager-1)创建实例。 |
| [ToneAttrs](arkts-audio-systemsoundmanager-toneattrs-i-sys.md) | 管理铃声属性。在调用ToneAttrs&lt;sup&gt;12+&lt;/sup&gt;的接口前，需要先通过[createCustomizedToneAttrs](arkts-audio-systemsoundmanager-createcustomizedtoneattrs-f-sys.md#createcustomizedtoneattrs-1)或[getDefaultRingtoneAttrs](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#getdefaultringtoneattrs-1)、[getRingtoneAttrList](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#getringtoneattrlist-1)等方法获取实例。 |
| [ToneHapticsAttrs](arkts-audio-systemsoundmanager-tonehapticsattrs-i-sys.md) | 系统铃音的振动属性。在调用ToneHapticsAttrs&lt;sup&gt;14+&lt;/sup&gt;的接口前，需要先通过[getToneHapticsList](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#gettonehapticslist-1)或[getHapticsAttrsSyncedWithTone](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#gethapticsattrssyncedwithtone-1)方法获取实例。 |
| [ToneHapticsSettings](arkts-audio-systemsoundmanager-tonehapticssettings-i-sys.md) | 系统铃音的振动设置。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [MediaType](arkts-audio-systemsoundmanager-mediatype-e-sys.md) | 枚举，媒体类型。 |
| [RingtoneType](arkts-audio-systemsoundmanager-ringtonetype-e-sys.md) | 枚举，铃声类型。 |
| [SystemSoundError](arkts-audio-systemsoundmanager-systemsounderror-e-sys.md) | 枚举，系统声音错误类型。 |
| [SystemSoundType](arkts-audio-systemsoundmanager-systemsoundtype-e.md) | 枚举，表示系统音效类型。 |
| [SystemToneType](arkts-audio-systemsoundmanager-systemtonetype-e-sys.md) | 枚举，系统铃声类型。 |
| [ToneCustomizedType](arkts-audio-systemsoundmanager-tonecustomizedtype-e-sys.md) | 枚举，铃声自定义类型。 |
| [ToneHapticsFeature](arkts-audio-systemsoundmanager-tonehapticsfeature-e-sys.md) | 枚举，系统振动风格定义。\| 名称 \| 值 \| 说明 \| \| ----------------------------- \| -- \| -------------------- \| \| STANDARD\| 0 \| 标准振动风格。 \| \| GENTLE \| 1 \| 轻柔振动风格。 \| |
| [ToneHapticsMode](arkts-audio-systemsoundmanager-tonehapticsmode-e-sys.md) | 枚举，系统铃音场景的振动模式。\| 名称 \| 值 \| 说明 \| \| ----------------------------- \| -- \| -------------------- \| \| NONE \| 0 \| 无振动模式。 \| \| SYNC \| 1 \| 与铃音同步模式。 \| \| NON_SYNC \| 2 \| 非同步模式。 \| |
| [ToneHapticsType](arkts-audio-systemsoundmanager-tonehapticstype-e-sys.md) | 枚举，系统铃音的振动类型。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [RingtoneOptions](arkts-audio-systemsoundmanager-ringtoneoptions-t-sys.md) | 系统铃音播放器配置项。 |
| [RingtonePlayer](arkts-audio-systemsoundmanager-ringtoneplayer-t-sys.md) | 系统铃音播放器对象。 |
| [SystemSoundPlayer](arkts-audio-systemsoundmanager-systemsoundplayer-t.md) | 系统音效播放器对象。 |
| [SystemToneOptions](arkts-audio-systemsoundmanager-systemtoneoptions-t-sys.md) | 系统提示音播放器配置项。 |
| [SystemTonePlayer](arkts-audio-systemsoundmanager-systemtoneplayer-t-sys.md) | 系统提示音播放器对象。 |
| [ToneAttrsArray](arkts-audio-systemsoundmanager-toneattrsarray-t-sys.md) | 铃音属性数组。 |
| [ToneHapticsAttrsArray](arkts-audio-systemsoundmanager-tonehapticsattrsarray-t-sys.md) | 系统铃音的振动属性数组。 |
<!--DelEnd-->

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

