# InputMethod
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=c9f68a28229d3fb5da602baa0bfb8e542d407a50 translatedAt=2026-09-02T02:25:53.556Z pushedAt=2026-09-02T07:01:48.213Z -->

## Overview

The **InputMethod** module provides C APIs for input method usage. These APIs are designed for invocation on the app side.

Function positioning: This module provides app developers with a complete set of C APIs for interactions between self‑drawn edit boxes and the input method service. Core capabilities include attaching to or detaching from the input method service, sending requests and notifications to the input method, receiving callback notifications from the input method, configuring edit box attributes, managing cursor and text avoidance information, and even more.

Usage scenarios: It applies to NDK-based apps with self-drawn edit boxes that require interactions with the system input method service. The typical workflow is as follows: the app creates a **TextEditorProxy** and **AttachOptions**, attaches to the input method service via the controller, interacts with the input method through **InputMethodProxy** after successful attachment, and detaches via the controller when operations are complete.

Use effect: After attaching to the input method, the app can receive callback notifications from the input method, such as text insertion, deletion, and cursor movement, and can also proactively send requests to the input method, such as cursor updates, selection changes, and private commands. After detachment, all interaction channels are closed and related resources are released.

Lifecycle management: This module enforces strict pairing rules for create‑destroy and attach‑detach operations:

- Attach-detach pairing: **OH_InputMethodController_Attach** must be called in pair with **OH_InputMethodController_Detach**. Failing to detach results in input method resource leaks.
- Create-destroy pairing: All objects created by Create‑prefixed functions must be destroyed by their corresponding Destroy functions; otherwise, memory leaks will occur.
- Calling sequence: Create dependent objects (**TextEditorProxy** and **AttachOptions**) first, and then call the **Attach** API to perform attachment. Use **InputMethodProxy** for interactions after successful attachment. Finally, call **Detach** and destroy all created objects.

Thread safety: The APIs in this module are not thread-safe. It is recommended that you call them on the main thread. The execution thread for **TextEditorProxy** callbacks can be configured via **OH_TextEditorProxy_SetCallbackInMainThread**.

**Library:** libohinputmethod.so

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

## Module Architecture

This module consists of nine header files which are divided into four layers by responsibility:

- Control layer: **inputmethod_controller_capi.h**. The core entry of the module. It provides capabilities to attach to and detach from the input method service, serving as the start and end point for all interactions.
- Interaction layer: **inputmethod_text_editor_proxy_capi.h** and **inputmethod_inputmethod_proxy_capi.h**. Bidirectional interaction channels. **TextEditorProxy** is the callback registration channel for traffic from the input method to the app, through which the app receives notifications such as text insertion and deletion from the input method. **InputMethodProxy** is the request sending channel for traffic from the app to the input method, through which the app sends notifications such as cursor updates and selection changes to the input method.
- Configuration layer: **inputmethod_attach_options_capi.h**, **inputmethod_text_config_capi.h**, **inputmethod_cursor_info_capi.h**, and **inputmethod_text_avoid_info_capi.h**. Carrier objects for various configurations and information. They manage attachment options, edit box configurations, cursor position information, and text avoidance information respectively.
- Data layer: **inputmethod_private_command_capi.h** and **inputmethod_types_capi.h**. Definitions for private command data and common types (such as enums and error codes).

Typical calling process:
1. Create a **TextEditorProxy** and register callbacks via **inputmethod_text_editor_proxy_capi.h**.
2. Create **AttachOptions** to configure attachment options via **inputmethod_attach_options_capi.h**.
3. Call **Attach** via **inputmethod_controller_capi.h** to attach to the input method service and obtain an **InputMethodProxy**.
4. Use **InputMethodProxy** to interact with the input method via **inputmethod_inputmethod_proxy_capi.h**.
5. Manage configuration information via **inputmethod_text_config_capi.h**, **inputmethod_cursor_info_capi.h**, and other related header files.
6. Call **Detach** to detach from the input method via **inputmethod_controller_capi.h** .
7. Destroy all created objects.

## Files

