# @ohos.multimodalAwareness.onScreen

This module provides the onscreen awareness capability.

> **NOTE:** &gt;

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

## Modules to Import

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [apperceive](arkts-multimodalawareness-onscreen-apperceive-f-sys.md) | Proactively triggers screen content awareness to obtain the screen content for snapshot analysis. |
| [capture](arkts-multimodalawareness-onscreen-capture-f-sys.md) | Proactively triggers screen content awareness to obtain page information. |
| [getPageContent](arkts-multimodalawareness-onscreen-getpagecontent-f-sys.md) | Obtains the onscreen content when a window is displayed on the screen. |
| [interact](arkts-multimodalawareness-onscreen-interact-f-sys.md) | Proactively triggers screen behavior interaction to identify screen behaviors and return behavior receipts. For<br> example, after a link is clicked, the system accurately jumps to the specified paragraph and <br> highlights the text based on the receipt information. |
| [offReadingScreenPermissionListener](arkts-multimodalawareness-onscreen-offreadingscreenpermissionlistener-f-sys.md) | Disables the screen content access permission monitoring. |
| [onReadingScreenPermissionListener](arkts-multimodalawareness-onscreen-onreadingscreenpermissionlistener-f-sys.md) | Enables the screen content access permission monitoring and returns the permission status in real time. |
| [sendControlEvent](arkts-multimodalawareness-onscreen-sendcontrolevent-f-sys.md) | If the target window is displayed on the screen, you can use this API to send screen control events based on the paragraph information obtained via [onScreen.getPageContent](arkts-multimodalawareness-onscreen-getpagecontent-f-sys.md). |
| [subscribe](arkts-multimodalawareness-onscreen-subscribe-f-sys.md) | Enables proactive awareness on screen content and subscribes to a screen awareness result. |
| [trigger](arkts-multimodalawareness-onscreen-trigger-f-sys.md) | Proactively triggers screen content awareness and obtains the current screen awareness result. |
| [unsubscribe](arkts-multimodalawareness-onscreen-unsubscribe-f-sys.md) | Disables proactive awareness on screen content and unsubscribes from a screen awareness result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AwarenessItem](arkts-multimodalawareness-onscreen-awarenessitem-i-sys.md) | Provides page information, which includes: |
| [ContentOptions](arkts-multimodalawareness-onscreen-contentoptions-i-sys.md) | Defines the options for obtaining the onscreen content. |
| [ControlEvent](arkts-multimodalawareness-onscreen-controlevent-i-sys.md) | Defines a control event. |
| [EntityInfo](arkts-multimodalawareness-onscreen-entityinfo-i-sys.md) | Provides entity information perceived, including content, links, images, and other types of entities. |
| [OnscreenAwarenessCap](arkts-multimodalawareness-onscreen-onscreenawarenesscap-i-sys.md) | Defines onscreen awareness capabilities (including but not limited to awareness in a reading scenario and OCR). |
| [OnscreenAwarenessInfo](arkts-multimodalawareness-onscreen-onscreenawarenessinfo-i-sys.md) | Returns the list of onscreen awareness information. |
| [OnscreenAwarenessOptions](arkts-multimodalawareness-onscreen-onscreenawarenessoptions-i-sys.md) | Defines the list of onscreen awareness parameters, which is used to obtain onscreen information in specific scenarios. For example, a window ID is provided to collect application UI content and links. |
| [PageContent](arkts-multimodalawareness-onscreen-pagecontent-i-sys.md) | Defines the onscreen content. |
| [Paragraph](arkts-multimodalawareness-onscreen-paragraph-i-sys.md) | Defines the paragraph information. |
| [ReadingScreenPermissionStatus](arkts-multimodalawareness-onscreen-readingscreenpermissionstatus-i-sys.md) | Returns the status of the permission for reading screen information. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [CollectStrategy](arkts-multimodalawareness-onscreen-collectstrategy-e-sys.md) | Defines a page information collection policy. |
| [EventType](arkts-multimodalawareness-onscreen-eventtype-e-sys.md) | Enumerates the control event types. |
| [Scenario](arkts-multimodalawareness-onscreen-scenario-e-sys.md) | Enumerates the scenarios of the onscreen content. |
<!--DelEnd-->
