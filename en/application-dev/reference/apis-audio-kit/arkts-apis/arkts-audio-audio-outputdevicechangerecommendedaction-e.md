# OutputDeviceChangeRecommendedAction

Enumerates the recommended actions to take after an output device changes.

Common scenario example: switching between a headset and a loudspeaker device. Upon switching from the loudspeaker device to the headset upon wearing, the system suggests continuing playback and prompts that the application does not need to pause. Upon transitioning from the headset to the loudspeaker device upon removal, the system suggests suspending playback.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Core

## DEVICE_CHANGE_RECOMMEND_TO_CONTINUE

```TypeScript
DEVICE_CHANGE_RECOMMEND_TO_CONTINUE = 0
```

Suggests continuing playback. (This event serves as a playback maintenance indication, informing the application that audio playback does not need to stop during this device change. However, it must not be used as a criterion for triggering audio playback.)

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Core

## DEVICE_CHANGE_RECOMMEND_TO_STOP

```TypeScript
DEVICE_CHANGE_RECOMMEND_TO_STOP = 1
```

Suggests stopping playback.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Core
