# getAttribute

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Text'): TextAttribute | undefined
```

Obtains the attributes of a **Text** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Text' | Yes | Node type. Set to **'Text'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [TextAttribute](../arkts-components/arkts-arkui-text-comp-attribute.md) &#124; undefined | Attributes of the **Text** node, or **undefined** if they fail to be obtained. |

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
    // Create a Text node.
    let text = typeNode.createNode(uiContext, 'Text');
    text.initialize('Hello');
    // Obtain the Text node attributes.
    typeNode.getAttribute(text, 'Text')?.fontColor(Color.Red)
    col.appendChild(text);
    // Create another text for comparison.
    let text2 = typeNode.createNode(uiContext, 'Text');
    text2.initialize('world');
    col.appendChild(text2);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('Text sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```


<a id="getattribute-1"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Column'): ColumnAttribute | undefined
```

Obtains the attributes of a **Column** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Column' | Yes | Node type. Set to **'Column'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ColumnAttribute](../arkts-components/arkts-arkui-column-comp-attribute.md) &#124; undefined | Attributes of the **Column** node, or **undefined** if they fail to be obtained. |

**Examples**

```TypeScript
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // Create a Column node.
    let col1 = typeNode.createNode(uiContext, 'Column');
    col1.initialize().width('50%').height('20%').backgroundColor(Color.Pink);
    // Obtain the attributes of the Column node.
    typeNode.getAttribute(col1, 'Column')?.backgroundColor(Color.Blue).width('100%');
    col.appendChild(col1);
    // Create another Column node for comparison.
    let col2 = typeNode.createNode(uiContext, 'Column');
    col2.initialize().width('50%').height('20%').backgroundColor(Color.Pink);
    col.appendChild(col2);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('Column sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```


<a id="getattribute-2"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Row'): RowAttribute | undefined
```

Obtains the attributes of a **Row** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Row' | Yes | Node type. Set to **'Row'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [RowAttribute](../arkts-components/arkts-arkui-row-comp-attribute.md) &#124; undefined | Attributes of the **Row** node, or **undefined** if they fail to be obtained. |

**Examples**

```TypeScript
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // Create a Row node.
    let row1 = typeNode.createNode(uiContext, 'Row');
    row1.initialize().width('50%').height('20%').backgroundColor(Color.Pink);
    // Obtain the attributes of the Row node.
    typeNode.getAttribute(row1, 'Row')?.backgroundColor(Color.Blue).width('100%');
    col.appendChild(row1);
    // Create another Row node for comparison.
    let row2 = typeNode.createNode(uiContext, 'Row');
    row2.initialize().width('50%').height('20%').backgroundColor(Color.Pink);
    col.appendChild(row2);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('Row sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```


<a id="getattribute-3"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Stack'): StackAttribute | undefined
```

Obtains the attributes of a **Stack** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Stack' | Yes | Node type. Set to **'Stack'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [StackAttribute](../arkts-components/arkts-arkui-stack-comp-attribute.md) &#124; undefined | Attributes of the **Stack** node, or **undefined** if they fail to be obtained. |

**Examples**

```TypeScript
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // Create a Stack node.
    let stack1 = typeNode.createNode(uiContext, 'Stack');
    stack1.initialize().width('50%').height('20%').backgroundColor(Color.Pink);
    // Obtain the Stack attributes.
    typeNode.getAttribute(stack1, 'Stack')?.backgroundColor(Color.Blue).width('100%')
    col.appendChild(stack1);
    // Create another Stack node for comparison.
    let stack2 = typeNode.createNode(uiContext, 'Stack');
    stack2.initialize().width('50%').height('20%').backgroundColor(Color.Pink);
    col.appendChild(stack2);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('Row sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```


<a id="getattribute-4"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Flex'): FlexAttribute | undefined
```

Obtains the Flex node attributes. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Flex' | Yes | Flex node type. |

**Return value:**

| Type | Description |
| --- | --- |
| [FlexAttribute](../arkts-components/arkts-arkui-flex-comp-attribute.md) &#124; undefined | Flex node type. If the operation fails, undefined is returned. |

**Examples**

```TypeScript
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // Create a Flex.
    let flex1 = typeNode.createNode(uiContext, 'Flex');
    flex1.initialize().width('50%').height('20%').backgroundColor(Color.Pink);
    // Obtain the Flex attributes.
    typeNode.getAttribute(flex1, 'Flex')?.backgroundColor(Color.Blue).width('100%')
    col.appendChild(flex1);
    // Create another Flex node for comparison.
    let flex2 = typeNode.createNode(uiContext, 'Flex');
    flex2.initialize().width('50%').height('20%').backgroundColor(Color.Pink);
    col.appendChild(flex2);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('Flex sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```


<a id="getattribute-5"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Swiper'): SwiperAttribute | undefined
```

Obtains the attributes of a **Swiper** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Swiper' | Yes | Node type. Set to **'Swiper'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [SwiperAttribute](../arkts-components/arkts-arkui-swiper-comp-attribute.md) &#124; undefined | Properties of the **Swiper** node, or **undefined** if they fail to be obtained. |

**Examples**

See the example for createNode('Swiper')12+.


<a id="getattribute-6"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Progress'): ProgressAttribute | undefined
```

Obtains the attributes of a **Progress** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Progress' | Yes | Node type. Set to **'Progress'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ProgressAttribute](../arkts-components/arkts-arkui-progress-comp-attribute.md) &#124; undefined | Properties of the **Progress** node, or **undefined** if they fail to be obtained. |

**Examples**

```TypeScript
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// Implement a custom Progress controller by extending NodeController.
class MyProgressNodeController extends NodeController {
  public uiContext: UIContext | null = null;
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.uiContext = uiContext;
    this.rootNode = new FrameNode(uiContext);
    let node = typeNode.createNode(uiContext, 'Progress');
    node.initialize({
      value: 15,
      total: 200,
      type: ProgressType.ScaleRing
    }).width(100)
      .height(100)
    // Obtain the attributes of the Progress node.
    typeNode.getAttribute(node, 'Progress');
    this!.rootNode!.appendChild(node);
    return this.rootNode;
  }
}

@Entry
@Component
struct Sample {
  build() {
    Column({ space: 10 }) {
      NodeContainer(new MyProgressNodeController()).margin(5)
    }.width('100%').height('100%')

  }
}
```


<a id="getattribute-7"></a>

## getAttribute

```TypeScript
function getAttribute(node: FrameNode, nodeType: 'Scroll'): ScrollAttribute | undefined
```

Obtains the attributes of a **Scroll** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Scroll' | Yes | Node type. Set to **'Scroll'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ScrollAttribute](../arkts-components/arkts-arkui-scroll-comp-attribute.md) &#124; undefined | Attributes of the **Scroll** node, or **undefined** if they fail to be obtained. |

**Examples**

See the example for createNode('Scroll').


<a id="getattribute-8"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'RelativeContainer'): RelativeContainerAttribute | undefined
```

Obtains the attributes of a **RelativeContainer** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'RelativeContainer' | Yes | Node type. Set to **'RelativeContainer'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [RelativeContainerAttribute](../arkts-components/arkts-arkui-relativecontainer-comp-attribute.md) &#124; undefined | Attributes of the **RelativeContainer** node, or **undefined** if they fail to be obtained. |

**Examples**

```TypeScript
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // Create a RelativeContainer node.
    let relative1 = typeNode.createNode(uiContext, 'RelativeContainer');
    relative1.initialize().width('50%').height('20%').backgroundColor(Color.Pink);
    // Obtain the attributes of the RelativeContainer node.
    typeNode.getAttribute(relative1, 'RelativeContainer')?.backgroundColor(Color.Blue).width('100%')
    col.appendChild(relative1);
    // Create another RelativeContainer node for comparison.
    let relative2 = typeNode.createNode(uiContext, 'RelativeContainer');
    relative2.initialize().width('50%').height('20%').backgroundColor(Color.Pink);
    col.appendChild(relative2);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('RelativeContainer sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```


<a id="getattribute-9"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'LoadingProgress'): LoadingProgressAttribute | undefined
```

Obtains the attributes of a [LoadingProgress](../arkts-components/arkts-arkui-loadingprogress-comp.md#loading_progress) node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'LoadingProgress' | Yes | Node type. Set to **'LoadingProgress'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [LoadingProgressAttribute](../arkts-components/arkts-arkui-loadingprogress-comp-attribute.md) &#124; undefined | Properties of the **LoadingProgress** node, or **undefined** if they fail to be obtained. |

**Examples**

```TypeScript
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// Implement a custom LoadingProgress controller by extending NodeController.
class MyLoadingProgressNodeController extends NodeController {
  public uiContext: UIContext | null = null;
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.uiContext = uiContext;
    this.rootNode = new FrameNode(uiContext);
    let node = typeNode.createNode(uiContext, 'LoadingProgress');
    node.initialize()
      .width(100)
      .height(100)
      .color(Color.Red)
      .enableLoading(true)
    // Obtain the attributes of the LoadingProgress node.
    typeNode.getAttribute(node, 'LoadingProgress');
    this!.rootNode!.appendChild(node);
    return this.rootNode;
  }
}

@Entry
@Component
struct Sample {
  build() {
    Column({ space: 10 }) {
      NodeContainer(new MyLoadingProgressNodeController()).margin(5)
    }.width('100%').height('100%')
  }
}
```


<a id="getattribute-10"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Image'): ImageAttribute | undefined
```

Obtains the attributes of an **Image** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Image' | Yes | Node type. Set to **'Image'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageAttribute](../arkts-components/arkts-arkui-image-comp-attribute.md) &#124; undefined | Properties of the **Image** node, or **undefined** if they fail to be obtained. |

**Examples**

```TypeScript
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// Implement a custom Image controller by extending NodeController.
class MyImageController extends NodeController {
  public uiContext: UIContext | null = null;
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.uiContext = uiContext;
    this.rootNode = new FrameNode(uiContext);
    let imageNode = typeNode.createNode(uiContext, 'Image');
    imageNode
      // Replace $r('app.media.img') with the image resource file you use.
      .initialize($r('app.media.img'))
      .width(100)
      .height(100)
      .fillColor(Color.Red)
      .objectFit(ImageFit.Contain)
      .renderMode(ImageRenderMode.Template)
      .fitOriginalSize(true)
      .matchTextDirection(true)
      .objectRepeat(ImageRepeat.X)
      .autoResize(true)
    // Obtain the attributes of the Image node.
    typeNode.getAttribute(imageNode, 'Image');
    this!.rootNode!.appendChild(imageNode);
    return this.rootNode;

  }
}

@Entry
@Component
struct Sample {
  build() {
    Column({ space: 10 }) {
      NodeContainer(new MyImageController()).margin(5)
    }.width('100%').height('100%')

  }
}
```


<a id="getattribute-11"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'List'): ListAttribute | undefined
```

Obtains the attributes of a **List** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'List' | Yes | Node type. Set to **'List'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ListAttribute](../arkts-components/arkts-arkui-list-comp-attribute.md) &#124; undefined | Attributes of the **List** node, or **undefined** if they fail to be obtained. |

**Examples**

See the example for createNode('List').


<a id="getattribute-12"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'ListItem'): ListItemAttribute | undefined
```

Obtains the attributes of a **ListItem** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'ListItem' | Yes | Node type. Set to **'ListItem'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ListItemAttribute](../arkts-components/arkts-arkui-listitem-comp-attribute.md) &#124; undefined | Attributes of the **ListItem** node, or **undefined** if they fail to be obtained. |

