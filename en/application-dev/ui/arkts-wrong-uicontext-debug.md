# UI Context Debugging
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
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

  **Table 1** Fields in the instance status update log

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

## Instance Details

Error messages from some instance-related APIs include information about the corresponding instance. Only instances in the cache list will output detailed information. The cache list stores only information about destroyed instances.

> **NOTE**
>
> - The current cache list size is 10, and the least recently used (LRU) mechanism is used for eviction.

### Cache Hit

When an abnormal instance hits the cache, the detailed information is output in the following format:

`DestroyedUIContextCacheInfo: instanceInfo: [instanceId:<instanceId_>, createTime:<createTime_>, destroyTime:<destroyTime_>], windowInfo: [windowId: <windowId_>, windowName: <windowName_>]`

### Cache Miss

When the requested instance does not exist in the cache (either never cached or evicted due to exceeding cache size), the detailed information is output in the following format:

`InstanceId not found in destroyed cache.`

### Full Message Example

Detailed information of a cached destroyed instance is output in the following format, including the instance ID, creation time, destruction time, window ID, and window name fields:

`UI execution context not found.InstanceId: 100001,`

`Reason to get the instance: The instance is determined by the caller,`

`DestroyedUIContextCacheInfo: instanceInfo: [instanceId:100001, createTime:2026-04-14 10:30:00.123, destroyTime:2026-04-14 10:35:22.456], windowInfo: [windowId: 1001, windowName: EntryAbility]`

The parameters in the preceding code are described as follows.

- **instanceId:100001**: indicates that instance 100001 is requested.
- **Reason to get the instance: The instance is determined by the caller**: indicates that the instance ID is explicitly specified by the caller.
- **createTime:2026-04-14 10:30:00.123**: indicates that the instance was created at 10:30 on April 14, 2026.
- **destroyTime:2026-04-14 10:35:22.456**: indicates that the instance was destroyed at 10:35 on April 14, 2026, and it survived for about 5 minutes and 22 seconds.
- **windowId: 1001**: indicates that the ID of the window associated with the instance is 1001.
- **windowName: EntryAbility**: indicates that the name of the window associated with the instance is **EntryAbility**.

**Table 2** Description of fields in a full message

| Field                      | Description                                         |
| -------------------------- | --------------------------------------------- |
| instanceId                 | Instance ID. The value is allocated by the system when the instance is created.             |
| Reason to get the instance | Reason for obtaining the instance. For details, see Table 3.|
| createTime                 | Time when the instance is created.                             |
| destroyTime                | Time when the instance is destroyed.                             |
| windowId                   | ID of the window corresponding to the instance.                         |
| windowName                 | ID of the window corresponding to the instance.                       |

**Table 3** Description of the reasons for instance specification

| Description                                                                                   | Description                                                                                                                    |
| --------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| The instance is determined by the caller.                                               | The instance ID is explicitly specified during the call. Generally, the application specifies the instance ID through the [UIContext](../reference/apis-arkui/arkts-apis-uicontext.md) API.|
| No specific instance was specified, so the most recently active instance was retrieved. | If no instance ID is explicitly specified, the system returns the most recently active instance.                                                                              |
| No specific instance was specified, return the foreground instance.                     | If no instance ID is explicitly specified, the system returns the instance running in the foreground.                                                                                    |
| No specific instance was specified, return the only remaining instance.                 | If no instance ID is explicitly specified, the system returns the only instance (when only one UI instance exists).                                                            |
| No specific instance was specified, using default.                                      | If no instance ID is explicitly specified, the default instance (the last created instance) is used.                                                                      |
| No valid instance exists.                                                               | No valid UI instance exists.                                                                                                    |

## Resolving Display Abnormalities Caused by UIContext Errors

**Symptom**

The following situations may occur:
1. When the [setStyledString](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#setstyledstring12) method is used to set the font size, the font size does not change as expected.
2. When a UIContext member method is used, the UI does not respond or is displayed incorrectly.

**Solution**

Obtain a valid UIContext object using one of these methods:
- Use the [getUIContext](../reference/apis-arkui/arkui-ts/ts-custom-component-api.md#getuicontext) method of the custom component.
- Use the [getUIContext](../reference/apis-arkui/arkts-apis-window-Window.md#getuicontext10) method of the window.
