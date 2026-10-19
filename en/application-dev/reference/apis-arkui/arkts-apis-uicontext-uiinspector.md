# Class (UIInspector)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=c43314d48e5bb6db0c940e002f5fb3a101c7f656 translatedAt=2026-08-05T03:05:15.424Z pushedAt=2026-08-06T02:04:06.134Z -->

Provides the capability to register callbacks for component layout and component draw-to-display completion notifications. "Draw-to-display" means that the drawing commands of the node are sent to the graphics service and have been successfully displayed. For example, you can obtain the precise component size after layout is complete, or perform operations such as screenshot capture or animation synchronization after draw-to-display is complete. This is suitable for scenarios where precise awareness of component layout and drawing timing is required.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 10.
>
> - In the following API examples, you must first use [getUIInspector()](arkts-apis-uicontext-uicontext.md#getuiinspector) in **UIContext** to obtain a **UIInspector** instance, and then call the APIs using the obtained instance.

## createComponentObserver

createComponentObserver(id: string): inspector.ComponentObserver

Registers callbacks for component layout and component draw-to-display completion notifications. For example, you can obtain the precise component size after layout is complete, or perform operations such as screenshot capture or animation synchronization after draw-to-display is complete.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction:** This API can be used only in the stage model.

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
        }.width(80)
      }.width(80)
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }

  uiInspector: UIInspector = this.getUIContext().getUIInspector();
  listener:inspector.ComponentObserver = this.uiInspector.createComponentObserver('TEXT_ID');

  aboutToAppear() {
    let onLayoutComplete: () => void = (): void => {
      console.info('TEXT_ID layout complete');
    }
    let onDrawComplete: () => void = (): void => {
      console.info('TEXT_ID draw complete');
    }

    this.listener.on('layout', onLayoutComplete);
    this.listener.on('draw', onDrawComplete);

    // Unregister callbacks through the handle. You should decide when to call these APIs.
    // this.listener.off('layout', onLayoutComplete)
    // this.listener.off('draw', onDrawComplete)
  }
}
```

## createComponentObserver<sup>23+</sup>

createComponentObserver(id: string | number): inspector.ComponentObserver

Registers callbacks for component layout and component draw-to-display completion notifications. "Draw-to-display" means that the drawing commands of the node are sent to the graphics service and have been successfully displayed. For example, you can obtain the precise component size after layout is complete, or perform operations such as screenshot capture or animation synchronization after draw-to-display is complete.

Compared with [createComponentObserver](#createcomponentobserver), this API additionally supports the input of **UniqueID** (the unique ID allocated by the system to a node).

**Atomic service API**: This API can be used in atomic services since API version 23.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type    | Mandatory  | Description     |
| ---- | ------ | ---- | ------- |
| id   | string \| number | Yes    | When string type is used, this parameter specifies the component ID, which is set through the universal attribute [id](./arkui-ts/ts-universal-attributes-component-id.md#id) or [key](./arkui-ts/ts-universal-attributes-component-id.md#key12). When using a component ID to create a listener handle, ensure that the component corresponding to the ID already exists; otherwise, the listener will not take effect. When the type is number, this parameter specifies the UniqueID, which is a unique identifier assigned by the system to a node and can be obtained through [getUniqueId](js-apis-arkui-frameNode.md#getuniqueid12). When using a UniqueID to create a listener handle, ensure that the node corresponding to the UniqueID already exists; otherwise, the listener will not take effect. The value range of the number type is an integer from 1 to 2147483647.|

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
        }.width(80)
      }.width(80)
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }

  uiInspector: UIInspector = this.getUIContext().getUIInspector();
  listener:inspector.ComponentObserver = this.uiInspector.createComponentObserver('TEXT_ID');

  aboutToAppear() {
    let onLayoutComplete: () => void = (): void => {
      console.info('TEXT_ID layout complete');
    }
    let onDrawComplete: () => void = (): void => {
      console.info('TEXT_ID draw complete');
    }
    let onLayoutChildrenComplete: () => void = (): void => {
      console.info('UIInspectorExample children layout');
    }

    this.listener.on('layout', onLayoutComplete);
    this.listener.on('draw', onDrawComplete);

    let listenerForThis = this.getUIContext().getUIInspector().createComponentObserver(this.getUniqueId());
    listenerForThis.onLayoutChildren(onLayoutChildrenComplete);

    // Unregister callbacks through the handle. You should decide when to call these APIs.
    // this.listener.off('layout', onLayoutComplete)
    // this.listener.off('draw', onDrawComplete)
  }
}
```