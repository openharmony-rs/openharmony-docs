# UI Context Debugging
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

This section describes how to resolve text display abnormalities caused by invalid [UIContext](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md). Using an invalid UIContext object (typically resulting from destruction of the corresponding UI instance) may cause subsequent UI operations to fail. This issue is common in multi-window scenarios. Starting from API version 12, it can also occur when the process cache is enabled via [setSupportedProcessCache](../reference/apis-ability-kit/js-apis-inner-application-applicationContext.md#applicationcontextsetsupportedprocesscache12) and the process is then rapidly restarted.

## Identifying UIContext Errors

Invalid UIContext may occur in the following scenarios:

- JavaScript exception: "Node Constructor error, param uiContext error".
  This error occurs when an invalid UIContext is used in [custom nodes](./arkts-user-defined-node.md), potentially causing subsequent UI operations to be incorrectly associated with the invalid context.

- Instance status update logs with context instance ID values greater than or equal to 100000 and less than 1000000.
  The format of the instance status update log is as follows:

  `({currentId}:{trackedId}:{trackedReason})][{bundleName}][{moduleName}][{thisInstanceId}]: window {status}`

  Fields in the log
  | Field| Type| Typical Value| Description|
  | ---- | ---- | ---- | ---- |
  |{currentId}| Integer| -1 | Context instance ID. In a normal application, this value is negative.|
  |{trackedId}| Integer| 100000  | ID of the indirectly traced instance. Usually a positive number; can be ignored.|
  |{trackedReason}| String| singleton | Reason for indirect tracing; can be ignored.|
  |{bundleName}| String| com.example.helloworld| Bundle name of the application.|
  |{moduleName}| String| entry| Module name of the current module.|
  |{thisInstanceId}| Positive number| 100000 | Notified UI instance ID.|
  |{status}| Status of the notified instance| focus | Available values:<br> - **focus**: focused<br> - **unfocus**: unfocused<br> - **foreground**: foreground<br> - **background**: background<br> - **destroy**: destroyed|

  Use this regular expression to match relevant logs:

  `\(-?\d+:-?\d+:(scope|active|default|singleton|foreground|undefined)\)\] \[[a-z0-9.]+\]\[[a-zA-Z][0-9a-zA-Z_.]*\]\[\d+\]: window (focus|unfocus|foreground|background|destroy)`

  **Example Analysis**

  - Normal log:

    `(-2:100000:singleton)] [com.example.helloworld][entry][100000]: window foreground`

  - Abnormal log:

    `(100000:100000:scoped)] [com.example.helloworld][entry][100001]: window background`

    This log indicates an error tracing the UI instance with ID 100000.

  - Destruction log:

    `(-2:100000:singleton)] [com.example.helloworld][entry][100000]: window destroy`

    This log indicates that the UI instance with ID 100000 has been destroyed; subsequent UI operations that rely on its context may be affected.

## Resolving Display Abnormalities Caused by UIContext Errors

**Symptom**

The following situations may occur:
1. When the [setStyledString](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#setstyledstring12) method is used to set the font size, the font size does not change as expected.
2. When a UIContext member method is used, the UI does not respond or is displayed incorrectly.

**Solution**

Obtain a valid UIContext object using one of these methods:
- Use the [getUIContext](../reference/apis-arkui/arkui-ts/ts-custom-component-api.md#getuicontext) method of the custom component.
- Use the [getUIContext](../reference/apis-arkui/arkts-apis-window-Window.md#getuicontext10) method of the window.