**Examples**

See the example for createNode('List').


<a id="getattribute-13"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'TextInput'): TextInputAttribute | undefined
```

Obtains the attributes of a **TextInput** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'TextInput' | Yes | Node type. Set to **'TextInput'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [TextInputAttribute](../arkts-components/arkts-arkui-textinput-comp-attribute.md) &#124; undefined | Properties of the **TextInput** node, or **undefined** if they fail to be obtained. |

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
    // Create a TextInput.
    let textInput = typeNode.createNode(uiContext, 'TextInput');
    textInput.initialize({ placeholder: 'TextInput placeholderColor' });
    // Obtain the attributes of the TextInput node.
    typeNode.getAttribute(textInput, 'TextInput')?.placeholderColor(Color.Red);
    col.appendChild(textInput);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('TextInput getAttribute sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```


<a id="getattribute-14"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Button'): ButtonAttribute | undefined
```

Obtains the attributes of a **Button** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Button' | Yes | Node type. Set to **'Button'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ButtonAttribute](../arkts-components/arkts-arkui-button-comp-attribute.md) &#124; undefined | Attributes of the **Button** node, or **undefined** if they fail to be obtained. |

**Examples**

```TypeScript
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// Implement a custom Button controller by extending NodeController.
class MyButtonController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    let button = typeNode.createNode(uiContext, 'Button')
    button.initialize('This is Button')
      .onClick(() => {
        uiContext.getPromptAction().showToast({ message: 'Button clicked' })
      })
    // Obtain the attributes of the Button node.
    typeNode.getAttribute(button, 'Button')?.buttonStyle(ButtonStyleMode.TEXTUAL);
    col.appendChild(button)

    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myButtonController: MyButtonController = new MyButtonController();

  build() {
    Column({ space: 5 }) {
      Text('ButtonSample')
      NodeContainer(this.myButtonController);

    }.width('100%')
  }
}
```


<a id="getattribute-15"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'ListItemGroup'): ListItemGroupAttribute | undefined
```

