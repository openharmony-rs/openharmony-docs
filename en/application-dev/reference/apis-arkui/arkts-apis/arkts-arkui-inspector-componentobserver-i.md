# ComponentObserver

```TypeScript
interface ComponentObserver
```

The ComponentObserver is used to listen for layout, draw and drawChildren events.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { inspector } from '@kit.ArkUI';
```

## off('layout')

```TypeScript
off(type: 'layout', callback?: () => void): void
```

Deregisters a callback with the corresponding query condition by using the handle. This callback is not triggered when the component layout complete.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'layout' | Yes | type of the listened event.<br>**Since:** 12 |
| callback | () =&gt; void | No | callback of the listened event.<br>**Since:** 12 |

## off('draw')

```TypeScript
off(type: 'draw', callback?: () => void): void
```

Deregisters a callback with the corresponding query condition by using the handle. This callback is not triggered when the component draw complete.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'draw' | Yes | type of the listened event.<br>**Since:** 12 |
| callback | () =&gt; void | No | callback of the listened event.<br>**Since:** 12 |

## off('drawChildren')

```TypeScript
off(type: 'drawChildren', callback?: Callback<void>): void
```

Deregisters a callback with the corresponding query condition by using the handle. This callback is not triggered when the child of component draw complete.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'drawChildren' | Yes | type of the listened event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | callback of the listened event. |

## offDrawChildren

```TypeScript
offDrawChildren(callback?: Callback<number[]>): void
```

Deregisters a callback with the corresponding query condition by using the handle. This callback is not triggered when the child of component draw complete.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number[]&gt; | No | callback of the listened event. |

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

Deregisters a callback with the corresponding query condition by using the handle. This callback will not be triggered when the child of component layout is complete.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | callback of the listened event. |

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

Registers a callback with the corresponding query condition by using the handle. This callback is triggered when the component layout complete.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'layout' | Yes | type of the listened event.<br>**Since:** 12 |
| callback | () =&gt; void | Yes | callback of the listened event.<br>**Since:** 12 |

## on('draw')

```TypeScript
on(type: 'draw', callback: () => void): void
```

Registers a callback with the corresponding query condition by using the handle. This callback is triggered when the component draw complete.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'draw' | Yes | type of the listened event.<br>**Since:** 12 |
| callback | () =&gt; void | Yes | callback of the listened event.<br>**Since:** 12 |

## on('drawChildren')

```TypeScript
on(type: 'drawChildren', callback: Callback<void>): void
```

Registers a callback with the corresponding query condition by using the handle. This callback is triggered when the child of component draw complete.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'drawChildren' | Yes | type of the listened event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | callback of the listened event. |

## onDrawChildren

```TypeScript
onDrawChildren(callback: Callback<number[]>): void
```

Registers a callback with the corresponding query condition by using the handle. This callback is triggered when the child of component draw complete.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number[]&gt; | Yes | callback of the listened event. |

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

Registers a callback with the corresponding query condition by using the handle. This callback will be triggered when the child of component layout is complete.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | callback of the listened event. |
