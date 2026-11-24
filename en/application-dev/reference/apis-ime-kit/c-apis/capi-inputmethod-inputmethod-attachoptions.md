# InputMethod_AttachOptions

```c
typedef struct InputMethod_AttachOptions InputMethod_AttachOptions
```

## Overview

Input method binding option, which is used to carry related configurations when the input method is bound. This is an opaque type. The caller cannot directly access its member variables and can perform operations only through the functions provided in this header file. <br><br>Function: This parameter is a mandatory parameter of OH_InputMethodController_Attach and OH_InputMethodController_AttachWithUIContext. It is used to configure the behavior options when the input method is bound, including: <br>- Whether to automatically display the keyboard( showKeyboard) during binding. Controls whether the keyboard pops up immediately after the binding is complete. <br>-Reason for requesting the keyboard(requestKeyboardReason): indicates the scenario reason that triggers the startup of the input method.(e.g., touch click, mouse click, or active application invoking) to help the system optimize the input experience. <br> <br>Application scenario: <br>- showKeyboard=true: applies to the scenario where you need to enter information immediately after the focus is obtained in the text box, for example, the text editing box. After the binding, the keyboard automatically pops up. <br>- showKeyboard=false: applies to scenarios where an interaction channel is established but a keyboard is not required(for example, the search box). After the binding, the keyboard is not displayed, and the ShowKeyboard is used to automatically start the interface. <br>- requestKeyboardReason: This parameter is applicable to the scenario where the reason for triggering the input method needs to be explained to the system, helping the system select an appropriate input policy. <br><br>Relationship with other structures: <br>- InputMethod_AttachOptions is a mandatory parameter of OH_InputMethodController_Attach and OH_InputMethodController_AttachWithUIContext. The Attach function requires both InputMethod_TextEditorProxy and InputMethod_AttachOptions. The requestKeyboardReason parameter in <br>- InputMethod_AttachOptions uses the InputMethod_RequestKeyboardReason enumeration type, which is defined in [inputmethod_types_capi.h](capi-inputmethod-types-capi-h.md). The <br>- OH_InputMethodProxy_ShowTextInput function also takes InputMethod_AttachOptions as a parameter to re-request the display keyboard in the bound state and specify the reason for the request. <br> <br>Handles and ownership: Only valid handles created by this API or borrowed handles provided by the framework can be used. Only independently created objects can be destroyed. The object provided by the callback and the child object view of TextConfig are borrowed objects. The provider returns IME_ERR_PARAMCHECK for an unregistered or invalid handle. The null parameter still returns an error according to the original rule. <br>Protection boundary: Life cycle check does not guarantee the thread safety of object members, nor does it identify all invalid addresses after address reuse. After the object is destroyed, the pointer should be null. The callback object must not be retained after the callback ends.

<!--Device-typedef struct InputMethod_AttachOptions InputMethod_AttachOptions--><!--Device-typedef struct InputMethod_AttachOptions InputMethod_AttachOptions-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-ime-kit-inputmethod.md)

**Header file**: [inputmethod_attach_options_capi.h](capi-inputmethod-attach-options-capi-h.md)