Obtains the attributes of a **ListItemGroup** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'ListItemGroup' | Yes | Node type. Set to **'ListItemGroup'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ListItemGroupAttribute](../arkts-components/arkts-arkui-listitemgroup-comp-attribute.md) &#124; undefined | Attributes of the **ListItemGroup** node, or **undefined** if they fail to be obtained. |

**Examples**

```TypeScript
typeNode.getAttribute(node, 'ListItemGroup');
```


<a id="getattribute-16"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'WaterFlow'): WaterFlowAttribute | undefined
```

Obtains the attributes of a **WaterFlow** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'WaterFlow' | Yes | Node type. Set to **'WaterFlow'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [WaterFlowAttribute](../arkts-components/arkts-arkui-waterflow-comp-attribute.md) &#124; undefined | Properties of the **WaterFlow** node, or **undefined** if they fail to be obtained. |

**Examples**

See the example for createNode('WaterFlow').


<a id="getattribute-17"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'FlowItem'): FlowItemAttribute | undefined
```

Obtains the attributes of a **FlowItem** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'FlowItem' | Yes | Node type. Set to **'FlowItem'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [FlowItemAttribute](../arkts-components/arkts-arkui-flowitem-comp-attribute.md) &#124; undefined | Properties of the **FlowItem** node, or **undefined** if they fail to be obtained. |

