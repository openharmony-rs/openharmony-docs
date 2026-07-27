# Class (UIInspector)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

Provides APIs for registering the component layout and drawing display completion callbacks.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 10.
>
> - In the following API examples, you must first use [getUIInspector()](arkts-apis-uicontext-uicontext.md#getuiinspector) in **UIContext** to obtain a **UIInspector** instance, and then call the APIs using the obtained instance.

## createComponentObserver

createComponentObserver(id: string): inspector.ComponentObserver

Registers a callback for layout and drawing display completion notifications for a specific component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type    | Mandatory  | Description     |
| ---- | ------ | ---- | ------- |
| id   | string | Yes   | ID of the target component, set using the universal attributes [id](./arkui-ts/ts-universal-attributes-component-id.md#id) or [key](./arkui-ts/ts-universal-attributes-component-id.md#key12).|

**Return value**

| Type                                                        | Description                                              |
| ------------------------------------------------------------ | -------------------------------------------------- |
| [inspector.ComponentObserver](js-apis-arkui-inspector.md#componentobserver) | Component observer, which is used to register or unregister listeners for completion of component layout or drawing display.|

**Example**

<!--code_no_check-->
```ts
import { inspector, UIInspector } from '@kit.ArkUI'

@Entry
@Component
struct UIInspectorExample {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row({ space: 5 }) {
          Text("UIInspector")
            .width(110)
            .height(110)
            .border({ width: 1 })
            .id('TEXT_ID')
        }.width(80).width(80)
      }.width(80).width(80)
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }

  uiInspector: UIInspector = this.getUIContext().getUIInspector();
  listener:inspector.ComponentObserver = this.uiInspector.createComponentObserver("TEXT_ID")

  aboutToAppear() {
    let onLayoutComplete:()=>void=():void=>{
      console.info("TEXT_ID layout complete")
    }
    let onDrawComplete:()=>void=():void=>{
      console.info("TEXT_ID draw complete")
    }

    this.listener.on('layout', onLayoutComplete)
    this.listener.on('draw', onDrawComplete)

    // Unregister callbacks through the handle. You should decide when to call these APIs.
    // this.listener.off('layout', onLayoutComplete)
    // this.listener.off('draw', onDrawComplete)
  }
}
```

## createComponentObserver<sup>23+</sup>

createComponentObserver(id: string | number): inspector.ComponentObserver

Registers a callback for layout and drawing display completion notifications for a specific component. Display refers to the process of sending the drawing command of a node to the graphics service and completing the display.

Compared with [createComponentObserver](#createcomponentobserver), this API supports the input of **UniqueID** (the unique ID allocated by the system to a node).


**Atomic service API**: This API can be used in atomic services since API version 23.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type    | Mandatory  | Description     |
| ---- | ------ | ---- | ------- |
| id   | string \| number | Yes   | This parameter in the string type indicates the ID of the specified component. The ID is set through the universal attribute [id](./arkui-ts/ts-universal-attributes-component-id.md#id) or [key](./arkui-ts/ts-universal-attributes-component-id.md#key12). This parameter in the number type indicates the unique ID of the node allocated by the system. The unique ID is obtained through [getUniqueId](js-apis-arkui-frameNode.md#getuniqueid12). When using the unique ID to create a listener handle, ensure that the node corresponding to the unique ID exists. Otherwise, the listener does not take effect. The value of the parameter in the number type is an integer ranging from 1 to 2147483647.|

**Return value**

| Type                                                        | Description                                              |
| ------------------------------------------------------------ | -------------------------------------------------- |
| [inspector.ComponentObserver](js-apis-arkui-inspector.md#componentobserver) | Component observer, which is used to register or unregister listeners for completion of component layout or drawing display.|

**Example**

```ts
import { inspector, UIInspector } from '@kit.ArkUI';

@Entry
@Component
struct UIInspectorExample {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row({ space: 5 }) {
          Text('UIInspector')
            .width(110)
            .height(110)
            .border({ width: 1 })
            .id('TEXT_ID')
        }.width(80).width(80)
      }.width(80).width(80)
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }

  uiInspector: UIInspector = this.getUIContext().getUIInspector();
  listener:inspector.ComponentObserver = this.uiInspector.createComponentObserver('TEXT_ID')

  aboutToAppear() {
    let onLayoutComplete:()=>void=():void=>{
      console.info('TEXT_ID layout complete')
    }
    let onDrawComplete:()=>void=():void=>{
      console.info('TEXT_ID draw complete')
    }
    let onLayoutChildrenComplete :()=>void=():void=> {
      console.info('UIInspectorExample children layout')
    }

    this.listener.on('layout', onLayoutComplete)
    this.listener.on('draw', onDrawComplete)

    let listenerForThis = this.getUIContext().getUIInspector().createComponentObserver(this.getUniqueId());
    listenerForThis.onLayoutChildren(onLayoutChildrenComplete);

    // Unregister callbacks through the handle. You should decide when to call these APIs.
    // this.listener.off('layout', onLayoutComplete)
    // this.listener.off('draw', onDrawComplete)
  }
}
```
