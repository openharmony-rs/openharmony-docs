# ComponentObserver

```TypeScript
interface ComponentObserver
```

Defines the handle for component layout and drawing completion callbacks. You can call the following APIs through this handle:

**Since:** 10

<!--Device-inspector-interface ComponentObserver--><!--Device-inspector-interface ComponentObserver-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { inspector } from '@kit.ArkUI';
```

## off('layout')

```TypeScript
off(type: 'layout', callback?: () => void): void
```

Unregisters the layout completion callback through this handle. This callback will no longer be triggered when the component layout is complete.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ComponentObserver-off(type: 'layout', callback?: () => void): void--><!--Device-ComponentObserver-off(type: 'layout', callback?: () => void): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'layout' | Yes | Event type. The value is fixed at **'layout'**.<br> **layout**: completion of component layout.<br>**Since:** 12 |
| callback | () =&gt; void | No | Callback to unregister. If this parameter is not specified, all callbacks under this handle are unregistered. The callback must be the same object as the one registered with the [on('layout')](#onlayout) API to successfully unregister.<br>**Since:** 12 |

## off('draw')

```TypeScript
off(type: 'draw', callback?: () => void): void
```

Unregisters the drawing completion callback through this handle. This callback will no longer be triggered when the component drawing is complete.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ComponentObserver-off(type: 'draw', callback?: () => void): void--><!--Device-ComponentObserver-off(type: 'draw', callback?: () => void): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'draw' | Yes | Event type. The value is fixed at **'draw'**.<br> draw: completion of component drawing.<br>**Since:** 12 |
| callback | () =&gt; void | No | Callback to unregister. If this parameter is not specified, all callbacks under this handle are unregistered. The callback must be the same object as the one registered with the [on('draw')](#ondraw) API to successfully unregister.<br>**Since:** 12 |

## off('drawChildren')

```TypeScript
off(type: 'drawChildren', callback?: Callback<void>): void
```

Unregisters the child component drawing completion callback through this handle. This callback will no longer be triggered when the child component drawing of the component is complete. When multiple **drawChildren** callbacks exist in the component tree, after the topmost callback is canceled, other **drawChildren** callbacks will not take effect.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ComponentObserver-off(type: 'drawChildren', callback?: Callback<void>): void--><!--Device-ComponentObserver-off(type: 'drawChildren', callback?: Callback<void>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'drawChildren' | Yes | Event type. The value is fixed at **'drawChildren'**.<br> **drawChildren**: completion of child component drawing. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Callback to unregister. If this parameter is not specified, all callbacks under this handle are unregistered. The callback must be the same object as the one registered with the [on('drawChildren')<sup>20+</sup>](#ondrawchildren) API to successfully unregister. |

## offDrawChildren

```TypeScript
offDrawChildren(callback?: Callback<number[]>): void
```

Unregisters the callback used to listen for the **drawChildren** event. <br>To stop triggering a specific callback after the child component drawing is complete, you only need to unregister the callback through the **ComponentObserver** handle. When multiple **drawChildren** callbacks exist in the component tree, after the topmost callback is canceled, other **drawChildren** callbacks will not take effect.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-ComponentObserver-offDrawChildren(callback?: Callback<int[]>): void--><!--Device-ComponentObserver-offDrawChildren(callback?: Callback<int[]>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number[]&gt; | No | Callback to unregister. If this parameter is not specified, all callbacks under this handle are unregistered. The callback must be the same object as the one registered with the [onDrawChildren](#ondrawchildren) API to successfully unregister. |

**Examples**

```TypeScript
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

## offLayoutChildren

```TypeScript
offLayoutChildren(callback?: Callback<void>): void
```

