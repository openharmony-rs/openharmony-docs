# ComponentSnapshot

Provides APIs for obtaining component snapshots, including snapshots of components that have been loaded and snapshots of components that have not been loaded yet.

> **NOTE:** 
> 
> - The initial APIs of this class are supported since API version 12.
> 
> - In the following API examples, you must first use [getComponentSnapshot()](arkts-arkui-arkui-uicontext-uicontext-c.md#getcomponentsnapshot)in **UIContext** to obtain a **ComponentSnapshot** instance, and then call the APIs using the obtained instance.
> 
> - Transformation properties such as scaling, translation, and rotation only apply to the child components of the target component. Applying these transformation properties directly to the target component itself has no effect;the snapshot will still display the component as it appears before any transformations are applied.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## createFromBuilder

```TypeScript
createFromBuilder(builder: CustomBuilder, callback: AsyncCallback<image.PixelMap>,
    delay?: number, checkImageStatus?: boolean, options?: componentSnapshot.SnapshotOptions): void
```

Captures a snapshot of an offscreen-rendered component created from a [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md). This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - Due to the need to wait for the component to be built and rendered, there is a delay of not more than 500 ms in the callback for off-screen snapshot capturing. Therefore, this API is not recommended for performance-sensitive scenarios.
> 
> - If a component is on a time-consuming task, for example, an [Image](../../apis-image-kit/arkts-apis/arkts-image-multimedia-image.md) or Web component that is loading online images, its loading may be still in progress when this API is called. In this case, the output snapshot does not represent the component in the way it looks when the loading is successfully completed.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) | Yes | Builder of the custom component.<br>Note: The global builder is not supported.<br>If the root component of the builder has a width or height of zero, the snapshot operation will fail with error code 100001. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Yes | Callback used to return the result. If the snapshot capture is successful, **err** is **undefined**, and **data** contains the resulting [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md). Otherwise, **err** provides detailed error information. The coordinates and size of the offscreen component's drawing area can be obtained through the callback. |
| delay | number | No | Delay time for triggering the screenshot command. When the layout includes an image component, it is necessary to set a delay time to allow the system to decode the image resources. The decoding time is subject to the resource size. In light of this, whenever possible, use pixel map resources that do not require decoding.<br> When PixelMap resources are used or when syncLoad is set to **true** for the **Image** component, you can set **delay** to **0** to forcibly capture snapshots without waiting. This delay time does not refer to the time from the API call to the return: As the system needs to temporarily construct the passed-in **builder** offscreen, the return time is usually longer than this delay.<br>Note: In the **builder** passed in, state variables should not be used to control the construction of child components. If they are used, they should not change when the API is called, so as to avoid unexpected snapshot results.<br> Default value: **300**<br> Unit: ms<br> Value range: [0, +∞). If the value is less than 0, the default value is used. |
| checkImageStatus | boolean | No | Whether to verify the image decoding status before taking a snapshot. If the value is **true**, the system checks whether all **Image** components have been decoded before taking the snapshot. If the check is not completed, the system aborts the snapshot and returns an exception.<br>Default value: **false**. |
| options | [componentSnapshot.SnapshotOptions](arkts-arkui-componentsnapshot-snapshotoptions-i.md) | No | Custom settings of the snapshot. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | The builder is not a valid build function. |
| [160001](../errorcode-snapshot.md#160001-image-loading-error) | An image component in builder is not ready for taking a snapshot. The check for the ready state is required when the checkImageStatus option is enabled. |
| [160003](../errorcode-snapshot.md#160003-color-space-or-dynamic-range-mode-set-in-screenshot-options-is-not-supported) | Unsupported color space or dynamic range mode in snapshot options.<br>**Applicable version:** 23 and later |
| [160004](../errorcode-snapshot.md#160004-offscreen-node-screenshot-does-not-support-setting-the-isauto-parameter-of-color-space-or-dynamic-range-mode-to-true) | isAuto(true) is not supported for offscreen node snapshots.<br>**Applicable version:** 23 and later |

## createFromBuilder

```TypeScript
createFromBuilder(builder: CustomBuilder, delay?: number,
    checkImageStatus?: boolean, options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>
```

Captures a snapshot of an offscreen-rendered component created from a [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md). This API uses a promise to return the result.

> **NOTE:** 
> 
> - Due to the need to wait for the component to be built and rendered, there is a delay of not more than 500 ms in the callback for off-screen snapshot capturing. Therefore, this API is not recommended for performance-sensitive scenarios.
> 
> - If a component is on a time-consuming task, for example, an [Image](../../apis-image-kit/arkts-apis/arkts-image-multimedia-image.md) or Web component that is loading online images, its loading may be still in progress when this API is called. In this case, the output snapshot does not represent the component in the way it looks when the loading is successfully completed.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) | Yes | Builder of the custom component.<br>Note: The global builder is not supported.<br>If the root component of the builder has a width or height of zero, the snapshot operation will fail with error code 100001. |
| delay | number | No | Delay time for triggering the screenshot command. When the layout includes an image component, it is necessary to set a delay time to allow the system to decode the image resources. The decoding time is subject to the resource size. In light of this, whenever possible, use pixel map resources that do not require decoding.<br> When PixelMap resources are used or when syncLoad is set to **true** for the **Image** component, you can set **delay** to **0** to forcibly capture snapshots without waiting. This delay time does not refer to the time from the API call to the return: As the system needs to temporarily construct the passed-in **builder** offscreen, the return time is usually longer than this delay.<br>Note: In the **builder** passed in, state variables should not be used to control the construction of child components. If they are used, they should not change when the API is called, so as to avoid unexpected snapshot results.<br> Default value: **300**<br> Unit: ms<br> Value range: [0, +∞). If the value is less than 0, the default value is used. |
| checkImageStatus | boolean | No | Whether to verify the image decoding status before taking a snapshot. If the value is **true**, the system checks whether all **Image** components have been decoded before taking the snapshot. If the check is not completed, the system aborts the snapshot and returns an exception.<br>Default value: **false**. |
| options | [componentSnapshot.SnapshotOptions](arkts-arkui-componentsnapshot-snapshotoptions-i.md) | No | Custom settings of the snapshot. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise used to return the snapshot object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | The builder is not a valid build function. |
| [160001](../errorcode-snapshot.md#160001-image-loading-error) | An image component in builder is not ready for taking a snapshot. The check for the ready state is required when the checkImageStatus option is enabled. |
| [160003](../errorcode-snapshot.md#160003-color-space-or-dynamic-range-mode-set-in-screenshot-options-is-not-supported) | Unsupported color space or dynamic range mode in snapshot options.<br>**Applicable version:** 23 and later |
| [160004](../errorcode-snapshot.md#160004-offscreen-node-screenshot-does-not-support-setting-the-isauto-parameter-of-color-space-or-dynamic-range-mode-to-true) | isAuto(true) is not supported for offscreen node snapshots.<br>**Applicable version:** 23 and later |

## createFromComponent

```TypeScript
createFromComponent<T extends Object>(content: ComponentContent<T>, delay?: number,
    checkImageStatus?: boolean, options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>
```

Captures a snapshot of the provided component content. This API uses a promise to return the result.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Component content to be captured. This is the content currently displayed in the **UIContext**. |
| delay | number | No | Delay time for triggering the screenshot command. When the layout includes an image component, it is necessary to set a delay time to allow the system to decode the image resources. The decoding time is subject to the resource size. In light of this, whenever possible, use pixel map resources that do not require decoding.<br> When PixelMap resources are used or when syncLoad is set to **true** for the **Image** component, you can set **delay** to **0** to forcibly capture snapshots without waiting. This delay time does not refer to the time from the API call to the return: As the system needs to temporarily construct the passed-in **builder** offscreen, the return time is usually longer than this delay.<br>Note: In the **builder** passed in, state variables should not be used to control the construction of child components. If they are used, they should not change when the API is called, so as to avoid unexpected snapshot results.<br> Value range: [0, +∞). If the value is less than 0, the default value is used.<br>Default value: **300**<br> Unit: ms |
| checkImageStatus | boolean | No | Whether to verify the image decoding status before taking a snapshot. If the value is **true**, the system checks whether all **Image** components have been decoded before taking the snapshot. If the check is not completed, the system aborts the snapshot and returns an exception.<br>Default value: **false**. |
| options | [componentSnapshot.SnapshotOptions](arkts-arkui-componentsnapshot-snapshotoptions-i.md) | No | Custom settings of the snapshot. You can specify the scale ratio for the pixelmap during rendering and whether to force the system to complete all rendering commands before taking the snapshot. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise used to return the snapshot object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | The builder is not a valid build function. |
| [160001](../errorcode-snapshot.md#160001-image-loading-error) | An image component in builder is not ready for taking a snapshot. The check for the ready state is required when the checkImageStatus option is enabled. |
| [160003](../errorcode-snapshot.md#160003-color-space-or-dynamic-range-mode-set-in-screenshot-options-is-not-supported) | Unsupported color space or dynamic range mode in snapshot options.<br>**Applicable version:** 23 and later |
| [160004](../errorcode-snapshot.md#160004-offscreen-node-screenshot-does-not-support-setting-the-isauto-parameter-of-color-space-or-dynamic-range-mode-to-true) | isAuto(true) is not supported for offscreen node snapshots.<br>**Applicable version:** 23 and later |

## get

```TypeScript
get(id: string, callback: AsyncCallback<image.PixelMap>, options?: componentSnapshot.SnapshotOptions): void
```

Obtains the snapshot of a component that has been loaded based on the provided [component ID](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-common.md). This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The snapshot captures content rendered in the last frame. If this API is called when the component triggers an
> update, the re-rendered content will not be included in the obtained snapshot.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | [ID](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-common.md) of the target component.<br>Note: Off-screen or cached components not mounted in the component tree are not supported. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Yes | Callback used to return the result. If the snapshot capture is successful, **err** is **undefined**, and **data** contains the resulting [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md). Otherwise, **err** provides detailed error information. |
| options | [componentSnapshot.SnapshotOptions](arkts-arkui-componentsnapshot-snapshotoptions-i.md) | No | Custom settings of the snapshot. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Invalid ID. |
| [160003](../errorcode-snapshot.md#160003-color-space-or-dynamic-range-mode-set-in-screenshot-options-is-not-supported) | Unsupported color space or dynamic range mode in snapshot options.<br>**Applicable version:** 23 and later |

## get

```TypeScript
get(id: string, options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>
```

Obtains the snapshot of a component that has been loaded based on the provided [component ID](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-common.md). This API uses a promise to return the result.

> **NOTE:** 
> 
> The snapshot captures content rendered in the last frame. If this API is called when the component triggers an
> update, the re-rendered content will not be included in the obtained snapshot.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | [ID](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-common.md) of the target component.<br>Note: Off-screen or cached components not mounted in the component tree are not supported. |
| options | [componentSnapshot.SnapshotOptions](arkts-arkui-componentsnapshot-snapshotoptions-i.md) | No | Custom settings of the snapshot. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise used to return the snapshot object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Invalid ID. |
| [160003](../errorcode-snapshot.md#160003-color-space-or-dynamic-range-mode-set-in-screenshot-options-is-not-supported) | Unsupported color space or dynamic range mode in snapshot options.<br>**Applicable version:** 23 and later |

## getSizeLimitation

```TypeScript
getSizeLimitation(): componentSnapshot.SnapshotSizeLimitation
```

Obtains the size limit of a component screenshot.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [componentSnapshot.SnapshotSizeLimitation](arkts-arkui-componentsnapshot-snapshotsizelimitation-i.md) | Size limit of a component screenshot. |

## getSync

```TypeScript
getSync(id: string, options?: componentSnapshot.SnapshotOptions): image.PixelMap
```

Obtains the snapshot of a component that has been loaded based on the provided [component ID](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-common.md). This API synchronously returns a [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) after completing the capture. Note that this API blocks the main thread and has a 3-second timeout. If the operation exceeds this limit, it throws an exception. Use with caution in performance-critical scenarios.

> **NOTE:** 
> 
> The snapshot captures content rendered in the last frame. If this API is called when the component triggers an
> update, the re-rendered content will not be included in the obtained snapshot.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | [ID](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-common.md) of the target component.<br>Note: Off-screen or cached components not mounted in the component tree are not supported. |
| options | [componentSnapshot.SnapshotOptions](arkts-arkui-componentsnapshot-snapshotoptions-i.md) | No | Custom settings of the snapshot. |

**Return value:**

| Type | Description |
| --- | --- |
| [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Invalid ID. |
| [160002](../errorcode-snapshot.md#160002-snapshot-timeout) | Timeout. |
| [160003](../errorcode-snapshot.md#160003-color-space-or-dynamic-range-mode-set-in-screenshot-options-is-not-supported) | Unsupported color space or dynamic range mode in snapshot options.<br>**Applicable version:** 23 and later |

## getSyncWithUniqueId

```TypeScript
getSyncWithUniqueId(uniqueId: number, options?: componentSnapshot.SnapshotOptions): image.PixelMap
```

Obtains the snapshot of a component that has been loaded based on the provided **uniqueId**. This API synchronously waits for the snapshot to complete and returns a [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) object.

> **NOTE:** 
> 
> The snapshot captures content rendered in the last frame. If this API is called when the component triggers an
> update, the re-rendered content will not be included in the obtained snapshot.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uniqueId | number | Yes | Unique ID of the target component. The unique ID of the **FrameNode** can be obtained via the [getUniqueId](arkts-arkui-framenode-c.md#getuniqueid) API.<br>Note: Off-screen or cached components not mounted in the component tree are not supported. |
| options | [componentSnapshot.SnapshotOptions](arkts-arkui-componentsnapshot-snapshotoptions-i.md) | No | Custom settings of the snapshot. |

**Return value:**

| Type | Description |
| --- | --- |
| [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Invalid ID. |
| [160002](../errorcode-snapshot.md#160002-snapshot-timeout) | Timeout. |
| [160003](../errorcode-snapshot.md#160003-color-space-or-dynamic-range-mode-set-in-screenshot-options-is-not-supported) | Unsupported color space or dynamic range mode in snapshot options.<br>**Applicable version:** 23 and later |

## getWithUniqueId

```TypeScript
getWithUniqueId(uniqueId: number, options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>
```

Obtains the snapshot of a component that has been loaded based on the provided **uniqueId**. This API uses a promise to return the result.

> **NOTE:** 
> 
> The snapshot captures content rendered in the last frame. If this API is called when the component triggers an
> update, the re-rendered content will not be included in the obtained snapshot.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uniqueId | number | Yes | Unique ID of the target component. The unique ID of the **FrameNode** can be obtained via the [getUniqueId](arkts-arkui-framenode-c.md#getuniqueid) API.<br>Note: Off-screen or cached components not mounted in the component tree are not supported. |
| options | [componentSnapshot.SnapshotOptions](arkts-arkui-componentsnapshot-snapshotoptions-i.md) | No | Custom settings of the snapshot. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise used to return the snapshot object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Invalid ID. |
| [160003](../errorcode-snapshot.md#160003-color-space-or-dynamic-range-mode-set-in-screenshot-options-is-not-supported) | Unsupported color space or dynamic range mode in snapshot options.<br>**Applicable version:** 23 and later |