**Examples**

See the example for createNode('WaterFlow').


<a id="getattribute-18"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'XComponent'): XComponentAttribute | undefined
```

Obtain the attributes of an **XComponent** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'XComponent' | Yes | Node type. Set to **'XComponent'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [XComponentAttribute](../arkts-components/arkts-arkui-xcomponent-comp-attribute.md) &#124; undefined | Properties of the **XComponent** node, or **undefined** if they fail to be obtained. |

**Examples**

```TypeScript
typeNode.getAttribute(node, 'XComponent');
```


<a id="getattribute-19"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Checkbox'): CheckboxAttribute | undefined
```

Obtains the attributes of a **Checkbox** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Checkbox' | Yes | Node type. Set to **'Checkbox'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [CheckboxAttribute](../arkts-components/arkts-arkui-checkbox-comp-attribute.md) &#124; undefined | Attributes of the **Checkbox** node, or **undefined** if they fail to be obtained. |

**Examples**

```TypeScript
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// Implement a custom Checkbox controller by extending NodeController.
class MyCheckboxController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    // Create a Checkbox node.
    let checkbox = typeNode.createNode(uiContext, 'Checkbox')
    checkbox.initialize({ name: 'checkbox1', group: 'checkboxGroup1' })

    // Create another Checkbox node.
    let checkbox1 = typeNode.createNode(uiContext, 'Checkbox')
    checkbox1.initialize({ name: 'checkbox2', group: 'checkboxGroup1' })
    // Set the shape attribute for another Checkbox.
    typeNode.getAttribute(checkbox1,'Checkbox')?.shape(CheckBoxShape.ROUNDED_SQUARE)
    // Add the two Checkbox nodes to col for comparison.
    col.appendChild(checkbox)
    col.appendChild(checkbox1)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myCheckboxController: MyCheckboxController = new MyCheckboxController();

  build() {
    Column({ space: 5 }) {
      Text('CheckboxSample')
      NodeContainer(this.myCheckboxController);
    }.width('100%')
  }
}
```


