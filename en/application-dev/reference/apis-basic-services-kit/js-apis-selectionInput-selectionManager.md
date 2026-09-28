# @ohos.selectionInput.selectionManager (Word Selection Management)

<!--Kit: Basic Services Kit-->
<!--Subsystem: SelectionInput-->
<!--Owner: @zl_startup-->
<!--Designer: @zl_startup-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=70b7aed6929032961b85d9a3537fc6d090c1285e translatedAt=2026-09-09T12:05:11.265Z pushedAt=2026-09-09T12:09:55.281Z -->

This module provides word selection management capabilities, including creating, displaying, moving, hiding, and destroying panels, listening for word selection events using a mouse or touchpad, and retrieving the selected text. The typical usage process is as follows:
1. Call [on('selectionCompleted')](#selectionmanageronselectioncompleted) to subscribe to the selection completion event.
2. In the callback, call [getSelectionContent](#getselectioncontent) to obtain the selected text.
3. Call [createPanel](#createpanel) to create a word selection panel.
4. Call [setUiContent](#setuicontent) to load the page content.
5. Call [moveToGlobalDisplay](#movetoglobaldisplay) to move the panel to the specified position.
6. Call [show](#show) to display the panel.
7. Call [destroyPanel](#destroypanel) to destroy the panel.
8. Call [off('selectionCompleted')](#selectionmanageroffselectioncompleted) to unsubscribe from the selection completion event.

> **NOTE**
>
> - This module supports both ArkTS-Dyn and ArkTS-Sta.
> - The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This module is supported only on PCs/2-in-1 devices. You can use **canIUse('SystemCapability.SelectionInput.Selection')** to check whether the current device supports this function.
> - APIs of this module can be called only by apps that integrate the extension ability for word selection. For details about how to implement the extension ability for word selection, see [SelectionExtensionAbility](js-apis-selectionInput-selectionExtensionAbility.md).

## Modules to Import

```ts
import selectionManager from '@ohos.selectionInput.selectionManager';
```

## selectionManager

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Dyn start version:** 24

**ArkTS-Sta start version:** 24

### selectionManager.on('selectionCompleted')

on(type: 'selectionCompleted', callback: Callback\<SelectionInfo>): void

Subscribes to the word selection completion event. This API is used together with [off('selectionCompleted')](#selectionmanageroffselectioncompleted). [off('selectionCompleted')](#selectionmanageroffselectioncompleted) is used to unsubscribe from the event.

**ArkTS mode:** This API is only applicable to ArkTS-Dyn.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Dyn start version:** 24

**Parameters**

| Name     | Type                                        | Mandatory | Description                                           |
| -------- | ------------------------------------------- | --------- | ---------------------------------------------- |
| type     | string                                      | Yes   | Sets the listener type. The value is fixed at 'selectionCompleted'. |
| callback | Callback\<[SelectionInfo](#selectioninfo)> | Yes   | Callback invoked to return the selection event information [SelectionInfo](#selectioninfo). This callback is triggered only when the user selects text (double-click/triple-click/drag) with the mouse or touchpad and then presses the Ctrl key.       |

**Error codes**

For details about the following error codes, see [Word Selection Error Codes](errorcode-selection.md). For details about other common error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                       |
| ---------- | ----------------------------- |
| 33600003   | The application calling the API does not match the application selected in the system settings. |

**Example**

```ts
import { selectionManager } from '@kit.BasicServicesKit';

try {
  // Subscribe to the selection completion event.
  selectionManager.on('selectionCompleted', (info: selectionManager.SelectionInfo) => {
    console.info('Enter the callback function.');
  });
} catch (err) {
  console.error(`Failed to register selectionCompleted callback. Error code: ${err.code}, error message: ${err.message}`);
}
```

### onSelectionComplete

onSelectionComplete(callback: Callback\<SelectionInfo>): void

Subscribes to the selection completion event. Used together with [offSelectionComplete](#offselectioncomplete) to unsubscribe.

**ArkTS mode:** This API is only applicable to ArkTS-Sta.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Sta Since Version:** 24

**Parameters**

| Name     | Type                                        | Mandatory | Description                                           |
| -------- | ------------------------------------------- | --------- | ---------------------------------------------- |
| callback | Callback\<[SelectionInfo](#selectioninfo)> | Yes   | Callback invoked to return the selection event information [SelectionInfo](#selectioninfo). This callback is triggered only when the user selects text (double-click/triple-click/drag) with the mouse or touchpad and then presses the Ctrl key.       |

**Error Code**

For details about the following error codes, see [Word Selection Error Codes](errorcode-selection.md). For details about other common error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                       |
| ---------- | ----------------------------- |
| 33600003   | The application calling the API does not match the application selected in the system settings. |

**Example**

```ts
import selectionManager from '@ohos.selectionInput.selectionManager';

try {
  // Subscribe to the selection completion event.
  selectionManager.onSelectionComplete((info: selectionManager.SelectionInfo) => {
    console.info(`SelectionInfo: ${JSON.stringify(info)}`);
  });
} catch (err) {
  console.error(`Failed to register selectionCompleted callback. Error code: ${err.code}, error message: ${err.message}`);
}
```

### selectionManager.off('selectionCompleted')

off(type: 'selectionCompleted', callback?: Callback\<SelectionInfo>): void

Unsubscribes from the word selection completion event. This API is used together with [on('selectionCompleted')](#selectionmanageronselectioncompleted).

**ArkTS mode:** This API is only applicable to ArkTS-Dyn.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Dyn start version:** 24

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| type | string | Yes | Type of the event to unsubscribe from. The value is fixed to 'selectionCompleted'. |
| callback | Callback\<[SelectionInfo](#selectioninfo)> | No | Callback function to cancel (that is, the callback instance previously used for subscription through the on method). If this parameter is not filled in, all callback events corresponding to the type are unsubscribed from. |

**Example**

```ts
import { selectionManager } from '@kit.BasicServicesKit';

// Define the callback function for the selection completion event, used for subscription and unsubscription.
let selectionChangeCallback = (info: selectionManager.SelectionInfo) => {
  console.info('Enter the callback function.');
};

// Subscribe to the selection completion event callback first to prepare for subsequent unsubscription.
selectionManager.on('selectionCompleted', selectionChangeCallback);
try {
  // Unsubscribe from the selection completion event.
  selectionManager.off('selectionCompleted', selectionChangeCallback);
} catch (err) {
  console.error(`Failed to unregister selectionCompleted. Error code: ${err.code}, error message: ${err.message}`);
}
```

### offSelectionComplete

offSelectionComplete(callback?: Callback\<SelectionInfo>): void

Unsubscribes from the selection complete event. This API is used together with [onSelectionComplete](#onselectioncomplete).

**ArkTS mode:** This API is only applicable to ArkTS-Sta.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Sta since version:** 24

**Parameters**

| Name   | Type                                        | Mandatory | Description                                                         |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback\<[SelectionInfo](#selectioninfo)> | No   | Callback for the selection complete event (that is, the callback instance previously used to subscribe through the onSelectionComplete method). If this parameter is not specified, all callbacks subscribed to the event are unsubscribed. |

**Example**

```ts
import selectionManager from '@ohos.selectionInput.selectionManager';

// Define the callback function for the selection complete event, used for subscription and unsubscription.
let selectionChangeCallback = (info: selectionManager.SelectionInfo) => {
  console.info(`Enter the callback function.`);
};

// Subscribe to the selection complete event callback first to prepare for the subsequent unsubscription.
selectionManager.onSelectionComplete(selectionChangeCallback);
try {
  // Unsubscribe from the selection complete event.
  selectionManager.offSelectionComplete(selectionChangeCallback);
} catch (err) {
  console.error(`Failed to unregister selectionCompleted. Error code: ${err.code}, error message: ${err.message}`);
}
```

### getSelectionContent()

getSelectionContent(): Promise\<string>

Obtains the content of the selected text. This API uses a promise to return the result. This API must be called in the [on('selectionCompleted')](#selectionmanageronselectioncompleted) callback and is valid only after the word selection completion event is triggered.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Dyn start version:** 24

**ArkTS-Sta start version:** 24

**Return value**
| Type   | Description                                                                 |
| ------- | ------------------------------------------------------------------ |
| Promise\<string> | Promise used to return the content of the selected text.  |

**Error codes**

For details about the following error codes, see [Word Selection Error Codes](errorcode-selection.md). For details about other common error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                       |
| ---------- | ----------------------------- |
| 33600001   | Selection service invocation exception. |
| 33600004   | The interface is called too frequently. |
| 33600005   | The interface is called at the wrong time. |
| 33600006   | The current application is prohibited from accessing content. |
| 33600007   | The length of selected content is out of range. |
| 33600008   | Getting the selected content times out. |

**Example**

ArkTS-Dyn example:
```ts
import { selectionManager } from '@kit.BasicServicesKit';

// Subscribe to the selection completion event and obtain the selected text in the callback.
selectionManager.on('selectionCompleted', async (info: selectionManager.SelectionInfo) => {
  try {
    // Obtain the selected text content.
    let content = await selectionManager.getSelectionContent();
    console.info(`Succeeded in getting selection content: ${content}`);
  } catch (err) {
    console.error(`Failed to get selection content. Error code: ${err.code}, error message: ${err.message}`);
  }
});
```

ArkTS-Sta example:
```ts
import selectionManager from '@ohos.selectionInput.selectionManager';

// Subscribe to the selection completion event and obtain the selected text in the callback.
selectionManager.onSelectionComplete((info: selectionManager.SelectionInfo) => {
  try {
    getSelectionContentAsync().catch((err) => {
      console.error(`Failed to get selection content. Error code: ${err.code}, error message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to get selection content. Error code: ${err.code}, error message: ${err.message}`);
  }
});

async function getSelectionContentAsync(): Promise<void> {
  // Obtain the selected text content.
  const content = await selectionManager.getSelectionContent();
  console.info(`Succeeded in getting selection content: ${content}`);
}

```

### createPanel

createPanel(ctx: Context, info: PanelInfo): Promise\<Panel>

Creates a word selection panel, which is used to display the service-related operation UI or text processing result. After the panel is used, call [destroyPanel](#destroypanel) to destroy the panel and release resources. This API uses a promise to return the result.

Only one [MENU_PANEL](js-apis-selectionInput-selectionPanel.md#paneltype) and one [MAIN_PANEL](js-apis-selectionInput-selectionPanel.md#paneltype) can be created for one word selection application.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Dyn start version:** 24

**ArkTS-Sta start version:** 24

**Parameters**

| Name   | Type        | Mandatory | Description                     |
| ------- | ----------- | ---- | ------------------------ |
| ctx     | [Context](../apis-ability-kit/js-apis-inner-application-context.md#context) | Yes   | Context information that the current selection panel depends on. It must be the context provided by SelectionExtensionAbility. |
| info    | [PanelInfo](js-apis-selectionInput-selectionPanel.md#panelinfo)   | Yes   | Configuration information of the selection panel, used to specify the panel type, position, width, and height. A single selection application can create only one MENU_PANEL and one MAIN_PANEL. |

**Return value**
| Type   | Description                                                                 |
| ------- | ------------------------------------------------------------------ |
| Promise\<[Panel](#panel)> | Promise used to return the **Panel** object created, which can be used to set, display, hide, and move the panel, and subscribe to events.  |

**Error codes**

For details about the following error codes, see [Word Selection Error Codes](errorcode-selection.md). For details about other common error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                       |
| ---------- | ----------------------------- |
| 33600001   | Selection service invocation exception. |
| 33600003   | The application calling the API does not match the application selected in the system settings. |

**Example**

ArkTS-Dyn example:
```ts
import { selectionManager, SelectionExtensionAbility, PanelInfo, PanelType, BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';
import { Want } from '@kit.AbilityKit';

class SelectionAbilityStub extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteMessageRequest(
    code: number,
    data: rpc.MessageSequence,
    reply: rpc.MessageSequence,
    options: rpc.MessageOption
  ): boolean | Promise<boolean> {
    return true;
  }
}

class ServiceExtAbility extends SelectionExtensionAbility {
  onConnect(want: Want): rpc.RemoteObject {
    // Configure the selection panel information, including the panel type, position, and size.
    let panelInfo: PanelInfo = {
      panelType: PanelType.MENU_PANEL,
      x: 0,
      y: 0,
      width: 500,
      height: 200
    };
    let selectionPanel: selectionManager.Panel | undefined = undefined;
    // Create the selection panel. this.context is obtained by inheriting SelectionExtensionAbility.
    selectionManager.createPanel(this.context, panelInfo)
      .then((panel: selectionManager.Panel) => {
        selectionPanel = panel;
        console.info('Succeed in creating panel.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to create panel. Error code: ${err.code}, error message: ${err.message}`);
    });
    return new SelectionAbilityStub('remote');
  }
}
export default ServiceExtAbility;
```

ArkTS-Sta example:
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import SelectionExtensionAbility from '@ohos.selectionInput.SelectionExtensionAbility';
import { PanelInfo, PanelType } from '@ohos.selectionInput.SelectionPanel';
import selectionManager from '@ohos.selectionInput.selectionManager';
import rpc from '@ohos.rpc';
import { Want } from '@kit.AbilityKit';

class SelectionAbilityStub extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteMessageRequest(
    code: number,
    data: rpc.MessageSequence,
    reply: rpc.MessageSequence,
    options: rpc.MessageOption
  ): boolean | Promise<boolean> {
    return true;
  }
}

class ServiceExtAbility extends SelectionExtensionAbility {
  onConnect(want: Want): rpc.RemoteObject {
    // Configure the selection panel information, including the panel type, position, and size.
    let panelInfo: PanelInfo = {
      panelType: PanelType.MENU_PANEL,
      x: 0,
      y: 0,
      width: 500,
      height: 200
    };
    let selectionPanel: selectionManager.Panel | undefined = undefined;
    // Create the selection panel.
    selectionManager.createPanel(this.context, panelInfo)
      .then((panel: selectionManager.Panel) => {
        selectionPanel = panel;
        console.info('Succeed in creating panel.');
      }).catch((err) => {
      console.error(`Failed to create panel. Error code: ${err.code}, error message: ${err.message}`);
    });
    return new SelectionAbilityStub('remote');
  }
}
export default ServiceExtAbility;
```

### destroyPanel

destroyPanel(panel: Panel): Promise\<void>

Destroys the word selection panel. This API is used together with [createPanel](#createpanel) to destroy the panel object created by **createPanel()**. This API uses a promise to return the result.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Dyn Since Version:** 24

**ArkTS-Sta Since Version:** 24

**Parameters**

| Name   | Type        | Mandatory | Description                     |
| ---------| ----------- | ---- | ------------------------ |
| panel    | [Panel](#panel)       | Yes   | Panel object to destroy.      |

**Return value**
| Type    | Description                                                                 |
| ------- | -------------------------------------------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the following error codes, see [Word Selection Error Codes](errorcode-selection.md). For details about other common error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                       |
| ---------- | ----------------------------- |
| 33600001   | Selection service invocation exception. |

**Example**

ArkTS-Dyn example:
```ts
import { selectionManager, SelectionExtensionAbility, PanelInfo, PanelType, BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';
import { Want } from '@kit.AbilityKit';

class SelectionAbilityStub extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteMessageRequest(
    code: number,
    data: rpc.MessageSequence,
    reply: rpc.MessageSequence,
    options: rpc.MessageOption
  ): boolean | Promise<boolean> {
    return true;
  }
}

class ServiceExtAbility extends SelectionExtensionAbility {
  onConnect(want: Want): rpc.RemoteObject {
    // Configure the selection panel information, including the panel type, position, and size.
    let panelInfo: PanelInfo = {
      panelType: PanelType.MENU_PANEL,
      x: 0,
      y: 0,
      width: 500,
      height: 200
    };
    let selectionPanel: selectionManager.Panel | undefined = undefined;
    // Create the selection panel first to obtain the panel instance for subsequent destruction. this.context is obtained by inheriting SelectionExtensionAbility.
    selectionManager.createPanel(this.context, panelInfo)
      .then((panel: selectionManager.Panel) => {
        console.info('Succeed in creating panel.');
        selectionPanel = panel;
        try {
          if (selectionPanel) {
            // Destroy the selection panel.
            selectionManager.destroyPanel(selectionPanel).then(() => {
              console.info('Succeed in destroying panel.');
            }).catch((err: BusinessError) => {
              console.error(`Failed to destroy panel. Error code: ${err.code}, error message: ${err.message}`);
            });
          }
        } catch (err) {
          console.error(`Failed to destroy panel. Error code: ${err.code}, error message: ${err.message}`);
        }
      }).catch((err: BusinessError) => {
        console.error(`Failed to create panel. Error code: ${err.code}, error message: ${err.message}`);
    });
    return new SelectionAbilityStub('remote');
  }
}
export default ServiceExtAbility;
```

ArkTS-Sta example:
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import SelectionExtensionAbility from '@ohos.selectionInput.SelectionExtensionAbility';
import { PanelInfo, PanelType } from '@ohos.selectionInput.SelectionPanel';
import selectionManager from '@ohos.selectionInput.selectionManager';
import rpc from '@ohos.rpc';
import { Want } from '@kit.AbilityKit';

class SelectionAbilityStub extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteMessageRequest(
    code: number,
    data: rpc.MessageSequence,
    reply: rpc.MessageSequence,
    options: rpc.MessageOption
  ): boolean | Promise<boolean> {
    return true;
  }
}

class ServiceExtAbility extends SelectionExtensionAbility {
  onConnect(want: Want): rpc.RemoteObject {
    // Configure the selection panel information, including the panel type, position, and size.
    let panelInfo: PanelInfo = {
      panelType: PanelType.MENU_PANEL,
      x: 0,
      y: 0,
      width: 500,
      height: 200
    };
    let selectionPanel: selectionManager.Panel | undefined = undefined;
    // Create the selection panel first to obtain the panel instance for subsequent destruction.
    selectionManager.createPanel(this.context, panelInfo)
      .then((panel: selectionManager.Panel) => {
        console.info('Succeed in creating panel.');
        selectionPanel = panel;
        try {
          if (selectionPanel) {
            // Destroy the selection panel.
            selectionManager.destroyPanel(selectionPanel as selectionManager.Panel).then(() => {
              console.info('Succeed in destroying panel.');
            }).catch((err) => {
              console.error(`Failed to destroy panel. Error code: ${err.code}, error message: ${err.message}`);
            });
          }
        } catch (err) {
          console.error(`Failed to destroy panel. Error code: ${err.code}, error message: ${err.message}`);
        }
      }).catch((err) => {
      console.error(`Failed to create panel. Error code: ${err.code}, error message: ${err.message}`);
    });
    return new SelectionAbilityStub('remote');
  }
}
export default ServiceExtAbility;
```

## SelectionInfo

Defines the information of a word selection event.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Dyn start version:** 24

**ArkTS-Sta start version:** 24

| Name      | Type | Read-only | Optional | Description         |
| --------- | -------- | ---- | ---- | ------------ |
| selectionType |[SelectionType](#selectiontype)   | No   | No   | Enum value of the selection mode. |
| startDisplayX |ArkTS-Dyn:number<br>ArkTS-Sta:int| No   | No   | X-axis coordinate of the selection start position on the screen, in px. |
| startDisplayY |ArkTS-Dyn:number<br>ArkTS-Sta:int| No   | No   | Y-axis coordinate of the selection start position on the screen, in px. |
| endDisplayX   |ArkTS-Dyn:number<br>ArkTS-Sta:int| No   | No   | X-axis coordinate of the selection end position on the screen, in px. |
| endDisplayY   |ArkTS-Dyn:number<br>ArkTS-Sta:int| No   | No   | Y-axis coordinate of the selection end position on the screen, in px. |
| startWindowX  |ArkTS-Dyn:number<br>ArkTS-Sta:int| No   | No   | X-axis coordinate of the selection start position on the window, in px. |
| startWindowY  |ArkTS-Dyn:number<br>ArkTS-Sta:int| No   | No   | Y-axis coordinate of the selection start position on the window, in px. |
| endWindowX    |ArkTS-Dyn:number<br>ArkTS-Sta:int| No   | No   | X-axis coordinate of the selection end position on the window, in px. |
| endWindowY    |ArkTS-Dyn:number<br>ArkTS-Sta:int| No   | No   | Y-axis coordinate of the selection end position on the window, in px. |
| displayID     |ArkTS-Dyn:number<br>ArkTS-Sta:int| No   | No   | Screen ID of the window of the selected application. |
| windowID      |ArkTS-Dyn:number<br>ArkTS-Sta:int| No   | No   | Window ID of the selected application. |
| bundleName    |string| No   | No   | Bundle name of the selected application. |

## Panel

Describes a **Panel** object, which is created using [createPanel](#createpanel). This method can be used to set, display, hide, and move the panel, as well as subscribe to events. It is applicable to scenarios where a custom operation UI needs to be displayed to users after word selection is complete.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Dyn start version:** 24

**ArkTS-Sta start version:** 24

In the following APIs, you must first use [createPanel](#createpanel) to obtain a **Panel** instance, and then call the APIs using the obtained instance.

### setUiContent

setUiContent(path: string): Promise\<void>

Sets the UI content for the current word selection panel, for example, to display translation results, search suggestions, or custom action buttons. This API can be called only after a **Panel** instance is obtained by calling [createPanel](#createpanel). This API uses a promise to return the result.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Dyn Since Version:** 24

**ArkTS-Sta Since Version:** 24

**Parameters**

| Name   | Type                   | Mandatory | Description     |
| -------- | ---------------------- | ---- | -------- |
| path | string | Yes   |  Path of the page content to be loaded into the panel. In the stage model, this path must be added to the resources/base/profile/main_pages.json file of the project. The FA model is not supported. |

**Return value**

| Type   | Description                             |
| ------- | ------------------------------ |
| Promise\<void> | Promise that returns no value.  |

**Error codes:**

For details about the following error codes, see [Word Selection Error Codes](errorcode-selection.md). For details about other common error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                       |
| ---------- | ----------------------------- |
| 33600001   | Selection service invocation exception. |
| 33600002   | This selection window has been destroyed. |

**Example**

ArkTS-Dyn example:
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Load the page content for the selection panel. selectionPanel is the panel instance created by createPanel.
  selectionPanel.setUiContent('pages/Index').then(() => {
    console.info('Succeeded in setting the content.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to setUiContent. Error code: ${err.code}, error message: ${err.message}`);
  });
} catch (err) {
  console.error(`Failed to setUiContent. Error code: ${err.code}, error message: ${err.message}`);
}
```

ArkTS-Sta example:
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Load the page content for the selection panel. selectionPanel is the panel instance created by createPanel.
  selectionPanel?.setUiContent('pages/Index').then(() => {
    console.info('Succeeded in setting the content.');
  }).catch((err) => {
    console.error(`Failed to setUiContent. Error code: ${err.code}, error message: ${err.message}`);
  });
} catch (err) {
  console.error(`Failed to setUiContent. Error code: ${err.code}, error message: ${err.message}`);
}
```

### show

show(): Promise\<void>

Shows the word selection panel. This API is used together with [hide](#hide). This API can be called only after a **Panel** instance is obtained by calling [createPanel](#createpanel). This API uses a promise to return the result.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Dyn start version:** 24

**ArkTS-Sta start version:** 24

**Return value**

| Type   | Description                             |
| ------- | ------------------------------ |
| Promise\<void> | Promise that returns no value.  |

**Error codes**

For details about the following error codes, see [Word Selection Error Codes](errorcode-selection.md). For details about other common error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                       |
| ---------- | ----------------------------- |
| 33600001   | Selection service invocation exception. |
| 33600002   | This selection window has been destroyed. |

**Example**

ArkTS-Dyn example:
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Display the selection panel. selectionPanel is the panel instance created by createPanel.
selectionPanel.show().then(() => {
  console.info('Succeeded in showing the panel.');
}).catch((err: BusinessError) => {
  console.error(`Failed to show panel. Error code: ${err.code}, error message: ${err.message}`);
});
```

ArkTS-Sta example:
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Display the selection panel. selectionPanel is the panel instance created by createPanel.
selectionPanel?.show().then(() => {
  console.info('Succeeded in showing the panel.');
}).catch((err) => {
  console.error(`Failed to show panel. Error code: ${err.code}, error message: ${err.message}`);
});
```

### hide

hide(): Promise\<void>

Hides the word selection panel. This API is used together with [show](#show). This API can be called only after a **Panel** instance is obtained by calling [createPanel](#createpanel). This API uses a promise to return the result. If this API is not called proactively, the panel is automatically hidden when it loses focus.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Dyn start version:** 24

**ArkTS-Sta start version:** 24

**Return value**

| Type   | Description                             |
| ------- | ------------------------------ |
| Promise\<void> | Promise that returns no value.  |

**Error codes**

For details about the following error codes, see [Word Selection Error Codes](errorcode-selection.md). For details about other common error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                       |
| ---------- | ----------------------------- |
| 33600001   | Selection service invocation exception. |
| 33600002   | This selection window has been destroyed. |

**Example**

ArkTS-Dyn example:
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Hide the Selection Panel. selectionPanel is the panel instance created by createPanel.
selectionPanel.hide().then(() => {
  console.info('Succeeded in hiding the panel.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide panel. Error code: ${err.code}, error message: ${err.message}`);
});
```

ArkTS-Sta example:
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Hide the Selection Panel. selectionPanel is the panel instance created by createPanel.
selectionPanel?.hide().then(() => {
  console.info('Succeeded in hiding the panel.');
}).catch((err) => {
  console.error(`Failed to hide panel. Error code: ${err.code}, error message: ${err.message}`);
});
```

### startMoving

startMoving(): Promise\<void>

Sets whether the word selection panel can be dragged along with the mouse, touchpad, or touchscreen. The panel automatically stops moving after the pointer is released. This API can be called only after a **Panel** instance is obtained by calling [createPanel](#createpanel). This API uses a promise to return the result. This API must be called in the **onTouch** callback, and the event type must be **TouchType.Down**.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Dyn Since Version:** 24

**ArkTS-Sta Since Version:** 24

**Return value**

| Type   | Description                             |
| ------- | ------------------------------ |
| Promise\<void> | Promise that returns no value.  |

**Error Code:**

For details about the following error codes, see [Word Selection Error Codes](errorcode-selection.md). For details about other common error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                       |
| ---------- | ----------------------------- |
| 33600001   | Selection service invocation exception. |
| 33600002   | This selection window has been destroyed. |

**Example**

ArkTS-Dyn example:
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Place this code in the build() method of an ArkUI page component. RelativeContainer is a built-in ArkUI component, and TouchEvent and TouchType are built-in types of the ArkUI framework.
RelativeContainer() {
  /* 
   * Page layout content, which developers need to supplement based on actual requirements.
   */
}
.onTouch((event: TouchEvent) => {
  if (event.type === TouchType.Down) {
    if (selectionPanel !== undefined) {
      // Make the selection panel movable by dragging with the mouse, touchpad, or touch screen. selectionPanel is the panel instance created by createPanel.
      selectionPanel.startMoving().then(() => {
        console.info('Succeeded in startMoving the panel.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to startMoving panel. Error code: ${err.code}, error message: ${err.message}`);
      });
    }
  }
})
```

ArkTS-Sta example:
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Place this code in the build() method of an ArkUI page component. RelativeContainer is a built-in ArkUI component, and TouchEvent and TouchType are built-in types of the ArkUI framework.
RelativeContainer() {
  /* 
   * Page layout content, to be supplemented by the developer as needed.
   */
}
.onTouch((event: TouchEvent) => {
  if (event.type === TouchType.Down) {
    if (selectionPanel !== undefined) {
      // Enable the selection panel to be dragged to move its position with the mouse, touchpad, or touchscreen. selectionPanel is the panel instance created by createPanel.
      selectionPanel?.startMoving().then(() => {
        console.info('Succeeded in startMoving the panel.');
      }).catch((err) => {
        console.error(`Failed to startMoving panel. Error code: ${err.code}, error message: ${err.message}`);
      });
    }
  }
})
```

<!--Del-->
### moveTo<sup>(deprecated)</sup>

moveTo(x: number, y: number): Promise\<void>

Moves the word selection panel to the specified coordinates in the global coordinate system of the screen. The panel can be moved to an extended screen. This API can be called only after a **Panel** instance is obtained by calling [createPanel](#createpanel). This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 20 and deprecated since API version 24. You are advised to use [moveToGlobalDisplay](#movetoglobaldisplay) instead.

**System API**: This is a system API.

**ArkTS mode:** This API is only applicable to ArkTS-Dyn.

**System capability:** SystemCapability.SelectionInput.Selection

**ArkTS-Dyn start version:** 20

**Parameters**

| Name   | Type                   | Mandatory | Description     |
| -------- | ---------------------- | ---- | -------- |
| x | number | Yes   |X-axis coordinate of the target position in the global coordinate system of the screen, in px. The global coordinate system uses the top-left corner of the main screen as the origin, with the positive direction of the x-axis pointing right. The x coordinate of an extended screen may be negative depending on the screen layout.|
| y | number | Yes   |Y-axis coordinate of the target position in the global coordinate system of the screen, in px. The global coordinate system uses the top-left corner of the main screen as the origin, with the positive direction of the y-axis pointing down. The y coordinate of an extended screen may be negative depending on the screen layout.|

**Return value**

| Type   | Description                             |
| ------- | ------------------------------ |
| Promise\<void> | Promise that returns no value.  |

**Error Codes**

For details about the following error codes, see [Word Selection Error Codes](errorcode-selection.md). For details about other common error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                       |
| ---------- | ----------------------------- |
| 33600001   | Selection service invocation exception. |
| 33600002   | This selection window has been destroyed. |

**Example**
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Move the selection panel to the specified position on the screen. selectionPanel is the panel instance created by createPanel.
  selectionPanel.moveTo(200, 200).then(() => {
    console.info('Succeeded in moving the panel.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to move panel. Error code: ${err.code}, error message: ${err.message}`);
  });
} catch (err) {
  console.error(`Failed to move panel. Error code: ${err.code}, error message: ${err.message}`);
}
```
<!--DelEnd-->

### moveToGlobalDisplay

ArkTS-Dyn: moveToGlobalDisplay(x: number, y: number): Promise\<void>

ArkTS-Sta: moveToGlobalDisplay(x: int, y: int): Promise\<void>

Moves the word selection panel to the specified coordinates in the global coordinate system of the screen. The panel can be moved to an extended screen. This API can be called only after a **Panel** instance is obtained by calling [createPanel](#createpanel). This API uses a promise to return the result.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Dyn start version:** 24

**ArkTS-Sta start version:** 24

**Parameters**

| Name   | Type                   | Mandatory | Description     |
| -------- | ---------------------- | ---- | -------- |
| x | ArkTS-Dyn:number<br>ArkTS-Sta:int | Yes   |X-axis coordinate of the target position in the global coordinate system on the screen, in px. The global coordinate system uses the top-left corner of the main screen as the origin, with the positive x-axis pointing right. The x coordinate of an extended screen may be negative depending on the screen layout.|
| y | ArkTS-Dyn:number<br>ArkTS-Sta:int | Yes   |Y-axis coordinate of the target position in the global coordinate system on the screen, in px. The global coordinate system uses the top-left corner of the main screen as the origin, with the positive y-axis pointing down. The y coordinate of an extended screen may be negative depending on the screen layout.|

**Return value**

| Type   | Description                             |
| ------- | ------------------------------ |
| Promise\<void> | Promise that returns no value.  |

**Error Code**

For details about the following error codes, see [Word Selection Error Codes](errorcode-selection.md). For details about other common error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                       |
| ---------- | ----------------------------- |
| 33600001   | Selection service invocation exception. |
| 33600002   | This selection window has been destroyed. |

**Example**

ArkTS-Dyn example:
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Move the selection panel to the specified position on the screen. selectionPanel is the panel instance created by createPanel.
  selectionPanel.moveToGlobalDisplay(200, 200).then(() => {
    console.info('Succeeded in moving the panel.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to move panel. Error code: ${err.code}, error message: ${err.message}`);
  });
} catch (err) {
  console.error(`Failed to move panel. Error code: ${err.code}, error message: ${err.message}`);
}
```

ArkTS-Sta example:
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Move the selection panel to the specified position on the screen. selectionPanel is the panel instance created by createPanel.
  selectionPanel?.moveToGlobalDisplay(200, 200).then(() => {
    console.info('Succeeded in moving the panel.');
  }).catch((err) => {
    console.error(`Failed to move panel. Error code: ${err.code}, error message: ${err.message}`);
  });
} catch (err) {
  console.error(`Failed to move panel. Error code: ${err.code}, error message: ${err.message}`);
}
```

### on('destroyed')

on(type: 'destroyed', callback: Callback\<void>): void

Subscribes to the word selection panel destruction event. This API is used together with [off('destroyed')](#offdestroyed). This API can be called only after a **Panel** instance is obtained by calling [createPanel](#createpanel).

**ArkTS mode:** This API is only applicable to ArkTS-Dyn.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Dyn start version:** 24

**Parameters**

| Name     | Type                                        | Mandatory | Description                                           |
| -------- | ------------------------------------------- | --------- | ---------------------------------------------- |
| type     | string                                      | Yes   | Sets the listener type. The fixed value is 'destroyed'. |
| callback | Callback\<void> | Yes   | Callback function, triggered when [destroyPanel](#destroypanel) is called to destroy the panel.       |

**Example**
<!--code_no_check-->
```ts
try {
  // Subscribe to the selection panel destruction event. selectionPanel is the panel instance created by createPanel.
  selectionPanel.on('destroyed', () => {
    console.info('Panel has been destroyed.');
  });
} catch (err) {
  console.error(`Failed to register destroyed callback. Error code: ${err.code}, error message: ${err.message}`);
}
```

### onDestroy

onDestroy(callback: Callback\<void>): void

Subscribes to the word selection panel destruction event. This API is used together with [offDestroy](#offdestroy). This API can be called only after a **Panel** instance is obtained by calling [createPanel](#createpanel).

**ArkTS mode:** This API is only applicable to ArkTS-Sta.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Sta start version:** 24

**Parameters**

| Name   | Type                                        | Mandatory | Description                                           |
| -------- | ------------------------------------------- | ---- | ---------------------------------------------- |
| callback | Callback\<void> | Yes   | Callback invoked when the panel is destroyed by calling [destroyPanel](#destroypanel).       |

**Example**
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Subscribe to the word selection panel destruction event. selectionPanel is the panel instance created by createPanel.
  selectionPanel?.onDestroy(() => {
    console.info('Panel has been destroyed.');
  });
} catch (err) {
  console.error(`Failed to register destroyed callback. Error code: ${err.code}, error message: ${err.message}`);
}
```

### off('destroyed')

off(type: 'destroyed', callback?: Callback\<void>): void

Unsubscribes from the word selection panel destruction event. This API is used together with [on('destroyed')](#ondestroyed). This API can be called only after a **Panel** instance is obtained by calling [createPanel](#createpanel).

**ArkTS mode:** This API is only applicable to ArkTS-Dyn.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Dyn start version:** 24

**Parameters**

| Name     | Type                                        | Mandatory | Description                                                         |
| -------- | ------------------------------------------- | --------- | ------------------------------------------------------------ |
| type     | string                                      | Yes       | Type of the event to unsubscribe from. The value is fixed to 'destroyed'.               |
| callback | Callback\<void> | No        | Callback function to cancel (that is, the callback instance previously used when subscribing through the on method). If this parameter is not filled in, all callback events corresponding to the type are unsubscribed.|

**Example**
<!--code_no_check-->
```ts
try {
  // Unsubscribe from the selection panel destroy event. selectionPanel is the panel instance created by createPanel.
  selectionPanel.off('destroyed');
} catch (err) {
  console.error(`Failed to unregister destroyed. Error code: ${err.code}, error message: ${err.message}`);
}
```

### offDestroy

offDestroy(callback?: Callback\<void>): void

Unsubscribes from the selection panel destruction event. This API is used together with [onDestroy](#ondestroy). This API can be called only after a **Panel** instance is obtained by calling [createPanel](#createpanel).

**ArkTS mode:** This API is only applicable to ArkTS-Sta.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Sta start version:** 24

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback\<void> | No | Callback function to be canceled (that is, the callback instance previously used when subscribing through the onDestroy method). If this parameter is not filled in, all callback events corresponding to the subscription are canceled.|

**Example**
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Unsubscribe from the selection panel destruction event. selectionPanel is the panel instance created by createPanel.
  selectionPanel?.offDestroy();
} catch (err) {
  console.error(`Failed to unregister destroyed. Error code: ${err.code}, error message: ${err.message}`);
}
```

### on('hidden')

on(type: 'hidden', callback: Callback\<void>): void

Subscribes to the word selection panel hiding event. This API is used together with [off('hidden')](#offhidden). This event is triggered when the panel is hidden by calling [hide](#hide) or automatically hidden when it loses focus. This API can be called only after a **Panel** instance is obtained by calling [createPanel](#createpanel).

**ArkTS mode:** This API is only applicable to ArkTS-Dyn.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Dyn start version:** 24

**Parameters**

| Name     | Type                                        | Mandatory | Description                                           |
| -------- | ------------------------------------------- | --------- | ---------------------------------------------- |
| type     | string                                      | Yes   | Sets the listener type. The value is fixed to 'hidden'. |
| callback | Callback\<void> | Yes   | Callback function invoked when the panel is hidden. The panel can be hidden proactively by calling [hide](#hide), or automatically when it loses focus.       |

**Example**
<!--code_no_check-->
```ts
try {
  // Subscribe to the selection panel hidden event. selectionPanel is the panel instance created by createPanel.
  selectionPanel.on('hidden', () => {
    console.info('Panel has been hidden.');
  });
} catch (err) {
  console.error(`Failed to register hidden callback. Error code: ${err.code}, error message: ${err.message}`);
}
```

### onHide

onHide(callback: Callback\<void>): void

Subscribes to the selection panel hiding event. This API is used together with [offHide](#offhide). This API can be called only after a **Panel** instance is obtained by calling [createPanel](#createpanel).

**ArkTS mode:** This API is only applicable to ArkTS-Sta.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Sta start version:** 24

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ------------------------------------------- | ---- | ---------------------------------------------- |
| callback | Callback\<void> | Yes | Callback invoked when the panel is hidden. The panel can be hidden proactively by calling [hide](#hide), or automatically when it loses focus. |

**Example**
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Subscribe to the selection panel hiding event. selectionPanel is the panel instance created by createPanel.
  selectionPanel?.onHide(() => {
    console.info('Panel has been hidden.');
  });
} catch (err) {
  console.error(`Failed to register hidden callback. Error code: ${err.code}, error message: ${err.message}`);
}
```

### off('hidden')

off(type: 'hidden', callback?: Callback\<void>): void

Unsubscribes from the word selection panel hiding event. This API is used together with [on('hidden')](#onhidden). This API can be called only after a **Panel** instance is obtained by calling [createPanel](#createpanel).

**ArkTS mode:** This API is only applicable to ArkTS-Dyn.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Dyn start version:** 24

**Parameters**

| Name     | Type                                        | Mandatory | Description                                                         |
| -------- | ------------------------------------------- | --------- | ------------------------------------------------------------ |
| type     | string                                      | Yes       | Type of the event to unsubscribe from. The value is fixed to 'hidden'.               |
| callback | Callback\<void> | No        | Callback function to cancel (that is, the callback instance previously used when subscribing through the on method). If this parameter is not filled in, all callback events corresponding to the type are unsubscribed from. |

**Example**
<!--code_no_check-->
```ts
try {
  // Unsubscribe from the selection panel hidden event. selectionPanel is the panel instance created by createPanel.
  selectionPanel.off('hidden');
} catch (err) {
  console.error(`Failed to unregister hidden. Error code: ${err.code}, error message: ${err.message}`);
}
```

### offHide

offHide(callback?: Callback\<void>): void

Unsubscribes from the selection panel hiding event. This API is used together with [onHide](#onhide). This API can be called only after a **Panel** instance is obtained by calling [createPanel](#createpanel).

**ArkTS mode:** This API is only applicable to ArkTS-Sta.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Sta start version:** 24

**Parameters**

| Name   | Type                                        | Mandatory | Description                                                         |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback\<void> | No   | Callback function to be unsubscribed (that is, the callback instance previously used when subscribing through the onHide method). If this parameter is not filled in, all callback events corresponding to the subscription are unsubscribed. |

**Example**
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Unsubscribe from the selection panel hiding event. selectionPanel is the panel instance created by createPanel.
  selectionPanel?.offHide();
} catch (err) {
  console.error(`Failed to unregister hidden. Error code: ${err.code}, error message: ${err.message}`);
}
```

### SelectionType

Enumerates the word selection types.

**System capability:** SystemCapability.SelectionInput.Selection

**Model restriction**: This API can be used only in the stage model.

**ArkTS-Dyn start version:** 24

**ArkTS-Sta start version:** 24

| Name         | Value | Description               |
| ------------ | -- | ------------------ |
| MOUSE_MOVE | 1 | Word selection by sliding the mouse or touchpad. |
| DOUBLE_CLICK   | 2 | Word selection by double-clicking the mouse or touchpad. |
| TRIPLE_CLICK   | 3 | Word selection by triple-clicking the mouse or touchpad. |
