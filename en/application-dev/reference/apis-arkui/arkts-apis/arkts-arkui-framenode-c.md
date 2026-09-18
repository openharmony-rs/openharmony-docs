# FrameNode

**FrameNode** represents an entity node in the component tree. It can be used by a [NodeController](arkts-arkui-nodecontroller-c.md) to mount a BuilderNode (that holds the FrameNode) to a NodeContainer or mount a [RenderNode](arkts-arkui-rendernode-c.md) to another FrameNode.&lt;!--RP2--&gt;&lt;!--RP2End--&gt;

> **NOTE:** 
> 
> - **FrameNode** is not available in DevEco Studio Previewer.
> 
> - FrameNodes cannot be dragged.
> 
> - FrameNode objects do not support JSON serialization.
> 
> - When the API of the [FrameNode](arkts-arkui-framenode-c.md) object is invoked in the scenario of [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context), you are advised to use the [runScopedTask](arkts-arkui-arkui-uicontext-uicontext-c.md#runscopedtask) API of [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to specify the UI context. For details, see [Executing the Closure Bound to a UI Instance](../../../ui/arkts-global-interface.md#executing-the-closure-bound-to-a-ui-instance).
> 
> - In the FrameNode APIs, only the mandatory parameters of the [Optional](../arkts-components/arkts-arkui-optional-t.md) type can be set to null or undefined.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## addComponentContent

```TypeScript
addComponentContent<T>(content: ComponentContent<T> | ReactiveComponentContent<T>): void
```

Adds component content. The current node must be modifiable, which means the return value of [isModifiable](#ismodifiable) must be **true**. If the node is not modifiable, an exception is thrown.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; &#124; [ReactiveComponentContent](arkts-arkui-componentcontent-reactivecomponentcontent-c.md)&lt;T&gt; | Yes | Component content to display on the FrameNode.<br>**Since:** 22 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode-not-modifiable) | The FrameNode is not modifiable. |

## addSupportedUIStates

```TypeScript
addSupportedUIStates(uiStates: number, statesChangeHandler: UIStatesChangeHandler, excludeInner?: boolean): void
```

Adds the polymorphic style states supported by the component.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uiStates | number | Yes | UI states of the target node to be processed.<br>Multiple states can be specified simultaneously using bitwise OR operations, for example, **targetUIStates = UIState.PRESSED  &#124;  UIState.FOCUSED**. |
| statesChangeHandler | [UIStatesChangeHandler](arkts-arkui-uistateschangehandler-t.md) | Yes | Callback invoked when the state changes. |
| excludeInner | boolean | No | Whether to disable the default state style processing. Default value: **false**.<br> **true**: Disable default state style processing. **false**: Enable default state style processing. |

**Examples**

```TypeScript
See Example of Setting and Deleting a Polymorphic Style State.
```

## adoptChild

```TypeScript
adoptChild(child: FrameNode): void
```

Adopts the target node as an affiliated node. The adopted node must not have an existing parent. This API is not used to add a node as a child node. Instead, it only allows the node to receive lifecycle callbacks of the corresponding child node.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| child | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Node to be adopted. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode-not-modifiable) | The current FrameNode is not modifiable. |
| [100025](../errorcode-node.md#100025-invalid-parameter-value) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'child' is invalid: it cannot be disposed." |
| [100026](../errorcode-node.md#100026-the-instance-object-used-to-call-the-api-has-been-unbound-from-the-backend-entity-node) | The current FrameNode has been disposed. |

**Examples**

```TypeScript
See Example of Adopting a Node as an Affiliate.
```

## appendChild

```TypeScript
appendChild(node: FrameNode): void
```

Appends a child node to the end of this FrameNode. If this FrameNode is not modifiable, an exception is thrown. When **appendChild** is called, [typeNode](arkts-arkui-typenode-n.md) validates the type or number of child nodes. If the validation fails, an exception is thrown. For specific limitations, see [typeNode](arkts-arkui-typenode-n.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Child node to append.<br> The target node must not be a declaratively created node, that is, a FrameNode that is not modifiable. Only declarative nodes obtained from a BuilderNode can be used as child nodes. If the child node does not meet the specifications, an exception is thrown. <br> The FrameNode cannot have a parent node. Otherwise, an exception is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode-not-modifiable) | The FrameNode is not modifiable. |
| [100025](../errorcode-node.md#100025-invalid-parameter-value) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'node' is invalid: it cannot be adopted."<br>**Applicable version:** 22 and later |

**Examples**

```TypeScript
See Example of Node Operations.
```

## cancelAnimations

```TypeScript
cancelAnimations(properties: AnimationPropertyType[]): boolean
```

Cancels all animations for specified properties on the FrameNode. This API executes synchronously in the node's owning thread and blocks until cancellation completes. Upon successful cancellation, the node's property values revert to their current display state at the time of cancellation.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| properties | [AnimationPropertyType](arkts-arkui-animationpropertytype-e.md)[] | Yes | Array of animation properties to cancel. You can simultaneously cancel the animations of multiple properties on the node. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Animation cancellation status. <br>**true**: successful. <br>**false**: failed. <br>The possible causes are as follows: <br>Additional notes: <br> 1. The node has been released (the [dispose](#dispose) API has been called). <br> 2. The node is a built-in component proxy (where [isModifiable](#ismodifiable) returns **false**). <br> 3. The property array contains invalid enumerated values. <br> 4. System error. Example: system IPC communication error. <br>Additional notes: <br> 1. This API returns **true** for properties without active animations, if there are no system errors. <br> 2. Valid parameters with normal node returning **false** indicate a system exception. In this case, you can retry cancellation later or use [createAnimation](#createanimation) with a zero duration as an alternative. |

**Examples**

```TypeScript
See Example of Creating and Canceling an Animation.
```

## clearChildren

```TypeScript
clearChildren(): void
```

Clears all child nodes of this FrameNode. If this FrameNode is not modifiable, an exception is thrown.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode-not-modifiable) | The FrameNode is not modifiable. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## constructor

```TypeScript
constructor(uiContext: UIContext)
```

A constructor used to create a FrameNode.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | Yes | UI context for node creation. |

## convertPosition

```TypeScript
convertPosition(position: Position, targetNode: FrameNode): Position
```

Converts a coordinate point from this node's coordinate system to the target node's coordinate system.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | [Position](arkts-arkui-position-t.md) | Yes | Coordinates relative to the current node's coordinate system. |
| targetNode | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node for coordinate transformation. |

**Return value:**

| Type | Description |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | Converted coordinates relative to the target node's local coordinate system. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100024](../errorcode-node.md#100024-no-common-ancestor-node-between-nodes) | The current FrameNode and the target FrameNode do not have a common ancestor node. |
| [100025](../errorcode-node.md#100025-invalid-parameter-value) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'targetNode' is invalid: it cannot be disposed." |

**Examples**

```TypeScript
@Entry
@Component
struct ConvertPositionTestOnly {
  private uiContext: UIContext = this.getUIContext();
  @State message: string = 'Hello World';
  @State nodeAOk: boolean = false;
  @State nodeBOk: boolean = false;

  build() {
    Column() {
      Text(this.message)
        .id('testNodeA')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .onAppear(() => {
          this.nodeAOk = true
        })
      Column() {
        Text('testNodeB')
          .id('testNodeB')
          .fontSize($r('app.float.page_text_font_size'))
          .fontWeight(FontWeight.Bold)
          .onAppear(() => {
            this.nodeBOk = true
          })

      }

      Button('Run convertPosition Test')
        .onClick(() => {
          this.runBasicTest();
        })
        .margin(20)

    }
    .width('100%')
    .height('100%')
  }

  private runBasicTest() {
    if (!this.nodeAOk || !this.nodeBOk) {
      return
    }

    // Wait for UI rendering completion.
    if (!this.uiContext) {
      return
    }
    const nodeA = this.uiContext.getAttachedFrameNodeById('testNodeA');
    const nodeB = this.uiContext.getAttachedFrameNodeById('testNodeB');

    if (!nodeA || !nodeB) {
      console.info('Failed to obtain test nodes');
      return;
    }

    const result: Position | undefined = nodeA.convertPosition({ x: 30, y: 10 }, nodeB); // Explicitly declare that the method may return undefined.
    if (result === undefined) {
      console.info('convertPosition Conversion failed, returning undefined');
      return;
    }
    console.info(`Converted coordinates: (${result.x}, ${result.y})`);

  }
}
```

## convertPositionFromWindow

```TypeScript
convertPositionFromWindow(positionByWindow: Position): Position
```

Converts the coordinates of a point from the coordinate system of the window where the current node is located to the coordinate system of the current node.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| positionByWindow | [Position](arkts-arkui-position-t.md) | Yes | Relative coordinates in the coordinate system of the window where the current node is located. |

**Return value:**

| Type | Description |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | Converted coordinates in the coordinate system of the current node. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100026](../errorcode-node.md#100026-the-instance-object-used-to-call-the-api-has-been-unbound-from-the-backend-entity-node) | The current FrameNode has been disposed. |
| [100028](../errorcode-node.md#100028-current-node-is-not-on-the-main-node-tree) | The current FrameNode is not on the main tree. |

**Examples**

```TypeScript
See Example of Converting Between Local Coordinates and Window Coordinates.
```

## convertPositionToWindow

```TypeScript
convertPositionToWindow(positionByLocal: Position): Position
```

Converts the coordinates of a point from the coordinate system of the current node to the coordinate system of the window where the current node is located.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| positionByLocal | [Position](arkts-arkui-position-t.md) | Yes | Coordinates relative to the current node's coordinate system. |

**Return value:**

| Type | Description |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | Converted coordinates in the coordinate system of the window where the current node is located. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100026](../errorcode-node.md#100026-the-instance-object-used-to-call-the-api-has-been-unbound-from-the-backend-entity-node) | The current FrameNode has been disposed. |
| [100028](../errorcode-node.md#100028-current-node-is-not-on-the-main-node-tree) | The current FrameNode is not on the main tree. |

**Examples**

```TypeScript
See Example of Converting Between Local Coordinates and Window Coordinates.
```

## createAnimation

```TypeScript
createAnimation(property: AnimationPropertyType, startValue: Optional<number[]>, endValue: number[], param: AnimateParam): boolean
```

Creates a property animation for the FrameNode.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| property | [AnimationPropertyType](arkts-arkui-animationpropertytype-e.md) | Yes | Animation property type. |
| startValue | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;number[]&gt; | Yes | Animation start value. The value can be **undefined** or an array. If the value is **undefined**, the animation uses the last set value of the property on the node as the starting value. If the value is an array, the length must match the property type requirements:<br>- **AnimationPropertyType.ROTATION**: [rotationX, rotationY, rotationZ] in degrees (°). <br>- **AnimationPropertyType.TRANSLATION**: [translateX, translateY] in px. <br>- **AnimationPropertyType.SCALE**: [scaleX, scaleY] (scale factors). <br>- **AnimationPropertyType.OPACITY**: [opacity] (value range: [0, 1]). <br>For the first animation of a property, **startValue** must be explicitly specified. For subsequent animations, it is recommended that you either omit **startValue** or set it to the previous animation's end value to avoid abrupt changes. |
| endValue | number[] | Yes | Animation end value. The value is an array. The array length must match the property type requirements:<br>- **AnimationPropertyType.ROTATION**: [rotationX, rotationY, rotationZ] in degrees (°). <br>- **AnimationPropertyType.TRANSLATION**: [translateX, translateY] in px. <br>- **AnimationPropertyType.SCALE**: [scaleX, scaleY] (scale factors). <br>- **AnimationPropertyType.OPACITY**: [opacity] (value range: [0, 1]). |
| param | [AnimateParam](../arkts-components/arkts-arkui-animateparam-i.md) | Yes | Animation parameters, including the duration, animation curve, and end callback. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the animation is created successfully. <br>Returns **true** if the animation is created successfully. If an end callback is specified in the animation parameters, it will be invoked upon animation completion. <br>Returns **false** if the animation creation fails. The end callback will not be invoked even if specified. <br>Possible failure reasons: <br>Additional notes: <br> 1. The node has been released (the [dispose](#dispose) API has been called). <br> 2. The node is a built-in component proxy (where [isModifiable](#ismodifiable) returns **false**). <br> 3. There is an invalid property enumeration or length mismatch between the property type and **startValue** or **endValue** arrays. <br> 4. No start value is available (**startValue** is **undefined** for the first animation of a property) or the start and end values are identical. |

**Examples**

```TypeScript
See Example of Creating and Canceling an Animation.
```

## createFrameNodes

```TypeScript
static createFrameNodes(uiContext: UIContext, count: number): FrameNode[]
```

Creates a specified number of FrameNodes in batches and returns a FrameNode array.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | Yes | UI context for node creation. |
| count | number | Yes | Number of nodes to be created. The value is an integer greater than 0. If the value is less than or equal to 0 or is not an integer, an empty array is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md)[] | Array of created FrameNodes. |

**Examples**

```TypeScript
import { NodeController, FrameNode } from '@kit.ArkUI';

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    // Create 20 FrameNodes and add them to the root node.
    const children: FrameNode[] = FrameNode.createFrameNodes(uiContext, 20);
    for (let i = 0; i < children.length; i++) {
      this.rootNode.appendChild(children[i]);
    }
    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column() {
      NodeContainer(this.myNodeController)
        .borderWidth(1)
        .width(300)
        .height(300)
    }.width('100%')
  }
}
```

## dispose

```TypeScript
dispose(): void
```

Immediately releases the reference to the underlying FrameNode entity.

> **NOTE:** 
> 
> - After the **dispose** API is called, the FrameNode object no longer corresponds to any entity FrameNode. In this case, attempts to call certain query APIs, such as [getMeasuredSize](#getmeasuredsize) and [getLayoutPosition](#getlayoutposition), will result in a JS crash in the application.
> 
> - To check whether the current FrameNode object corresponds to an entity FrameNode, you can use [getUniqueId](#getuniqueid) API. A **UniqueId** value greater than 0 indicates that the object is associated with an entity FrameNode.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
import { NodeController, FrameNode, BuilderNode } from '@kit.ArkUI';

@Component
struct TestComponent {
  build() {
    Column() {
      Text('This is a BuilderNode.')
        .fontSize(16)
        .fontWeight(FontWeight.Bold)
    }
    .width('100%')
    .backgroundColor(Color.Gray)
  }

  aboutToAppear() {
    console.info('aboutToAppear');
  }

  aboutToDisappear() {
    console.info('aboutToDisappear');
  }
}

@Builder
function buildComponent() {
  TestComponent()
}

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private builderNode: BuilderNode<[]> | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    this.builderNode = new BuilderNode(uiContext, { selfIdealSize: { width: 200, height: 100 } });
    this.builderNode.build(new WrappedBuilder(buildComponent));

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.size = { width: 200, height: 200 };
      rootRenderNode.backgroundColor = 0xffd5d5d5;
      rootRenderNode.appendChild(this.builderNode!.getFrameNode()!.getRenderNode());
    }

    return this.rootNode;
  }

  disposeFrameNode() {
    if (this.rootNode !== null && this.builderNode !== null) {
      // Remove all child nodes from rootNode before clearing the reference relationships.
      this.rootNode.removeChild(this.builderNode.getFrameNode());
      // Release the reference between builderNode and FrameNode.
      this.builderNode.dispose();
      // Release the reference between rootNode and FrameNode.
      this.rootNode.dispose();
    }
  }

  removeBuilderNode() {
    const rootRenderNode = this.rootNode!.getRenderNode();
    if (rootRenderNode !== null && this.builderNode !== null && this.builderNode.getFrameNode() !== null) {
      rootRenderNode.removeChild(this.builderNode!.getFrameNode()!.getRenderNode());
    }
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 4 }) {
      NodeContainer(this.myNodeController)
      Button('FrameNode dispose')
        .onClick(() => {
          this.myNodeController.disposeFrameNode();
        })
        .width('100%')
    }
  }
}
```

## disposeTree

```TypeScript
disposeTree(): void
```

Traverses down the tree and recursively releases the subtree with this node as the root.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
import { FrameNode, NodeController, BuilderNode } from '@kit.ArkUI';

// Custom component with mounted event handling, serving as the entry point for the custom component tree.
@Component
struct TestComponent {
  private myNodeController: MyNodeController = new MyNodeController(wrapBuilder(buildComponent2));

  build() {
    Column() {
      Text('This is a BuilderNode.')
        .fontSize(16)
        .fontWeight(FontWeight.Bold)
      NodeContainer(this.myNodeController)
    }
    .width('100%')
    .backgroundColor(Color.Gray)
  }

  aboutToAppear() {
    console.info('BuilderNode aboutToAppear');
  }

  aboutToDisappear() {
    console.info('BuilderNode aboutToDisappear');
  }
}

// Custom component with mounted event handling, serving as the child component of TestComponent1 and the parent component of TestComponent3 and TestComponent4.
@Component
struct TestComponent2 {
  private myNodeController: MyNodeController = new MyNodeController(wrapBuilder(buildComponent3));
  private myNodeController2: MyNodeController = new MyNodeController(wrapBuilder(buildComponent4));

  build() {
    Column() {
      Text('This is a BuilderNode 2.')
        .fontSize(16)
        .fontWeight(FontWeight.Bold)
      NodeContainer(this.myNodeController)
      NodeContainer(this.myNodeController2)
    }
    .width('100%')
    .backgroundColor(Color.Gray)
  }

  aboutToAppear() {
    console.info('BuilderNode 2 aboutToAppear');
  }

  aboutToDisappear() {
    console.info('BuilderNode 2 aboutToDisappear');
  }
}

// Custom component with mounted event handling, serving as the child component of buildComponent2.
@Component
struct TestComponent3 {
  build() {
    Column() {
      Text('This is a BuilderNode 3.')
        .fontSize(16)
        .fontWeight(FontWeight.Bold)

    }
    .width('100%')
    .backgroundColor(Color.Gray)
  }

  aboutToAppear() {
    console.info('BuilderNode 3 aboutToAppear');
  }

  aboutToDisappear() {
    console.info('BuilderNode 3 aboutToDisappear');
  }
}

// Custom component with mounted event handling, serving as the child component of buildComponent2.
@Component
struct TestComponent4 {
  build() {
    Column() {
      Text('This is a BuilderNode 4.')
        .fontSize(16)
        .fontWeight(FontWeight.Bold)

    }
    .width('100%')
    .backgroundColor(Color.Gray)
  }

  aboutToAppear() {
    console.info('BuilderNode 4 aboutToAppear');
  }

  aboutToDisappear() {
    console.info('BuilderNode 4 aboutToDisappear');
  }
}

@Builder
function buildComponent() {
  TestComponent()
}

@Builder
function buildComponent2() {
  TestComponent2()
}

@Builder
function buildComponent3() {
  TestComponent3()
}

@Builder
function buildComponent4() {
  TestComponent4()
}

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private builderNode: BuilderNode<[]> | null = null;
  private wrappedBuilder: WrappedBuilder<[]>;

  constructor(builder: WrappedBuilder<[]>) {
    super();
    this.wrappedBuilder = builder;
  }

  makeNode(uiContext: UIContext): FrameNode | null {
    this.builderNode = new BuilderNode(uiContext, { selfIdealSize: { width: 200, height: 100 } });
    this.builderNode.build(this.wrappedBuilder);

    return this.builderNode.getFrameNode();
  }

  dispose() {
    if (this.builderNode !== null) {
      // Traverse down the tree and recursively release the subtree with the current node as the root.
      this.builderNode.getFrameNode()?.disposeTree()
    }
  }

  removeBuilderNode() {
    const rootRenderNode = this.rootNode!.getRenderNode();
    if (rootRenderNode !== null && this.builderNode !== null && this.builderNode.getFrameNode() !== null) {
      rootRenderNode.removeChild(this.builderNode!.getFrameNode()!.getRenderNode());
    }
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController(wrapBuilder(buildComponent));

  build() {
    Column({ space: 4 }) {
      NodeContainer(this.myNodeController)
      Button('BuilderNode dispose')
        .onClick(() => {
          this.myNodeController.dispose();
        })
        .width('100%')
      Button('BuilderNode rebuild')
        .onClick(() => {
          this.myNodeController.rebuild();
        })
        .width('100%')
    }
  }
}
```

## getChild

```TypeScript
getChild(index: number): FrameNode | null
```

Obtains the child node in the specified position of this node.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the child node to obtain.<br>The value range of index is [0, +∞). If the current node has n child nodes, the valid value range of index is [0, n-1]. |

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) &#124; null | Child node obtained. If the FrameNode does not contain the specified child node, null is returned. |

**Examples**

```TypeScript
See Example of Node Operations.
```

```TypeScript
See Example of Node Operations in the LazyForEach Scenario.
```

## getChild

```TypeScript
getChild(index: number, expandMode?: ExpandMode): FrameNode | null
```

Obtains a child node at a specified index from this FrameNode, with optional support for specifying the expansion mode of the child node.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the child node to obtain.<br>The value range of index is [0, +∞). If the current node has n child nodes, the valid value range of index is [0, n-1]. |
| expandMode | [ExpandMode](arkts-arkui-framenode-expandmode-e.md) | No | Expansion mode of the child node.<br>Default value: **ExpandMode.EXPAND**. |

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) &#124; null | Child node obtained. If the FrameNode does not contain the specified child node, null is returned. |

**Examples**

See [getChild](#getchild)

## getChildrenCount

```TypeScript
getChildrenCount(): number
```

Obtains the number of child nodes of this FrameNode.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of child nodes of the current FrameNode. |

**Examples**

```TypeScript
See Example of Node Operations.
```

```TypeScript
import { NodeController, FrameNode, UIContext, BuilderNode, ChildrenCountMode, LengthUnit } from '@kit.ArkUI';

const TEST_TAG: string = 'FrameNode ';

// BasicDataSource implements the IDataSource API to manage listeners and notify LazyForEach of data updates.
class BasicDataSource implements IDataSource {
  private listeners: DataChangeListener[] = [];
  private originDataArray: string[] = [];

  public totalCount(): number {
    return 0;
  }

  public getData(index: number): string {
    return this.originDataArray[index];
  }

  // Called by the framework to register a listener with the LazyForEach data source.
  registerDataChangeListener(listener: DataChangeListener): void {
    if (this.listeners.indexOf(listener) < 0) {
      console.info('add listener');
      this.listeners.push(listener);
    }
  }

  // This method is called by the framework to remove the listener from the LazyForEach data source.
  unregisterDataChangeListener(listener: DataChangeListener): void {
    const pos = this.listeners.indexOf(listener);
    if (pos >= 0) {
      console.info('remove listener');
      this.listeners.splice(pos, 1);
    }
  }

  // Notify LazyForEach that all child components need to be reloaded.
  notifyDataReload(): void {
    this.listeners.forEach(listener => {
      listener.onDataReloaded();
    })
  }

  // Notify LazyForEach that a child component needs to be added for the data item with the specified index.
  notifyDataAdd(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataAdd(index);
    })
  }

  // Notify LazyForEach that the data item with the specified index has changed and the child component needs to be rebuilt.
  notifyDataChange(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataChange(index);
    })
  }

  // Notify LazyForEach that the child component that matches the specified index needs to be deleted.
  notifyDataDelete(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataDelete(index);
    })
  }

  // Notify LazyForEach that data needs to be swapped between the from and to positions.
  notifyDataMove(from: number, to: number): void {
    this.listeners.forEach(listener => {
      listener.onDataMove(from, to);
    })
  }

  notifyDatasetChange(operations: DataOperation[]): void {
    this.listeners.forEach(listener => {
      listener.onDatasetChange(operations);
    })
  }
}

// Manage the string array using the custom data management class.
class MyDataSource extends BasicDataSource {
  private dataArray: string[] = []

  public totalCount(): number {
    return this.dataArray.length;
  }

  public getData(index: number): string {
    return this.dataArray[index];
  }

  public addData(index: number, data: string): void {
    this.dataArray.splice(index, 0, data);
    this.notifyDataAdd(index);
  }

  public pushData(data: string): void {
    this.dataArray.push(data);
    this.notifyDataAdd(this.dataArray.length - 1);
  }
}

class Params {
  data: MyDataSource | null = null;
  scroller: Scroller | null = null;

  constructor(data: MyDataSource, scroller: Scroller) {
    this.data = data;
    this.scroller = scroller;
  }
}

@Builder
function buildData(params: Params) {
  List({ scroller: params.scroller }) {
    LazyForEach(params.data, (item: string) => {
      ListItem() {
        Column() {
          Text(item)
            .fontSize(20)
            .onAppear(() => {
              console.info(`${TEST_TAG} node appear: ${item}`)
            })
            .backgroundColor(Color.Pink)
            .margin({
              top: 30,
              bottom: 30,
              left: 10,
              right: 10
            })
        }
      }
      .id(item)
    }, (item: string) => item)
  }
  .cachedCount(5)
  .listDirection(Axis.Horizontal)
}

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private uiContext: UIContext | null = null;
  private data: MyDataSource = new MyDataSource();
  private scroller: Scroller = new Scroller();

  makeNode(uiContext: UIContext): FrameNode | null {
    this.uiContext = uiContext;
    for (let i = 0; i <= 20; i++) {
      this.data.pushData(`N${i}`);
    }
    const params: Params = new Params(this.data, this.scroller);
    const dataNode: BuilderNode<[Params]> = new BuilderNode(uiContext);
    dataNode.build(wrapBuilder<[Params]>(buildData), params);
    this.rootNode = dataNode.getFrameNode();
    const scrollToIndexOptions: ScrollToIndexOptions = {
      extraOffset: {
        value: 20, unit: LengthUnit.VP
      }
    };
    this.scroller.scrollToIndex(6, true, ScrollAlign.START, scrollToIndexOptions);
    return this.rootNode;
  }

  getChildCountAllExpand() {
    const childCount = this.rootNode?.getChildrenCount(ChildrenCountMode.ALL_EXPAND);
    console.info(TEST_TAG + 'ALL_EXPAND, childCount=' + childCount);
  }

  getChildCountOnlyExpanded() {
    const childCount = this.rootNode?.getChildrenCount(ChildrenCountMode.ONLY_EXPANDED);
    console.info(TEST_TAG + 'ONLY_EXPANDED, childCount=' + childCount);
  }
  
  getChildCountAllNotExpand() {
    const childCount = this.rootNode?.getChildrenCount(ChildrenCountMode.ALL_NOT_EXPAND);
    console.info(TEST_TAG + 'ALL_NOT_EXPAND, childCount=' + childCount);
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();
  private scroller: Scroller = new Scroller();

  build() {
    Scroll(this.scroller) {
      Column({ space: 8 }) {
        Column() {
          Text('This is a NodeContainer.')
            .textAlign(TextAlign.Center)
            .borderRadius(10)
            .backgroundColor(0xFFFFFF)
            .width('100%')
            .fontSize(16)
          NodeContainer(this.myNodeController)
            .borderWidth(1)
            .width(300)
            .height(100)
        }

        Button('getChildCount(ALL_EXPAND)')
          .width(300)
          .onClick(() => {
            this.myNodeController.getChildCountAllExpand();
          })
        Button('getChildCount(ONLY_EXPANDED)')
          .width(300)
          .onClick(() => {
            this.myNodeController.getChildCountOnlyExpanded();
          })
        Button('getChildCount(ALL_NOT_EXPAND)')
          .width(300)
          .onClick(() => {
            this.myNodeController.getChildCountAllNotExpand();
          })
      }
      .width('100%')
    }
    .scrollable(ScrollDirection.Vertical) // The scrollbar scrolls in the vertical direction.
  }
}
```

## getChildrenCount

```TypeScript
getChildrenCount(countMode?: ChildrenCountMode): number
```

Obtains the number of child nodes of this FrameNode based on the specified counting mode.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| countMode | [ChildrenCountMode](arkts-arkui-framenode-childrencountmode-e.md) | No | The children count mode. Default value is ChildrenCountMode.ALL_EXPAND. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the number of children of the current FrameNode based on the count mode. |

**Examples**

See [getChildrenCount](#getchildrencount)

## getCrossLanguageOptions

```TypeScript
getCrossLanguageOptions(): CrossLanguageOptions
```

Obtains the cross-language access options for this FrameNode. For example, for nodes created using ArkTS, this API can obtain whether non-ArkTS languages are allowed to set the properties of these nodes and perform operations on the cross-language component tree. Since API version 26.0.0, this API can obtain whether non-ArkTS languages are allowed to perform operations on the component tree.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [CrossLanguageOptions](arkts-arkui-framenode-crosslanguageoptions-i.md) | Cross-ArkTS language access options. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## getCustomProperty

```TypeScript
getCustomProperty(name: string): Object | undefined
```

Obtains the component's custom property by its name.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the custom property. |

**Return value:**

| Type | Description |
| --- | --- |
| Object &#124; undefined | Value of the custom property. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## getFirstChild

```TypeScript
getFirstChild(): FrameNode | null
```

Obtains the first child node of this FrameNode.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) &#124; null | First child node. If the FrameNode does not contain any child node, null is returned. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## getFirstChildIndexWithoutExpand

```TypeScript
getFirstChildIndexWithoutExpand(): number
```

Obtains the sequence number of the first child node of this node that is in the main node tree. The child node sequence numbers are calculated based on all child nodes.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Sequence number of the first child node of this node that is in the main node tree. |

**Examples**

```TypeScript
See Example of Node Operations in the LazyForEach Scenario.
```

## getFrameNodeById

```TypeScript
getFrameNodeById(id: string): FrameNode | null
```

Searches for all child nodes layer by layer from the current node (which is used as the root node) and returns the first node that matches the specified ID. The search sequence is as follows: Search for direct child nodes first, then level-2 child nodes, and so on. The search stops as soon as a matching node is found.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | ID of the child node to be queried, which is the same as the component ID. |

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) &#124; null | First node that matches the specified ID, which is returned by searching for all child nodes layer by layer from the current node (which is used as the root node). If no child node of the current node matches the specified ID, a null is returned. |

**Examples**

```TypeScript
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  public rootNode: FrameNode | null = null;
  private id: string = 'text';

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    // Create a Column node.
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    this.rootNode.appendChild(col);

    // Create a Text component and add it to the Column node.
    let text = typeNode.createNode(uiContext, 'Text');
    text.initialize('Hello').id(this.id);
    col.appendChild(text);

    // Create another Text component with the same ID and add it to the Column node.
    let text1 = typeNode.createNode(uiContext, 'Text');
    text1.initialize('World').id(this.id);
    col.appendChild(text1);
    this.update();
    return this.rootNode;
  }

  update() {
    if (this.rootNode) {
      // Query and return the first component whose ID is text, and set the backgroundColor attribute.
      let node = this.rootNode.getFrameNodeById(this.id);
      node?.commonAttribute.backgroundColor('rgb(39,135,217)');
    }
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column() {
      NodeContainer(this.myNodeController)
        .borderWidth(1)
        .width(300)
        .height(300)
    }.width('100%')
  }
}
```

## getFrameNodeByUniqueId

```TypeScript
getFrameNodeByUniqueId(id: number): FrameNode | null
```

Searches for and returns the child node with the specified unique ID (which can be obtained using the [getUniqueId](#getuniqueid) API) under the current node (which is used as the root node).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | Unique ID of the child node to be queried. |

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) &#124; null | Child node with the unique ID, which is found from the current node (which is used as the root node). If the child node with the unique ID cannot be found under the current node, a null is returned. |

**Examples**

```TypeScript
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  public rootNode: FrameNode | null = null;
  private uniqueId: number = 0;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    // Create a Column node.
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    this.rootNode.appendChild(col);

    // Create a Text component and add it to the Column node.
    let text = typeNode.createNode(uiContext, 'Text');
    text.initialize('Hello');
    col.appendChild(text);

    // Create another Text component and add it to the Column node.
    let text1 = typeNode.createNode(uiContext, 'Text');
    text1.initialize('World');
    this.uniqueId = text1.getUniqueId();
    col.appendChild(text1);
    this.update();
    return this.rootNode;
  }

  update() {
    if (this.rootNode) {
      // Query and return the component with the unique ID, and set the backgroundColor attribute.
      let node = this.rootNode.getFrameNodeByUniqueId(this.uniqueId);
      node?.commonAttribute.backgroundColor('rgb(39,135,217)');
    }
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column() {
      NodeContainer(this.myNodeController)
        .borderWidth(1)
        .width(300)
        .height(300)
    }.width('100%')
  }
}
```

## getGlobalPositionOnDisplay

```TypeScript
getGlobalPositionOnDisplay(): Position
```

Obtains the position offset of this FrameNode relative to the global display, in vp.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | Position offset of the node relative to the global display, in vp. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## getId

```TypeScript
getId(): string
```

Obtains the node ID set by the user, which is the same as the value of the component ID.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| string | Node ID set by the user, which is the same as the value of the component ID. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## getInspectorInfo

```TypeScript
getInspectorInfo(): Object
```

Obtains the structure information of the node, which is consistent with what is found in DevEco Studio's built-in &lt;!--RP1--&gt;ArkUI Inspector &lt;!--RP1End--&gt;tool.

> **NOTE:** 
> 
> The **getInspectorInfo** API is designed for debugging purposes to obtain information about all nodes. Frequent
> calls to this API may cause performance degradation.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Object | Structure information of the node. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## getInteractionEventBindingInfo

```TypeScript
getInteractionEventBindingInfo(eventType: EventQueryType): InteractionEventBindingInfo | undefined
```

Obtains the event binding information for the target node. Returns **undefined** if the specified interaction event type is not bound to the component node.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| eventType | [EventQueryType](arkts-arkui-eventquerytype-e.md) | Yes | Type of the interaction event to query. |

**Return value:**

| Type | Description |
| --- | --- |
| [InteractionEventBindingInfo](arkts-arkui-framenode-interactioneventbindinginfo-i.md) &#124; undefined | Returns an **InteractionEventBindingInfo** object containing event binding details if the interaction event is bound to the current node; returns **undefined** otherwise. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## getLastChildIndexWithoutExpand

```TypeScript
getLastChildIndexWithoutExpand(): number
```

Obtains the sequence number of the last child node of this node that is in the main node tree. The child node sequence numbers are calculated based on all child nodes.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Sequence number of the last child node of this node that is in the main node tree. |

**Examples**

```TypeScript
See Example of Node Operations in the LazyForEach Scenario.
```

## getLayoutPosition

```TypeScript
getLayoutPosition(): Position
```

Obtains the position offset of this FrameNode relative to the parent component after layout, in px. The offset is the result of the parent component's layout on this node; therefore, the **offset** attribute that takes effect after layout and the **position** attribute that does not participate in layout do not affect this offset value.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | Position offset of the current FrameNode relative to the parent component after layout, in px. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## getMeasuredSize

```TypeScript
getMeasuredSize(): Size
```

Obtains the measured size of this FrameNode, in px.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Size | Measured size of the node, in px. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## getNextSibling

```TypeScript
getNextSibling(): FrameNode | null
```

Obtains the next sibling node of this FrameNode.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) &#124; null | Next sibling node of the current FrameNode. If the FrameNode does not have the next sibling node, null is returned. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## getNodePropertyValue

```TypeScript
getNodePropertyValue(property: AnimationPropertyType): number[]
```

Obtains the property value of the FrameNode.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| property | [AnimationPropertyType](arkts-arkui-animationpropertytype-e.md) | Yes | Animation property type. |

**Return value:**

| Type | Description |
| --- | --- |
| number[] | Current property value from the render node. The array length corresponds to the property type. <br>The return value format varies by property: <br>- An empty array (length 0) is returned if the node has been disposed, the [dispose](#dispose) API has been called, or the property enumeration is invalid. <br>- **AnimationPropertyType.ROTATION**: [rotationX, rotationY, rotationZ] in degrees (°). <br>- **AnimationPropertyType.TRANSLATION**: [translateX, translateY] in px. <br>- **AnimationPropertyType.SCALE**: [scaleX, scaleY] (scale factors). <br>- **AnimationPropertyType.OPACITY**: [opacity]. <br>1. After animation cancellation, the node's property value is restored to the display value at the time of cancellation, which can be obtained using this API. <br>2. During animation playback, this API returns the final target value rather than real-time interpolated values. <br> |

**Examples**

```TypeScript
See Example of Creating and Canceling an Animation.
```

## getNodeType

```TypeScript
getNodeType(): string
```

Obtains the type of the node. For built-in components, the node type corresponds to the component name. For example, the node type of the Button component is **Button**. For custom components that implement rendering, the node type is **__Common__**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| string | Type of the node. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## getOpacity

```TypeScript
getOpacity(): number
```

Obtains the opacity of the node. The minimum value is 0, and the maximum value is 1.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Opacity of the node. Value range: [0, 1]. A larger value indicates lower opacity. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## getParent

```TypeScript
getParent(): FrameNode | null
```

Obtains the parent node of this FrameNode.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) &#124; null | Parent node of the current FrameNode. If the FrameNode does not contain a parent node, null is returned. |

**Examples**

```TypeScript
See Example of Node Operations and Example of Obtaining the Root Node.
```

## getPositionToParent

```TypeScript
getPositionToParent(): Position
```

Obtains the position offset of this FrameNode relative to the parent component, in vp.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | Position offset of the node relative to the parent component, in vp. |

**Examples**

```TypeScript
import { NodeController, FrameNode, UIContext } from '@kit.ArkUI';

const TEST_TAG: string = 'FrameNode ';

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  public frameNode: FrameNode | null = null;
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    this.frameNode = new FrameNode(uiContext);
    this.frameNode.commonAttribute.backgroundColor(Color.Pink);
    this.frameNode.commonAttribute.size({ width: 100, height: 100 });
    this.rootNode.appendChild(this.frameNode);
    return this.rootNode;
  }

  getPositionToParent() {
    // Obtain the offset of FrameNode relative to its parent component.
    let positionToParent = this.rootNode?.getPositionToParent();
    console.info(`${TEST_TAG}${JSON.stringify(positionToParent)}`);
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();
  private scroller: Scroller = new Scroller();

  build() {
    Scroll(this.scroller) {
      Column({ space: 8 }) {
        Column() {
          Text('This is a NodeContainer.')
            .textAlign(TextAlign.Center)
            .borderRadius(10)
            .backgroundColor(0xFFFFFF)
            .width('100%')
            .fontSize(16)
          NodeContainer(this.myNodeController)
            .borderWidth(1)
            .width(300)
            .height(100)
        }

        Button('getPositionToParent')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToParent();
          })
      }
      .width('100%')
    }
    .scrollable(ScrollDirection.Vertical) // The scrollbar scrolls in the vertical direction.
  }
}
```

## getPositionToParentWithTransform

```TypeScript
getPositionToParentWithTransform(): Position
```

Obtains the position offset of a FrameNode relative to its drawing-enabled parent component, in vp. Drawing attributes include transform and translate. This API returns the upper left corner coordinates after component layout.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | Position offset of the node relative to the parent component, in vp. If other drawing attributes (such as **transform** and **translate**) are set, the return value may slightly deviate due to the precision of floating point numbers. |

**Examples**

```TypeScript
import { NodeController, FrameNode, UIContext } from '@kit.ArkUI';

const TEST_TAG: string = 'FrameNode ';

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  public frameNode: FrameNode | null = null;
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    this.frameNode = new FrameNode(uiContext);
    this.frameNode.commonAttribute.backgroundColor(Color.Pink);
    this.frameNode.commonAttribute.size({ width: 100, height: 100 });
    this.rootNode.appendChild(this.frameNode);
    return this.rootNode;
  }

  getPositionToParentWithTransform() {
    // Obtain the offset of the FrameNode relative to its drawing-enabled parent component.
    let positionToParentWithTransform = this.rootNode?.getPositionToParentWithTransform();
    console.info(`${TEST_TAG}${JSON.stringify(positionToParentWithTransform)}`);
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();
  private scroller: Scroller = new Scroller();

  build() {
    Scroll(this.scroller) {
      Column({ space: 8 }) {
        Column() {
          Text('This is a NodeContainer.')
            .textAlign(TextAlign.Center)
            .borderRadius(10)
            .backgroundColor(0xFFFFFF)
            .width('100%')
            .fontSize(16)
          NodeContainer(this.myNodeController)
            .borderWidth(1)
            .width(300)
            .height(100)
        }

        Button('getPositionToParentWithTransform')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToParentWithTransform();
          })
      }
      .width('100%')
    }
    .scrollable(ScrollDirection.Vertical) // The scrollbar scrolls in the vertical direction.
  }
}
```

## getPositionToScreen

```TypeScript
getPositionToScreen(): Position
```

Obtains the position offset of this FrameNode relative to the screen, in vp.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | Position offset of the node relative to the screen, in vp. |

**Examples**

```TypeScript
import { NodeController, FrameNode, UIContext } from '@kit.ArkUI';

const TEST_TAG: string = 'FrameNode ';

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  public frameNode: FrameNode | null = null;
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    this.frameNode = new FrameNode(uiContext);
    this.frameNode.commonAttribute.backgroundColor(Color.Pink);
    this.frameNode.commonAttribute.size({ width: 100, height: 100 });
    this.rootNode.appendChild(this.frameNode);
    return this.rootNode;
  }

  getPositionToScreen() {
    // Obtain the offset of a FrameNode relative to the screen.
    let positionToScreen = this.rootNode?.getPositionToScreen();
    console.info(`${TEST_TAG}${JSON.stringify(positionToScreen)}`);
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();
  private scroller: Scroller = new Scroller();

  build() {
    Scroll(this.scroller) {
      Column({ space: 8 }) {
        Column() {
          Text('This is a NodeContainer.')
            .textAlign(TextAlign.Center)
            .borderRadius(10)
            .backgroundColor(0xFFFFFF)
            .width('100%')
            .fontSize(16)
          NodeContainer(this.myNodeController)
            .borderWidth(1)
            .width(300)
            .height(100)
        }

        Button('getPositionToScreen')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToScreen();
          })
      }
      .width('100%')
    }
    .scrollable(ScrollDirection.Vertical) // The scrollbar scrolls in the vertical direction.
  }
}
```

## getPositionToScreenWithTransform

```TypeScript
getPositionToScreenWithTransform(): Position
```

Obtains the position offset of a FrameNode relative to the drawing-enabled screen, in vp. Drawing attributes include transform and translate. This API returns the upper left corner coordinates after component layout.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | Position offset of the node relative to the screen, in vp. If other drawing attributes (such as **transform** and **translate**) are set, the return value may slightly deviate due to the precision of floating point numbers. |

**Examples**

```TypeScript
import { NodeController, FrameNode, UIContext } from '@kit.ArkUI';

const TEST_TAG: string = 'FrameNode ';

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  public frameNode: FrameNode | null = null;
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    this.frameNode = new FrameNode(uiContext);
    this.frameNode.commonAttribute.backgroundColor(Color.Pink);
    this.frameNode.commonAttribute.size({ width: 100, height: 100 });
    this.rootNode.appendChild(this.frameNode);
    return this.rootNode;
  }

  getPositionToScreenWithTransform() {
    // Obtain the offset of the FrameNode relative to the drawing-enabled screen.
    let positionToScreenWithTransform = this.rootNode?.getPositionToScreenWithTransform();
    console.info(`${TEST_TAG}${JSON.stringify(positionToScreenWithTransform)}`);
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();
  private scroller: Scroller = new Scroller();

  build() {
    Scroll(this.scroller) {
      Column({ space: 8 }) {
        Column() {
          Text('This is a NodeContainer.')
            .textAlign(TextAlign.Center)
            .borderRadius(10)
            .backgroundColor(0xFFFFFF)
            .width('100%')
            .fontSize(16)
          NodeContainer(this.myNodeController)
            .borderWidth(1)
            .width(300)
            .height(100)
        }

        Button('getPositionToScreenWithTransform')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToScreenWithTransform();
          })
      }
      .width('100%')
    }
    .scrollable(ScrollDirection.Vertical) // The scrollbar scrolls in the vertical direction.
  }
}
```

## getPositionToWindow

```TypeScript
getPositionToWindow(): Position
```

Obtains the position offset of this FrameNode relative to the window, in vp.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | Position offset of the node relative to the window, in vp. |

**Examples**

```TypeScript
import { NodeController, FrameNode, UIContext } from '@kit.ArkUI';

const TEST_TAG: string = 'FrameNode ';

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  public frameNode: FrameNode | null = null;
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    this.frameNode = new FrameNode(uiContext);
    this.frameNode.commonAttribute.backgroundColor(Color.Pink);
    this.frameNode.commonAttribute.size({ width: 100, height: 100 });
    this.rootNode.appendChild(this.frameNode);
    return this.rootNode;
  }

  getPositionToWindow() {
    // Obtain the offset of a FrameNode relative to the window.
    let positionToWindow = this.rootNode?.getPositionToWindow();
    console.info(`${TEST_TAG}${JSON.stringify(positionToWindow)}`);
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();
  private scroller: Scroller = new Scroller();

  build() {
    Scroll(this.scroller) {
      Column({ space: 8 }) {
        Column() {
          Text('This is a NodeContainer.')
            .textAlign(TextAlign.Center)
            .borderRadius(10)
            .backgroundColor(0xFFFFFF)
            .width('100%')
            .fontSize(16)
          NodeContainer(this.myNodeController)
            .borderWidth(1)
            .width(300)
            .height(100)
        }

        Button('getPositionToWindow')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToWindow();
          })
      }
      .width('100%')
    }
    .scrollable(ScrollDirection.Vertical) // The scrollbar scrolls in the vertical direction.
  }
}
```

## getPositionToWindowWithTransform

```TypeScript
getPositionToWindowWithTransform(): Position
```

Obtains the position offset of a FrameNode relative to the drawing-enabled window, in vp. Drawing attributes include transform and translate. This API returns the upper left corner coordinates after component layout.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | Position offset of the node relative to the window, in vp. If other drawing attributes (such as **transform** and **translate**) are set, the return value may slightly deviate due to the precision of floating point numbers. |

**Examples**

```TypeScript
import { NodeController, FrameNode, UIContext } from '@kit.ArkUI';

const TEST_TAG: string = 'FrameNode ';

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  public frameNode: FrameNode | null = null;
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    this.frameNode = new FrameNode(uiContext);
    this.frameNode.commonAttribute.backgroundColor(Color.Pink);
    this.frameNode.commonAttribute.size({ width: 100, height: 100 });
    this.rootNode.appendChild(this.frameNode);
    return this.rootNode;
  }

  getPositionToWindowWithTransform() {
    // Obtain the offset of the FrameNode relative to the drawing-enabled window.
    let positionToWindowWithTransform = this.rootNode?.getPositionToWindowWithTransform();
    console.info(`${TEST_TAG}${JSON.stringify(positionToWindowWithTransform)}`);
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();
  private scroller: Scroller = new Scroller();

  build() {
    Scroll(this.scroller) {
      Column({ space: 8 }) {
        Column() {
          Text('This is a NodeContainer.')
            .textAlign(TextAlign.Center)
            .borderRadius(10)
            .backgroundColor(0xFFFFFF)
            .width('100%')
            .fontSize(16)
          NodeContainer(this.myNodeController)
            .borderWidth(1)
            .width(300)
            .height(100)
        }
        Button('getPositionToWindowWithTransform')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToWindowWithTransform();
          })
      }
      .width('100%')
    }
    .scrollable(ScrollDirection.Vertical) // The scrollbar scrolls in the vertical direction.
  }
}
```

## getPreviousSibling

```TypeScript
getPreviousSibling(): FrameNode | null
```

Obtains the previous sibling node of this FrameNode.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) &#124; null | Previous sibling node of the current FrameNode. If the FrameNode does not have the previous sibling node, null is returned. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## getRenderNode

```TypeScript
getRenderNode(): RenderNode | null
```

Obtains the [RenderNode](arkts-arkui-rendernode-c.md) held by the FrameNode.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [RenderNode](arkts-arkui-rendernode-c.md) &#124; null | **RenderNode** instance. If the current FrameNode does not hold any RenderNode, **null** is returned. If the current FrameNode is a node created by a declarative component, **null** is returned. |

**Examples**

```TypeScript
import { NodeController, FrameNode } from '@kit.ArkUI';

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    // Obtain the RenderNode held by rootNode.
    const renderNode = this.rootNode.getRenderNode();
    if (renderNode !== null) {
      renderNode.size = { width: 100, height: 100 };
      renderNode.backgroundColor = 0XFFFF0000;
    }

    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Row() {
      NodeContainer(this.myNodeController)
    }
  }
}
```

## getUniqueId

```TypeScript
getUniqueId(): number
```

Obtains the system-assigned unique ID of the node.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | System-assigned unique ID of the node. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## getUserConfigBorderWidth

```TypeScript
getUserConfigBorderWidth(): Edges<LengthMetrics>
```

Obtains the border width set by the user.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Edges](arkts-arkui-graphics-edges-i.md)&lt;[LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)&gt; | Border width set by the user. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## getUserConfigMargin

```TypeScript
getUserConfigMargin(): Edges<LengthMetrics>
```

Obtains the margin set by the user.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Edges](arkts-arkui-graphics-edges-i.md)&lt;[LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)&gt; | Margin set by the user. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## getUserConfigPadding

```TypeScript
getUserConfigPadding(): Edges<LengthMetrics>
```

Obtains the padding set by the user.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Edges](arkts-arkui-graphics-edges-i.md)&lt;[LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)&gt; | Padding set by the user. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## getUserConfigSize

