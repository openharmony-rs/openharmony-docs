# createPanel

## Modules to Import

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';
```

## createPanel

```TypeScript
function createPanel(ctx: Context, info: PanelInfo): Promise<Panel>
```

Creates a word selection panel, which is used to display the service-related operation UI or text processing result. After the panel is used, call [destroyPanel](arkts-basicservices-selectionmanager-destroypanel-f.md) to destroy the panel and release resources. This API uses a promise to return the result.

Only one [MENU_PANEL](arkts-basicservices-selectioninput-selectionpanel-paneltype-e.md) and one [MAIN_PANEL](arkts-basicservices-selectioninput-selectionpanel-paneltype-e.md) can be created for one word selection application.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.SelectionInput.Selection

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ctx | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context that the current word selection panel depends on, which is provided by **SelectionExtensionAbility**. |
| info | [PanelInfo](arkts-basicservices-selectioninput-selectionpanel-panelinfo-i.md) | Yes | Configuration information of the word selection panel, which is used to specify the panel type, position, width, and height. Only one **MENU_PANEL** and one **MAIN_PANEL** can be created for one word selection app. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Panel](arkts-basicservices-selectionmanager-panel-i.md)&gt; | Promise used to return the **Panel** object created, which can be used to set, display, hide, and move the panel, and subscribe to events. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [33600001](../errorcode-selection.md#33600001-word-selection-service-invocation-error) | Selection service invocation exception. |
| [33600003](../errorcode-selection.md#33600003-api-caller-and-word-selection-application-mismatched) | The application calling the API does not match the application selected in the system settings. |

**Examples**

```TypeScript
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
    // Configure the word selection panel, including the panel type, position, and size.
    let panelInfo: PanelInfo = {
      panelType: PanelType.MENU_PANEL,
      x: 0,
      y: 0,
      width: 500,
      height: 200
    };
    let selectionPanel: selectionManager.Panel | undefined = undefined;
    // Create a word selection panel. Obtain this.context by inheriting SelectionExtensionAbility.
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