<a id="getattribute-20"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Radio'): RadioAttribute | undefined
```

Obtains the attributes of a **Radio** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Radio' | Yes | Node type. Set to **'Radio'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [RadioAttribute](../arkts-components/arkts-arkui-radio-comp-attribute.md) &#124; undefined | Properties of the **Radio** node, or **undefined** if they fail to be obtained. |

**Examples**

```TypeScript
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// Implement a custom Radio controller by extending NodeController.
class MyRadioController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    // Create a Radio node.
    let radio1 = typeNode.createNode(uiContext, 'Radio')
    radio1.initialize({ value: 'radio1', group: 'radioGroup' })
    typeNode.getAttribute(radio1,'Radio')?.checked(true)
    // Create another Radio node for comparison.
    let radio2 = typeNode.createNode(uiContext, 'Radio')
    radio2.initialize({ value: 'radio2', group: 'radioGroup' })


    col.appendChild(radio1)
    col.appendChild(radio2)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myRadioController: MyRadioController = new MyRadioController();

  build() {
    Column({ space: 5 }) {
      Text('RadioSample')
      NodeContainer(this.myRadioController);
    }.width('100%')
  }
}
```


<a id="getattribute-21"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Slider'): SliderAttribute | undefined
```

Obtains the attributes of a **Slider** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Slider' | Yes | Node type. Set to **'Slider'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [SliderAttribute](../arkts-components/arkts-arkui-slider-comp-attribute.md) &#124; undefined | Properties of the **Slider** node, or **undefined** if they fail to be obtained. |

**Examples**

```TypeScript
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// Implement a custom Slider controller by extending NodeController.
class MySliderController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    // Create a Slider node.
    let slider = typeNode.createNode(uiContext, 'Slider')
    slider.initialize({value:50})
    typeNode.getAttribute(slider,'Slider')?.selectedColor(Color.Pink)
    col.appendChild(slider)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private mySliderController: MySliderController = new MySliderController();

  build() {
    Column({ space: 5 }) {
      Text('SliderSample')
      NodeContainer(this.mySliderController);

    }.width('100%')
  }
}
```


<a id="getattribute-22"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Toggle'): ToggleAttribute | undefined
```

Obtains the attributes of a **Toggle** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Toggle' | Yes | Node type. Set to **'Toggle'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ToggleAttribute](../arkts-components/arkts-arkui-toggle-comp-attribute.md) &#124; undefined | Properties of the **Toggle** node, or **undefined** if they fail to be obtained. |

**Examples**

```TypeScript
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// Implement a custom Toggle controller by extending NodeController.
class MyToggleController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    // Create a Toggle node.
    let toggleSwitch = typeNode.createNode(uiContext, 'Toggle')
    toggleSwitch.initialize({ type: ToggleType.Switch })
    typeNode.getAttribute(toggleSwitch,'Toggle')?.selectedColor(Color.Orange)
    col.appendChild(toggleSwitch)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myToggleController: MyToggleController = new MyToggleController();

  build() {
    Column({ space: 5 }) {
      Text('ToggleSample')
      NodeContainer(this.myToggleController);

    }.width('100%')
  }
}
```


<a id="getattribute-23"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'TextArea'): TextAreaAttribute | undefined
```

Obtains the attributes of a **TextArea** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'TextArea' | Yes | Node type. Set to **'TextArea'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [TextAreaAttribute](../arkts-components/arkts-arkui-textarea-comp-attribute.md) &#124; undefined | Properties of the **TextArea** node, or **undefined** if they fail to be obtained. |

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
    // Create a TextArea node.
    let textArea = typeNode.createNode(uiContext, 'TextArea');
    textArea.initialize({ placeholder: 'TextArea placeholderColor' });
    col.appendChild(textArea);
    // Obtain the attributes of the TextArea node.
    typeNode.getAttribute(textArea, 'TextArea')?.placeholderColor(Color.Red);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('TextArea getAttribute sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```


<a id="getattribute-24"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Grid'): GridAttribute | undefined
```

Obtains the attributes of a **Grid** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Grid' | Yes | Node type. Set to **'Grid'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [GridAttribute](../arkts-components/arkts-arkui-grid-comp-attribute.md) &#124; undefined | Properties of the **Grid** node, or **undefined** if they fail to be obtained. |

**Examples**

See the example for createNode('Grid').


<a id="getattribute-25"></a>

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'GridItem'): GridItemAttribute | undefined
```

Obtains the attributes of a **GridItem** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'GridItem' | Yes | Node type. Set to **'GridItem'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [GridItemAttribute](../arkts-components/arkts-arkui-griditem-comp-attribute.md) &#124; undefined | Properties of the **GridItem** node, or **undefined** if they fail to be obtained. |

**Examples**

See the example for createNode('Grid').
