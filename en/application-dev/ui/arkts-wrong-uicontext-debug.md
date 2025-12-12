# UI Context Debugging
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @HelloCrease-->

This section describes how to resolve text display abnormalities caused by invalid [UIContext](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md). Using an invalid UIContext object (typically resulting from destruction of the corresponding UI instance) may cause subsequent UI operations to fail. This issue commonly occurs in multi-window scenarios and, since API version 12, may also appear when process caching is enabled via [setSupportedProcessCache](../reference/apis-ability-kit/js-apis-inner-application-applicationContext.md#applicationcontextsetsupportedprocesscache12) during rapid application launches.

## Identifying UIContext Errors

Invalid UIContext may occur in the following scenarios:

- **JavaScript exception**: "Node Constructor error, param uiContext error".
  This error occurs when an invalid UIContext is used within [custom nodes](./arkts-user-defined-node.md), potentially causing subsequent UI operations to be incorrectly associated with the invalid context.

- Instance status update logs: context instance ID values greater than or equal to 100000 and less than 1000000.
  The format of the instance status update log is as follows:

  `({currentId}:{trackedId}:{trackedReason})][{bundleName}][{moduleName}][{thisInstanceId}]: window {status}`

  Fields in the log
  | Field| Type| Typical Value| Description|
  | ---- | ---- | ---- | ---- |
  |{currentId}| Integer| -1 | Context instance ID. If the application is normal, the value of this field is a negative number.|
  |{trackedId}| Integer| 100000  | ID of the instance that can be indirectly traced. The value is usually a positive number. You can ignore it.|
  |{trackedReason}| String| singleton | Reason for indirect tracing. You can ignore this field.|
  |{bundleName}| String| com.example.helloworld| Bundle name of the application.|
  |{moduleName}| String| entry| Module name of the current module.|
  |{thisInstanceId}| Positive number| 100000 | Notified UI instance ID.|
  |{status}| Status of the notified instance.| focus | The options are as follows:<br> - **focus**: focused<br> - **unfocus**: unfocused<br> - **foreground**: foreground<br> - **background**: background<br> - **destroy**: destroyed|

  Use this regular expression to match relevant logs:

  `\(-?\d+:-?\d+:(scope|active|default|singleton|foreground|undefined)\)\] \[[a-z0-9.]+\]\[[a-zA-Z][0-9a-zA-Z_.]*\]\[\d+\]: window (focus|unfocus|foreground|background|destroy)`

  **Example Analysis**

  - Normal log:

    `(-2:100000:singleton)] [com.example.helloworld][entry][100000]: window foreground`

  - Abnormal log:

    `(100000:100000:scoped)] [com.example.helloworld][entry][100001]: window background`

    The preceding log indicates that there is an error tracing UI instance whose ID is 100000.

  - Destruction log:

    `(-2:100000:singleton)] [com.example.helloworld][entry][100000]: window destroy`

    The UI instance whose ID is 100000 has been destroyed, and subsequent UI operations may be affected by its context.

## Resolving Display Abnormalities from UIContext Errors

**Symptom**

The following situations may occur:
1. When the [setStyledString](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#setstyledstring12) method is used to set the font size, the font size does not change as expected.
2. When the UIContext member method is used, the UI does not respond or is displayed abnormally.

**Solution**

Obtain a valid UIContext object using one of these methods:
- Use the [getUIContext](../reference/apis-arkui/arkui-ts/ts-custom-component-api.md#getuicontext) method of the custom component.
- Use the [getUIContext](../reference/apis-arkui/arkts-apis-window-Window.md#getuicontext10) method of the window.
