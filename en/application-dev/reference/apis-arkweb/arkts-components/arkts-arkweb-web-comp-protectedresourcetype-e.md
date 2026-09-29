# ProtectedResourceType

```TypeScript
declare enum ProtectedResourceType
```

Defines the types of protected resources that the Web component needs to access. It is used to control access permissions for sensitive resources such as MIDI, camera, microphone, and sensors, helping developers provide rich web functionality while protecting user privacy.

**Since:** 9

<!--Device-unnamed-declare enum ProtectedResourceType--><!--Device-unnamed-declare enum ProtectedResourceType-End-->

**System capability:** SystemCapability.Web.Webview.Core

## MidiSysex

```TypeScript
MidiSysex = "TYPE_MIDI_SYSEX"
```

MIDI SYSEX resource.

Currently, only permission events can be reported. MIDI devices are not yet supported.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ProtectedResourceType-MidiSysex = "TYPE_MIDI_SYSEX"--><!--Device-ProtectedResourceType-MidiSysex = "TYPE_MIDI_SYSEX"-End-->

**System capability:** SystemCapability.Web.Webview.Core

## VIDEO_CAPTURE

```TypeScript
VIDEO_CAPTURE = "TYPE_VIDEO_CAPTURE"
```

Video capture resource, such as a camera.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ProtectedResourceType-VIDEO_CAPTURE = "TYPE_VIDEO_CAPTURE"--><!--Device-ProtectedResourceType-VIDEO_CAPTURE = "TYPE_VIDEO_CAPTURE"-End-->

**System capability:** SystemCapability.Web.Webview.Core

## AUDIO_CAPTURE

```TypeScript
AUDIO_CAPTURE = "TYPE_AUDIO_CAPTURE"
```

Audio capture resource, such as a microphone.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ProtectedResourceType-AUDIO_CAPTURE = "TYPE_AUDIO_CAPTURE"--><!--Device-ProtectedResourceType-AUDIO_CAPTURE = "TYPE_AUDIO_CAPTURE"-End-->

**System capability:** SystemCapability.Web.Webview.Core

## SENSOR

```TypeScript
SENSOR = 'TYPE_SENSOR'
```

Sensor resource, such as an acceleration sensor.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ProtectedResourceType-SENSOR = 'TYPE_SENSOR'--><!--Device-ProtectedResourceType-SENSOR = 'TYPE_SENSOR'-End-->

**System capability:** SystemCapability.Web.Webview.Core
