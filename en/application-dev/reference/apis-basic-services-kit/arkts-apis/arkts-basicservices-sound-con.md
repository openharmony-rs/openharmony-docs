# Constants

## AFFECTED_MODE_RINGER_STREAMS

```TypeScript
const AFFECTED_MODE_RINGER_STREAMS: string
```

Specifies which audio streams are affected by changes on the ringing mode and Do Not Disturb (DND) mode.

<p>If you want a specific audio stream to be affected by changes of the ringing mode and DDN mode, set the corresponding bit to `1`.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## AFFECTED_MUTE_STREAMS

```TypeScript
const AFFECTED_MUTE_STREAMS: string
```

Specifies which audio streams are affected by the mute mode.

<p>If you want a specific audio stream to remain muted in mute mode, set the corresponding bit to `1`.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## DEFAULT_ALARM_ALERT

```TypeScript
const DEFAULT_ALARM_ALERT: string
```

Indicates the storage area of the system default alarm.

<p>You can obtain the URI of the system default alarm.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## DEFAULT_NOTIFICATION_SOUND

```TypeScript
const DEFAULT_NOTIFICATION_SOUND: string
```

Indicates the storage area of the system default notification tone.

<p>You can obtain the URI of the system default notification tone.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## DEFAULT_RINGTONE

```TypeScript
const DEFAULT_RINGTONE: string
```

Indicates the storage area of the system default ringtone.

<p>You can obtain the URI of the system default ringtone.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## DTMF_TONE_TYPE_WHILE_DIALING

```TypeScript
const DTMF_TONE_TYPE_WHILE_DIALING: string
```

Indicates the type of the dual-tone multifrequency (DTMF) tone played when dialing.

<p>The value `0` indicates the normal short sound effect, and `1` indicates the long sound effect.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## DTMF_TONE_WHILE_DIALING

```TypeScript
const DTMF_TONE_WHILE_DIALING: string
```

Specifies whether the DTMF tone is played when dialing.

<p>If the value is `1`, the DTMF tone is played. If the value is `0`, the DTMF tone is not played.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## HAPTIC_FEEDBACK_STATUS

```TypeScript
const HAPTIC_FEEDBACK_STATUS: string
```

Indicates whether the device enables haptic feedback.

<p>The value is of the boolean type.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## SOUND_EFFECTS_STATUS

```TypeScript
const SOUND_EFFECTS_STATUS: string
```

Specifies whether the sound effects are enabled.

<p>If the value is `0`, the sound effects are disabled. If the value is `1`, the sound effects are enabled.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## VIBRATE_STATUS

```TypeScript
const VIBRATE_STATUS: string
```

Specifies whether the device vibrates for an event. This parameter is used inside the system.

<p>If the value is `1`, the device vibrates for an event. If the value is `0`, the device does not vibrate for an event.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## VIBRATE_WHILE_RINGING

```TypeScript
const VIBRATE_WHILE_RINGING: string
```

Indicates whether the device vibrates when it is ringing for an incoming call.

<p>This constant will be used by Phone and Settings applications. The value is of the boolean type. This constant affects only the scenario where the device rings for an incoming call. It does not affect any other application or scenario.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core
