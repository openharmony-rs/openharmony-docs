# Implementing Interaction Responses
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

The ArkUI framework offers a comprehensive set of APIs for handling input events from various peripherals. Beyond basic input handling, ArkUI also provides advanced APIs for responding to normalized user interactions such as gestures, drag and drop, and focus management.

Compared with raw input events, gestures are the preferred method for handling user interactions. Gestures abstract away device-specific differences and represent high-level interaction intent. For example, a click operation may be implemented by using a finger touch control, or may be completed by using a mouse click. An application only needs to connect to one [TapGesture](../reference/apis-arkui/arkui-ts/ts-basic-gestures-tapgesture.md) to support click interactions on various input equipment.

[Interaction Mechanism Overview](arkts-interaction-basic-principles.md): explains the core concepts and principles behind ArkUI's interaction model.

[Input Devices and Events](arkts-interaction-development-guide-raw-input-event.md): covers raw input events from different devices and how to process them.

[Implementing Gesture Responses](arkts-interaction-development-guide-support-gesture.md): explains how to handle standardized gesture interactions.

[Supporting Unified Drag-and-Drop](arkts-common-events-drag-event.md): guides you through implementing consistent drag and drop behavior across devices.

[Supporting Focus Processing](arkts-common-events-focus-event.md): shows how to manage component focus within the UI.

When developing UI components using the NDK, you can add interaction responses through the following resources:
- [Binding Basic Input Events](ndk-bind-input-events.md): Add basic input event responses to components using NDK APIs.
- [Binding Gesture Events](ndk-bind-gesture-events.md): Add gesture support to components for richer interaction.
- [Binding Drag Events](ndk-drag-event.md): Implement unified drag and drop functionality using NDK APIs.