| Name| Description|
| -- | -- |
| [inputmethod_controller_capi.h](capi-inputmethod-controller-capi-h.md) | Header file for the input method controller, providing the core methods for attach to and detach from the input method service. It is the entry and endpoint of the interaction between the app and the input method service. **Attach** must be called after you create **TextEditorProxy** and **AttachOptions**, and **Detach** must be called when the input method is no longer used to release resources. **Attach** and **Detach** must be called in pairs. |
| [inputmethod_text_editor_proxy_capi.h](capi-inputmethod-text-editor-proxy-capi-h.md) | Header file for the text editor proxy, providing methods for creating or destroying **TextEditorProxy** instances and registering or obtaining callback functions. **TextEditorProxy** is the callback channel through which the app receives notifications and requests from the input method. Before attachment, the app must create **TextEditorProxy** and register the necessary callback functions (such as **InsertText** and **DeleteForward**). After attachment, the input method interacts with the app through these callbacks. The lifecycle is managed by you, and **Create** and **Destroy** must be called in pairs. |
| [inputmethod_inputmethod_proxy_capi.h](capi-inputmethod-inputmethod-proxy-capi-h.md) | Header file for the input method proxy, providing methods for the app to proactively send requests and notifications to the input method service, including showing/hiding the keyboard, notifying selection changes, notifying cursor updates, notifying configuration changes, and sending private commands. The **InputMethodProxy** instance is returned by **OH_InputMethodController_Attach** and cannot be created independently. It remains valid until **Detach** is called. |
| [inputmethod_attach_options_capi.h](capi-inputmethod-attach-options-capi-h.md) | Header file for input method attachment options, providing creation, destruction and property read/write methods for the **AttachOptions** instance. **AttachOptions** is used to configure the behavior parameters for input method attachment, such as **showKeyboard** and **requestKeyboardReason**. It is a mandatory parameter for calling **Attach**. **Create** and **Destroy** must be called in pairs. |
| [inputmethod_text_config_capi.h](capi-inputmethod-text-config-capi-h.md) | Header file for input box configuration information, providing creation, destruction and property read/write methods for the **TextConfig** instance. **TextConfig** carries the complete configuration information of the input box, including the input type, Enter key type, cursor information, avoidance information, selection range, window ID, and placeholder text. It is returned to the input method in the **GetTextConfig** callback of **TextEditorProxy**. **Create** and **Destroy** must be called in pairs. |
| [inputmethod_cursor_info_capi.h](capi-inputmethod-cursor-info-capi-h.md) | Header file for cursor information, providing creation, destruction and property read/write methods for the **CursorInfo** instance. **CursorInfo** describes the position and size of the cursor on the physical screen. The coordinates must be absolute coordinates on the physical screen (in px), and are used by the input method to locate the cursor area for precise input and cursor following. The cursor information can be passed to the input method through **TextConfig** or proactively reported to the input method through **NotifyCursorUpdate**. **Create** and **Destroy** must be called in pairs. |
| [inputmethod_text_avoid_info_capi.h](capi-inputmethod-text-avoid-info-capi-h.md) | Header file for input box avoidance information, providing creation, destruction and property read/write methods for the **TextAvoidInfo** instance. **TextAvoidInfo** describes the area that needs to be avoided when the keyboard is raised (**positionY** and **height**), and is used by the app to inform the input method of the current avoidance area information in **TextConfig**. **Create** and **Destroy** must be called in pairs. |
| [inputmethod_private_command_capi.h](capi-inputmethod-private-command-capi-h.md) | Header file for private commands, providing creation, destruction and property read/write methods for the **PrivateCommand** instance. **PrivateCommand** is used to transfer custom private data between the app and the input method. It supports three value types: string, Boolean, and int32. It is sent through **SendPrivateCommand** or received in the **ReceivePrivateCommand** callback. The total command size is limited to 32 KB, and the array can contain up to 5 elements. **Create** and **Destroy** must be called in pairs. |
| [inputmethod_types_capi.h](capi-inputmethod-types-capi-h.md) | Header file for common type definitions of the input method, providing the definitions of all enums and error codes in the module, including keyboard status (**KeyboardStatus**), Enter key type (**EnterKeyType**), direction (**Direction**), extended action (**ExtendAction**), text input type (**TextInputType**), command value type (**CommandValueType**), keyboard request reason (**RequestKeyboardReason**), and error code (**ErrorCode**). This header file contains no callable functions and is referenced by other header files only as type definitions.  |
