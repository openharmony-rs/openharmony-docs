# AudioPrivacyType

表示对应播放音频流是否支持被其他应用录制的枚举。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-audio-enum AudioPrivacyType--><!--Device-audio-enum AudioPrivacyType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## PRIVACY_TYPE_PUBLIC

```TypeScript
PRIVACY_TYPE_PUBLIC = 0
```

表示音频流可以被其他应用录制或屏幕投射，不包含隐私类型的流。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-AudioPrivacyType-PRIVACY_TYPE_PUBLIC = 0--><!--Device-AudioPrivacyType-PRIVACY_TYPE_PUBLIC = 0-End-->

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## PRIVACY_TYPE_PRIVATE

```TypeScript
PRIVACY_TYPE_PRIVATE = 1
```

表示音频流不可以被其他应用录制或屏幕投射。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-AudioPrivacyType-PRIVACY_TYPE_PRIVATE = 1--><!--Device-AudioPrivacyType-PRIVACY_TYPE_PRIVATE = 1-End-->

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## PRIVACY_TYPE_SHARED

```TypeScript
PRIVACY_TYPE_SHARED = 2
```

表示音频流可以被其他应用录制或屏幕投射，包含隐私类型的流。 例如，在PRIVACY\_TYPE\_PUBLIC策略下，[STREAM\_USAGE\_VOICE\_COMMUNICATION]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_类型音频流不会被其他应用录制或屏幕投射。 然而，在PRIVACY\_TYPE\_SHARED策略下，这些音频流将会允许被其他应用录制或屏幕投射。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为24。

<!--Device-AudioPrivacyType-PRIVACY_TYPE_SHARED = 2--><!--Device-AudioPrivacyType-PRIVACY_TYPE_SHARED = 2-End-->

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

