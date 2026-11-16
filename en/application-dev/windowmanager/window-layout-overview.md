# Window Layout Development

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @wxcHello-->
<!--Designer: @ALTNAT-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=0ebec3b1d2e176109fe439d58888a4e9114ba429 translatedAt=2026-11-12T04:54:30.774Z pushedAt=2026-11-12T07:52:09.926Z nl=1 -->

## When to Use

**Window layout** refers to the capability to configure and manage the size, position, scaling, and content layout of a window. With the window layout capability, developers can flexibly control how application windows appear on the screen, and enable window content to be properly arranged across different sizes and window forms.

Window layout includes the following three documents:

- [Managing Window Position and Size](window-layout.md): Set the position coordinates and width/height of a window on the screen, constrain the window's size range and aspect ratio, and provide the ability to query and listen for window position and size changes.

- [Window Freeform Resize Development Practice Case](window-freeform-resize-practical-case.md): A window in the [freeform window](freeform-window-overview.md#freeform-window) state can be continuously dragged and resized, ensuring that content is displayed correctly and completely at any window size.

- [Window Adaptive Layout Development Practice Case](window-adaptive-practical-case.md): In scenarios where the window size changes dynamically, such as freeform resizing, split screen, cross-screen, and rotation, content is automatically rearranged along with the window size to ensure a reasonable layout across multiple forms.

The typical scenarios are as follows:

| Typical Scenario | Corresponding Capability | Specific Section                                                 |
| -------- | -------- |------------------------------------------------------|
| Set the initial position and size of an application window at startup | Managing window position and size | [Setting the Initial Position and Size of the Main Window at Startup](window-layout.md#setting-the-initial-position-and-size-of-the-main-window-at-startup) |
| Dynamically adjust the position and size of a window at runtime | Managing window position and size | [Dynamically Adjusting Window Position and Size](window-layout.md#dynamically-adjusting-the-window-position-and-size)          |
| Change the position and size of a window by dragging | Managing window position and size | [Changing Window Position and Size by Dragging](window-layout.md#changing-the-window-position-and-size-by-dragging)      |
| Constrain the window size range or aspect ratio to prevent the window from being too large or too small | Managing window position and size | [Managing Window Size Limits or Aspect Ratio Limits](window-layout.md#managing-the-window-size-or-aspect-ratio-limits)    |
| Continuously drag and resize a window | Window freeform resize | [Window Freeform Resize Development Practice Case](window-freeform-resize-practical-case.md) |
| Automatically rearrange content when the window size changes | Window adaptive layout | [Window Adaptive Layout Development Practice Case](window-adaptive-practical-case.md)   |
