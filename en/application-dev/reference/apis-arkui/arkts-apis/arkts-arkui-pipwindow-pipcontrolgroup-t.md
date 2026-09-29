# PiPControlGroup

```TypeScript
type PiPControlGroup = VideoPlayControlGroup | VideoCallControlGroup | VideoMeetingControlGroup | VideoLiveControlGroup
```

Describes the optional component groups of the PiP controller. An application can configure whether to display these optional components. This API must match [PiPTemplateType](arkts-arkui-pipwindow-piptemplatetype-e.md) when being used. Otherwise, the [create](arkts-arkui-pipwindow-create-f.md) API returns error code 401.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PiPWindow-type PiPControlGroup = VideoPlayControlGroup | VideoCallControlGroup | VideoMeetingControlGroup    | VideoLiveControlGroup--><!--Device-PiPWindow-type PiPControlGroup = VideoPlayControlGroup | VideoCallControlGroup | VideoMeetingControlGroup    | VideoLiveControlGroup-End-->

**System capability:** SystemCapability.Window.SessionManager

| Type | Description |
| --- | --- |
| [VideoPlayControlGroup](arkts-arkui-pipwindow-videoplaycontrolgroup-e.md) | Video playback component group. |
| [VideoCallControlGroup](arkts-arkui-pipwindow-videocallcontrolgroup-e.md) | Video call component group. |
| [VideoMeetingControlGroup](arkts-arkui-pipwindow-videomeetingcontrolgroup-e.md) | Video meeting component group. |
| [VideoLiveControlGroup](arkts-arkui-pipwindow-videolivecontrolgroup-e.md) | Live video component group. |
