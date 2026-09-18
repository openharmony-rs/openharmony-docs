# @ohos.multimedia.systemSoundManager(System Sound Management)

This module provides basic capabilities for managing system sound effects, including defining system sound effect types and obtaining system sound effect players.

**Since:** 23

**System capability:** SystemCapability.Multimedia.SystemSound.Core

## Modules to Import

```TypeScript
import { systemSoundManager } from '@kit.AudioKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createSystemSoundPlayer](arkts-audio-systemsoundmanager-createsystemsoundplayer-f.md) | Creates a SystemSoundPlayer instance. This function uses a promise to return the result. This player can be used to play some system sounds for media or camera actions. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [createCustomizedToneAttrs](arkts-audio-systemsoundmanager-createcustomizedtoneattrs-f-sys.md) | Create customized tone attributes. |
| [getSystemSoundManager](arkts-audio-systemsoundmanager-getsystemsoundmanager-f-sys.md) | Gets system sound manager for all type sound. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [SystemSoundManager](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md) | System sound manager object. |
| [ToneAttrs](arkts-audio-systemsoundmanager-toneattrs-i-sys.md) | Tone attributes. |
| [ToneHapticsAttrs](arkts-audio-systemsoundmanager-tonehapticsattrs-i-sys.md) | Haptics attributes in tone scenario. |
| [ToneHapticsSettings](arkts-audio-systemsoundmanager-tonehapticssettings-i-sys.md) | Haptics settings in tone scenario. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [SystemSoundType](arkts-audio-systemsoundmanager-systemsoundtype-e.md) | Enumerates the system sound effect types. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [MediaType](arkts-audio-systemsoundmanager-mediatype-e-sys.md) | Enum for media type. |
| [RingtoneType](arkts-audio-systemsoundmanager-ringtonetype-e-sys.md) | Enum for ringtone type. |
| [SystemSoundError](arkts-audio-systemsoundmanager-systemsounderror-e-sys.md) | Error enum for system sound. |
| [SystemToneType](arkts-audio-systemsoundmanager-systemtonetype-e-sys.md) | Enum for system tone type. |
| [ToneCustomizedType](arkts-audio-systemsoundmanager-tonecustomizedtype-e-sys.md) | Enum for tone customized type. |
| [ToneHapticsFeature](arkts-audio-systemsoundmanager-tonehapticsfeature-e-sys.md) | Definition of haptics feature in tone scenario. |
| [ToneHapticsMode](arkts-audio-systemsoundmanager-tonehapticsmode-e-sys.md) | Enum for haptics mode in tone scenario. |
| [ToneHapticsType](arkts-audio-systemsoundmanager-tonehapticstype-e-sys.md) | Enum for haptics in tone scenario. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [SystemSoundPlayer](arkts-audio-systemsoundmanager-systemsoundplayer-t.md) | Represents the system sound effect player object. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [RingtoneOptions](arkts-audio-systemsoundmanager-ringtoneoptions-t-sys.md) | Interface for ringtone options. |
| [RingtonePlayer](arkts-audio-systemsoundmanager-ringtoneplayer-t-sys.md) | Ringtone player object. |
| [SystemToneOptions](arkts-audio-systemsoundmanager-systemtoneoptions-t-sys.md) | System tone options. |
| [SystemTonePlayer](arkts-audio-systemsoundmanager-systemtoneplayer-t-sys.md) | SystemTone player object. |
| [ToneAttrsArray](arkts-audio-systemsoundmanager-toneattrsarray-t-sys.md) | Array of tone attributes. |
| [ToneHapticsAttrsArray](arkts-audio-systemsoundmanager-tonehapticsattrsarray-t-sys.md) | Type definition of tone haptics array. |
<!--DelEnd-->

<!--Del-->
### Constants(System API)

| Name | Description |
| --- | --- |
| [TONE_CATEGORY_ALARM](arkts-audio-systemsoundmanager-con-sys.md#tone_category_alarm) | Define the alarm tone category. |
| [TONE_CATEGORY_CONTACTS](arkts-audio-systemsoundmanager-con-sys.md#tone_category_contacts) | Define the contact tone category. |
| [TONE_CATEGORY_NOTIFICATION](arkts-audio-systemsoundmanager-con-sys.md#tone_category_notification) | Define the notification tone category. |
| [TONE_CATEGORY_NOTIFICATION_APP](arkts-audio-systemsoundmanager-con-sys.md#tone_category_notification_app) | Define the app notification tone category. |
| [TONE_CATEGORY_RINGTONE](arkts-audio-systemsoundmanager-con-sys.md#tone_category_ringtone) | Define the ringtone category. |
| [TONE_CATEGORY_TEXT_MESSAGE](arkts-audio-systemsoundmanager-con-sys.md#tone_category_text_message) | Define the text message tone category. |
<!--DelEnd-->
