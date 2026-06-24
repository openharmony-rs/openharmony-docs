# UIContext

UIContext实例对象。

> **说明：**

> - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。
>
> - 以下API需要通过对应的UIContext实例调用。获取UIContext分为三种方式，第一种是使用ohos.window中的
> [getUIContext()](../../../../reference/apis-arkui/arkts-apis-window-Window.md#getuicontext10)方法获取UIContext实例，第二种是通过自定
> 义组件内置方法[getUIContext()](../../../../reference/apis-arkui/arkui-ts/ts-custom-component-api.md#getuicontext)获取UIContext
> 实例，第三种是通过UIContext类的静态方法如[getCallingScopeUIContext](arkts-arkui-uicontext-c.md#getCallingScopeUIContext-1)获取UIContext实例。本文中
> UIContext对象以uiContext表示。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addLocalInputEventMonitor

```TypeScript
addLocalInputEventMonitor(eventMask: number, listener: InputEventListener): InputEventMonitor
```

Registers a local input event monitor.
The "Local" in the interface name indicates that the monitor is only valid within the current UIContext,
and does not affect other UIContext instances. Each UIContext maintains its own independent list of monitors.
> **NOTE**
> Performance Warning: Do not perform time-consuming operations in the callback!
> Monitor Object Notes:
> - The returned Monitor object is a unique identifier created by the system.
> - Developers cannot actively construct or forge this object.
> - Must save the returned monitor object reference for subsequent cancellation.
> - It is recommended to use a variable to save it to avoid losing the reference.
> Usage Examples:
> ```typescript
> // Monitor a single event type
> const monitor1 = uiContext.addLocalInputEventMonitor(
> InputEventSubTypeMask.LEFT_MOUSE_DOWN,
> (wrapper: RawInputEventWrapper) => {
> if (wrapper.isMouseEvent()) {
> const mouseEvent = wrapper.asMouseEvent();
> console.log(`Mouse: (${mouseEvent.windowX}, ${mouseEvent.windowY})`);
> return { action: InputEventInterceptAction.CONTINUE }; // Allow event to continue
> }
> return { action: InputEventInterceptAction.BLOCK }; // Block event
> }
> );
> // Monitor multiple event types (using bitwise operations)
> const monitor2 = uiContext.addLocalInputEventMonitor(
> InputEventSubTypeMask.LEFT_MOUSE_DOWN | InputEventSubTypeMask.RIGHT_MOUSE_DOWN,
> (wrapper: RawInputEventWrapper) => {
> if (wrapper.isMouseEvent()) {
> const mouseEvent = wrapper.asMouseEvent()!;
> console.log(`Mouse button: ${mouseEvent.button}`);
> return { action: InputEventInterceptAction.BLOCK };
> }
> return { action: InputEventInterceptAction.CONTINUE };
> }
> );
> // When unregistering the monitor, use the returned Monitor object
> uiContext.removeLocalInputEventMonitor(monitor1);
> uiContext.removeLocalInputEventMonitor(monitor2);
> ```.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventMask | number | 是 | Event type mask, specifying the types of events to monitor through<br/>bitwise operations.<br/>The value should be an integer. |
| listener | InputEventListener | 是 | Event listener callback function. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| InputEventMonitor | Unique identifier object for the monitor, used for subsequent<br/>cancellation of registration. |

## animateTo

```TypeScript
animateTo(value: AnimateParam, event: () => void): void
```

提供animateTo接口，用于为闭包代码中的状态变化添加过渡动画效果。

> **说明：**
>
> - 不推荐在aboutToAppear、aboutToDisappear中调用动画。
>
> - 如果在[aboutToAppear](../../../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoappear)中调用动
> 画，自定义组件内的build还未执行，内部组件还未创建，动画时机过早，动画属性没有初值无法对组件产生动画。
>
> - 执行[aboutToDisappear](../../../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttodisappear)
> 时，组件即将销毁，不能在aboutToDisappear里面做动画。
>
> - 在组件出现和消失时，可以通过[组件内转场](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)添加动画效果。
>
> - 组件内转场不支持的属性，可以参考[显式动画](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)中的
> [示例2](../../../../reference/apis-arkui/arkui-ts/ts-explicit-animation.md#示例2动画执行结束后组件消失)，使用animateTo实现动画执行结束后组件消失的效
> 果。
>
> - 某些场景下，在[状态管理V2](../../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)中使用animateTo动画，会产生异常效果，
> 具体可参考：[在状态管理V2中使用animateTo动画效果异常](../../../../ui/state-management/arkts-new-local.md#在状态管理v2中使用animateto动画效果异常)。
>
> - UIAbility从前台切换至后台时会立即结束仍在步进中的有限循环动画，从而触发动画播放完成回调[onFinish](arkts-arkui-common-animateparam-i.md#AnimateParam)。
>
> - 在设置的开发者选项中关闭过渡动画，动画会当帧结束，onFinish动画播放完成回调会立即执行，请避免在回调中加入时序相关的功能逻辑。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | AnimateParam | 是 | 设置动画效果相关参数。 |
| event | () =&gt; void | 是 | 指定显示动效的闭包函数，在闭包函数中导致的状态变化系统会自动插入过渡动画。 |

## bindTabsToNestedScrollable

```TypeScript
bindTabsToNestedScrollable(tabsController: TabsController, parentScroller: Scroller, childScroller: Scroller): void
```

Bind tabs to nested scrollable container components to automatically hide tab bar.

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tabsController | TabsController | 是 | The controller of the tabs. |
| parentScroller | Scroller | 是 | The controller of the parent scrollable container component. |
| childScroller | Scroller | 是 | The controller of the child scrollable container component. |

## bindTabsToScrollable

```TypeScript
bindTabsToScrollable(tabsController: TabsController, scroller: Scroller): void
```

Bind tabs to scrollable container component to automatically hide tab bar.

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tabsController | TabsController | 是 | The controller of the tabs. |
| scroller | Scroller | 是 | The controller of the scrollable container component. |

## closeBindSheet

```TypeScript
closeBindSheet<T extends Object>(bindSheetContent: ComponentContent<T>): Promise<void>
```

关闭bindSheetContent对应的半模态页面，使用Promise异步回调。

> **说明：**
>
> 使用此接口关闭半模态页面时，不会触发shouldDismiss回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bindSheetContent | ComponentContent&lt;T&gt; | 是 | 半模态页面中显示的组件内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [120001](../../errorcode-universal.md#120001-The) | The bindSheetContent is incorrect. |
| [120003](../../errorcode-universal.md#120003-The) | The bindSheetContent cannot be found. |

## constructor

```TypeScript
constructor()
```

构造UIContext对象。

> **说明：**
>
> 通过构造函数创建的UIContext对象指向不明确的UI上下文，即不指向任何UI实例。该UIContext对应实例的唯一标识ID为-1。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## createAnimator

```TypeScript
createAnimator(options: AnimatorOptions): AnimatorResult
```

定义Animator类。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | AnimatorOptions | 是 | 定义动画选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AnimatorResult | Animator结果接口。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |

## createAnimator

```TypeScript
createAnimator(options: AnimatorOptions | SimpleAnimatorOptions): AnimatorResult
```

创建animator动画结果对象（AnimatorResult）。与[createAnimator](arkts-arkui-uicontext-c.md#createAnimator-1)相比，新增对
[SimpleAnimatorOptions](arkts-arkui-simpleanimatoroptions-c.md#SimpleAnimatorOptions)类型入参的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | AnimatorOptions \| SimpleAnimatorOptions | 是 | 定义动画选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AnimatorResult | Animator结果接口。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |

## createUIContextWithoutWindow

```TypeScript
static createUIContextWithoutWindow(context: common.UIAbilityContext | common.ExtensionContext) : UIContext | undefined
```

创建一个不依赖窗口的UI实例，并返回其UI上下文。该接口所创建的UI实例是单例。

> **说明：**
>
> 返回的UI上下文只可用于创建[自定义节点](../../../../ui/arkts-user-defined-node.md)，不能执行其他UI操作。

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | common.UIAbilityContext \| common.ExtensionContext | 是 | * [UIAbility](../../apis-ability-kit/arkts-apis/arkts-app-ability-uiability.md)或<br/>[ExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-extensionability-c.md#ExtensionAbility)所对应的上下文环境。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| UIContext | Context of the created UI instance, or **undefined** if creation fails. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. The number of parameters is incorrect.<br/><br/>2. Invalid parameter type of context. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |

## destroyUIContextWithoutWindow

```TypeScript
static destroyUIContextWithoutWindow(): void
```

销毁[createUIContextWithoutWindow](arkts-arkui-uicontext-c.md#createUIContextWithoutWindow-1)创建的UI实例。

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dispatchKeyEvent

```TypeScript
dispatchKeyEvent(node: number | string, event: KeyEvent): boolean
```

Dispach keyboard event to the frameNode with inspector key.

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | number \| string | 是 | The uniqueId or inspector key of the target FrameNode. |
| event | KeyEvent | 是 | The key event to be sent. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns whether the key event is consumed. |

## enableEventPassthrough

```TypeScript
enableEventPassthrough(enabled: boolean, eventType: RawInputEventType): void
```

Whether to enable or disable event passthrough.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | enable or disable event passthrough. The default value is false. |
| eventType | RawInputEventType | 是 | the type of raw input event. |

## enableSwipeBack

```TypeScript
enableSwipeBack(enabled: Optional<boolean>): void
```

whether to enable or disable swipe to back event.

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | Optional&lt;boolean&gt; | 是 | enable or disable swipe to back event. |

## fp2px

```TypeScript
fp2px(value: number): number
```

Converts a value in fp units to a value in px.

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | @syscap SystemCapability.ArkUI.ArkUI.Full<br/>@stagemodelonly<br/>@crossplatform<br/>@atomicservice |

## getAllUIContexts

```TypeScript
static getAllUIContexts(): UIContext[]
```

获取所有当前有效的UIContext实例。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| UIContext[] | Array of all currently valid UIContext instances. Returns an empty array if no valid<br/>UIContext instance exists. |

## getAtomicServiceBar

```TypeScript
getAtomicServiceBar(): Nullable<AtomicServiceBar>
```

Get AtomicServiceBar.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Nullable&lt;AtomicServiceBar&gt; | The atomic service bar. |

## getAttachedFrameNodeById

```TypeScript
getAttachedFrameNodeById(id: string): FrameNode | null
```

通过组件的id获取当前窗口上的实体节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 节点对应的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FrameNode | The instance of FrameNode. |

## getCallingScopeUIContext

```TypeScript
static getCallingScopeUIContext(): UIContext | undefined
```

获取当前[调用作用域](../../../../ui/arkts-global-interface.md#基本概念)的UIContext，调用作用域不明确时返回undefined。

> **说明：**
>
> 返回的UIContext对象可能指向一个已销毁的UI实例，通常在由已销毁的实例抛出异步任务时出现。建议通过[isAvailable](arkts-arkui-uicontext-c.md#isAvailable-1)接口判断其有效性。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| UIContext | UIContext of the current<br/>[calling scope](../../../../ui/arkts-global-interface.md#basic-concepts). Returns **undefined** if the calling<br/>scope is ambiguous. |

## getComponentSnapshot

```TypeScript
getComponentSnapshot(): ComponentSnapshot
```

Get ComponentSnapshot.

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ComponentSnapshot | the ComponentSnapshot |

## getComponentUtils

```TypeScript
getComponentUtils(): ComponentUtils
```

get object ComponentUtils.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ComponentUtils | object ComponentUtils. |

## getContextMenuController

```TypeScript
getContextMenuController(): ContextMenuController
```

Get object context menu controller.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ContextMenuController | object context menu controller. |

## getCursorController

```TypeScript
getCursorController(): CursorController
```

Get object cursor controller.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| CursorController | object cursor controller. |

## getDragController

```TypeScript
getDragController(): DragController
```

Get DragController.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DragController | the DragController |

## getFilteredInspectorTree

```TypeScript
getFilteredInspectorTree(filters?: Array<string>): string
```

get the filtered attributes of the component tree.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filters | Array&lt;string&gt; | 否 | the list of filters used to filter out component tree to be obtained. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the specified attributes of the component tree in json string. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |

## getFilteredInspectorTreeById

```TypeScript
getFilteredInspectorTreeById(id: string, depth: number, filters?: Array<string>): string
```

get the filtered attributes of the component tree with the specified id and depth

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | ID of the specified component tree to be obtained. |
| depth | number | 是 | depth of the component tree to be obtained. |
| filters | Array&lt;string&gt; | 否 | the list of filters used to filter out component tree to be obtained. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the specified attributes of the component tree in json string. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |

## getFocusController

```TypeScript
getFocusController(): FocusController
```

Get FocusController.

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FocusController | the FocusController |

## getFont

```TypeScript
getFont(): Font
```

get object font.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Font | object Font. |

## getFrameNodeById

```TypeScript
getFrameNodeById(id: string): FrameNode | null
```

通过组件的id获取组件树的实体节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 节点对应的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FrameNode | The instance of FrameNode. |

## getFrameNodeByUniqueId

```TypeScript
getFrameNodeByUniqueId(id: number): FrameNode | null
```

提供getFrameNodeByUniqueId接口通过组件的uniqueId获取组件树的实体节点。

1. 当uniqueId对应的是系统组件时，返回组件所对应的FrameNode；
2. 当uniqueId对应的是自定义组件时：
- 若其有渲染内容，且没有被[@Reusable装饰器](../../../../ui/state-management/arkts-reusable.md)修饰时，返回该自定义组件的根节点，类型为__Common__。
- 若其无渲染内容，或者被[@Reusable装饰器](../../../../ui/state-management/arkts-reusable.md)修饰时，在该自定义组件的子组件创建完成前调用此接口，将返回null；在该自定义组件的子组件创建完成后调用，返回其第一个子组件的FrameNode。
3. 当uniqueId无对应的组件时，返回null。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 节点对应的UniqueId |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FrameNode | - The FrameNode with the target uniqueId, or null if the frameNode is not existed. |

## getHostContext

```TypeScript
getHostContext(): Context | undefined
```

获得当前元能力的Context。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Context | Context of the ability. The context type depends on the ability type. For example,<br/>if this API is called in a page within a UIAbility window, the returned context type is<br/>[UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md#UIAbilityContext). If this API is called in a page within an<br/>ExtensionAbility window, the returned context type is<br/>[ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md#ExtensionContext). If the ability context does not exist,<br/>**undefined** is returned. |

## getId

```TypeScript
getId(): number
```

获取UI实例对象唯一标识，多实例场景下，开发者可使用此唯一标识区分多个UI实例对象，便于管理。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 后端实例的唯一标识。取值范围为[-1, +∞)。 |

## getKeyboardAvoidMode

```TypeScript
getKeyboardAvoidMode(): KeyboardAvoidMode
```

Obtains the avoidance mode of the virtual keyboard.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| KeyboardAvoidMode | Avoidance mode of the virtual keyboard. |

## getLastFocusedUIContext

```TypeScript
static getLastFocusedUIContext(): UIContext | undefined
```

获取最近一次切换到获焦状态的UI实例的UIContext。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| UIContext | UIContext of the UI instance that most recently switched to the focused state.<br/>Returns **undefined** if the most recently focused instance has been destroyed or if no instance has ever been<br/>focused. |

## getLastForegroundUIContext

```TypeScript
static getLastForegroundUIContext(): UIContext | undefined
```

获取最近一次切换到前台状态的UI实例的UIContext。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| UIContext | UIContext of the UI instance that most recently switched to the foreground<br/>state. Returns **undefined** if the most recently foreground UI instance has been destroyed or if no UI<br/>instance has ever been in the foreground. |

## getMagnifier

```TypeScript
getMagnifier(): Magnifier
```

Obtains the Magnifier object.

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Magnifier | Magnifier instance obtained. |

## getMaxFontScale

```TypeScript
getMaxFontScale(): number
```

Get the max font scale.

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | The max font scale. |

## getMeasureUtils

```TypeScript
getMeasureUtils(): MeasureUtils
```

Get MeasureUtils.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| MeasureUtils | the MeasureUtils |

## getMediaQuery

```TypeScript
getMediaQuery(): MediaQuery
```

get object mediaQuery.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| MediaQuery | object MediaQuery. |

## getNavigationInfoByUniqueId

```TypeScript
getNavigationInfoByUniqueId(id: number): observer.NavigationInfo | undefined
```

Get navigation information of the frameNode with uniqueId.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | The uniqueId of the target FrameNode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| observer.NavigationInfo | - The navigation information of the frameNode with the<br/>target uniqueId, or undefined if the frameNode is not existed or does not have navigation information. |

## getOverlayManager

```TypeScript
getOverlayManager(): OverlayManager
```

Obtains the OverlayManager object.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| OverlayManager | OverlayManager instance obtained. |

## getOverlayManagerOptions

```TypeScript
getOverlayManagerOptions(): OverlayManagerOptions
```

Get object OverlayManagerOptions.

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| OverlayManagerOptions | object OverlayManagerOptions. |

## getPageInfoByUniqueId

```TypeScript
getPageInfoByUniqueId(id: number): PageInfo
```

Get page information of the frameNode with uniqueId.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | The uniqueId of the target FrameNode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PageInfo | - The page information of the frameNode with the target uniqueId, includes<br/>navDestination and router page information. If the frame node does not have navDestination and<br/>router page information, it will return an empty object. |

## getPageRootNode

```TypeScript
getPageRootNode(): FrameNode | null
```

获取UIContext对应页面的根节点。

**起始版本：** 24

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FrameNode | FrameNode of the root node of the page or **null**.<br/><br/>If no valid FrameNode is available, **null** is returned.<br/><br/>If no page is loaded in the window, **null** is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [120007](../../errorcode-universal.md#120007-The) | The UIContext is not available. |

## getPixelRoundMode

```TypeScript
getPixelRoundMode(): PixelRoundMode
```

Obtains the pixel rounding mode for this page.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelRoundMode | Pixel rounding mode of the current page. |

## getPromptAction

```TypeScript
getPromptAction(): PromptAction
```

Obtains a PromptAction object.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PromptAction | PromptAction object. |

## getRouter

```TypeScript
getRouter(): Router
```

Obtains a Router object.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Router | Router object. |

## getSharedLocalStorage

```TypeScript
getSharedLocalStorage(): LocalStorage | undefined
```

获取当前stage共享的LocalStorage实例。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| LocalStorage | **LocalStorage** instance if it exists; **undefined** if it does not exist. |

## getSmartGestureController

```TypeScript
getSmartGestureController(): SmartGestureController
```

Get object smart gesture controller.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SmartGestureController | object smart gesture controller. |

## getTextMenuController

```TypeScript
getTextMenuController(): TextMenuController
```

Get object text menu controller.

**起始版本：** 16

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TextMenuController | object text menu controller. |

## getUIInspector

```TypeScript
getUIInspector(): UIInspector
```

get object UIInspector.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| UIInspector | object UIInspector. |

## getUIObserver

```TypeScript
getUIObserver(): UIObserver
```

获取UIObserver对象。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| UIObserver | 返回UIObserver实例对象。 |

## getWindowHeightBreakpoint

```TypeScript
getWindowHeightBreakpoint(): HeightBreakpoint
```

获取当前实例所在窗口的高度断点。具体枚举值根据窗口高宽比确定，详见 [HeightBreakpoint](arkts-arkui-enums-heightbreakpoint-e.md#HeightBreakpoint)。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| HeightBreakpoint | 当前实例所在窗口的宽高比对应的高度断点枚举值。若窗口高宽比为0，则返回HEIGHT_SM。 |

## getWindowId

```TypeScript
getWindowId(): number | undefined
```

获取当前应用实例所属的窗口ID。

> **说明：**
>
> 若UIContext位于主应用程序进程中的[UIExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-uiextensionability-c.md#UIExtensionAbility)内，则返回主应用程
> 序的顶层窗口ID。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | ID of the window to which the current application instance belongs. If the window<br/>does not exist, **undefined** is returned. |

## getWindowName

```TypeScript
getWindowName(): string | undefined
```

获取当前实例所在窗口的名称。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Name of the window where the current instance is located. If the window does not<br/>exist, **undefined** is returned. |

## getWindowWidthBreakpoint

```TypeScript
getWindowWidthBreakpoint(): WidthBreakpoint
```

获取当前实例所在窗口的宽度断点枚举值。具体枚举值根据窗口宽度vp值确定，详见 [WidthBreakpoint](arkts-arkui-enums-widthbreakpoint-e.md#WidthBreakpoint)。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| WidthBreakpoint | 当前实例所在窗口的宽度断点枚举值。若窗口宽度为 0vp，则返回WIDTH_XS。 |

## isAvailable

```TypeScript
isAvailable(): boolean
```

判断UIContext对象对应的UI实例是否有效。使用
[getUIContext](../../../../reference/apis-arkui/arkts-apis-window-Window.md#getuicontext10)方法获取UIContext对象。后端UI实例存在时，
该UI实例有效。通过new UIContext()创建的UIContext对象无对应的UI实例；多次
[loadContent](../../../../reference/apis-arkui/arkts-apis-window-Window.md#loadcontent9)后，旧的UI实例会失效。多窗口应用场景，当窗口关闭后，该窗
口的UI实例失效。总而言之，当UIContext对象没有对应的后端UI实例时，该对象是无效的。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回UIContext对象对应的UI实例是否有效。true表示有效，false表示无效。 |

## isEasySplit

```TypeScript
isEasySplit(): boolean
```

Checks whether the current UI instance is in easy split mode.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the current UI instance is in easy split mode; returns false otherwise. |

## isFollowingSystemFontScale

```TypeScript
isFollowingSystemFontScale(): boolean
```

Checks whether current font scale follows the system.

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if current font scale follows the system; returns false otherwise. |

## keyframeAnimateTo

```TypeScript
keyframeAnimateTo(param: KeyframeAnimateParam, keyframes: Array<KeyframeState>): void
```

产生关键帧动画。该接口的使用说明请参考[keyframeAnimateTo](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | KeyframeAnimateParam | 是 | 关键帧动画的整体动画参数。 |
| keyframes | Array&lt;KeyframeState&gt; | 是 | 所有的关键帧状态的列表。 |

## lpx2px

```TypeScript
lpx2px(value: number): number
```

Converts a value in lpx units to a value in px.

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | @syscap SystemCapability.ArkUI.ArkUI.Full<br/>@stagemodelonly<br/>@crossplatform<br/>@atomicservice |

## openBindSheet

```TypeScript
openBindSheet<T extends Object>(bindSheetContent: ComponentContent<T>, sheetOptions?: SheetOptions, targetId?: number): Promise<void>
```

创建并弹出以bindSheetContent作为内容的半模态页面，使用Promise异步回调。通过该接口弹出的半模态页面样式完全按照bindSheetContent中设置的样式显示。

> **说明：**
>
> 1. 使用该接口时，若未传入有效的targetId，则不支持设置SheetOptions.preferType为POPUP模式、不支持设置SheetOptions.mode为EMBEDDED模式。
>
> 2. 由于[updateBindSheet](arkts-arkui-uicontext-c.md#updateBindSheet-1)和[closeBindSheet](arkts-arkui-uicontext-c.md#closeBindSheet-1)依赖
> bindSheetContent去更新或者关闭指定的半模态页面，开发者需自行维护传入的bindSheetContent。
>
> 3. 不支持设置SheetOptions.UIContext。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bindSheetContent | ComponentContent&lt;T&gt; | 是 | 半模态页面中显示的组件内容。 |
| sheetOptions | SheetOptions | 否 | 半模态页面样式。<br/>**说明：**<br/>1. 不支持设置SheetOptions.uiContext，该属性的值固定为当前实例的<br/>UIContext。<br/>2. 若不传递targetId，则不支持设置SheetOptions.preferType为POPUP样式，若设置了POPUP样式则使用CENTER样式替代。<br/>3. 若不传递<br/>targetId，则不支持设置SheetOptions.mode为EMBEDDED模式，默认为OVERLAY模式。<br/>4. 其余属性的默认值参考[SheetOptions](arkts-arkui-common-sheetoptions-i.md#SheetOptions)文<br/>档。 |
| targetId | number | 否 | 需要绑定组件的ID，若不指定则不绑定任何组件。id不存在时返回错误码120004。在传入undefined时返回错误码401。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [120001](../../errorcode-universal.md#120001-The) | The bindSheetContent is incorrect. |
| [120002](../../errorcode-universal.md#120002-The) | The bindSheetContent already exists. |
| [120004](../../errorcode-universal.md#120004-The) | The targetId does not exist. |
| [120005](../../errorcode-universal.md#120005-The) | The node of targetId is not in the component tree. |
| [120006](../../errorcode-universal.md#120006-The) | The node of targetId is not a child of the page node or NavDestination node. |

## postDelayedFrameCallback

```TypeScript
postDelayedFrameCallback(frameCallback: FrameCallback, delayTime: number): void
```

注册一个回调，在延迟一段时间后的下一帧进行渲染时执行。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| frameCallback | FrameCallback | 是 | 下一帧需要执行的回调。 |
| delayTime | number | 是 | 延迟的时间，以毫秒为单位。传入null、undefined或小于0的值，会按0处理。 |

## postFrameCallback

```TypeScript
postFrameCallback(frameCallback: FrameCallback): void
```

注册一个回调，仅在下一帧渲染时调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| frameCallback | FrameCallback | 是 | 下一帧需要执行的回调。 |

## px2fp

```TypeScript
px2fp(value: number): number
```

Converts a value in px units to a value in fp.

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | @syscap SystemCapability.ArkUI.ArkUI.Full<br/>@stagemodelonly<br/>@crossplatform<br/>@atomicservice |

## px2lpx

```TypeScript
px2lpx(value: number): number
```

Converts a value in px units to a value in lpx.

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | @syscap SystemCapability.ArkUI.ArkUI.Full<br/>@stagemodelonly<br/>@crossplatform<br/>@atomicservice |

## px2vp

```TypeScript
px2vp(value: number): number
```

Converts a value in px units to a value in vp.

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | @syscap SystemCapability.ArkUI.ArkUI.Full<br/>@stagemodelonly<br/>@crossplatform<br/>@atomicservice |

## removeLocalInputEventMonitor

```TypeScript
removeLocalInputEventMonitor(monitor: InputEventMonitor): void
```

Removes a local input event monitor.

**Important Notes**:
- Only Monitor objects returned by addLocalInputEventMonitor can be removed.
- Cannot unregister a monitor by manually constructing an object.
- If an invalid object is passed, the system silently ignores it.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| monitor | InputEventMonitor | 是 | Monitor identifier object (returned by addLocalInputEventMonitor). |

## requireDynamicSyncScene

```TypeScript
requireDynamicSyncScene(id: string): Array<DynamicSyncScene>
```

Require DynamicSyncScene by id.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | The id of DynamicSyncScene. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;DynamicSyncScene&gt; | The instance of SwiperDynamicSyncScene. |

## resolveUIContext

```TypeScript
static resolveUIContext(): ResolvedUIContext
```

使用优先级策略获取带有解析策略的UIContext实例对象。

> **说明：**
>
> 按照预定义的优先级顺序解析并返回UIContext实例和UIContext的解析策略。
>
> 解析规则按顺序如下：
>
> 1. 当前调用作用域中的UIContext。
>
> 2. 如果只存在一个UI实例，则返回其UIContext。
>
> 3. 如果存在UI实例切换到获焦状态，且最近一次切换到获焦状态的UI实例未销毁，则返回最近一次获焦UI实例的UIContext。
>
> 4. 如果存在UI实例切换到前台状态，且最近一次切换到前台状态的UI实例未销毁，则返回最近一次切换到前台状态的UI实例的UIContext。
>
> 5. 如果存在多个UI实例，则返回实例唯一标识的ID最大的UIContext。
>
> 6. 如果以上条件均不满足，则返回一个无效的UIContext实例。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ResolvedUIContext | 返回带有解析策略的UIContext实例对象。 |

## runScopedTask

```TypeScript
runScopedTask(callback: () => void): void
```

在当前UI上下文执行传入的回调函数。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; void | 是 | 回调函数 |

## setCustomKeyboardContinueFeature

```TypeScript
setCustomKeyboardContinueFeature(feature: CustomKeyboardContinueFeature): void
```

Set custom keyboard continue feature.

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| feature | CustomKeyboardContinueFeature | 是 | The custom keyboard continue feature. |

## setImageCacheCount

```TypeScript
setImageCacheCount(value: number): void
```

Set image cache capacity of decoded image count.
if not set, the application will not cache any decoded image.

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | capacity of decoded image count. |

## setImageRawDataCacheSize

```TypeScript
setImageRawDataCacheSize(value: number): void
```

Set image cache capacity of raw image data size in bytes before decode.
if not set, the application will not cache any raw image data.

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | capacity of raw image data size in bytes. |

## setKeyboardAvoidMode

```TypeScript
setKeyboardAvoidMode(value: KeyboardAvoidMode): void
```

Sets the avoidance mode for the virtual keyboard.

> **NOTE**
>
> With **KeyboardAvoidMode.RESIZE**, the page is resized to prevent the virtual keyboard from obstructing the
> view. Regarding components on the page, those whose width and height are set in percentage are resized with the
> page, and those whose width and height are set to specific values are laid out according to their settings.
> With **KeyboardAvoidMode.RESIZE**, **expandSafeArea([SafeAreaType.KEYBOARD],[SafeAreaEdge.BOTTOM])** does not
> take effect.
>
> With **KeyboardAvoidMode.NONE**, keyboard avoidance is disabled, and the page will be covered by the displayed
> keyboard.
>
> **setKeyboardAvoidMode** only affects page layouts. It does not apply to popup components, including the
> following: **Dialog**, **Popup**, **Menu**, **BindSheet**, **BindContentCover**, **Toast**, **OverlayManager**.
> For details about the avoidance mode of popup components, see
> [CustomDialogControllerOptions](../../../../reference/arkui-ts/ts-methods-custom-dialog-box.md).

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | KeyboardAvoidMode | 是 | Avoidance mode of the virtual keyboard.<br/>Default value:<br/>**KeyboardAvoidMode.OFFSET**, which means that the page moves up when the keyboard is displayed.<br/>When<br/>**setKeyboardAvoidMode** is set to an invalid value, this attribute does not take effect. |

## setOverlayManagerOptions

```TypeScript
setOverlayManagerOptions(options: OverlayManagerOptions): boolean
```

Init OverlayManager.

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | OverlayManagerOptions | 是 | Options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if it is called first and before getting an OverlayManager instance; returns false otherwise. |

## setPixelRoundMode

```TypeScript
setPixelRoundMode(mode: PixelRoundMode): void
```

Sets the pixel rounding mode for this page.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | PixelRoundMode | 是 | Pixel rounding mode.<br/>Default value:**PixelRoundMode.PIXEL_ROUND_ON_LAYOUT_FINISH**.<br/>If this parameter is set to an invalid value,<br/>the default value will be used. |

## setResourceManagerCacheMaxCountForHSP

```TypeScript
static setResourceManagerCacheMaxCountForHSP(count: number): void
```

Set the upper limit for the cache count of HSP resource management objects.

If the upper limit of the cache is set too high, there is a risk of excessive memory overhead.
It is recommended to configure it according to actual needs.

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | number | 是 | The cache limit of resource manager for HSP, must be non negative integers. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100101](../../errorcode-universal.md#100101-The) | The parameter is less than 0. |
| [100102](../../errorcode-universal.md#100102-The) | The parameter value cannot be a floating point number. |
| [100103](../../errorcode-universal.md#100103-The) | The function cannot be called from a non main thread.<br/>@static |

## setTextSelectionClearPolicy

```TypeScript
setTextSelectionClearPolicy(policy: TextSelectionClearPolicy): void
```

Sets the text selection clear policy for text component.
Default policy: **TextSelectionClearPolicy.KEEP_SELECTED_TEXT_ON_EXTERNAL_TOUCH**

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| policy | TextSelectionClearPolicy | 是 | The text selection clear policy. |

## showActionSheet

```TypeScript
showActionSheet(value: ActionSheetOptions): void
```

Shows an action sheet in the given settings.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ActionSheetOptions | 是 | Parameters of the action sheet. |

## showAlertDialog

```TypeScript
showAlertDialog(options: AlertDialogParamWithConfirm | AlertDialogParamWithButtons | AlertDialogParamWithOptions): void
```

Shows an alert dialog box.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | AlertDialogParamWithConfirm \| AlertDialogParamWithButtons \| AlertDialogParamWithOptions | 是 | Shows<br/>an AlertDialog component in the given settings. |

## showDatePickerDialog

```TypeScript
showDatePickerDialog(options: DatePickerDialogOptions): void
```

datePickerDialog display.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | DatePickerDialogOptions | 是 | Options. |

## showTextPickerDialog

```TypeScript
showTextPickerDialog(options: TextPickerDialogOptions): void
```

textPickerDialog display.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | TextPickerDialogOptions | 是 | Options. |

## showTextPickerDialog

```TypeScript
showTextPickerDialog(style: TextPickerDialogOptions | TextPickerDialogOptionsExt): void
```

textPickerDialog display.

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | TextPickerDialogOptions \| TextPickerDialogOptionsExt | 是 | Dialog style. |

## showTimePickerDialog

```TypeScript
showTimePickerDialog(options: TimePickerDialogOptions): void
```

timePickerDialog display.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | TimePickerDialogOptions | 是 | Options. |

## unbindTabsFromNestedScrollable

```TypeScript
unbindTabsFromNestedScrollable(tabsController: TabsController, parentScroller: Scroller, childScroller: Scroller): void
```

Unbind tabs from nested scrollable container components.

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tabsController | TabsController | 是 | The controller of the tabs. |
| parentScroller | Scroller | 是 | The controller of the parent scrollable container component. |
| childScroller | Scroller | 是 | The controller of the child scrollable container component. |

## unbindTabsFromScrollable

```TypeScript
unbindTabsFromScrollable(tabsController: TabsController, scroller: Scroller): void
```

Unbind tabs from scrollable container component.

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tabsController | TabsController | 是 | The controller of the tabs. |
| scroller | Scroller | 是 | The controller of the scrollable container component. |

## updateBindSheet

```TypeScript
updateBindSheet<T extends Object>(bindSheetContent: ComponentContent<T>, sheetOptions: SheetOptions, partialUpdate?: boolean): Promise<void>
```

更新bindSheetContent对应的半模态页面的样式，使用Promise异步回调。

> **说明：**
>
> 不支持更新SheetOptions.UIContext、SheetOptions.mode、回调函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bindSheetContent | ComponentContent&lt;T&gt; | 是 | 半模态页面中显示的组件内容。 |
| sheetOptions | SheetOptions | 是 | 半模态页面样式。<br/>**说明：**<br/>不支持更新SheetOptions.uiContext、SheetOptions.mode、回调函<br/>数。 |
| partialUpdate | boolean | 否 | 半模态页面更新方式, 默认值为false。<br/>**说明：**<br/>1. true为增量更新，保留当前值，更新SheetOptions中的指定属性。<br/><br/>2. false为全量更新，除SheetOptions中的指定属性，其他属性恢复默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [120001](../../errorcode-universal.md#120001-The) | The bindSheetContent is incorrect. |
| [120003](../../errorcode-universal.md#120003-The) | The bindSheetContent cannot be found. |

## vp2px

```TypeScript
vp2px(value: number): number
```

Converts a value in vp units to a value in px.

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | @syscap SystemCapability.ArkUI.ArkUI.Full<br/>@stagemodelonly<br/>@crossplatform<br/>@atomicservice |

