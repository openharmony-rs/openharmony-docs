# VideoPlayControlGroup

```TypeScript
enum VideoPlayControlGroup
```

Enumerates the video playback component groups. They are used only when [PiPTemplateType](arkts-arkui-pipwindow-piptemplatetype-e.md) is set to **VIDEO_PLAY**.

**Since:** 12

<!--Device-PiPWindow-enum VideoPlayControlGroup--><!--Device-PiPWindow-enum VideoPlayControlGroup-End-->

**System capability:** SystemCapability.Window.SessionManager

## VIDEO_PREVIOUS_NEXT

```TypeScript
VIDEO_PREVIOUS_NEXT = 101
```

Previous/Next component group for video playback.

This component group is mutually exclusive with the fast-forward/rewind component group. It cannot be added if the fast-forward/rewind component group is added.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-VideoPlayControlGroup-VIDEO_PREVIOUS_NEXT = 101--><!--Device-VideoPlayControlGroup-VIDEO_PREVIOUS_NEXT = 101-End-->

**System capability:** SystemCapability.Window.SessionManager

## FAST_FORWARD_BACKWARD

```TypeScript
FAST_FORWARD_BACKWARD = 102
```

Fast-forward/Rewind component group for video playback.

This component group is mutually exclusive with the previous/next component group. It cannot be added if the previous/next component group is added.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-VideoPlayControlGroup-FAST_FORWARD_BACKWARD = 102--><!--Device-VideoPlayControlGroup-FAST_FORWARD_BACKWARD = 102-End-->

**System capability:** SystemCapability.Window.SessionManager
