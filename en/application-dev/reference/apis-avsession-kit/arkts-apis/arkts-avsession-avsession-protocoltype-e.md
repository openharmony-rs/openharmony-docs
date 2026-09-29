# ProtocolType

```TypeScript
enum ProtocolType
```

Define different protocol capability

**Since:** 11

<!--Device-avSession-enum ProtocolType--><!--Device-avSession-enum ProtocolType-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## TYPE_LOCAL

```TypeScript
TYPE_LOCAL = 0
```

The default cast type "local", media can be routed on the same device, including internal speakers or audio jack on the device itself, A2DP devices.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ProtocolType-TYPE_LOCAL = 0--><!--Device-ProtocolType-TYPE_LOCAL = 0-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## TYPE_CAST_PLUS_STREAM

```TypeScript
TYPE_CAST_PLUS_STREAM = 2
```

The Cast+ Stream indicating the media is presenting on a different device the application need get an AVCastController to control remote playback.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ProtocolType-TYPE_CAST_PLUS_STREAM = 2--><!--Device-ProtocolType-TYPE_CAST_PLUS_STREAM = 2-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## TYPE_DLNA

```TypeScript
TYPE_DLNA = 4
```

The DLNA type indicates the device supports DLNA protocol, the application needs to get an AVCastController to control remote playback.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ProtocolType-TYPE_DLNA = 4--><!--Device-ProtocolType-TYPE_DLNA = 4-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## TYPE_CAST_PLUS_AUDIO

```TypeScript
TYPE_CAST_PLUS_AUDIO = 8
```

This type indicates the device supports audio casting with high definition to get a better sound quality.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-ProtocolType-TYPE_CAST_PLUS_AUDIO = 8--><!--Device-ProtocolType-TYPE_CAST_PLUS_AUDIO = 8-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVCast
