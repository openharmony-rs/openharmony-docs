# AudioSessionBehaviorFlags

Enumerates audio session behavior flags.

**Since:** 24

**System capability:** SystemCapability.Multimedia.Audio.Core

## VOIP_CAPTURE_MIX_WITH_OTHERS

```TypeScript
VOIP_CAPTURE_MIX_WITH_OTHERS = 0x20000000
```

Allows the VoIP capture stream of the current application to run concurrently with other existing VoIP capture streams. When a later VoIP capture stream arrives, it can interrupt the current stream.

This flag only takes effect when used in setIndependentAudioSessionStrategy. When using this flag, the permission ohos.permission.VOIP_CAPTURE_CONCURRENCY must be verified.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

**System API:** This is a system API.
