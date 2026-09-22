# create

## Modules to Import

```TypeScript
import { PiPWindow } from '@kit.ArkUI';
```

## create

```TypeScript
function create(config: PiPConfiguration): Promise<PiPController>
```

Creates a PiP controller. This API uses a promise to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [PiPConfiguration](arkts-arkui-pipwindow-pipconfiguration-i.md) | Yes | Options for creating the PiP controller. This parameter cannot be empty, and **context** and **componentController** that are used to construct this parameter cannot be empty. When constructing this parameter, **templateType** (if specified) must be a value defined in [PiPTemplateType](arkts-arkui-pipwindow-piptemplatetype-e.md), and **controlGroups** (if specified) must match the value of **templateType**. For details, see [PiPControlGroup](arkts-arkui-pipwindow-pipcontrolgroup-t.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PiPController](arkts-arkui-pipwindow-pipcontroller-i.md)&gt; | Promise used to return the PiP controller. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { BuilderNode, FrameNode, NodeController, UIContext } from '@kit.ArkUI';

class Params {
  text: string = '';
  constructor(text: string) {
    this.text = text;
  }
}

// You can use the @Builder decorator to construct layouts.
@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(20)
      .fontColor(Color.Red)
  }
  .width('100%') // The PiP window is displayed at full size in the width direction.
  .height('100%') // The PiP window is displayed at full size in the height direction.
}

// You can extend NodeController to customize the UI controller.
class TextNodeController extends NodeController {
  private message: string;
  private textNode: BuilderNode<[Params]> | null = null;
  constructor(message: string) {
    super();
    this.message = message;
  }

  // Use BuilderNode to load the custom layouts.
  makeNode(context: UIContext): FrameNode | null {
    this.textNode = new BuilderNode(context);
    this.textNode.build(wrapBuilder<[Params]>(buildText), new Params(this.message));
    return this.textNode.getFrameNode();
  }

  // You can customize this method to update layouts.
  update(message: string) {
    console.info(`update message: ${message}`);
    if (this.textNode !== null) {
      this.textNode.update(new Params(message));
    }
  }
}

@Entry
@Component
struct Index {
    private message: string = 'createPiP';
    private pipController: PiPWindow.PiPController | undefined = undefined;
    private mXComponentController: XComponentController = new XComponentController(); // Use the mXComponentController to initialize the XComponent: XComponent( {id: 'video', type: 'surface', controller: mXComponentController} ). This ensures that the XComponent content can be migrated to the PiP window.
    private nodeController: TextNodeController = new TextNodeController('this is custom UI');
    private navId: string = "page_1"; // The navigation ID of the current page is page_1. For details, see the definition of PiPConfiguration. The navigation name is customized.
    private contentWidth: number = 800; // The content width is 800 px.
    private contentHeight: number = 600; // The content height is 600 px.
    private pageId: number = this.getUniqueId(); // Obtain the ID of the current page.
    private para: Record<string, number> = { 'PropA': 47 };
    private localStorage: LocalStorage = new LocalStorage(this.para);
    private res: boolean = this.localStorage.setOrCreate('PropB', 121);
    private defaultWindowSizeType: number = 1; // Set the window to be a small window when first pulled up in PiP.
    private cornerAdsorptionEnabled: boolean = true;
    private config: PiPWindow.PiPConfiguration = {
        context: this.getUIContext().getHostContext() as Context,
        componentController: this.mXComponentController,
        navigationId: this.navId,
        handleId: this.pageId,
        templateType: PiPWindow.PiPTemplateType.VIDEO_PLAY,
        contentWidth: this.contentWidth,
        contentHeight: this.contentHeight,
        controlGroups: [PiPWindow.VideoPlayControlGroup.VIDEO_PREVIOUS_NEXT],
        customUIController: this.nodeController, // Optional. Set this parameter if you want to display the custom UI at the top of the PiP window.
        localStorage: this.localStorage, // Optional. Set this parameter if you want to track the main window instance.
        defaultWindowSizeType: this.defaultWindowSizeType, // Optional. If you need to configure the default window size upon launch, set this parameter.
        cornerAdsorptionEnabled: this.cornerAdsorptionEnabled, // Optional. The default value is true. If you do not want the PiP window to automatically snap to screen corners, set this parameter to false.
    };

