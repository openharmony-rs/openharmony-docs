# @ohos.arkui.inspector (Layout Callback)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e2e8608c64e606248f00eb66f3b2d4805fae44da translatedAt=2026-08-29T09:32:48.237Z pushedAt=2026-08-31T12:25:33.368Z -->

The **Inspector** module provides APIs for registering the component layout and drawing completion callbacks. By registering callbacks, you can receive notifications in a timely manner after component layout or drawing is complete. It is suitable for scenarios where custom logic needs to be executed after component layout or drawing is complete, helping you precisely control the component rendering timing.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

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
> - This API is supported since API version 10 and deprecated since API version 18. You are advised to use [getUIInspector](arkts-apis-uicontext-uicontext.md#getuiinspector) in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain a [UIInspector](arkts-apis-uicontext-uiinspector.md) instance, and then call the replacement method [createComponentObserver](arkts-apis-uicontext-uiinspector.md#createcomponentobserver) through this instance.
>
> - Since API version 10, you can use [getUIInspector](arkts-apis-uicontext-uicontext.md#getuiinspector) in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [UIInspector](arkts-apis-uicontext-uiinspector.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

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
let listener: inspector.ComponentObserver = inspector.createComponentObserver('COMPONENT_ID'); // Listen for callback events for the component whose ID is COMPONENT_ID.
```

## ComponentObserver

Defines the handle for component layout and drawing completion callbacks. You can call the following APIs through this handle:

### on('layout')

on(type: 'layout', callback: () => void): void

Registers a layout completion callback through this handle. This callback is triggered when the component layout is complete. Note that this API cannot listen for window size changes. For related requirements, see [on('windowSizeChange')](./arkts-apis-window-Window.md#onwindowsizechange7). In addition, there is no deterministic execution order dependency between the layout callback and the window size change callback.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type  | Mandatory| Description|
| -------- | ------ | ---- | -------------------------------------|
| type | string | Yes | Event type. The value is fixed at **'layout'**.<br>**layout**: completion of component layout. |
| callback | () => void   | Yes  | Layout completion callback.|

### off('layout')

off(type: 'layout', callback?: () => void): void

Unregisters the layout completion callback through this handle. This callback will no longer be triggered when the component layout is complete.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type  | Mandatory| Description|
| -------- | ------ | ---- | -------------------------------------------- |
| type     | string | Yes  | Event type. The value is fixed at **'layout'**.<br>**layout**: completion of component layout. |
| callback | () => void   | No  | Callback to unregister. If this parameter is not specified, all callbacks under this handle are unregistered. The callback must be the same object as the one registered with the [on('layout')](#onlayout) API to successfully unregister.|

### on('draw')

on(type: 'draw', callback: () => void): void

Registers a drawing completion callback through this handle. This callback is triggered when the component drawing is complete.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type | string | Yes | Event type. The value is fixed at **'draw'**.<br>**draw**: completion of component drawing. |
| callback | () => void   | Yes  | Drawing completion callback.                                    |

### off('draw')

off(type: 'draw', callback?: () => void): void

Unregisters the drawing completion callback through this handle. This callback will no longer be triggered when the component drawing is complete.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | Yes   | Event type. The value is fixed at **'draw'**.<br>draw: completion of component drawing.|
| callback | () => void   | No  | Callback to unregister. If this parameter is not specified, all callbacks under this handle are unregistered. The callback must be the same object as the one registered with the [on('draw')](#ondraw) API to successfully unregister.|

### on('drawChildren')<sup>20+</sup>

on(type: 'drawChildren', callback: Callback\<void\>): void

Registers a child component drawing completion callback through [ComponentObserver](#componentobserver). This callback is triggered when the child component of the component is in the main component tree and its drawing is complete. When multiple **drawChildren** callbacks exist in the component tree, only the topmost callback will be triggered. After the topmost callback is canceled, other **drawChildren** callbacks will not take effect. After a callback is registered on the current node, changing its hierarchical position in the main tree of the UI component is not supported. If adjustment is needed, unregister the event callback first and then register it again.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type | string | Yes | Event type. The value is fixed at **'drawChildren'**.<br>**drawChildren**: completion of child component drawing. |
| callback | [Callback](./arkui-ts/ts-types.md#callback12)\<void\> | Yes | Child component drawing completion callback. |

### off('drawChildren')<sup>20+</sup>

off(type: 'drawChildren', callback?: Callback\<void\>): void

Unregisters the child component drawing completion callback through this handle. This callback will no longer be triggered when the child component drawing of the component is complete. When multiple **drawChildren** callbacks exist in the component tree, after the topmost callback is canceled, other **drawChildren** callbacks will not take effect.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type | string | Yes | Event type. The value is fixed at **'drawChildren'**.<br>**drawChildren**: completion of child component drawing. |
| callback | [Callback](./arkui-ts/ts-types.md#callback12)\<void\> | No | Callback to unregister. If this parameter is not specified, all callbacks under this handle are unregistered. The callback must be the same object as the one registered with the [on('drawChildren')<sup>20+</sup>](#ondrawchildren20) API to successfully unregister. |

### onLayoutChildren<sup>23+</sup>

onLayoutChildren(callback: Callback\<void\>): void

Registers a callback used to listen for the **layoutChildren** event using [ComponentObserver](#componentobserver). This API uses an asynchronous callback to return the result.

With the node where the event callback is currently registered being used as the root node, when the node in the subtree is in the main tree of the UI component and completes layout, this callback is triggered. When multiple **layoutChildren** callbacks exist in the component tree, only the topmost callback will be triggered. After the topmost callback is canceled through [offLayoutChildren](#offlayoutchildren23), other **layoutChildren** callbacks will not take effect. After a callback is registered on the current node, changing its hierarchical position in the main tree of the UI component is not supported. If adjustment is needed, unregister the event callback first and then register it again.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | [Callback](./arkui-ts/ts-types.md#callback12)\<void\>  | Yes | Callback used to listen for the **layoutChildren** event.                              |

### offLayoutChildren<sup>23+</sup>

offLayoutChildren(callback?: Callback\<void\>): void

Unregisters the callback used to listen for the **layoutChildren** event.

To stop triggering a specific callback after the child component layout is complete, you only need to unregister the callback using the **ComponentObserver** handle. When multiple **layoutChildren** callbacks exist in the component tree, after the topmost callback is canceled, other **layoutChildren** callbacks will not take effect.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | [Callback](./arkui-ts/ts-types.md#callback12)\<void\> | No | Callback to unregister. If this parameter is not specified, all callbacks under this handle are unregistered. The callback must be the same object as the one in the [onLayoutChildren<sup>23+</sup>](#onlayoutchildren23) API to successfully unregister. |

**Example**

The following example demonstrates how to register the component layout and drawing completion callbacks. In addition, you can use the [onLayoutChildren<sup>23+</sup>](#onlayoutchildren23) API to listen for the callback event triggered when the layout of a node in the subtree is complete.

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

  listenerForImage: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('IMAGE_ID');
  listenerForRow: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('ROW_ID');

  aboutToAppear() {
    let onLayoutComplete: () => void = (): void => {
      // Supplement the implementation code as required.
    };
    let onDrawComplete: () => void = (): void => {
      // Supplement the implementation code as required.
    };
    let onDrawChildrenComplete: () => void = (): void => {
      // Supplement the implementation code as required.
    };
    // Bind to the current JS instance.
    let funcLayout = onLayoutComplete;
    let funcDraw = onDrawComplete;
    let funcDrawChildren = onDrawChildrenComplete;
    let offFuncLayout = onLayoutComplete;
    let offFuncDraw = onDrawComplete;
    let offFuncDrawChildren = onDrawChildrenComplete;

    this.listenerForImage.on('layout', funcLayout);
    this.listenerForImage.on('draw', funcDraw);
    this.listenerForRow.on('drawChildren', funcDrawChildren);

    // Unregister callbacks through the handle. You should decide when to call these APIs.
    // this.listenerForImage.off('layout', offFuncLayout)
    // this.listenerForImage.off('draw', offFuncDraw)
    // this.listenerForRow.off('drawChildren', offFuncDrawChildren)

    let onLayoutChildrenComplete: () => void = (): void => {
      // After the layoutChildren event is received, you can customize the implementation logic.
    };

    let uniqueId: number = 0; // Replace it with the unique ID of the actual component.
    let listenerForUniqueId: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver(uniqueId.toString());
    listenerForUniqueId.onLayoutChildren(onLayoutChildrenComplete);
  }

  // Unregister callbacks through the handle. You should decide when to call these APIs.
  // listenerForUniqueId.offLayoutChildren(onLayoutChildrenComplete)
}
```

### onDrawChildren<sup>24+</sup>

onDrawChildren(callback: Callback\<number[]\>): void

Registers a callback used to listen for the **drawChildren** event through [ComponentObserver](#componentobserver). This API uses an asynchronous callback to return the result. Compared with [on('drawChildren')](#ondrawchildren20), this API additionally returns the **uniqueId** information of the child components in the callback (**Callback<number[]>**), making it easier for you to locate specific child components. If you need to obtain child component identifiers, this API is recommended. If child component information is not required, either API can be used.

With the node where the event callback is currently registered being used as the root node, when the child component of the component is in the main tree of the UI component and completes drawing, this callback is triggered. When multiple **drawChildren** callbacks exist in the component tree, only the topmost callback will be triggered. After the topmost callback is canceled, other **drawChildren** callbacks will not take effect. After a callback is registered on the current node, changing its hierarchical position in the main tree of the UI component is not supported. If adjustment is needed, unregister the event callback first and then register it again.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | [Callback](./arkui-ts/ts-types.md#callback12)\<number[]\>  | Yes   | Callback used to listen for the **drawChildren** event. The callback parameter is an array of unique IDs of the child components that have finished drawing.                              |

**Example**

The following example demonstrates how to register the component layout and drawing completion callbacks. A callback is registered through the [onDrawChildren<sup>24+</sup>](#ondrawchildren24) API. After the rendering of the node in the subtree is complete, the callback returns the unique ID of the node.

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

  listenerForRow: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('ROW_ID');

  aboutToAppear() {
    let onDrawChildrenCompleteUniqueId: (childIds: number[]) => void = (childIds: number[]): void => {
      // Since API version 24, the onDrawChildren API is added. After the drawChildren event is received, you can customize the implementation logic.
    };

    this.listenerForRow.onDrawChildren(onDrawChildrenCompleteUniqueId);
  }
}
```

### offDrawChildren<sup>24+</sup>

offDrawChildren(callback?: Callback\<number[]\>): void

Unregisters the callback used to listen for the **drawChildren** event.

To stop triggering a specific callback after the child component drawing is complete, you only need to unregister the callback through the **ComponentObserver** handle. When multiple **drawChildren** callbacks exist in the component tree, after the topmost callback is canceled, other **drawChildren** callbacks will not take effect.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | [Callback](./arkui-ts/ts-types.md#callback12)\<number[]\> | No | Callback to unregister. If this parameter is not specified, all callbacks under this handle are unregistered. The callback must be the same object as the one registered with the [onDrawChildren](#ondrawchildren24) API to successfully unregister. |

**Example**

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

  listenerForRow: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('ROW_ID');

  aboutToAppear() {
    let onDrawChildrenCompleteUniqueId: (childIds: number[]) => void = (childIds: number[]): void => {
      // The onDrawChildren API is added since API version 24. After the DrawChildren event is received, you can customize the implementation logic.
    };

    this.listenerForRow.onDrawChildren(onDrawChildrenCompleteUniqueId);
  }
  // Unregister callback through the handle. You can decide when to call the API.
  // this.listenerForRow.offDrawChildren(onDrawChildrenCompleteUniqueId)
}
```