```TypeScript
getUserConfigSize(): SizeT<LengthMetrics>
```

Obtains the width and height set by the user.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [SizeT](arkts-arkui-graphics-sizet-i.md)&lt;[LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)&gt; | Width and height set by the user. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## insertChildAfter

```TypeScript
insertChildAfter(child: FrameNode, sibling: FrameNode | null): void
```

Inserts a child node after the specified child node of this FrameNode. If this FrameNode is not modifiable, an exception is thrown.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| child | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Child node to add.<br>The target child node must not be a declaratively created node, that is, a FrameNode that is not modifiable. Only declarative nodes obtained from a BuilderNode can be used as child nodes. If the child node does not meet the specifications, an exception is thrown. <br> The child node cannot have a parent node. Otherwise, an exception is thrown. |
| sibling | [FrameNode](arkts-arkui-framenode-c.md) &#124; null | Yes | Node after which the new child node will be inserted. If this parameter is left empty, the new node is inserted before the first subnode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode-not-modifiable) | The FrameNode is not modifiable. |
| [100025](../errorcode-node.md#100025-invalid-parameter-value) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'child' is invalid: it cannot be adopted."<br>**Applicable version:** 22 and later |

**Examples**

```TypeScript
See Example of Node Operations.
```

## invalidate

```TypeScript
invalidate(): void
```

Invalidates this FrameNode to trigger a re-rendering of the self-drawing content.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## invalidateAttributes

```TypeScript
invalidateAttributes(): void
```

Forces immediate node property updates in this frame.

By default, property modifications applied after the build phase are deferred until the next frame.

This API ensures rendering synchronization by triggering immediate property updates.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
Starting from API version 21, when dynamically switching between nodes using if/else statements, you can call invalidateAttributes during node creation to trigger immediate attribute updates, preventing visual flickering during component switching.
```

## isAttached

```TypeScript
isAttached(): boolean
```

Obtains whether the node is mounted to the main node tree.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the node is mounted to the main node tree.<br>The value **true** means that the node is mounted to the main node tree, and **false** means the opposite. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## isClipToFrame

```TypeScript
isClipToFrame(): boolean
```

Checks whether the node is clipped to the component area. This API returns **true** after the [dispose](#dispose) API is called to release the reference to the FrameNode.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the node is clipped to the component area.<br>The value **true** means that the node is clipped to the component area, and **false** means the opposite. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## isDisposed

```TypeScript
isDisposed(): boolean
```

Checks whether this FrameNode object has released its reference to its backend entity node. Frontend nodes maintain references to corresponding backend entity nodes. After a node calls the **dispose** API to release this reference, subsequent API calls may cause crashes or return default values. This API facilitates validation of node validity prior to operations, thereby mitigating risks in scenarios where calls after disposal are required.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the reference to the backend node is released. The value **true** means that the reference to backend node is released, and **false** means the opposite. |

**Examples**

```TypeScript
See FrameNode Validity Check Example.
```

## isInRenderState

```TypeScript
isInRenderState(): boolean
```

Checks whether this node is in render state. A node is considered to be in render state when its corresponding RenderNode is present in the render tree.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the node is in render state.<br>**true**: The node is in render state. **false**: The node is not in render state. |

**Examples**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @State message: string = 'is on render tree';
  @State @Watch('change') isShow: boolean = true;
  data: Array<string> = ['hello1', 'hello2', 'hello3', 'hello4', 'hello5', 'hello6', 'hello7', 'hello8'];

  // Listen for state changes and log the render status.
  change() {
    let buttonNode = this.getUIContext().getFrameNodeById('testButton');
    if (buttonNode == null) {
      return;
    }
    let isOnRenderTree = buttonNode!.isInRenderState();
    if (isOnRenderTree) {
      hilog.info(1, 'frameNode', 'is on render tree');
    } else {
      hilog.info(1, 'frameNode', 'is not on render tree');
    }
  }

  build() {
    Column() {
      Button('change button visibility').onClick(() => {
        // Change the visibility status of the button.
        this.isShow = !this.isShow;
      })
        .margin({ top: 20 })
      Button('test button')
        .visibility(this.isShow ? Visibility.Visible : Visibility.Hidden)
        .margin(20).id('testButton')

      List() {
        ForEach(this.data, (item: string, index: number) => {
          ListItem() {
            Text(item).id(item)
          }.alignSelf(ItemAlign.Center).width('100%')
        })
      }
      .width('30%')
      .alignSelf(ItemAlign.Center)
      .height('10%')
      .onReachEnd(() => {
        let textNode8 = this.getUIContext().getFrameNodeById('hello8');
        if (textNode8 != null) {
          let isOnRenderTree = textNode8!.isInRenderState();
          hilog.info(1, 'frameNode', 'is hello8 on RenderTree: %{public}s', isOnRenderTree);
        }
        let textNode1 = this.getUIContext().getFrameNodeById('hello1');
        if (textNode1 != null) {
          let isOnRenderTree = textNode1!.isInRenderState();
          if (isOnRenderTree) { this.message = 'is on render tree'; }
          hilog.info(1, 'frameNode', 'is hello1 on RenderTree: %{public}s', isOnRenderTree);
        }
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

## isModifiable

```TypeScript
isModifiable(): boolean
```

Checks whether this FrameNode is modifiable.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether this FrameNode is modifiable. <br>The value **true** means that the FrameNode is modifiable, and **false** means the opposite. <br>Returns **false** if the node is a system component proxy node in a [custom component node](../../../ui/arkts-user-defined-node.md#custom-component-node-framenode) or the node has been [disposed](#dispose). <br>When **false** is returned, the current FrameNode does not support operations such as [appendChild](#appendchild), [insertChildAfter](#insertchildafter), [removeChild](#removechild), [clearChildren](#clearchildren), [createAnimation](#createanimation), and [cancelAnimations](#cancelanimations). |

**Examples**

```TypeScript
See Example of Node Operations.
```

## isOnMainTree

```TypeScript
isOnMainTree(): boolean
```

Queries whether a node is mounted to the main node tree.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the node is mounted to the main node tree.<br>The value **true** means that the node is mounted to the main node tree, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100026](../errorcode-node.md#100026-the-instance-object-used-to-call-the-api-has-been-unbound-from-the-backend-entity-node) | The current FrameNode has been disposed. |

**Examples**

```TypeScript
import { NodeController, FrameNode, UIContext, typeNode } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

const TEST_TAG: string = 'FrameNode ';

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  public frameNode: FrameNode | null = null;
  public childList: Array<FrameNode> = new Array<FrameNode>();
  private rootNode: FrameNode | null = null;
  private uiContext: UIContext | null = null;
  private childrenCount: number = 0;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    this.uiContext = uiContext;

    this.frameNode = new FrameNode(uiContext);
    this.frameNode.commonAttribute.backgroundColor(Color.Pink);
    this.frameNode.commonAttribute.size({ width: 100, height: 100 });
    this.addCommonEvent(this.frameNode)
    this.rootNode.appendChild(this.frameNode);
    this.childrenCount = this.childrenCount + 1;
    for (let i = 0; i < 10; i++) {
      let childNode = new FrameNode(uiContext);
      this.childList.push(childNode);
      this.frameNode.appendChild(childNode);
    }
    let stackNode = typeNode.createNode(uiContext, 'Stack');
    this.frameNode.appendChild(stackNode);
    return this.rootNode;
  }

  addCommonEvent(frameNode: FrameNode) {
    frameNode.commonEvent.setOnClick((event: ClickEvent) => {
      console.info(`Click FrameNode: ${JSON.stringify(event)}`)
    })
  }

  createFrameNode() {
    let frameNode = new FrameNode(this.uiContext!);
    frameNode.commonAttribute.backgroundColor(Color.Pink);
    frameNode.commonAttribute.size({ width: 100, height: 100 });
    frameNode.commonAttribute.position({ x: this.childrenCount * 120, y: 0 });

    return frameNode;
  }

  appendChild() {
    const childNode = this.createFrameNode();
    this.rootNode!.appendChild(childNode);
    this.childrenCount = this.childrenCount + 1;
  }

  insertChildAfter(index: number) {
    let insertNode = this.createFrameNode();
    let childNode = this.rootNode!.getChild(index);
    this.rootNode!.insertChildAfter(insertNode, childNode);
    this.childrenCount = this.childrenCount + 1;
  }

  removeChild(index: number) {
    let childNode = this.rootNode!.getChild(index);
    if (childNode == null) {
      console.info(`${TEST_TAG} getchild at index {${index}} : fail`);
      return;
    }
    this.rootNode!.removeChild(childNode);
    this.childrenCount = this.childrenCount - 1;
  }

  getChildNumber() {
    console.info(`${TEST_TAG} getChildNumber ${this.rootNode!.getChildrenCount()}`)
    console.info(`${TEST_TAG} children count is ${this.childrenCount}`);
  }

  clearChildren() {
    this.rootNode!.clearChildren();
  }

  searchFrameNode() {
    if (this.rootNode!.getFirstChild() === null) {
      console.info(`${TEST_TAG} the rootNode does not have child node.`)
    }
    if (this.rootNode!.getFirstChild() === this.frameNode) {
      console.info(`${TEST_TAG} getFirstChild result: success. The first child of the rootNode is equals to frameNode.`);
    } else {
      console.info(`${TEST_TAG} getFirstChild result: fail. The first child of the rootNode is not equals to frameNode.`);
    }
    if (this.frameNode!.getChild(5) === this.frameNode!.getChild(4)!.getNextSibling()) {
      console.info(`${TEST_TAG} getNextSibling result: success.`);
    } else {
      console.info(`${TEST_TAG} getNextSibling result: fail.`);
    }
    if (this.frameNode!.getChild(3) === this.frameNode!.getChild(4)!.getPreviousSibling()) {
      console.info(`${TEST_TAG} getPreviousSibling result: success.`);
    } else {
      console.info(`${TEST_TAG} getPreviousSibling result: fail.`);
    }
    if (this.rootNode!.getFirstChild() !== null && this.rootNode!.getFirstChild()!.getParent() === this.rootNode) {
      console.info(`${TEST_TAG} getParent result: success.`);
    } else {
      console.info(`${TEST_TAG} getParent result: fail.`);
    }
    if (this.rootNode!.getParent() !== null) {
      console.info(`${TEST_TAG} get ArkTsNode success.`)
      console.info(`${TEST_TAG} check rootNode whether is modifiable ${this.rootNode!.isModifiable()}`)
      console.info(`${TEST_TAG} check getParent whether is modifiable ${this.rootNode!.getParent()!.isModifiable()}`)
    } else {
      console.info(`${TEST_TAG} get ArkTsNode fail.`);
    }
  }

  moveFrameNode() {
    const currentNode = this.frameNode!.getChild(10);
    try {
      currentNode!.moveTo(this.rootNode, 0);
      if (this.rootNode!.getChild(0) === currentNode) {
        console.info(`${TEST_TAG} moveTo result: success.`);
      } else {
        console.info(`${TEST_TAG} moveTo result: fail.`);
      }
    } catch (err) {
      console.error(`${TEST_TAG} ${(err as BusinessError).code} : ${(err as BusinessError).message}`);
      console.error(`${TEST_TAG} moveTo result: fail.`);
    }
  }

  getPositionToWindow() {
    let positionToWindow = this.rootNode?.getPositionToWindow();
    console.info(`${TEST_TAG}${JSON.stringify(positionToWindow)}`);
  }

  getPositionToParent() {
    let positionToParent = this.rootNode?.getPositionToParent();
    console.info(`${TEST_TAG}${JSON.stringify(positionToParent)}`);
  }

  getPositionToScreen() {
    let positionToScreen = this.rootNode?.getPositionToScreen();
    console.info(`${TEST_TAG}${JSON.stringify(positionToScreen)}`);
  }

  getGlobalPositionOnDisplay() {
    let positionOnGlobalDisplay = this.rootNode?.getGlobalPositionOnDisplay();
    console.info(`${TEST_TAG}${JSON.stringify(positionOnGlobalDisplay)}`);
  }

  getPositionToWindowWithTransform() {
    let positionToWindowWithTransform = this.rootNode?.getPositionToWindowWithTransform();
    console.info(`${TEST_TAG}${JSON.stringify(positionToWindowWithTransform)}`);
  }

  getPositionToParentWithTransform() {
    let positionToParentWithTransform = this.rootNode?.getPositionToParentWithTransform();
    console.info(`${TEST_TAG}${JSON.stringify(positionToParentWithTransform)}`);
  }

  getPositionToScreenWithTransform() {
    let positionToScreenWithTransform = this.rootNode?.getPositionToScreenWithTransform();
    console.info(`${TEST_TAG}${JSON.stringify(positionToScreenWithTransform)}`);
  }

  getMeasuredSize() {
    let measuredSize = this.frameNode?.getMeasuredSize();
    console.info(`${TEST_TAG}${JSON.stringify(measuredSize)}`);
  }

  getLayoutPosition() {
    let layoutPosition = this.frameNode?.getLayoutPosition();
    console.info(`${TEST_TAG}${JSON.stringify(layoutPosition)}`);
  }

  getUserConfigBorderWidth() {
    let userConfigBorderWidth = this.frameNode?.getUserConfigBorderWidth();
    console.info(`${TEST_TAG}${JSON.stringify(userConfigBorderWidth)}`);
  }

  getUserConfigPadding() {
    let userConfigPadding = this.frameNode?.getUserConfigPadding();
    console.info(`${TEST_TAG}${JSON.stringify(userConfigPadding)}`);
  }

  getUserConfigMargin() {
    let userConfigMargin = this.frameNode?.getUserConfigMargin();
    console.info(`${TEST_TAG}${JSON.stringify(userConfigMargin)}`);
  }

  getUserConfigSize() {
    let userConfigSize = this.frameNode?.getUserConfigSize();
    console.info(`${TEST_TAG}${JSON.stringify(userConfigSize)}`);
  }

  getId() {
    let id = this.frameNode?.getId();
    console.info(`${TEST_TAG}${id}`);
  }

  getUniqueId() {
    let uniqueId = this.frameNode?.getUniqueId();
    console.info(`${TEST_TAG}${uniqueId}`);
  }

  getNodeType() {
    let nodeType = this.frameNode?.getNodeType();
    console.info(`${TEST_TAG}${nodeType}`);
  }

  getOpacity() {
    let opacity = this.frameNode?.getOpacity();
    console.info(`${TEST_TAG}${JSON.stringify(opacity)}`);
  }

  isVisible() {
    let visible = this.frameNode?.isVisible();
    console.info(`${TEST_TAG}${JSON.stringify(visible)}`);
  }

  isClipToFrame() {
    let clipToFrame = this.frameNode?.isClipToFrame();
    console.info(`${TEST_TAG}${JSON.stringify(clipToFrame)}`);
  }

  isAttached() {
    let attached = this.frameNode?.isAttached();
    console.info(`${TEST_TAG}${JSON.stringify(attached)}`);
  }

  isOnMainTree() {
    let attached = this.frameNode?.isOnMainTree();
    console.info(`${TEST_TAG}${JSON.stringify(attached)}`);
  }

  getInspectorInfo() {
    let inspectorInfo = this.frameNode?.getInspectorInfo();
    console.info(`${TEST_TAG}${JSON.stringify(inspectorInfo)}`);
  }

  setCrossLanguageOptions() {
    console.info(`${TEST_TAG} getCrossLanguageOptions ${JSON.stringify(this.frameNode?.getCrossLanguageOptions())}`);
    try {
      this.frameNode?.setCrossLanguageOptions({
        attributeSetting: true
      });
      console.info(`${TEST_TAG} setCrossLanguageOptions success.`);
    } catch (err) {
      console.error(`${TEST_TAG} ${(err as BusinessError).code} : ${(err as BusinessError).message}`);
      console.error(`${TEST_TAG} setCrossLanguageOptions fail.`);
    }
    console.info(`${TEST_TAG} getCrossLanguageOptions ${JSON.stringify(this.frameNode?.getCrossLanguageOptions())}`);
  }

  getInteractionEventBindingInfo() {
    let bindingInfo = this.frameNode?.getInteractionEventBindingInfo(EventQueryType.ON_CLICK);
    console.info(`${TEST_TAG}${bindingInfo?.baseEventRegistered}`);
    console.info(`${TEST_TAG}${bindingInfo?.nodeEventRegistered}`);
    console.info(`${TEST_TAG}${bindingInfo?.nativeEventRegistered}`);
    console.info(`${TEST_TAG}${bindingInfo?.builtInEventRegistered}`);
    console.info(`${TEST_TAG}${JSON.stringify(bindingInfo)}`);
  }

  throwError() {
    try {
      this.rootNode!.getParent()!.clearChildren();
    } catch (err) {
      console.error(`${TEST_TAG} ${(err as BusinessError).code} : ${(err as BusinessError).message}`);
    }
    try {
      this.rootNode!.getParent()!.appendChild(new FrameNode(this.uiContext));
    } catch (err) {
      console.error(`${TEST_TAG} ${(err as BusinessError).code} : ${(err as BusinessError).message}`);
    }
    try {
      this.rootNode!.getParent()!.removeChild(this.rootNode!.getParent()!.getChild(0));
    } catch (err) {
      console.error(`${TEST_TAG} ${(err as BusinessError).code} : ${(err as BusinessError).message}`);
    }
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();
  private scroller: Scroller = new Scroller();
  @State index: number = 0;

  build() {
    Scroll(this.scroller) {
      Column({ space: 8 }) {
        Column() {
          Row() {
            Button('ADD')
              .onClick(() => {
                this.index++;
              })
            Button('DEC')
              .onClick(() => {
                this.index--;
              })
          }

          Text('Current index is ' + this.index)
            .textAlign(TextAlign.Center)
            .borderRadius(10)
            .backgroundColor(0xFFFFFF)
            .width('100%')
            .fontSize(16)
        }

        Column() {
          Text('This is a NodeContainer.')
            .textAlign(TextAlign.Center)
            .borderRadius(10)
            .backgroundColor(0xFFFFFF)
            .width('100%')
            .fontSize(16)
          NodeContainer(this.myNodeController)
            .borderWidth(1)
            .width(300)
            .height(100)
        }

        Button('appendChild')
          .width(300)
          .onClick(() => {
            this.myNodeController.appendChild();
          })
        Button('insertChildAfter')
          .width(300)
          .onClick(() => {
            this.myNodeController.insertChildAfter(this.index);
          })
        Button('removeChild')
          .width(300)
          .onClick(() => {
            this.myNodeController.removeChild(this.index);
          })
        Button('clearChildren')
          .width(300)
          .onClick(() => {
            this.myNodeController.clearChildren();
          })
        Button('getChildNumber')
          .width(300)
          .onClick(() => {
            this.myNodeController.getChildNumber();
          })
        Button('searchFrameNode')
          .width(300)
          .onClick(() => {
            this.myNodeController.searchFrameNode();
          })
        Button('moveFrameNode')
          .width(300)
          .onClick(() => {
            this.myNodeController.moveFrameNode();
          })
        Button('getPositionToWindow')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToWindow();
          })
        Button('getPositionToParent')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToParent();
          })
        Button('getPositionToScreen')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToScreen();
          })
        Button('getGlobalPositionOnDisplay')
          .width(300)
          .onClick(() => {
            this.myNodeController.getGlobalPositionOnDisplay();
          })
        Button('getPositionToParentWithTransform')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToParentWithTransform();
          })
        Button('getPositionToWindowWithTransform')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToWindowWithTransform();
          })
        Button('getPositionToScreenWithTransform')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToScreenWithTransform();
          })
        Button('getMeasuredSize')
          .width(300)
          .onClick(() => {
            this.myNodeController.getMeasuredSize();
          })
        Button('getLayoutPosition')
          .width(300)
          .onClick(() => {
            this.myNodeController.getLayoutPosition();
          })
        Button('getUserConfigBorderWidth')
          .width(300)
          .onClick(() => {
            this.myNodeController.getUserConfigBorderWidth();
          })
        Button('getUserConfigPadding')
          .width(300)
          .onClick(() => {
            this.myNodeController.getUserConfigPadding();
          })
        Button('getUserConfigMargin')
          .width(300)
          .onClick(() => {
            this.myNodeController.getUserConfigMargin();
          })
        Button('getUserConfigSize')
          .width(300)
          .onClick(() => {
            this.myNodeController.getUserConfigSize();
          })
        Button('getId')
          .width(300)
          .onClick(() => {
            this.myNodeController.getId();
          })
        Button('getUniqueId')
          .width(300)
          .onClick(() => {
            this.myNodeController.getUniqueId();
          })
        Button('getNodeType')
          .width(300)
          .onClick(() => {
            this.myNodeController.getNodeType();
          })
        Button('getOpacity')
          .width(300)
          .onClick(() => {
            this.myNodeController.getOpacity();
          })
        Button('isVisible')
          .width(300)
          .onClick(() => {
            this.myNodeController.isVisible();
          })
        Button('isClipToFrame')
          .width(300)
          .onClick(() => {
            this.myNodeController.isClipToFrame();
          })
        Button('isAttached')
          .width(300)
          .onClick(() => {
            this.myNodeController.isAttached();
          })
        Button('isOnMainTree')
          .width(300)
          .onClick(() => {
            this.myNodeController.isOnMainTree();
          })
        Button('getInspectorInfo')
          .width(300)
          .onClick(() => {
            this.myNodeController.getInspectorInfo();
          })
        Button('getCustomProperty')
          .width(300)
          .onClick(() => {
            const uiContext: UIContext = this.getUIContext();
            if (uiContext) {
              const node: FrameNode | null = uiContext.getFrameNodeById('Test_Button') || null;
              if (node) {
                for (let i = 1; i < 4; i++) {
                  const key = 'customProperty' + i;
                  const property = node.getCustomProperty(key);
                  console.info(`${TEST_TAG}${key}`, JSON.stringify(property));
                }
              }
            }
          })
          .id('Test_Button')
          .customProperty('customProperty1', {
            'number': 10,
            'string': 'this is a string',
            'bool': true,
            'object': {
              'name': 'name',
              'value': 100
            }
          })
          .customProperty('customProperty2', {})
          .customProperty('customProperty2', undefined)
        Button('setCrossLanguageOptions')
          .width(300)
          .onClick(() => {
            this.myNodeController.setCrossLanguageOptions();
          })
        Button('getInteractionEventBindingInfo')
          .width(300)
          .onClick(() => {
            this.myNodeController.getInteractionEventBindingInfo();
          })
        Button('throwError')
          .width(300)
          .onClick(() => {
            this.myNodeController.throwError();
          })
      }
      .width('100%')
    }
    .scrollable(ScrollDirection.Vertical) // The scrollbar scrolls in the vertical direction.
  }
}
```

## isTransferred

```TypeScript
isTransferred(): boolean
```

Returns a flag indicating whether the current FrameNode was obtained through dynamic-static conversion, includes conversions in both directions: dynamic-to-static and static-to-dynamic.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if the FrameNode was converted between dynamic and static states, otherwise, returns false. |

## isVisible

```TypeScript
isVisible(): boolean
```

Obtains whether the node is visible.

> **NOTE:** 
> 
> The visibility of a node is determined by the **visibility** attribute of the component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the node is visible.<br>The value **true** means that the node is visible, and **false** means the opposite. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## layout

```TypeScript
layout(position: Position): void
```

Lays out this FrameNode, specifying the layout positions for the FrameNode and its child nodes. If the layout method is overridden, the overridden method is called. It is recommended that this API be called in [onLayout](#onlayout).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | [Position](arkts-arkui-position-t.md) | Yes | Position information used in layout. |

**Examples**

```TypeScript
See Example of Customizing a Node.
```

## measure

```TypeScript
measure(constraint: LayoutConstraint): void
```

Measures this FrameNode and calculates its size based on the layout constraints of the parent container. If the measurement method is overridden, the overridden method is called. It is recommended that this API be called in [onMeasure](#onmeasure).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| constraint | [LayoutConstraint](arkts-arkui-framenode-layoutconstraint-i.md) | Yes | Parent container layout constraints used for measurement. |

**Examples**

```TypeScript
See Example of Customizing a Node.
```

## moveTo

```TypeScript
moveTo(targetParent: FrameNode, index?: number): void
```

Moves this FrameNode to a specified position within the target FrameNode. If this FrameNode is not modifiable, an exception is thrown. When **targetParent** is a [typeNode](arkts-arkui-typenode-n.md), the API validates the type or number of child nodes. If the validation fails, an exception is thrown. For specific limitations, see [typeNode](arkts-arkui-typenode-n.md).

> **NOTE:** 
> 
> Currently, only the following types of [TypedFrameNode](arkts-arkui-framenode-typedframenode-i.md) are supported for the movement
> operations: [Stack](arkts-arkui-typenode-stack-t.md), [XComponent](arkts-arkui-typenode-xcomponent-t.md). This API does not work for
> other node types.
> 
> This API only supports [BuilderNode](arkts-arkui-buildernode-c.md) with root components of these types:
> Stack, XComponent,
> EmbeddedComponent. This API does not work for other
> component types.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetParent | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target parent node.<br>The target parent node must not be a declaratively created node, that is, a FrameNode that is not modifiable. If it does not meet the specifications, an exception is thrown. |
| index | number | No | Index of the child node. The current FrameNode will be inserted before the child node at the specified sequence number in the target FrameNode. If the target FrameNode has *n* nodes, the value range for **index** is 0, *n*-1].<br>If the parameter is invalid or not specified, the current FrameNode will be added to the end of the target FrameNode. <br>Default value: **-1** |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode-not-modifiable) | The FrameNode is not modifiable. |
| [100027](../errorcode-node.md#100027-the-current-node-has-been-adopted-as-a-child-node) | The current node has been adopted.<br>**Applicable version:** 22 and later |

**Examples**

```TypeScript
See Example of Node Operations.
```

## onDraw

```TypeScript
onDraw?(context: DrawContext): void
```

Implements custom drawing for the FrameNode. This API overrides the default drawing behavior and is invoked during FrameNode content rendering.

Note: The Canvas provided in the [DrawContext](arkts-arkui-graphics-drawcontext-c.md) parameter is a temporary command- recording canvas, not the actual rendering canvas of the node. For usage instructions, see [Adjusting the Transformation Matrix of the Custom Drawing Canvas](../../../ui/arkts-user-defined-arktsNode-frameNode.md#adjusting-the-transformation-matrix-of-the-custom-drawing-canvas).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [DrawContext](arkts-arkui-graphics-drawcontext-c.md) | Yes | Graphics drawing context. The self-drawing area cannot exceed the component's own size. |

**Examples**

```TypeScript
See Example of Customizing a Node.
```

## onLayout

```TypeScript
onLayout(position: Position): void
```

Called when this FrameNode needs to determine its layout. This API provides custom layout and overrides the default layout method. It can be used to specify how the FrameNode and its child nodes are positioned and sized within the layout.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | [Position](arkts-arkui-position-t.md) | Yes | Position information used in layout. |

**Examples**

```TypeScript
See Example of Customizing a Node.
```

## onMeasure

```TypeScript
onMeasure(constraint: LayoutConstraint): void
```

Called when this FrameNode needs to determine its size. This API provides custom measurement and overrides the default measurement method.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| constraint | [LayoutConstraint](arkts-arkui-framenode-layoutconstraint-i.md) | Yes | Layout constraints used by the component for measurement. |

**Examples**

```TypeScript
See Example of Customizing a Node.
```

## recycle

```TypeScript
recycle(): void
```

Triggers child component recycling in global reuse scenarios and fully releases FrameNode backend resources for reuse. This ensures efficient resource reclamation and reuse.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
See Example of Reusing and Recycling Nodes.
```