    createPiP() {
        let promise: Promise<PiPWindow.PiPController> = PiPWindow.create(this.config);  // Create a PiP controller.
        promise.then((data: PiPWindow.PiPController) => {
            this.pipController = data;
            console.info(`Succeeded in creating pip controller. Data:${data}`);
        }).catch((err: BusinessError) => {
            console.error(`Failed to create pip controller. Cause:${err.code}, message:${err.message}`);
        });
    }

    // This is for function testing only. In actual development, you should design components according to the service requirements.
    build() {
        RelativeContainer() {
            Button(this.message)
                .onClick(() => {
                    this.createPiP();
                })
        }
    }
}
```


<a id="create-1"></a>

## create

```TypeScript
function create(config: PiPConfiguration, contentNode: typeNode.XComponent): Promise<PiPController>
```

Creates a PiP controller. This API uses **typeNode** to add a custom UI node for PiP. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [PiPConfiguration](arkts-arkui-pipwindow-pipconfiguration-i.md) | Yes | Options for creating the PiP controller. This parameter cannot be empty, and **context** that is used to construct this parameter cannot be empty. When constructing this parameter, **templateType** (if specified) must be a value defined in [PiPTemplateType](arkts-arkui-pipwindow-piptemplatetype-e.md), and **controlGroups** (if specified) must match the value of **templateType**. For details, see [PiPControlGroup](arkts-arkui-pipwindow-pipcontrolgroup-t.md). |
| contentNode | [typeNode.XComponent](arkts-arkui-typenode-xcomponent-t.md) | Yes | Content to be rendered in the PiP window. The parameter value cannot be empty. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PiPController](arkts-arkui-pipwindow-pipcontroller-i.md)&gt; | Promise used to return the PiP controller. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { PiPWindow, typeNode, UIContext } from '@kit.ArkUI';

@Entry
@Component
struct Index {
    private message = 'createPiP'
    private pipController: PiPWindow.PiPController | undefined = undefined;
    private xComponentController: XComponentController = new XComponentController();
    private context: UIContext | undefined = this.getUIContext(); // You can pass UIContext or use this.getUIContext() in the layout to assign a valid value to context.
    private contentWidth: number = 800; // The content width is 800 px.
    private contentHeight: number = 600; // The content height is 600 px.
    private config: PiPWindow.PiPConfiguration = {
        context: this.getUIContext().getHostContext() as Context,
        componentController: this.xComponentController,
        templateType: PiPWindow.PiPTemplateType.VIDEO_PLAY,
        contentWidth: this.contentWidth,
        contentHeight: this.contentHeight,
    };
    private options: XComponentOptions = {
        type: XComponentType.SURFACE,
        controller: this.xComponentController
    }
    private xComponent = typeNode.createNode(this.context, 'XComponent', this.options); // Create an XComponent node to render the PiP content.

    createPiP() {
        let promise: Promise<PiPWindow.PiPController> = PiPWindow.create(this.config, this.xComponent); // Use typeNode to create a PiP controller.
        promise.then((data: PiPWindow.PiPController) => {
            this.pipController = data;
            console.info(`Succeeded in creating pip controller. Data:${data}`);
        }).catch((err: BusinessError) => {
            console.error(`Failed to create pip controller. Cause:${err.code}, message:${err.message}`);
        });
    }

    // This is for function testing only. In actual development, you should design components according to the service requirements.
    build() {
        RelativeContainer() {
            Button(this.message)
                .onClick(() => {
                    this.createPiP();
                })
        }
    }
}
```