Unregisters the callback used to listen for the **layoutChildren** event. <br>To stop triggering a specific callback after the child component layout is complete, you only need to unregister the callback using the **ComponentObserver** handle. When multiple **layoutChildren** callbacks exist in the component tree, after the topmost callback is canceled, other **layoutChildren** callbacks will not take effect.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-ComponentObserver-offLayoutChildren(callback?: Callback<void>): void--><!--Device-ComponentObserver-offLayoutChildren(callback?: Callback<void>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Callback to unregister. If this parameter is not specified, all callbacks under this handle are unregistered. The callback must be the same object as the one in the [onLayoutChildren<sup>23+</sup>](#onlayoutchildren) API to successfully unregister. |

**Examples**

The following example demonstrates how to register the component layout and drawing completion callbacks. In addition, you can use the [onLayoutChildren23+](#onlayoutchildren) API to listen for the callback event triggered when the layout of a node in the subtree is complete.

```TypeScript
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

## on('layout')

```TypeScript
on(type: 'layout', callback: () => void): void
```

Registers a layout completion callback through this handle. This callback is triggered when the component layout is complete. Note that this API cannot listen for window size changes. For related requirements, see [on('windowSizeChange')](./arkts-apis-window-Window.md#onwindowsizechange7). In addition, there is no deterministic execution order dependency between the layout callback and the window size change callback.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ComponentObserver-on(type: 'layout', callback: () => void): void--><!--Device-ComponentObserver-on(type: 'layout', callback: () => void): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'layout' | Yes | Event type. The value is fixed at **'layout'**.<br> **layout**: completion of component layout.<br>**Since:** 12 |
| callback | () =&gt; void | Yes | Layout completion callback.<br>**Since:** 12 |

## on('draw')

```TypeScript
on(type: 'draw', callback: () => void): void
```

Registers a drawing completion callback through this handle. This callback is triggered when the component drawing is complete.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ComponentObserver-on(type: 'draw', callback: () => void): void--><!--Device-ComponentObserver-on(type: 'draw', callback: () => void): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'draw' | Yes | Event type. The value is fixed at **'draw'**.<br> **draw**: completion of component drawing.<br>**Since:** 12 |
| callback | () =&gt; void | Yes | Drawing completion callback.<br>**Since:** 12 |

## on('drawChildren')

```TypeScript
on(type: 'drawChildren', callback: Callback<void>): void
```

Registers a child component drawing completion callback through ComponentObserver. This callback is triggered when the child component of the component is in the main component tree and its drawing is complete. When multiple **drawChildren** callbacks exist in the component tree, only the topmost callback will be triggered. After the topmost callback is canceled, other **drawChildren** callbacks will not take effect. After a callback is registered on the current node, changing its hierarchical position in the main tree of the UI component is not supported. If adjustment is needed, unregister the event callback first and then register it again.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ComponentObserver-on(type: 'drawChildren', callback: Callback<void>): void--><!--Device-ComponentObserver-on(type: 'drawChildren', callback: Callback<void>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'drawChildren' | Yes | Event type. The value is fixed at **'drawChildren'**.<br> **drawChildren**: completion of child component drawing. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Child component drawing completion callback. |

## onDrawChildren

```TypeScript
onDrawChildren(callback: Callback<number[]>): void
```

Registers a callback used to listen for the **drawChildren** event through ComponentObserver. This API uses an asynchronous callback to return the result. Compared with [on('drawChildren')](#ondrawchildren), this API additionally returns the **uniqueId** information of the child components in the callback (**Callback<number[]>**), making it easier for you to locate specific child components. If you need to obtain child component identifiers, this API is recommended. If child component information is not required, either API can be used. <br>With the node where the event callback is currently registered being used as the root node, when the child component of the component is in the main tree of the UI component and completes drawing, this callback is triggered. When multiple **drawChildren** callbacks exist in the component tree, only the topmost callback will be triggered. After the topmost callback is canceled, other **drawChildren** callbacks will not take effect. After a callback is registered on the current node, changing its hierarchical position in the main tree of the UI component is not supported. If adjustment is needed, unregister the event callback first and then register it again.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-ComponentObserver-onDrawChildren(callback: Callback<int[]>): void--><!--Device-ComponentObserver-onDrawChildren(callback: Callback<int[]>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number[]&gt; | Yes | Callback used to listen for the **drawChildren** event. The callback parameter is an array of unique IDs of the child components that have finished drawing. |

**Examples**

The following example demonstrates how to register the component layout and drawing completion callbacks. A callback is registered through the [onDrawChildren24+](#ondrawchildren) API. After the rendering of the node in the subtree is complete, the callback returns the unique ID of the node.

```TypeScript
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

## onLayoutChildren

```TypeScript
onLayoutChildren(callback: Callback<void>): void
```

Registers a callback used to listen for the **layoutChildren** event using ComponentObserver. This API uses an asynchronous callback to return the result. <br>With the node where the event callback is currently registered being used as the root node, when the node in the subtree is in the main tree of the UI component and completes layout, this callback is triggered. When multiple **layoutChildren** callbacks exist in the component tree, only the topmost callback will be triggered. After the topmost callback is canceled through [offLayoutChildren](#offlayoutchildren), other **layoutChildren** callbacks will not take effect. After a callback is registered on the current node, changing its hierarchical position in the main tree of the UI component is not supported. If adjustment is needed, unregister the event callback first and then register it again.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-ComponentObserver-onLayoutChildren(callback: Callback<void>): void--><!--Device-ComponentObserver-onLayoutChildren(callback: Callback<void>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback used to listen for the **layoutChildren** event. |
