# bindController

## bindController

```TypeScript
export function bindController(node: FrameNode, controller: TextController, nodeType: 'Text'): void
```

Binds a [TextController](../arkts-components/arkts-arkui-text-comp-textcontroller-c.md) instance to a [Text](arkts-arkui-typenode-text-t.md) node. Cross-language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node for controller binding. |
| controller | [TextController](../arkts-components/arkts-arkui-text-comp-textcontroller-c.md) | Yes | **TextController** instance to bind. |
| nodeType | 'Text' | Yes | Node type. Set to **'Text'**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100023](../errorcode-node.md#100023-parameter-error) | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| [100021](../errorcode-node.md#100021-framenode-not-modifiable) | The FrameNode is not modifiable. |

**Examples**

```TypeScript
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  // Configure the TextController instance, which can be obtained from an external source.
  controller: TextController = new TextController()

  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // Create a Text node.
    let text = typeNode.createNode(uiContext, 'Text');
    text.initialize('Hello').fontColor(Color.Blue).fontSize(14);
    typeNode.getAttribute(text, 'Text')?.fontWeight(FontWeight.Bold)
    // Bind a TextController instance.
    typeNode.bindController(text, this.controller, 'Text');
    col.appendChild(text);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  @State line: number = 0
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('Text bindController Sample')
      NodeContainer(this.myNodeController)
      Text(`Current line count: ${this.line}`)
      Button(`Obtain Line Count`)
        .onClick(() => {
          this.line = this.myNodeController.controller.getLayoutManager().getLineCount()
        })
    }
  }
}
```


<a id="bindcontroller-1"></a>

## bindController

```TypeScript
export function bindController(node: FrameNode, controller: SwiperController, nodeType: 'Swiper'): void
```

Binds a [SwiperController](../arkts-components/arkts-arkui-swiper-comp-swipercontroller-c.md) instance to the [Swiper](arkts-arkui-typenode-swiper-t.md) node. Cross- language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node for controller binding. |
| controller | [SwiperController](../arkts-components/arkts-arkui-swiper-comp-swipercontroller-c.md) | Yes | **SwiperController** instance. |
| nodeType | 'Swiper' | Yes | Node type. Set to **'Swiper'**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100023](../errorcode-node.md#100023-parameter-error) | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| [100021](../errorcode-node.md#100021-framenode-not-modifiable) | The FrameNode is not modifiable. |

**Examples**

See the example for createNode('Swiper')12+.


<a id="bindcontroller-2"></a>

## bindController

```TypeScript
function bindController(node: FrameNode, controller: Scroller, nodeType: 'Scroll'): void
```

Binds the [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) to the [Scroll](arkts-arkui-typenode-scroll-t.md) node. Cross-language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API supports declaratively created nodes since API version 26.0.0.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node to which the scroll controller is bound. |
| controller | [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) | Yes | Scroll controller. |
| nodeType | 'Scroll' | Yes | Node type, which is **Scroll** in this API. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. the type of the node is error. 2. the node is null or undefined. |
| [100021](../errorcode-node.md#100021-framenode-not-modifiable) | The FrameNode is not modifiable. Introduced in API version 15 and will not be thrown above API version 24.<br>**Applicable version:** 15 - 24 |

**Examples**

```TypeScript
typeNode.bindController(node, scroller, 'Scroll');
```


<a id="bindcontroller-3"></a>

## bindController

```TypeScript
export function bindController(node: FrameNode, controller: Scroller, nodeType: 'List'): void
```

Binds a [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) instance to the [List](arkts-arkui-typenode-list-t.md) node. Cross-language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API supports declaratively created nodes since API version 26.0.0.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node to which the scroll controller is bound. |
| controller | [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) | Yes | Scroll controller. |
| nodeType | 'List' | Yes | Node type. Set to **'List'**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100023](../errorcode-node.md#100023-parameter-error) | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| [100021](../errorcode-node.md#100021-framenode-not-modifiable) | The FrameNode is not modifiable. Introduced in API version 20 and will not be thrown above API version 24.<br>**Applicable version:** 20 - 24 |

**Examples**

```TypeScript
typeNode.bindController(node, scroller, 'List');
```


<a id="bindcontroller-4"></a>

## bindController

```TypeScript
export function bindController(node: FrameNode, controller: TextInputController, nodeType: 'TextInput'): void
```

Binds the [TextInputController](../arkts-components/arkts-arkui-textinput-comp-textinputcontroller-c.md) to the [TextInput](arkts-arkui-typenode-textinput-t.md) node. Cross -language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API supports declaratively created nodes since API version 26.0.0.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node to which the input box controller is bound. |
| controller | [TextInputController](../arkts-components/arkts-arkui-textinput-comp-textinputcontroller-c.md) | Yes | Input box controller. |
| nodeType | 'TextInput' | Yes | Node type. Set to **'TextInput'**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100023](../errorcode-node.md#100023-parameter-error) | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| [100021](../errorcode-node.md#100021-framenode-not-modifiable) | The FrameNode is not modifiable. |

**Examples**

```TypeScript
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // Create and initialize TextInput. By default, the focus is obtained.
    let textInput = typeNode.createNode(uiContext, 'TextInput');
    textInput.initialize({ text: 'TextInput' })
      .defaultFocus(true)
    col.appendChild(textInput);
    // Bind TextInputController and set the cursor position.
    let controller: TextInputController = new TextInputController();
    typeNode.bindController(textInput, controller, 'TextInput');
    controller.caretPosition(3);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('TextInput bindController sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```


<a id="bindcontroller-5"></a>

## bindController

```TypeScript
export function bindController(node: FrameNode, controller: Scroller, nodeType: 'WaterFlow'): void
```

Binds a [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) instance to the [WaterFlow](arkts-arkui-typenode-waterflow-t.md) node. Cross-language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API supports declaratively created nodes since API version 26.0.0.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node to which the scroll controller is bound. |
| controller | [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) | Yes | Scroll controller. |
| nodeType | 'WaterFlow' | Yes | Node type. Set to **'WaterFlow'**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100023](../errorcode-node.md#100023-parameter-error) | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| [100021](../errorcode-node.md#100021-framenode-not-modifiable) | The FrameNode is not modifiable. Introduced in API version 20 and will not be thrown above API version 24.<br>**Applicable version:** 20 - 24 |

**Examples**

```TypeScript
typeNode.bindController(node, scroller, 'WaterFlow');
```


<a id="bindcontroller-6"></a>

## bindController

```TypeScript
export function bindController(node: FrameNode, controller: TextAreaController, nodeType: 'TextArea'): void
```

Binds a [TextAreaController](../arkts-components/arkts-arkui-textarea-comp-textareacontroller-c.md) instance to the [TextArea](arkts-arkui-typenode-textarea-t.md) node. Cross-language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API supports declaratively created nodes since API version 26.0.0.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node to which the input box controller is bound. |
| controller | [TextAreaController](../arkts-components/arkts-arkui-textarea-comp-textareacontroller-c.md) | Yes | Input box controller. |
| nodeType | 'TextArea' | Yes | Node type. Set to **'TextArea'**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100023](../errorcode-node.md#100023-parameter-error) | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| [100021](../errorcode-node.md#100021-framenode-not-modifiable) | The FrameNode is not modifiable. |

**Examples**

```TypeScript
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // Create and initialize a TextArea node. By default, the node is focused.
    let textArea = typeNode.createNode(uiContext, 'TextArea');
    textArea.initialize({ text: 'TextArea' })
      .defaultFocus(true)
    col.appendChild(textArea);
    // Bind a TextAreaController instance and set the cursor position.
    let controller: TextAreaController = new TextAreaController()
    typeNode.bindController(textArea, controller, 'TextArea');
    controller.caretPosition(3);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('TextArea bindController sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```


<a id="bindcontroller-7"></a>

## bindController

```TypeScript
export function bindController(node: FrameNode, controller: Scroller, nodeType: 'Grid'): void
```

Binds a [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) instance to the [Grid](arkts-arkui-typenode-grid-t.md) node. Cross-language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API supports declaratively created nodes since API version 26.0.0.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node to which the scroll controller is bound. |
| controller | [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) | Yes | Scroll controller. |
| nodeType | 'Grid' | Yes | Node type. Set to **'Grid'**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100023](../errorcode-node.md#100023-parameter-error) | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| [100021](../errorcode-node.md#100021-framenode-not-modifiable) | The FrameNode is not modifiable. Introduced in API version 20 and will not be thrown above API version 24.<br>**Applicable version:** 20 - 24 |

**Examples**

```TypeScript
typeNode.bindController(node, scroller, 'Grid');
```
