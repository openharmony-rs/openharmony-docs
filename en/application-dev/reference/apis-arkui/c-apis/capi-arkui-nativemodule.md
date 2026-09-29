# ArkUI_NativeModule

## Overview

Provides UI capabilities of ArkUI on the native side, such as UI component creation and destruction, tree node operations, attribute setting, and event listening.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

## Files

| Name | Description |
| -- | -- |
| [native_material.h](capi-native-material-h.md) | Declares the immersive material types and APIs for ArkUI on the native side. |
| [native_gesture.h](capi-native-gesture-h.md) | Declares the APIs of **NativeGesture**. |
| [native_animate.h](capi-native-animate-h.md) | Defines a set of animation APIs of ArkUI on the native side. The APIs in **native_animate.h** must be called in the main thread. |
| [native_type_visual.h](capi-native-type-visual-h.md) | Defines the visual effect types for the native module. |
| [native_node.h](capi-native-node-h.md) | Provides type definitions for <b>NativeNode</b> APIs. |
| [native_node_ani.h](capi-native-node-ani-h.md) | Declares APIs for converting <b>FrameNode</b> objects on the ArkTS side to <b>ArkUI_NodeHandle</b> objects on the native side. |
| [native_key_event.h](capi-native-key-event-h.md) | Declares the APIs of **NativeKeyEvent**. |
| [drag_and_drop.h](capi-drag-and-drop-h.md) | Declares the APIs of **NativeDrag**. |
| [native_interface.h](capi-native-interface-h.md) | Provides a unified entry for the native module APIs. |
| [native_interface_focus.h](capi-native-interface-focus-h.md) | Declares APIs for focus management, mainly used for actively transferring focus, managing the default focus transfer behavior, and controlling the focus activation state. |
| [native_type.h](capi-native-type-h.md) | Defines the common types for the native module. |
| [native_dialog.h](capi-native-dialog-h.md) | Defines a set of custom dialog box APIs of ArkUI on the native side. |
| [error_code.h](capi-error-code-h.md) | Defines the error code for the native module. |
| [common_type.h](capi-common-type-h.md) | Defines the common types for ArkUI native APIs. |
| [drawable_descriptor.h](capi-drawable-descriptor-h.md) | Declares the APIs of **NativeDrawableDescriptor**. |
| [native_node_napi.h](capi-native-node-napi-h.md) | Declares APIs for converting <b>FrameNode</b> objects on the ArkTS side to <b>ArkUI_NodeHandle</b> objects on the native side. |
| [styled_string.h](capi-styled-string-h.md) | Defines the text style and layout manager for the component whose [type](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-historicalpoint.md) is set to **ARKUI_NODE_TEXT**<br>on the native side. |
| [custom_span.h](capi-custom-span-h.md) | Defines enumerations and APIs related to **CustomSpan**, which is used to implement precise size measurement, layout typesetting, and drawing effects for custom spans. It supports you in implementing text and image layout, emoji embedding, custom markers, and other features in scenarios such as rich text editors, chat applications, and document applications, providing flexible custom span capabilities to help improve development efficiency and achieve richer text layout effects. |
| [node_water_flow.h](capi-node-water-flow-h.md) | Defines enumerations and APIs related to **WaterFlow**. |
| [swiper.h](capi-swiper-h.md) | Defines the enumerations and APIs of the **Swiper** component for implementing scenarios such as carousel display and content navigation. It supports custom navigation indicators (dot/number types), navigation arrow styles, nested scrolling modes, mouse wheel page-turning modes, and animation modes, helping users quickly build carousel interaction experiences. |
| [common_attributes.h](capi-common-attributes-h.md) | Defines the common property and method types for the native module. |
| [navigation_router.h](capi-navigation-router-h.md) | Defines the enumerations related to the **NavDestination** and **Router** components. |
| [scroll.h](capi-scroll-h.md) | Provides shared scroll-related enum definitions for <b>NativeNode</b> APIs. |
| [list_item.h](capi-list-item-h.md) | Provides shared list item-related type and function definitions for <b>NativeNode</b> APIs. |
| [node_grid.h](capi-node-grid-h.md) | Defines enumerations and APIs related to **Grid**. |
| [custom_attributes.h](capi-custom-attributes-h.md) | Provides custom node event definitions for <b>NativeNode</b> APIs. |
| [xcomponent.h](capi-xcomponent-h.md) | Defines xcomponent attribute enum value. |
| [rich_editor.h](capi-rich-editor-h.md) | Defines structs, enumerations, and APIs related to <b>RichEditor</b>. <b>RichEditor</b> provides rich text editing capabilities, supporting custom text selection menus, styled string controllers, paragraph and text style settings, and haptic feedback control. It is suitable for scenarios where rich text editing and custom interaction menus need to be implemented in applications. |
| [image_span.h](capi-image-span-h.md) | Defines enumerations related to **ImageSpan**, which are used to embed images in rich text and control the alignment between images and text. Multiple alignment modes are supported for mixed image-text layout scenarios, enabling precise alignment of images with text and improving the display of rich text. |
| [progress.h](capi-progress-h.md) | Defines enumerations and APIs related to **Progress**, supporting multiple progress indicator types such as linear, ring, eclipse, and capsule, and providing customization capabilities for linear progress indicator style options (smooth animation, scan effect, width, and corner radius). It is suitable for scenarios such as displaying task progress and loading states, helping you quickly implement diverse progress displays and interactive feedback. |
| [slider.h](capi-slider-h.md) | Provides Slider node type definitions for <b>NativeNode</b> APIs. |
| [image_animator.h](capi-image-animator-h.md) | Defines **ImageAnimator** node types for **NativeNode** APIs. |
| [layout.h](capi-layout-h.md) | Defines the layout-related types for the native module. |
| [text_common.h](capi-text-common-h.md) | Defines common text enumerations and APIs, covering text alignment, decoration line styles, copy and paste, overflow handling, line break policies, and menu customization. It is applicable to scenarios such as text boxes and text display, helping you flexibly control text styles and interaction behavior while reducing development complexity. |
| [text_input.h](capi-text-input-h.md) | Defines enumerations related to **TextInput**, which supports multiple input type configurations (including text, numbers, passwords, emails, and phone numbers),  style customization of the clear button, auto-filling content type settings, and input box style selection. It is applicable to scenarios requiring user interaction input, such as login and registration, form filling, and search input, helping you quickly implement single-line text input that meets service requirements. |
| [checkbox.h](capi-checkbox-h.md) | Provides Checkbox node type definitions for <b>NativeNode</b> APIs. |
| [list.h](capi-list-h.md) | Defines enumerations and APIs related to **List**. |
| [text.h](capi-text-h.md) | Defines enumerations and APIs related to **Text** for configuring text styles, controlling marquee effects, implementing text entity recognition, and managing text controllers. It is applicable to scenarios such as customizing text display effects, implementing dynamic text interaction, recognizing special entities in text (such as addresses and phone numbers), and precisely controlling text font weight. With these configuration APIs, you can flexibly control the display effects and interaction behaviors of text components to improve user experience. |
| [image.h](capi-image-h.md) | Defines **Image** node types for **NativeNode** APIs. |
| [embedded_component.h](capi-embedded-component-h.md) | Defines embedded component attribute and interface. |
| [picker.h](capi-picker-h.md) | Defines **Picker** node types for **NativeNode** APIs. |
| [button.h](capi-button-h.md) | Provides Button node type definitions for <b>NativeNode</b> APIs. |
| [text_area.h](capi-text-area-h.md) | Defines enumerations related to **TextArea**. The **TextArea** component is used for receiving multi-line text input. The enumerated values specify different input types, which affect the validation rules for input content, such as basic input, pure numbers, phone numbers, email addresses, and verification codes. You can select the appropriate enumerated value based on the form type, and the system will automatically provide corresponding content validation, thereby optimizing the user input experience and ensuring the correctness of the data format. |