## removeAdoptedChild

```TypeScript
removeAdoptedChild(child: FrameNode): void
```

Removes a previously-adopted affiliated node.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| child | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Node to remove. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode-not-modifiable) | The current FrameNode is not modifiable. |
| [100025](../errorcode-node.md#100025-invalid-parameter-value) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'child' is invalid: it cannot be null." |
| [100026](../errorcode-node.md#100026-the-instance-object-used-to-call-the-api-has-been-unbound-from-the-backend-entity-node) | The current FrameNode has been disposed. |

**Examples**

```TypeScript
See Example of Adopting a Node as an Affiliate.
```

## removeChild

```TypeScript
removeChild(node: FrameNode): void
```

Deletes the specified child node from this FrameNode. If this FrameNode is not modifiable, an exception is thrown.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Child node to delete. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode-not-modifiable) | The FrameNode is not modifiable. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## removeSupportedUIStates

```TypeScript
removeSupportedUIStates(uiStates: number): void
```

Removes the state processing registration from the component.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uiStates | number | Yes | UI states to be removed.<br>Multiple states can be specified simultaneously using bitwise OR operations, for example, **targetUIStates = UIState.PRESSED  &#124;  UIState.FOCUSED**. |

**Examples**

```TypeScript
See Example of Setting and Deleting a Polymorphic Style State.
```

## reuse

```TypeScript
reuse(): void
```

Triggers child component reuse in global reuse scenarios to recycle FrameNode backend resources and improve resource utilization. To ensure adequate resource availability, call this API after the **recycle** API has been executed.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
See Example of Reusing and Recycling Nodes.
```

## setCrossLanguageOptions

```TypeScript
setCrossLanguageOptions(options: CrossLanguageOptions): void
```

Sets the cross-language access options for this FrameNode. For example, for nodes created using ArkTS, this API can set whether non-ArkTS languages are allowed to set the attributes of these nodes. Since API version 26.0.0, this API can set whether non-ArkTS languages are allowed to perform operations on the component tree. If the current FrameNode is not modifiable or does not support setting cross-language access options, an exception will be thrown.

> **NOTE:** 
> 
> Currently, the cross-ArkTS language access option can only be configured for the following components:
> [Scroll](arkts-arkui-typenode-scroll-t.md), [Swiper](arkts-arkui-typenode-swiper-t.md), [List](arkts-arkui-typenode-list-t.md),
> [ListItem](arkts-arkui-typenode-listitem-t.md), [ListItemGroup](arkts-arkui-typenode-listitemgroup-t.md),
> [WaterFlow](arkts-arkui-typenode-waterflow-t.md), [FlowItem](arkts-arkui-typenode-flowitem-t.md), [Grid](arkts-arkui-typenode-grid-t.md),
> [GridItem](arkts-arkui-typenode-griditem-t.md), [TextInput](arkts-arkui-typenode-textinput-t.md), [TextArea](arkts-arkui-typenode-textarea-t.md),
> [Column](arkts-arkui-typenode-column-t.md), [Row](arkts-arkui-typenode-row-t.md), [Stack](arkts-arkui-typenode-stack-t.md),
> [Flex](arkts-arkui-typenode-flex-t.md), [RelativeContainer](arkts-arkui-typenode-relativecontainer-t.md),
> [Progress](arkts-arkui-typenode-progress-t.md), [LoadingProgress](arkts-arkui-typenode-loadingprogress-t.md),
> [Image](arkts-arkui-typenode-image-t.md), [Button](arkts-arkui-typenode-button-t.md), [CheckBox](arkts-arkui-typenode-checkbox-t.md),
> [Radio](arkts-arkui-typenode-radio-t.md), [Slider](arkts-arkui-typenode-slider-t.md), [Toggle](arkts-arkui-typenode-toggle-t.md), and
> [TypedFrameNode](arkts-arkui-framenode-typedframenode-i.md) of the [XComponent](arkts-arkui-typenode-xcomponent-t.md) type.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [CrossLanguageOptions](arkts-arkui-framenode-crosslanguageoptions-i.md) | Yes | Cross-ArkTS language access options. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100022](../errorcode-node.md#100022-component-type-of-the-framenode-does-not-support-adjusting-the-cross-language-common-attribute-configuration-permission) | The FrameNode cannot be set whether to support cross-language common attribute setting. |

**Examples**

```TypeScript
See Example of Node Operations.
```

## setLayoutPosition

```TypeScript
setLayoutPosition(position: Position): void
```

Sets the position of this FrameNode after layout. The default unit is PX.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | [Position](arkts-arkui-position-t.md) | Yes | Position of the FrameNode after layout. |

**Examples**

```TypeScript
See Example of Customizing a Node.
```

## setMeasuredSize

```TypeScript
setMeasuredSize(size: Size): void
```

Sets the measured size of this FrameNode. The default unit is PX. If the configured width or height values are negative, they are automatically set to 0.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | Size | Yes | Measured size of the FrameNode. |

**Examples**

```TypeScript
See Example of Customizing a Node.
```

## setNeedsLayout

```TypeScript
setNeedsLayout(): void
```

Marks this FrameNode as needing layout, so that it will be relaid out in the next frame.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
See Example of Customizing a Node.
```

## commonAttribute

```TypeScript
get commonAttribute(): CommonAttribute
```

Obtains the **CommonAttribute** API associated with the FrameNode, which is used to configure universal attributes and universal events.

Note that only the attributes of a custom node can be modified.

> **NOTE:** 
> 
> The visual representation of the FrameNode is similar to that of a
> Stack container that is aligned to the top start edge.
> 
> For details about the supported attributes, see
> [attributeModifier Support for Attributes and Events](../../../ui/arkts-user-defined-extension-attributeModifier.md#attributemodifier-support-for-attributes-and-events).

**Type:** [CommonAttribute](../arkts-components/arkts-arkui-common-comp-attribute.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
See Basic Event Example.
```

## commonEvent

```TypeScript
get commonEvent(): UICommonEvent
```

Obtains the **UICommonEvent** object held in this FrameNode to set basic events. The set basic events will compete with declaratively defined events for event handling without overriding them. If both event callbacks are registered, the declaratively defined event callback takes precedence.

In scenarios involving **LazyForEach**, where nodes may be destroyed and reconstructed, you need to reset or re- attach event listeners to the newly created nodes to ensure they respond to events correctly.

**Type:** [UICommonEvent](../arkts-components/arkts-arkui-uicommonevent-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
See Basic Event Example and Example of Using Basic Events in the LazyForEach Scenario.
```

## gestureEvent

```TypeScript
get gestureEvent(): UIGestureEvent
```

Obtains the **UIGestureEvent** object held by this FrameNode, which is used to set gesture events bound to the component. Gesture events set using the **gestureEvent** API will not override gestures bound using the gesture binding API. If both APIs are used to set gestures, the gesture binding API takes precedence.

**Type:** [UIGestureEvent](../arkts-components/arkts-arkui-uigestureevent-i.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
For details, see Gesture Event Example.
```
