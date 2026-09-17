# Panel

Describes a **Panel** object, which is created using [createPanel](arkts-basicservices-selectionmanager-createpanel-f.md). This method can be used to set, display, hide, and move the panel, as well as subscribe to events. It is applicable to scenarios where a custom operation UI needs to be displayed to users after word selection is complete.

**Since:** 24

**System capability:** SystemCapability.SelectionInput.Selection

## Modules to Import

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';
```

## hide

```TypeScript
hide(): Promise<void>
```

Hides the word selection panel. This API is used together with [show](#show). This API can be called only after a **Panel** instance is obtained by calling [createPanel](arkts-basicservices-selectionmanager-createpanel-f.md). This API uses a promise to return the result. If this API is not called proactively, the panel is automatically hidden when it loses focus.

**Since:** 24

**System capability:** SystemCapability.SelectionInput.Selection

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [33600001](../errorcode-selection.md#33600001-word-selection-service-invocation-error) | Selection service invocation exception. |
| [33600002](../errorcode-selection.md#33600002-word-selection-panel-has-been-destroyed) | This selection window has been destroyed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Hide the word selection panel. selectionPanel is a Panel instance created by createPanel.
selectionPanel.hide().then(() => {
  console.info('Succeeded in hiding the panel.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide panel. Error code: ${err.code}, error message: ${err.message}`);
});
```

## moveToGlobalDisplay

```TypeScript
moveToGlobalDisplay(x: number, y: number): Promise<void>
```

Moves the word selection panel to the specified coordinates in the global coordinates system of the screen. The panel can be moved to an extended screen. This API can be called only after a **Panel** instance is obtained by calling [createPanel](arkts-basicservices-selectionmanager-createpanel-f.md). This API uses a promise to return the result.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.SelectionInput.Selection

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the target position in the global coordinate system of the screen, in px. The upper left corner of the main screen is the origin of the global coordinate system, and the positive direction of the X axis is rightward. The x-coordinate of an extended screen may be negative, depending on the screen layout. |
| y | number | Yes | Y-coordinate of the target position in the global coordinate system of the screen, in px. The upper left corner of the main screen is the origin of the global coordinate system, and the positive direction of the Y axis is downward. The y-coordinate of an extended screen may be negative, depending on the screen layout. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [33600001](../errorcode-selection.md#33600001-word-selection-service-invocation-error) | Selection service invocation exception. |
| [33600002](../errorcode-selection.md#33600002-word-selection-panel-has-been-destroyed) | This selection window has been destroyed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Move the word selection panel to the specified coordinates on the screen. selectionPanel is a Panel instance created by createPanel.
  selectionPanel.moveToGlobalDisplay(200, 200).then(() => {
    console.info('Succeeded in moving the panel.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to move panel. Error code: ${err.code}, error message: ${err.message}`);
  });
} catch (err) {
  console.error(`Failed to move panel. Error code: ${err.code}, error message: ${err.message}`);
}
```

## off('destroyed')

```TypeScript
off(type: 'destroyed', callback?: Callback<void>): void
```

Unsubscribes from the word selection panel destruction event. This API is used together with [on('destroyed')](#ondestroyed). This API can be called only after a **Panel** instance is obtained by calling [createPanel](arkts-basicservices-selectionmanager-createpanel-f.md).

**Since:** 24

**System capability:** SystemCapability.SelectionInput.Selection

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'destroyed' | Yes | Type of the event to unsubscribe from. The value is fixed to **'destroyed'**. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Callback to be unregistered, which the callback instance registered using **on**. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

## off('hidden')

```TypeScript
off(type: 'hidden', callback?: Callback<void>): void
```

Unsubscribes from the word selection panel hiding event. This API is used together with [on('hidden')](#onhidden). This API can be called only after a **Panel** instance is obtained by calling [createPanel](arkts-basicservices-selectionmanager-createpanel-f.md).

**Since:** 24

**System capability:** SystemCapability.SelectionInput.Selection

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'hidden' | Yes | Type of the event to unsubscribe from. The value is fixed to **'hidden'**. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Callback to be unregistered, which the callback instance registered using **on**. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

## on('destroyed')

```TypeScript
on(type: 'destroyed', callback: Callback<void>): void
```

Subscribes to the word selection panel destruction event. This API is used together with [off('destroyed')](#offdestroyed). This API can be called only after a **Panel** instance is obtained by calling [createPanel](arkts-basicservices-selectionmanager-createpanel-f.md).

**Since:** 24

**System capability:** SystemCapability.SelectionInput.Selection

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'destroyed' | Yes | Event type, which is **'destroyed'**. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback used to return the result, which is triggered when [destroyPanel](arkts-basicservices-selectionmanager-destroypanel-f.md) is called to destroy the panel. |

## on('hidden')

```TypeScript
on(type: 'hidden', callback: Callback<void>): void
```

Subscribes to the word selection panel hiding event. This API is used together with [off('hidden')](#offhidden). This event is triggered when the panel is hidden by calling [hide](#hide) or automatically hidden when it loses focus. This API can be called only after a **Panel** instance is obtained by calling [createPanel](arkts-basicservices-selectionmanager-createpanel-f.md).

**Since:** 24

**System capability:** SystemCapability.SelectionInput.Selection

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'hidden' | Yes | Event type, which is **'hidden'**. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback used to return the result, which is triggered when the panel is hidden. The panel can be hidden by calling [hide](#hide) or automatically hidden when it loses focus. |

## setUiContent

```TypeScript
setUiContent(path: string): Promise<void>
```

Sets the UI content for the current word selection panel, for example, to display translation results, search suggestions, or custom action buttons. This API can be called only after a **Panel** instance is obtained by calling [createPanel](arkts-basicservices-selectionmanager-createpanel-f.md). This API uses a promise to return the result.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.SelectionInput.Selection

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the page content to be set. This path is configured in the **resources/base/profile/main_pages.json** file of the project in the stage model. The FA model is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [33600001](../errorcode-selection.md#33600001-word-selection-service-invocation-error) | Selection service invocation exception. |
| [33600002](../errorcode-selection.md#33600002-word-selection-panel-has-been-destroyed) | This selection window has been destroyed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Load page content for the word selection panel. selectionPanel is a Panel instance created by createPanel.
  selectionPanel.setUiContent('pages/Index').then(() => {
    console.info('Succeeded in setting the content.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to setUiContent. Error code: ${err.code}, error message: ${err.message}`);
  });
} catch (err) {
  console.error(`Failed to setUiContent. Error code: ${err.code}, error message: ${err.message}`);
}
```

## show

```TypeScript
show(): Promise<void>
```

Shows the word selection panel. This API is used together with [hide](#hide). This API can be called only after a **Panel** instance is obtained by calling [createPanel](arkts-basicservices-selectionmanager-createpanel-f.md). This API uses a promise to return the result.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.SelectionInput.Selection

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [33600001](../errorcode-selection.md#33600001-word-selection-service-invocation-error) | Selection service invocation exception. |
| [33600002](../errorcode-selection.md#33600002-word-selection-panel-has-been-destroyed) | This selection window has been destroyed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Show the word selection panel. selectionPanel is a Panel instance created by createPanel.
selectionPanel.show().then(() => {
  console.info('Succeeded in showing the panel.');
}).catch((err: BusinessError) => {
  console.error(`Failed to show panel. Error code: ${err.code}, error message: ${err.message}`);
});
```

