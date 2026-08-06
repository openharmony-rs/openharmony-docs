# FloatViewController

标准悬浮窗控制器实例。用于启动、停止标准悬浮窗以及注册回调等操作。 下列API示例中都需先使用[floatView.create()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_方法获取到标准悬浮窗控制器实例（即floatViewController），再通过此实例调用对应方法。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-floatView-interface FloatViewController--><!--Device-floatView-interface FloatViewController-End-->

**系统能力：** SystemCapability.Window.SessionManager

## getWindowProperties

```TypeScript
getWindowProperties(): FloatViewProperties
```

获取标准悬浮窗窗口的属性。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-getWindowProperties(): FloatViewProperties--><!--Device-FloatViewController-getWindowProperties(): FloatViewProperties-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回标准悬浮窗窗口的属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300031](../errorcode-window.md#1300031-闪控窗状态不支持该操作) | This operation is not supported on the float view in the current state.Possible cause: The float view window has not started, has stopped, or is in an error state. |

## offLimitsChange

```TypeScript
offLimitsChange(callback?: Callback<FloatViewLimits>): void
```

取消标准悬浮窗限制变化的监听事件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-offLimitsChange(callback?: Callback<FloatViewLimits>): void--><!--Device-FloatViewController-offLimitsChange(callback?: Callback<FloatViewLimits>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FloatViewLimits&gt; | 否 | 回调函数。返回当前的标准悬浮窗限制变化信息。若传入参数，则停止该监听。若未传入参数，则停止所有标准悬浮窗限制变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |

## offRectChange

```TypeScript
offRectChange(callback?: Callback<FloatViewRectChangeInfo>): void
```

取消标准悬浮窗矩形区域变化的监听事件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-offRectChange(callback?: Callback<FloatViewRectChangeInfo>): void--><!--Device-FloatViewController-offRectChange(callback?: Callback<FloatViewRectChangeInfo>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FloatViewRectChangeInfo&gt; | 否 | 回调函数。返回当前的标准悬浮窗矩形区域变化信息。若传入参数，则停止该监听。若未传入参数，则停止所有标准悬浮窗矩形区域变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |

## offStateChange

```TypeScript
offStateChange(callback?: Callback<FloatViewStateChangeInfo>): void
```

取消标准悬浮窗状态变化的监听事件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-offStateChange(callback?: Callback<FloatViewStateChangeInfo>): void--><!--Device-FloatViewController-offStateChange(callback?: Callback<FloatViewStateChangeInfo>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FloatViewStateChangeInfo&gt; | 否 | 回调函数。返回当前的标准悬浮窗状态变化信息。若传入参数，则停止该监听。若未传入参数，则停止所有标准悬浮窗状态变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |

## onLimitsChange

```TypeScript
onLimitsChange(callback: Callback<FloatViewLimits>): void
```

注册标准悬浮窗限制变化的监听事件，当限制规格变化时触发回调，例如设备折叠或者展开。不再使用时，取消监听以避免内存泄漏。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-onLimitsChange(callback: Callback<FloatViewLimits>): void--><!--Device-FloatViewController-onLimitsChange(callback: Callback<FloatViewLimits>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FloatViewLimits&gt; | 是 | 回调函数。返回当前的标准悬浮窗限制变化信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300030](../errorcode-window.md#1300030-重复操作闪控窗) | Repeated operations on the float view. Possible cause:The callback has already registered. |

## onRectChange

```TypeScript
onRectChange(callback: Callback<FloatViewRectChangeInfo>): void
```

注册标准悬浮窗矩形区域（位置和大小）变化的监听事件。不再使用时，取消监听以避免内存泄漏。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-onRectChange(callback: Callback<FloatViewRectChangeInfo>): void--><!--Device-FloatViewController-onRectChange(callback: Callback<FloatViewRectChangeInfo>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FloatViewRectChangeInfo&gt; | 是 | 回调函数。返回当前的标准悬浮窗矩形区域变化信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300030](../errorcode-window.md#1300030-重复操作闪控窗) | Repeated operations on the float view. Possible cause:The callback has already registered. |

## onStateChange

```TypeScript
onStateChange(callback: Callback<FloatViewStateChangeInfo>): void
```

注册标准悬浮窗状态变化的监听事件。不再使用时，取消监听以避免内存泄漏。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-onStateChange(callback: Callback<FloatViewStateChangeInfo>): void--><!--Device-FloatViewController-onStateChange(callback: Callback<FloatViewStateChangeInfo>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FloatViewStateChangeInfo&gt; | 是 | 回调函数。返回当前的标准悬浮窗状态变化信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300030](../errorcode-window.md#1300030-重复操作闪控窗) | Repeated operations on the float view. Possible cause:The callback has already registered. |

## restoreMainWindow

```TypeScript
restoreMainWindow(wantParameters?: Record<string, Object>): Promise<void>
```

恢复标准悬浮窗的主窗口到前台显示。如果主窗口已处于前台时调用，将抬升主窗口层级。此接口只能在标准悬浮窗窗口被点击后使用。当主窗口处于PAUSED生命周期或处于多任务状态时，调用接口将抛出错误码1300032。使用Promise 异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-restoreMainWindow(wantParameters?: Record<string, Object>): Promise<void>--><!--Device-FloatViewController-restoreMainWindow(wantParameters?: Record<string, Object>): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wantParameters | Record&lt;string, Object&gt; | 否 | 恢复标准悬浮窗的主窗口时会给主窗口传递的自定义参数，主窗口会在触发[onNewWant]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_回调时收到。默认值为空，代表不向主窗传入任何自定义参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. Possible cause:Internal IPC error. |
| [1300031](../errorcode-window.md#1300031-闪控窗状态不支持该操作) | This operation is not supported on the float view in the current state.Possible cause: The float view window is not started when restoring. |
| [1300032](../errorcode-window.md#1300032-恢复主窗口失败) | Failed to restore the main window. Possible cause:1. User has never clicked the float view window before restore.2. The float view window is not in the foreground.3. The main window is in PAUSED lifecycle state.4. The main window is in background during recent. |

## setFloatViewVisibilityInApp

```TypeScript
setFloatViewVisibilityInApp(isVisible: boolean): Promise<void>
```

设置应用在前台时标准悬浮窗窗口是否可见。使用Promise异步回调。 创建标准悬浮窗后未调用此接口前，默认其在应用处于前台时为可见状态。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-setFloatViewVisibilityInApp(isVisible: boolean): Promise<void>--><!--Device-FloatViewController-setFloatViewVisibilityInApp(isVisible: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isVisible | boolean | 是 | 应用在前台时标准悬浮窗是否可见，true表示可见，false表示不可见。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. Possible cause:Internal IPC error. |

## setUIContext

```TypeScript
setUIContext(path: string, storage?: LocalStorage): Promise<void>
```

根据当前工程中指定的页面路径为标准悬浮窗加载具体页面内容，通过LocalStorage传递状态属性至加载页面。使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-setUIContext(path: string, storage?: LocalStorage): Promise<void>--><!--Device-FloatViewController-setUIContext(path: string, storage?: LocalStorage): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 要加载到窗口中的页面内容的路径，该路径需添加到工程的main\_\_\_ESCAPED\_UNDERSCORE\_\_\_pages.json文件中。不支持相对路径写法，需与main\_\_\_ESCAPED\_UNDERSCORE\_\_\_pages.json中的src取值保持一致。 |
| storage | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 页面级UI状态存储单元，用于为加载到窗口的页面内容传递状态属性。默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300016](../errorcode-window.md#1300016-参数校验错误) | Parameter error. Possible causes: Invalid path. |

## setUIContextByName

```TypeScript
setUIContextByName(name: string, storage?: LocalStorage): Promise<void>
```

根据指定路由页面名称为当前窗口加载\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_页面，通过LocalStorage传递状态属性至加载页面，使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-setUIContextByName(name: string, storage?: LocalStorage): Promise<void>--><!--Device-FloatViewController-setUIContextByName(name: string, storage?: LocalStorage): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 命名路由页面的名称。 |
| storage | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 页面级UI状态存储单元，用于为加载到窗口的页面内容传递状态属性。默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300016](../errorcode-window.md#1300016-参数校验错误) | Parameter error. Possible causes: Invalid name. |

## setWindowSize

```TypeScript
setWindowSize(size: window.Size): Promise<void>
```

设置标准悬浮窗窗口大小。建议先调用[getFloatViewLimits]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口获取推荐的宽高范围和宽高比范围，再根据推荐值调用本接口。窗口实际大小变化可通 过[onRectChange]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口监 听。使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-setWindowSize(size: window.Size): Promise<void>--><!--Device-FloatViewController-setWindowSize(size: window.Size): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | window.Size | 是 | 表示窗口的大小。建议大小满足[getFloatViewLimits]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_接口返回的限制。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. Possible cause:Internal IPC error. |
| [1300016](../errorcode-window.md#1300016-参数校验错误) | Parameter error.Possible cause: The value of the size is less than or equal to 0. |

## start

```TypeScript
start(): Promise<void>
```

启动标准悬浮窗窗口。接口返回不表示start流程结束，需要通过 [onStateChange]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接 口监听到STARTED回调时判断启动成功。建议在调用[setUIContext()]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_或 [setUIContextByName()]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_后调用start()。使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**需要权限：** ohos.permission.FLOAT_VIEW

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-start(): Promise<void>--><!--Device-FloatViewController-start(): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. Possible cause:The application does not have the permission required to call the API. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. Possible cause:Internal IPC error. |
| [1300030](../errorcode-window.md#1300030-重复操作闪控窗) | Repeated operations on the float view. Possible cause:The float view is starting or has already started. |
| [1300031](../errorcode-window.md#1300031-闪控窗状态不支持该操作) | The float view state does not support this operation. Possible cause:The float view is stopping. |
| [1300033](../errorcode-window.md#1300033-启动闪控窗失败) | Failed to start float view. Possible causes:1. Start multiple float views.2. The main window of context is not foreground. |
| [1300034](../errorcode-window.md#1300034-闪控窗与其他悬浮窗口操作冲突) | This operation conflicts with other floating windows. Possible cause:App has already started floating ball or pip window. |

## stop

```TypeScript
stop(): Promise<void>
```

停止标准悬浮窗窗口。接口返回不表示stop流程结束，需要通过 [onStateChange]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接 口监听到STOPPED回调时判断停止成功。使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-stop(): Promise<void>--><!--Device-FloatViewController-stop(): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. Possible cause:Internal IPC error. |
| [1300030](../errorcode-window.md#1300030-重复操作闪控窗) | Repeated operations on the float view. Possible cause:The float view is stopping or has already stopped. |
| [1300031](../errorcode-window.md#1300031-闪控窗状态不支持该操作) | This operation is not supported on the float view in the current state.Possible cause: The float view window is not started. |

## switchTemplate

```TypeScript
switchTemplate(templateProperty: TemplateProperty): Promise<void>
```

切换标准悬浮窗的模板并改变其窗口尺寸。建议先调用[getFloatViewLimits]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口获取目标模板类型推荐的宽高范围和宽高比范围，再根据推荐值调用本 接口。窗口实际大小变化可通过 [onRectChange]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口监听 。使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-switchTemplate(templateProperty: TemplateProperty): Promise<void>--><!--Device-FloatViewController-switchTemplate(templateProperty: TemplateProperty): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| templateProperty | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 表示需要切换的窗口模板类型及大小。建议大小满足[getFloatViewLimits]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_接口返回的限制。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. Possible cause:Internal IPC error. |
| [1300016](../errorcode-window.md#1300016-参数校验错误) | Parameter error. Possible cause:1. Invalid template type.2. The value of the size is less than or equal to 0. |

