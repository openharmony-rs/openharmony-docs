# AudioStreamDeviceChangeReason

Enumerates the reasons for audio stream device changes.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Device

## REASON_UNKNOWN

```TypeScript
REASON_UNKNOWN = 0
```

Unknown reason.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Device

## REASON_NEW_DEVICE_AVAILABLE

```TypeScript
REASON_NEW_DEVICE_AVAILABLE = 1
```

A new device is available.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Device

## REASON_OLD_DEVICE_UNAVAILABLE

```TypeScript
REASON_OLD_DEVICE_UNAVAILABLE = 2
```

The old device is unavailable. When this reason is reported, consider pausing audio playback.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Device

## REASON_OVERRODE

```TypeScript
REASON_OVERRODE = 3
```

Forcibly selected.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Device

## REASON_SESSION_ACTIVATED

```TypeScript
REASON_SESSION_ACTIVATED = 4
```

The audio session has been activated.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Device

## REASON_STREAM_PRIORITY_CHANGED

```TypeScript
REASON_STREAM_PRIORITY_CHANGED = 5
```

An audio stream with higher priority appears.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Device
