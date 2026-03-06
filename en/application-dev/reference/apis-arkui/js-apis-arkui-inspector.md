# @ohos.arkui.inspector (Layout Callback)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

The **Inspector** module provides APIs for registering the component layout and drawing completion callbacks.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

<!--deprecated_code_no_check-->
```ts
import { inspector } from '@kit.ArkUI';
```

## inspector.createComponentObserver<sup>(deprecated)</sup>

createComponentObserver(id: string): ComponentObserver

Binds to the specified component and returns the corresponding observation handle.

> **NOTE**
> 
> - This method has been deprecated since API version 18. You are advised to use the [getUIInspector](arkts-apis-uicontext-uicontext.md#getuiinspector) method in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [UIInspector](arkts-apis-uicontext-uiinspector.md) instance, and then use the instance to call the substitute method [createComponentObserver](arkts-apis-uicontext-uiinspector.md#createcomponentobserver).
>
> - Since API version 10, you can use the [getUIInspector](arkts-apis-uicontext-uicontext.md#getuiinspector) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [UIInspector](arkts-apis-uicontext-uiinspector.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description      |
| ------ | ------ | ---- | ---------- |
| id     | string | Yes  | ID of the target component, set using the universal attributes [id](./arkui-ts/ts-universal-attributes-component-id.md#id) or [key](./arkui-ts/ts-universal-attributes-component-id.md#key12).|

**Return value**

| Type             | Description                                            |
| ----------------- | ------------------------------------------------ |
|[ComponentObserver](#componentobserver)| Component observer handle, which is used to register and unregister callbacks.|

**Example**

```ts
let listener:inspector.ComponentObserver = inspector.createComponentObserver('COMPONENT_ID'); // Listen for callback events for the component whose ID is COMPONENT_ID.
```

## ComponentObserver

Implements an observer for layout and drawing completion callbacks for components, containing the initial query results from when the observer was created.

### on('layout')

on(type: 'layout', callback: () => void): void

Registers a layout completion callback through this handle.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description|
| -------- | ------ | ---- | -------------------------------------|
| type     | string | Yes  | Event type. The value is fixed at **'layout'**.<br>**'layout'**: completion of component layout.|
| callback | () => void   | Yes  | Layout completion callback.|

### off('layout')

off(type: 'layout', callback?: () => void): void

Unregisters the layout completion callback through this handle.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description|
| -------- | ------ | ---- | -------------------------------------------- |
| type     | string | Yes  | Event type. The value is fixed at **'layout'**.<br>**'layout'**: completion of component layout.|
| callback | () => void   | No  | Callback to unregister. If this parameter is not specified, all callbacks under this handle are unregistered. The callback must be the same object as the one registered with the [on('layout')](#onlayout) API to successfully unregister.|

### on('draw')

on(type: 'draw', callback: () => void): void

Registers a drawing completion callback through this handle.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | Yes  | Event type. The value is fixed at **'draw'**.<br>**'draw'**: completion of component drawing.|
| callback | () => void   | Yes  | Drawing completion callback.                                    |

### off('draw')

off(type: 'draw', callback?: () => void): void

Unregisters the drawing completion callback through this handle.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | Yes  | Event type. The value is fixed at **'draw'**.<br>**'draw'**: completion of component drawing.|
| callback | () => void   | No  | Callback to unregister. If this parameter is not specified, all callbacks under this handle are unregistered. The callback must be the same object as the one registered with the [on('draw')](#ondraw) API to successfully unregister.|

### on('drawChildren')<sup>20+</sup>

on(type: 'drawChildren',  callback: Callback\<void\>): void

Registers a child component drawing completion callback through [ComponentObserver](#componentobserver). When multiple **drawChildren** callbacks exist in the component tree, only the topmost callback will be triggered.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | Yes  | Event type. The value is fixed at **'drawChildren'**.<br>**'drawChildren'**: completion of child component drawing.|
| callback | Callback\<void\>  | Yes  | Child component drawing completion callback.                                    |

### off('drawChildren')<sup>20+</sup>

off(type: 'drawChildren', callback?: Callback\<void\>): void

Unregisters the child component drawing completion callback through this handle.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | Yes  | Event type. The value is fixed at **'drawChildren'**.<br>**'drawChildren'**: completion of child component drawing.|
| callback | Callback\<void\>   | No  | Callback to unregister. If this parameter is not specified, all callbacks under this handle are unregistered. The callback must be the same object as the one registered with the [on('drawChildren')20+](#ondrawchildren20) API to successfully unregister.|

### onLayoutChildren<sup>23+</sup>

onLayoutChildren(callback: Callback\<void\>): void

Registers a callback used to listen for the **layoutChildren** event using [ComponentObserver](#componentobserver). This API uses an asynchronous callback to return the result.

When the node that is currently listened is used as the root node and the nodes in the subtree are laid out, this callback is triggered. When multiple **layoutChildren** callbacks exist in the component tree, only the topmost callback will be triggered.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | Callback\<void\>  | Yes  | Callback used to listen for the **layoutChildren** event.                             |

### offLayoutChildren<sup>23+</sup>

offLayoutChildren(callback?: Callback\<void\>): void

Unregisters the callback used to listen for the **layoutChildren** event. This API uses an asynchronous callback to return the result.

To stop triggering a specific callback after the child component layout is complete, you only need to unregister the callback based on the corresponding query condition using its handle.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | Callback\<void\>   | No  | Callback to unregister. If this parameter is not specified, all callbacks under this handle are unregistered. The callback can be successfully unregistered only when it matches the callback in the [onLayoutChildren23+](#onlayoutchildren23) method.|

## Example

The following example demonstrates how to register the component layout and drawing completion callbacks. Since API version 23, the [onLayoutChildren](#onlayoutchildren23) API is available to listen for the layout completion events of nodes in the subtree.

```ts
import { inspector } from '@kit.ArkUI';

@Entry
@Component
struct ImageExample {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row({ space: 5 }) {
          Image($r('app.media.startIcon'))
            .width(110)
            .height(110)
            .border({ width: 1 })
            .id('IMAGE_ID')
        }
        .id('ROW_ID')
      }
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }

  listenerForImage: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('IMAGE_ID')
  listenerForRow: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('ROW_ID')

  aboutToAppear() {
    let onLayoutComplete: () => void = (): void => {
      // Supplement the implementation code as required.
    }
    let onDrawComplete: () => void = (): void => {
      // Supplement the implementation code as required.
    }
    let onDrawChildrenComplete: () => void = (): void => {
      // Supplement the implementation code as required.
    }
    // Bind to the current JS instance.
    let FuncLayout = onLayoutComplete
    let FuncDraw = onDrawComplete
    let FuncDrawChildren = onDrawChildrenComplete
    let OffFuncLayout = onLayoutComplete
    let OffFuncDraw = onDrawComplete
    let OffFuncDrawChildren = onDrawChildrenComplete

    this.listenerForImage.on('layout', FuncLayout)
    this.listenerForImage.on('draw', FuncDraw)
    this.listenerForRow.on('drawChildren', FuncDrawChildren)

    // Unregister callbacks through the handle. You should decide when to call these APIs.
    // this.listenerForImage.off('layout', OffFuncLayout)
    // this.listenerForImage.off('draw', OffFuncDraw)
    // this.listenerForRow.off('drawChildren', OffFuncDrawChildren)
    
    let onLayoutChildrenComplete: () => void = (): void => {
      // After the LayoutChildren event is received, you can customize the implementation logic.
    }
    let uniqueId: number = this.getUniqueId();
    let listenerForUniqueId: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver(uniqueId)
    listenerForUniqueId.onLayoutChildren(onLayoutChildrenComplete)
    // Unregister callbacks through the handle. You should decide when to call these APIs.
    // listenerForUniqueId.offLayoutChildren(onLayoutChildrenComplete)
  }
}
```
