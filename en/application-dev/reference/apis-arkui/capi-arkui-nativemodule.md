# ArkUI_NativeModule
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @wangyang2022-->
<!--Designer: @piggyguy; @wangyang2022-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Provides the APIs for accessing and managing page interaction of ArkUI on the native side. It is applicable to scenarios where the NDK is used to build UIs, process input events, bind gestures, execute animations, and manage node trees.

Provides the basic input event APIs of ArkUI on the native side. For details, see [Binding Basic Input Events](../../ui/ndk-bind-input-events.md).

Provides drag and drop APIs of ArkUI on the native side. For details, see [Drag Event](../../ui/ndk-drag-event.md).

Provides the general key event APIs of ArkUI on the native side. For details, see [Binding Basic Input Events](../../ui/ndk-bind-input-events.md#key-event).

Provides the ArkUI APIs for gesture recognition, gesture event processing, and gesture callback on the native side. For details, see [Binding Gesture Events](../../ui/ndk-bind-gesture-events.md).

Provides the ArkUI APIs for animation creation, control, and callback on the native side. For details, see [Animation Overview](../../ui/ndk-use-animation.md).

Provides the UI APIs of ArkUI on the native side, such as UI component creation and destruction, tree node operations, attribute setting, and event listening. For details, see [Integrating with ArkTS Pages](../../ui/ndk-access-the-arkts-page.md).

The preceding APIs are applicable to scenarios where input events, drag operations, gestures, animations, and UI component operations are processed on the native side. They can be used to implement ArkUI page interaction and component tree management.

**Since**: 12

## Files

| Name| Description|
| -- | -- |
| [common_attributes.h](capi-common-attributes-h.md) | Defines the types of common attributes and events of **NativeModule**.|
| [embedded_component.h](capi-embedded-component-h.md) | Defines the structs and APIs of the **EmbeddedComponent** component.|
| [image.h](capi-image-h.md) | Defines **Image** node types for **NativeNode** APIs.|
| [image_animator.h](capi-image-animator-h.md) | Defines **ImageAnimator** node types for **NativeNode** APIs.|
| [layout.h](capi-layout-h.md) | Defines layout-related enumerations and APIs.|
| [custom_attributes.h](capi-native-node-node-attributes-custom-attributes-h.md) | Defines measurement, layout, and drawing event types for custom components in **NativeNode** APIs. These types are used to register and handle measurement, layout, and drawing events for the content layer, foreground layer, and floating layer.|
| [grid.h](capi-grid-h.md) | Defines the enumerations and APIs of the **Grid** component.|
| [list.h](capi-list-h.md) | Defines the enumerations and APIs of the **List** component.|
| [list_item.h](capi-list-item-h.md) | Defines the enumerations and APIs related to the swipe operation of the **ListItem** component.|
| [navigation_router.h](capi-navigation-router-h.md) | Defines the enumerations and APIs of the **Navigation** or **Router** component.|
| [scroll.h](capi-scroll-h.md) | Defines the enumerations related to the **Scroll** component.|
| [swiper.h](capi-swiper-h.md) | Defines the enumerations and APIs of the **Swiper** component.|
| [water_flow.h](capi-water-flow-h.md) | Defines the enumerations and APIs of the **WaterFlow** component.|
| [drag_and_drop.h](capi-drag-and-drop-h.md) | Declares the APIs of **NativeDrag**.|
| [drawable_descriptor.h](capi-drawable-descriptor-h.md) | Declares the APIs of **NativeDrawableDescriptor**.|
| [native_animate.h](capi-native-animate-h.md) | Declares a set of animation APIs of ArkUI on the native side.|
| [native_dialog.h](capi-native-dialog-h.md) | Declares a set of custom dialog box APIs of ArkUI on the native side.|
| [native_gesture.h](capi-native-gesture-h.md) | Declares the APIs of **NativeGesture**.|
| [native_interface.h](capi-native-interface-h.md) | Declares a unified entry for the native module APIs.|
| [native_interface_focus.h](capi-native-interface-focus-h.md) | Declares the APIs for focus management, mainly used for actively transferring focus, controlling the default focus transfer behavior, and controlling the focus activation state.|
| [native_key_event.h](capi-native-key-event-h.md) | Declares the APIs of **NativeKeyEvent**.|
| [native_material.h](capi-native-material-h.md) | Provides immersive material types and API declarations for ArkUI on the native side.|
| [native_node.h](capi-native-node-h.md) | Declares the APIs of **NativeNode**.|
| [native_node_napi.h](capi-native-node-napi-h.md) | Declares the APIs used to convert FrameNodes on the ArkTS side into **ArkUI_NodeHandle**s.|
| [native_type.h](capi-native-type-h.md) | Defines the common types for the native module.|
| [text.h](capi-text-h.md) | Defines the enumerations and APIs related to text, which are used to configure text styles, control the marquee effect, implement text entity recognition, and manage text controllers. It is applicable to scenarios where you need to customize the text display effect, implement dynamic text interaction, recognize special entities (such as addresses and phone numbers) in text, and precisely control the font weight of text. Through these configuration APIs, you can flexibly control the display effect and interaction behavior of text components, improving user experience.|
| [text_common.h](capi-text-common-h.md) | Defines common enumerations and APIs for text components, covering capabilities such as text alignment, decoration line styling, copy and paste, overflow handling, line break policy configuration, and menu customization. It is applicable to scenarios such as text input boxes and text display, helping you flexibly control text styles and interaction behaviors and simplifying development.|
| [text_input.h](capi-text-input-h.md) | Defines the enumerations related to **TextInput**. It supports multiple input types (including the text, number, password, email address, and phone number), custom styles for the clear button, settings for autofilling content types, and selection of input box styles. It is suitable for scenarios that require user interaction, such as login and registration, form filling, and search input. It helps you quickly implement single-line text input features that meet service requirements.|
| [text_area.h](capi-text-area-h.md) | Defines the enumerations related to **TextArea**. The **TextArea** component is used to receive multi-line text input. The enumerated values are used to specify different input types, which affect the validation rules of the input content. For example, the input types can be basic input, digits only, phone number, email address, and verification code. You can select an appropriate enumerated value based on the form type. The system will automatically provide the corresponding content validation, optimizing user input experience and ensuring the correctness of the data format.|
| [image_span.h](capi-image-span-h.md) | Defines the enumerations related to **ImageSpan**, which is used to embed images in rich text and control the alignment mode between images and text. It supports multiple alignment modes and is applicable to mixed arrangement of images and text. This allows for precise alignment between images and text, enhancing the display effect of rich text.|
| [progress.h](capi-progress-h.md) | Defines the enumerations and APIs related to **Progress**. It supports multiple types of progress bars, such as linear, ring, circular, and capsule. It also allows for customization of linear progress bar styles (smooth animation, scan effect, width, and corner radius). This is applicable to scenarios where task progress and loading status need to be displayed, helping you quickly implement diverse progress display and interactive feedback.|
| [rich_editor.h](capi-rich-editor-h.md) | Defines enumerations and APIs related to **RichEditor**.|
| [custom_span.h](capi-custom-span-h.md) | Defines the structs and APIs related to **CustomSpan** to implement precise size measurement, layout, and drawing effect of custom spans. It allows you to implement features such as mixed arrangement of images and texts, emoticon embedding, and custom tags in scenarios such as rich text editors, chat applications, and document applications. It provides flexible custom span drawing capabilities, helping you improve development efficiency and achieve richer text layout effects.|
| [picker.h](capi-picker-h.md) | Defines **Picker** node types for **NativeNode** APIs.|
| [button.h](capi-button-h.md) | Defines **Button** node types for **NativeNode** APIs.|
| [checkbox.h](capi-checkbox-h.md) | Defines **Checkbox** node types for **NativeNode** APIs.|
| [slider.h](capi-slider-h.md) | Defines **Slider** node types for **NativeNode** APIs.|
| [styled_string.h](capi-styled-string-h.md) | Declares styled string APIs of ArkUI on the native side.|
| [xcomponent.h](capi-xcomponent-h.md) | Defines the enumerations of the **XComponent** component.|
| [error_code.h](capi-arkui-nativemodule-arkui-error-code-h.md) |  Enumerates error codes of ArkUI native APIs.|

<!--no_check-->