## startMoving

```TypeScript
startMoving(): Promise<void>
```

Sets whether the word selection panel can be dragged along with the mouse, touchpad, or touchscreen. The panel automatically stops moving after the pointer is released. This API can be called only after a **Panel** instance is obtained by calling [createPanel](arkts-basicservices-selectionmanager-createpanel-f.md). This API uses a promise to return the result. This API must be called in the **onTouch** callback, and the event type must be **TouchType.Down**.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.SelectionInput.Selection

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [33600001](../errorcode-selection.md#33600001-word-selection-service-invocation-error) | Selection service invocation exception. |
| [33600002](../errorcode-selection.md#33600002-word-selection-panel-has-been-destroyed) | This selection window has been destroyed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// This code must be placed in build() of the ArkUI page component. RelativeContainer is a built-in component of ArkUI. TouchEvent and TouchType are built-in types of ArkUI.
RelativeContainer() {
  /* 
   * Page layout content, which should be defined based on your actual needs.
   */
}
.onTouch((event: TouchEvent) => {
  if (event.type === TouchType.Down) {
    if (selectionPanel !== undefined) {
      // Enable the word selection panel to be dragged and moved with the mouse, touchpad, or touchscreen. selectionPanel is the panel instance created by createPanel.
      selectionPanel.startMoving().then(() => {
        console.info('Succeeded in startMoving the panel.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to startMoving panel. Error code: ${err.code}, error message: ${err.message}`);
      });
    }
  }
})
```
