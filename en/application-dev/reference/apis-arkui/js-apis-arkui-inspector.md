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
> - This API is supported since API version 10 and deprecated since API version 18. You are advised to use [createComponentObserver](arkts-apis-uicontext-uiinspector.md#createcomponentobserver) instead on the obtained [UIInspector](arkts-apis-uicontext-uiinspector.md) object.
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

### on('drawChildren')<sup>20+<sup>

on(type: 'drawChildren',  callback: Callback\<void\>): void

Registers a child component drawing completion callback through [ComponentObserver](#componentobserver). When multiple **drawChildren** callbacks exist in the component tree, only the topmost callback will be triggered.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | Yes  | Event type. The value is fixed at **'drawChildren'**.<br>**'drawChildren'**: completion of child component drawing.|
| callback | Callback\<void\>  | Yes  | Child component drawing completion callback.                                    |

### off('drawChildren')<sup>20+<sup>

off(type: 'drawChildren', callback?: Callback\<void\>): void

Unregisters the child component drawing completion callback through this handle.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | Yes  | Event type. The value is fixed at **'drawChildren'**.<br>**'drawChildren'**: completion of child component drawing.|
| callback | Callback\<void\>   | No  | Callback to unregister. If this parameter is not specified, all callbacks under this handle are unregistered. The callback must be the same object as the one registered with the [on('drawChildren')20+](#ondrawchildren20) API to successfully unregister.|

## Example

The following example demonstrates how to register the component layout and drawing completion callbacks.

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
  }
}
```
