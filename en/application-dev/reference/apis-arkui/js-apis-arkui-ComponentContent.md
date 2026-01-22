# ComponentContent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyi0309-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

You can create an entity encapsulation component in either of the following ways: You can select either of the following methods during development:

**ComponentContent** represents an entity encapsulation of component content, which can be created and transmitted outside of UI components. It allows you to encapsulate and decouple dialog box components. Its underlying implementation uses BuilderNode. For details, see [BuilderNode](js-apis-arkui-builderNode.md).

**ReactiveComponentContent** represents an entity encapsulation of component content, which can be created and transmitted outside of UI components. It allows you to encapsulate and decouple dialog box components. Its underlying implementation uses **ReactiveBuilderNode**. For details, see [ReactiveBuilderNode](js-apis-arkui-builderNode.md#reactivebuildernode22).

> **NOTE**
> 
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 
> **ComponentContent** and **ReactiveComponentContent** are not available in DevEco Studio Previewer.


## Modules to Import

```ts
import { ComponentContent, ReactiveComponentContent } from '@kit.ArkUI';
```

## ComponentContent

Inherits from [Content](js-apis-arkui-Content.md#content-1).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(uiContext: UIContext, builder: WrappedBuilder\<[]>)

A constructor used to create a **ComponentContent** object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                                     | Mandatory| Description                              |
| --------- | ----------------------------------------- | ---- | ---------------------------------- |
| uiContext | [UIContext](./arkts-apis-uicontext-uicontext.md) | Yes  | UI context required for creating a node.|
| builder  | [WrappedBuilder\<[]>](../../ui/state-management/arkts-wrapBuilder.md) | Yes  |   **WrappedBuilder** object that encapsulates a builder function that has no parameters.|

### constructor

constructor(uiContext: UIContext, builder: WrappedBuilder\<[T]>, args: T)

A constructor used to create a **ComponentContent** object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                                     | Mandatory| Description                              |
| --------- | ----------------------------------------- | ---- | ---------------------------------- |
| uiContext | [UIContext](./arkts-apis-uicontext-uicontext.md) | Yes  | UI context required for creating a node.|
| builder  | [WrappedBuilder\<[T]>](../../ui/state-management/arkts-wrapBuilder.md) | Yes  |   **WrappedBuilder** object that encapsulates a builder function that has parameters.|
| args     |     T     |   Yes  |   Parameters of the builder function encapsulated in the **WrappedBuilder** object.|

### constructor

  constructor(uiContext: UIContext, builder: WrappedBuilder\<[T]>, args: T, options: BuildOptions)

A constructor used to create a **ComponentContent** object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                                     | Mandatory| Description                              |
| --------- | ----------------------------------------- | ---- | ---------------------------------- |
| uiContext | [UIContext](./arkts-apis-uicontext-uicontext.md) | Yes  | UI context required for creating a node.|
| builder  | [WrappedBuilder\<[T]>](../../ui/state-management/arkts-wrapBuilder.md) | Yes  |   **WrappedBuilder** object that encapsulates a builder function that has parameters.|
| args     |     T     |   Yes  |   Parameters of the builder function encapsulated in the **WrappedBuilder** object.|
| options | [BuildOptions](./js-apis-arkui-builderNode.md#buildoptions12)                                                    | Yes  |  Build options, which determine whether to support the behavior of nesting **@Builder** within **@Builder**.                                        |

**Example**
``` ts
import { ComponentContent, NodeContent, typeNode } from "@kit.ArkUI";

interface ParamsInterface {
  text: string;
  func: Function;
}

@Builder
function buildTextWithFunc(fun: Function) {
  Text(fun())
    .fontSize(50)
    .fontWeight(FontWeight.Bold)
    .margin({ bottom: 36 })
}

@Builder
function buildText(params: ParamsInterface) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
    buildTextWithFunc(params.func)
  }
}

@Entry
@Component
struct Index {
  @State message: string = "HELLO";
  private content: NodeContent = new NodeContent();

  build() {
    Row() {
      Column() {
        Button('addComponentContent')
          .onClick(() => {
            let column = typeNode.createNode(this.getUIContext(), "Column");
            column.initialize();
            column.addComponentContent(new ComponentContent<ParamsInterface>(this.getUIContext(),
              wrapBuilder<[ParamsInterface]>(buildText), {
                text: this.message, func: () => {
                  return "FUNCTION"
                }
              }, { nestingBuilderSupported: true }));
            this.content.addFrameNode(column);
          })
        ContentSlot(this.content)
      }
      .id("column")
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}

```

### update

update(args: T): void

Updates the builder function parameters encapsulated by the [WrappedBuilder](../../ui/state-management/arkts-wrapBuilder.md) object. The parameter type must be the same as that passed by constructor.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description                                                        |
| ------ | ---- | ---- | ------------------------------------------------------------ |
| args   | T    | Yes  | Updates the builder function parameters encapsulated by the [WrappedBuilder](../../ui/state-management/arkts-wrapBuilder.md) object. The parameter type must be the same as that passed by constructor.|

**Example**

```ts
import { ComponentContent } from "@kit.ArkUI";

class Params {
  text: string = "";
  constructor(text: string) {
    this.text = text;
  }
}

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
      .margin({bottom: 36})
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@Component
struct Index {
  @State message: string = "hello";

  build() {
    Row() {
      Column() {
        Button("click me")
            .onClick(() => {
                let uiContext = this.getUIContext();
                let promptAction = uiContext.getPromptAction();
                let contentNode = new ComponentContent(uiContext, wrapBuilder(buildText), new Params(this.message));
                promptAction.openCustomDialog(contentNode);

                setTimeout(() => {
                  contentNode.update(new Params("new message"));
                }, 2000);    // Automatically update the text in the dialog box after 2 seconds.
            })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

### reuse

reuse(param?: Object): void

Triggers component reuse for custom components under this **ComponentContent**. For details about component reuse, see [\@Reusable Decorator: Reusing Components](../../ui/state-management/arkts-reusable.md). For details about the scenarios involving **ComponentContent** unbinding, see [Canceling the Reference to the Entity Node](../../ui/arkts-user-defined-arktsNode-builderNode.md#canceling-the-reference-to-the-entity-node).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                                                    |
| ------ | ------ | ---- | ------------------------------------------------------------------------ |
| param  | Object | No  | Parameters for **ComponentContent** reuse. This parameter is passed to all top-level custom components within the **ComponentContent** during reuse and must include all required constructor parameters for each component; otherwise, undefined behavior may occur. Calling this method synchronously triggers the [aboutToReuse](../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoreuse10) lifecycle callback of internal custom components, with this parameter as the callback input. The default value is undefined. In this case, the custom component in ComponentContent directly uses the data source during construction.|

### recycle

recycle(): void

- Triggers recycling of custom components under this **ComponentContent**. Component recycling is part of the component reuse mechanism. For details, see [\@Reusable Decorator: Reusing Components](../../ui/state-management/arkts-reusable.md).
- **ComponentContent** completes the reuse event transfer between internal and external custom components through **reuse** and **recycle**. For specific usage scenarios, see [Implementing Node Reuse with the BuilderNode reuse and recycle APIs](../../ui/arkts-user-defined-arktsNode-builderNode.md#implementing-node-reuse-with-the-buildernode-reuse-and-recycle-apis).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

```ts
import { NodeContent, typeNode, ComponentContent } from "@kit.ArkUI";

const TEST_TAG: string = "Reuse+Recycle";

class MyDataSource {
  private dataArray: string[] = [];
  private listener: DataChangeListener | null = null;

  public totalCount(): number {
    return this.dataArray.length;
  }

  public getData(index: number) {
    return this.dataArray[index];
  }

  public pushData(data: string) {
    this.dataArray.push(data);
  }

  public reloadListener(): void {
    this.listener?.onDataReloaded();
  }

  public registerDataChangeListener(listener: DataChangeListener): void {
    this.listener = listener;
  }

  public unregisterDataChangeListener(): void {
    this.listener = null;
  }
}

class Params {
  item: string = '';

  constructor(item: string) {
    this.item = item;
  }
}

@Builder
function buildNode(param: Params = new Params("hello")) {
  Row() {
    Text(`C${param.item} -- `)
    ReusableChildComponent2({ item: param.item }) // This custom component cannot be correctly reused in the ComponentContent.
  }
}

// The custom component that is reused and recycled will have its state variables updated, and the state variables of the nested custom component ReusableChildComponent3 will also be updated. However, the ComponentContent will block this propagation process.
@Reusable
@Component
struct ReusableChildComponent {
  @Prop item: string = '';
  @Prop switch: string = '';
  private content: NodeContent = new NodeContent();
  private componentContent: ComponentContent<Params> = new ComponentContent<Params>(
    this.getUIContext(),
    wrapBuilder<[Params]>(buildNode),
    new Params(this.item),
    { nestingBuilderSupported: true });

  aboutToAppear() {
    let column = typeNode.createNode(this.getUIContext(), "Column");
    column.initialize();
    column.addComponentContent(this.componentContent);
    this.content.addFrameNode(column);
  }

  aboutToRecycle(): void {
    console.info(`${TEST_TAG} ReusableChildComponent aboutToRecycle ${this.item}`);

    // When the switch is open, pass the recycle event to the nested custom component, such as ReusableChildComponent2, through the ComponentContent's recycle API to complete recycling.
    if (this.switch === 'open') {
      this.componentContent.recycle();
    }
  }

  aboutToReuse(params: object): void {
    console.info(`${TEST_TAG} ReusableChildComponent aboutToReuse ${JSON.stringify(params)}`);

    // When the switch is open, pass the reuse event to the nested custom component, such as ReusableChildComponent2, through the ComponentContent's reuse API to complete reuse.
    if (this.switch === 'open') {
      this.componentContent.reuse(params);
    }
  }

  build() {
    Row() {
      Text(`A${this.item}--`)
      ReusableChildComponent3({ item: this.item })
      ContentSlot(this.content)
    }
  }
}

@Component
struct ReusableChildComponent2 {
  @Prop item: string = "false";

  aboutToReuse(params: Record<string, object>) {
    console.info(`${TEST_TAG} ReusableChildComponent2 aboutToReuse ${JSON.stringify(params)}`);
  }

  aboutToRecycle(): void {
    console.info(`${TEST_TAG} ReusableChildComponent2 aboutToRecycle ${this.item}`);
  }

  build() {
    Row() {
      Text(`D${this.item}`)
        .fontSize(20)
        .backgroundColor(Color.Yellow)
        .margin({ left: 10 })
    }.margin({ left: 10, right: 10 })
  }
}

@Component
struct ReusableChildComponent3 {
  @Prop item: string = "false";

  aboutToReuse(params: Record<string, object>) {
    console.info(`${TEST_TAG} ReusableChildComponent3 aboutToReuse ${JSON.stringify(params)}`);
  }

  aboutToRecycle(): void {
    console.info(`${TEST_TAG} ReusableChildComponent3 aboutToRecycle ${this.item}`);
  }

  build() {
    Row() {
      Text(`B${this.item}`)
        .fontSize(20)
        .backgroundColor(Color.Yellow)
        .margin({ left: 10 })
    }.margin({ left: 10, right: 10 })
  }
}


@Entry
@Component
struct Index {
  @State data: MyDataSource = new MyDataSource();

  aboutToAppear() {
    for (let i = 0; i < 100; i++) {
      this.data.pushData(i.toString());
    }
  }

  build() {
    Column() {
      List({ space: 3 }) {
        LazyForEach(this.data, (item: string) => {
          ListItem() {
            ReusableChildComponent({
              item: item,
              switch: 'open' // Changing open to close can be used to observe the behavior of custom components inside the ComponentContent when reuse and recycle events are not passed through the ComponentContent's reuse and recycle APIs.
            })
          }
        }, (item: string) => item)
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

### dispose

dispose(): void

Immediately releases the reference relationship between this **ComponentContent** object and its [entity node](../../ui/arkts-user-defined-node.md#basic-concepts). For details about the scenarios involving **ComponentContent** unbinding, see [Canceling the Reference to the Entity Node](../../ui/arkts-user-defined-arktsNode-builderNode.md#canceling-the-reference-to-the-entity-node).

> **NOTE**
>
> After calling **dispose()**, the **ComponentContent** object cancels its reference to the backend entity node. If the frontend object **ComponentContent** cannot be released, memory leaks may occur. To avoid this, be sure to call **dispose()** on the **ComponentContent** object when you no longer need it. This reduces the complexity of reference relationships and lowers the risk of memory leaks.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { ComponentContent } from '@kit.ArkUI';

class Params {
  text: string = "";
  constructor(text: string) {
    this.text = text;
  }
}

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@Component
struct Index {
  @State message: string = "hello";

  build() {
    Row() {
      Column() {
        Button("click me")
            .onClick(() => {
                let uiContext = this.getUIContext();
                let promptAction = uiContext.getPromptAction();
                let contentNode = new ComponentContent(uiContext, wrapBuilder(buildText), new Params(this.message));
                promptAction.openCustomDialog(contentNode);

                setTimeout(() => {
                  promptAction.closeCustomDialog(contentNode)
                    .then(() => {
                      console.info('customDialog closed.');
                      if (contentNode !== null) {
                        contentNode.dispose();   // Dispose of the contentNode object.
                      }
                    }).catch((error: BusinessError) => {
                      let message = (error as BusinessError).message;
                      let code = (error as BusinessError).code;
                      console.error(`closeCustomDialog args error code is ${code}, message is ${message}`);
                    })
                }, 2000);     // Automatically close the dialog box after 2 seconds.
            })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```


### updateConfiguration

updateConfiguration(): void

Updates the configuration of the entire node by passing in a [system environment change](../apis-ability-kit/js-apis-app-ability-configuration.md) event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

> **NOTE**
>
> The updateConfiguration API is used to notify an object of updating the current system environment change.

**Example**
```ts
import { NodeController, FrameNode, ComponentContent, UIContext, FrameCallback } from '@kit.ArkUI';
import { AbilityConstant, Configuration, EnvironmentCallback, ConfigurationConstant } from '@kit.AbilityKit';

@Builder
function buildText() {
  Column() {
    Text('Hello')
      .fontSize(36)
      .fontWeight(FontWeight.Bold)
  }
  .backgroundColor($r('sys.color.ohos_id_color_background'))
  .width('100%')
  .alignItems(HorizontalAlign.Center)
  .padding(16)
}

const componentContentMap: Array<ComponentContent<[Object]>> = new Array();

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    return this.rootNode;
  }

  createNode(context: UIContext) {
    this.rootNode = new FrameNode(context);
    let component = new ComponentContent<Object>(context, wrapBuilder(buildText));
    componentContentMap.push(component);
    this.rootNode.addComponentContent(component);
  }

  deleteNode() {
    let node = componentContentMap.pop();
    this.rootNode?.dispose();
    node?.dispose();
  }
}

class MyFrameCallback extends FrameCallback {
  onFrame() {
    updateColorMode();
  }
}

function updateColorMode() {
  componentContentMap.forEach((value, index) => {
    value.updateConfiguration();
  })
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  aboutToAppear(): void {
    let environmentCallback: EnvironmentCallback = {
      onMemoryLevel: (level: AbilityConstant.MemoryLevel): void => {
        console.info('onMemoryLevel');
      },
      onConfigurationUpdated: (config: Configuration): void => {
        console.info(`onConfigurationUpdated ${config}`);
        this.getUIContext()?.postFrameCallback(new MyFrameCallback());
      }
    }
    // Register a callback.
    this.getUIContext().getHostContext()?.getApplicationContext().on('environment', environmentCallback);
    // Set the application color mode to follow the system settings.
    this.getUIContext()
      .getHostContext()?.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_NOT_SET);
    this.myNodeController.createNode(this.getUIContext());
  }

  aboutToDisappear(): void {
    // Remove the reference to the custom node from the map and release the node.
    this.myNodeController.deleteNode();
  }

  build() {
    Column({ space: 16 }) {
      NodeContainer(this.myNodeController);
      Button('Switch to Dark Mode')
        .onClick(() => {
          this.getUIContext()
            .getHostContext()?.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_DARK);
        })
      Button('Switch to Light Mode')
        .onClick(() => {
          this.getUIContext()
            .getHostContext()?.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_LIGHT);
        })
    }
  }
}
```

### isDisposed<sup>20+</sup>

isDisposed(): boolean

Checks whether this **ComponentContent** object has released its reference to its backend entity node. All frontend nodes are bound to corresponding backend entity nodes. After **dispose()** is called, subsequent calls may cause crashes or return default values. This API facilitates validation of node validity prior to operations, thereby mitigating risks in scenarios where calls after disposal are required.


**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type   | Description              |
| ------- | ------------------ |
| boolean | Whether the reference to the backend node is released. The value **true** means that the reference to backend node is released, and **false** means the opposite.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { ComponentContent } from '@kit.ArkUI';

class Params {
  text: string = "";
  constructor(text: string) {
    this.text = text;
  }
}

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@Component
struct Index {
  @State message: string = "hello";
  @State beforeDispose: string = ''
  @State afterDispose: string = ''

  build() {
    Row() {
      Column() {
        Button("click me")
          .onClick(() => {
            let uiContext = this.getUIContext();
            let promptAction = uiContext.getPromptAction();
            let contentNode = new ComponentContent(uiContext, wrapBuilder(buildText), new Params(this.message));
            promptAction.openCustomDialog(contentNode);

            setTimeout(() => {
              promptAction.closeCustomDialog(contentNode)
                .then(() => {
                  console.info('customDialog closed.');
                  if (contentNode !== null) {
                    this.beforeDispose = contentNode.isDisposed() ? 'before dispose componentContent isDisposed is true' : 'before dispose componentContent isDisposed is false';
                    contentNode.dispose();   // Dispose of the contentNode object.
                    this.afterDispose = contentNode.isDisposed() ? 'after dispose componentContent isDisposed is true' : 'after dispose componentContent isDisposed is false';
                  }
                }).catch((error: BusinessError) => {
                let message = (error as BusinessError).message;
                let code = (error as BusinessError).code;
                console.error(`closeCustomDialog args error code is ${code}, message is ${message}`);
              })
            }, 1000); // Automatically close the dialog box 1 second later.
          })
        Text(this.beforeDispose)
          .fontSize(25)
          .margin({ top: 10, bottom: 10 })
        Text(this.afterDispose)
          .fontSize(25)
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

![](figures/component_content_isDisposed.gif)

### inheritFreezeOptions<sup>20+</sup>

inheritFreezeOptions(enabled: boolean): void

Sets whether this **ComponentContent** object inherits the freeze policy from its parent component's custom components. When inheritance is disabled (set to **false**), the **ComponentContent** object's freeze policy is set to **false**, which means its associated node remains unfrozen even in an inactive state.

> **NOTE**
>
> When **inheritFreezeOptions** is set to **true** for **ComponentContent** and the parent component is a custom component, BuilderNode, ComponentContent, ReactiveBuilderNode, or ReactiveComponentContent, the freeze policy of the parent component is inherited. If the child component is a custom component, its freeze policy is not transferred to the child component.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                                                    |
| ------ | ------ | ---- | ------------------------------------------------------------------------ |
| enabled  | boolean | Yes | Whether the current **ComponentContent** object inherits the freeze policy from its parent component's custom components. The value **true** means to inherit the freeze policy from the parent component's custom components, and **false** means the opposite.|

**Example**

```ts

import { ComponentContent, FrameNode, NodeController } from '@kit.ArkUI';

class Params {
  count: number = 0;

  constructor(count: number) {
    this.count = count;
  }
}

@Builder // Builder component
function buildText(params: Params) {

  Column() {
    TextBuilder({ message: params.count })
  }
}

class TextNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private contentNode: ComponentContent<Params> | null = null;
  private count: number = 0;

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    this.contentNode = new ComponentContent(context, wrapBuilder(buildText), new Params(this.count)); // Create ComponentContent using buildText.
    this.contentNode.inheritFreezeOptions(true); // Configure the ComponentContent object to inherit the freeze policy from its parent component.
    if (this.rootNode !== null) {
      this.rootNode.addComponentContent(this.contentNode); // Add ComponentContent to the tree.
    }
    return this.rootNode;
  }

  update(): void {
    if (this.contentNode !== null) {
      this.count += 1;
      this.contentNode.update(new Params(this.count)); // Update the ComponentContent data, which triggers logs.
    }
  }
}

const textNodeController: TextNodeController = new TextNodeController();

@Entry
@Component
struct MyNavigationTestStack {
  @Provide('pageInfo') pageInfo: NavPathStack = new NavPathStack();
  @State message: number = 0;
  @State logNumber: number = 0;

  @Builder
  PageMap(name: string) {
    if (name === 'pageOne') {
      pageOneStack({ message: this.message, logNumber: this.logNumber })
    } else if (name === 'pageTwo') {
      pageTwoStack({ message: this.message, logNumber: this.logNumber })
    }
  }

  build() {
    Column() {
      Button('update ComponentContent') // Clicking the button updates ComponentContent.
        .onClick(() => {
          textNodeController.update();
        })
      Navigation(this.pageInfo) {
        Column() {
          Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
            .width('80%')
            .height(40)
            .margin(20)
            .onClick(() => {
              this.pageInfo.pushPath({ name: 'pageOne' }); // Push the navigation destination page specified by name to the navigation stack.
            })
        }
      }.title('NavIndex')
      .navDestination(this.PageMap)
      .mode(NavigationMode.Stack)
    }
  }
}

@Component
struct pageOneStack { // Page 1
  @Consume('pageInfo') pageInfo: NavPathStack;
  @State index: number = 1;
  @Link message: number;
  @Link logNumber: number;

  build() {
    NavDestination() {
      Column() {
        NavigationContentMsgStack({ message: this.message, index: this.index, logNumber: this.logNumber })
        Button('Next Page', { stateEffect: true, type: ButtonType.Capsule }) // Navigate to page 2.
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pushPathByName('pageTwo', null);
          })
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule }) // Return to the home page.
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pop();
          })
      }.width('100%').height('100%')
    }.title('pageOne')
    .onBackPressed(() => {
      this.pageInfo.pop();
      return true;
    })
  }
}

@Component
struct pageTwoStack { // Page 2
  @Consume('pageInfo') pageInfo: NavPathStack;
  @State index: number = 2;
  @Link message: number;
  @Link logNumber: number;

  build() {
    NavDestination() {
      Column() {
        NavigationContentMsgStack({ message: this.message, index: this.index, logNumber: this.logNumber })
        Text('BuilderNode is frozen')
          .fontWeight(FontWeight.Bold)
          .margin({ top: 48, bottom: 48 })
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule }) // Return to page 1.
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pop();
          })
      }.width('100%').height('100%')
    }.title('pageTwo')
    .onBackPressed(() => {
      this.pageInfo.pop();
      return true;
    })
  }
}

@Component({ freezeWhenInactive: true }) // Set the freeze policy to freeze when inactive.
struct NavigationContentMsgStack {
  @Link message: number;
  @Link index: number;
  @Link logNumber: number;

  build() {
    Column() {
      if (this.index === 1) {
        NodeContainer(textNodeController)
      }
    }
  }
}

@Component({ freezeWhenInactive: true }) // Set the freeze policy to freeze when inactive.
struct TextBuilder {
  @Prop @Watch("info") message: number = 0;

  info() {
    console.info(`freeze-test TextBuilder message callback ${this.message}`); // Print logs based on the message content change to determine whether the freeze occurs.
  }

  build() {
    Row() {
      Column() {
        Text(`Update count: ${this.message}`)
          .fontWeight(FontWeight.Bold)
          .margin({ top: 48, bottom: 48 })
      }
    }
  }
}
```

![](figures/component_content_inheritFreezeOptions.gif)

## ReactiveComponentContent<sup>22+</sup>

ReactiveComponentContent is inherited from [Content](js-apis-arkui-Content.md#content-1) and is a container component used to dynamically bear and reuse UI content. It uses the @Builder function to build the UI and uses [ReactiveBuilderNode](./js-apis-arkui-builderNode.md#reactivebuildernode22) to generate and manage the component tree. The core value of this component is to provide complete lifecycle management for dynamic content so that it can be integrated into the ArkUI component reuse system. This component is especially suitable for scenarios that require high-performance rendering, such as long lists.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor<sup>22+</sup>

constructor(uiContext: UIContext, builder: WrappedBuilder&lt;T&gt;, config: BuildOptions, ...args: T)

Constructor of ReactiveComponentContent.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                                     | Mandatory| Description                              |
| --------- | ----------------------------------------- | ---- | ---------------------------------- |
| uiContext | [UIContext](./arkts-apis-uicontext-uicontext.md) | Yes  | UI context for node creation.|
| builder  | [WrappedBuilder\<T>](../../ui/state-management/arkts-wrapBuilder.md) | Yes  |   Encapsulates the WrappedBuilder object of the @Builder function with parameters.|
| config | [BuildOptions](./js-apis-arkui-builderNode.md#buildoptions12)  | Yes  |  Configures the build behavior of the builder. All attributes in BuildOptions are optional. The default value is the corresponding default value in BuildOptions.                                       |
| ...args     | T      | No  | Parameters of the builder function encapsulated in the **WrappedBuilder** object. Transfers external data to the WrappedBuilder&lt;T&gt and build functions specified in the constructor. Multiple input parameters are supported. The default value is **undefined**.|

**Example**

This example demonstrates how to use the ReactiveComponentContent constructor to dynamically create UI components that contain reactive content, implementing nested calls to the Builder function and flexible transfer of function parameters.

``` ts
import { ReactiveComponentContent, NodeContent, typeNode } from '@kit.ArkUI';

@Builder
function buildTextWithFunc(fun: Function) {
  Text(fun())
    .fontSize(20)
    .fontWeight(FontWeight.Bold)
    .margin({ bottom: 36 })
}

@Builder
function buildText(text: string, func: Function) {
  Column() {
    Text(text)
      .fontSize(20)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 12 })
    buildTextWithFunc(func)
  }
}

@Entry
@Component
struct Index {
  @State message: string = 'HELLO';
  private content: NodeContent = new NodeContent();

  build() {
    Row() {
      Column({ space: 12 }) {
        Button('addComponentContent')
          .onClick(() => {
            // Dynamically create a column node.
            let column = typeNode.createNode(this.getUIContext(), 'Column');
            column.initialize();
            // Create a ReactiveComponentContent and add it to the Column node.
            column.addComponentContent(new ReactiveComponentContent<[string, Function]>(this.getUIContext(),
              wrapBuilder<[string, Function]>(buildText), { nestingBuilderSupported: true },
              this.message,
              () => {
                return 'FUNCTION'
              }
            ));
            // Add the built node to the content container.
            this.content.addFrameNode(column);
          })
        ContentSlot(this.content) // Display the dynamically added content.
      }
      .id('column')
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

![](figures/ReactiveComponentContent_constructor.gif)

### reuse<sup>22+</sup>

reuse(param?: Object): void

Triggers component reuse for custom components under this **ReactiveComponentContent**. For details about component reuse, see [\@Reusable Decorator: Reusing Components](../../ui/state-management/arkts-reusable.md). For details about the scenarios involving **ReactiveComponentContent** unbinding, see [Canceling the Reference to the Entity Node](../../ui/arkts-user-defined-arktsNode-builderNode.md#canceling-the-reference-to-the-entity-node).

**ReactiveComponentContent** completes the reuse event transfer between internal and external custom components through **reuse** and [recycle](#recycle). For specific usage scenarios, see [Implementing Node Reuse with the BuilderNode reuse and recycle APIs](../../ui/arkts-user-defined-arktsNode-builderNode.md#implementing-node-reuse-with-the-buildernode-reuse-and-recycle-apis).

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                                                    |
| ------ | ------ | ---- | ------------------------------------------------------------------------ |
| param  | Object | No  | Parameter used to reuse [ReactiveComponentContent](./js-apis-arkui-builderNode.md#reactivebuildernode22). This parameter is directly used for reusing all top-level custom components in **ReactiveComponentContent**. It should contain the content required by the constructor parameters of each custom component. Otherwise, undefined behavior may occur. Calling this method synchronously triggers the [aboutToReuse](../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoreuse10) lifecycle callback of internal custom components, with this parameter as the callback input. The default value is undefined. In this case, the custom component in ReactiveComponentContent directly uses the data source during construction.|

**Example**

For details, see the example in [recycle](#recycle22).

### recycle<sup>22+</sup>

recycle(): void

Recycles the custom component in ReactiveComponentContent. Component recycling is part of the component reuse mechanism. For details, see [\@Reusable Decorator: Reusing Components](../../ui/state-management/arkts-reusable.md).

ReactiveBuilderNode completes the reuse event transfer between internal and external custom components through [reuse](#reuse22) and **recycle**. For specific usage scenarios, see [Implementing Node Reuse with the BuilderNode reuse and recycle APIs](../../ui/arkts-user-defined-arktsNode-builderNode.md#implementing-node-reuse-with-the-buildernode-reuse-and-recycle-apis).

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

A high-performance long list that contains multi-layer component reuse is implemented. ReactiveComponentContent dynamically manages Builder content and automatically reclaims and reuses components when the list scrolls.

```ts
import { NodeContent, typeNode, ReactiveComponentContent } from '@kit.ArkUI';

const TEST_TAG: string = 'Reuse+Recycle';

// Custom data source class, which is used to manage list data.
class MyDataSource {
  private dataArray: string[] = [];
  private listener: DataChangeListener | null = null;

  public totalCount(): number {
    return this.dataArray.length;
  }

  public getData(index: number) {
    return this.dataArray[index];
  }

  public pushData(data: string) {
    this.dataArray.push(data);
  }

  public reloadListener(): void {
    this.listener?.onDataReloaded();
  }

  public registerDataChangeListener(listener: DataChangeListener): void {
    this.listener = listener;
  }

  public unregisterDataChangeListener(): void {
    this.listener = null;
  }
}

@Builder
function buildNode(param: string) {
  Row() {
    Text(`C${param} -- `)
    ReusableChildComponent2({ item: param })
  }
}

@Reusable
@Component
struct ReusableChildComponent {
  @Prop item: string = '';
  @Prop switch: string = '';
  private content: NodeContent = new NodeContent();
  
  // Create a ReactiveComponentContent instance and encapsulate the builder dynamic content.
  private componentContent: ReactiveComponentContent<[string]> = new ReactiveComponentContent<[string]>(
    this.getUIContext(),
    wrapBuilder<[string]>(buildNode),
    { nestingBuilderSupported: true },
    this.item);

  aboutToAppear() {
    let column = typeNode.createNode(this.getUIContext(), 'Column');
    column.initialize();
    column.addComponentContent(this.componentContent);
    this.content.addFrameNode(column);
  }

  // Recycle the component lifecycle callback.
  aboutToRecycle(): void {
    console.info(`${TEST_TAG} ReusableChildComponent aboutToRecycle ${this.item}`);

    // When the switch is turned on, the recycling of the internal ReactiveComponentContent is triggered.
    if (this.switch === 'open') {
      this.componentContent.recycle();
    }
  }

  // Lifecycle callback during component reuse
  aboutToReuse(params: object): void {
    console.info(`${TEST_TAG} ReusableChildComponent aboutToReuse ${JSON.stringify(params)}`);

    // When the switch is turned on, the reuse of the internal ReactiveComponentContent is triggered.
    if (this.switch === 'open') {
      this.componentContent.reuse(params);
    }
  }

  build() {
    Row() {
      Text(`A${this.item}--`)
      ReusableChildComponent3({ item: this.item })
      ContentSlot(this.content)
    }
  }
}

@Component
struct ReusableChildComponent2 {
  @Prop item: string = 'false';

  aboutToReuse(params: Record<string, object>) {
    console.info(`${TEST_TAG} ReusableChildComponent2 aboutToReuse ${JSON.stringify(params)}`);
  }

  aboutToRecycle(): void {
    console.info(`${TEST_TAG} ReusableChildComponent2 aboutToRecycle ${this.item}`);
  }

  build() {
    Row() {
      Text(`D${this.item}`)
        .fontSize(20)
        .backgroundColor(Color.Yellow)
        .margin({ left: 10 })
    }.margin({ left: 10, right: 10 })
  }
}

@Component
struct ReusableChildComponent3 {
  @Prop item: string = 'false';

  aboutToReuse(params: Record<string, object>) {
    console.info(`${TEST_TAG} ReusableChildComponent3 aboutToReuse ${JSON.stringify(params)}`);
  }

  aboutToRecycle(): void {
    console.info(`${TEST_TAG} ReusableChildComponent3 aboutToRecycle ${this.item}`);
  }

  build() {
    Row() {
      Text(`B${this.item}`)
        .fontSize(20)
        .backgroundColor(Color.Yellow)
        .margin({ left: 10 })
    }.margin({ left: 10, right: 10 })
  }
}

@Entry
@Component
struct Index {
  @State data: MyDataSource = new MyDataSource();

  aboutToAppear() {
    // Initialize 100 test data records.
    for (let i = 0; i < 100; i++) {
      this.data.pushData(i.toString());
    }
  }

  build() {
    Column() {
      // Use LazyForEach to render a long list and enable component reuse.
      List({ space: 3 }) {
        LazyForEach(this.data, (item: string) => {
          ListItem() {
            ReusableChildComponent({
              item: item,
              switch: 'open'
            })
          }
        }, (item: string) => item)
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

![](figures/ReactiveComponentContent_recycle.gif)

### dispose<sup>22+</sup>

dispose(): void

> **NOTE**
>
> After calling **dispose**, the **ReactiveComponentContent** object cancels its reference to the backend entity node. If the frontend object **ReactiveComponentContent** cannot be released, memory leaks may occur. To avoid this, be sure to call **dispose** on the **ReactiveComponentContent** object when you no longer need it. This reduces the complexity of reference relationships and lowers the risk of memory leaks.

Immediately releases the reference relationship between this **ReactiveComponentContent** object and its [entity node](../../ui/arkts-user-defined-node.md#basic-concepts). For details about the scenarios involving **ReactiveComponentContent** unbinding, see [Canceling the Reference to the Entity Node](../../ui/arkts-user-defined-arktsNode-builderNode.md#canceling-the-reference-to-the-entity-node).

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

The following example shows how to use the **dispose** API to correctly release the **ReactiveComponentContent** object and manage the node lifecycle.

```ts
import {
  ReactiveComponentContent,
  Binding,
  MutableBinding,
  UIContext,
  UIUtils,
  NodeController,
  FrameNode
} from '@kit.ArkUI';

//dispose
@Builder
function buildText(
  MsgAge: MutableBinding<number>,
  message: MutableBinding<string>
) {
  Column() {
    Row() {
      Text(`age: ${MsgAge.value}, name: ${message.value}`)
    }
  }
  .justifyContent(FlexAlign.Center)
  .alignItems(HorizontalAlign.Center)
  .width('100%')
  .height('100%')
}

interface GeneratedObjectLiteralInterface_1 {
  MsgAge: number;
  message: string;
}

const params: GeneratedObjectLiteralInterface_1 = {
  MsgAge: 10,
  message: 'Mike',
};

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private contentNode: ReactiveComponentContent<[Binding<number>, Binding<string>]> | null = null;

  makeNode(context: UIContext): FrameNode | null {
    // Create a FrameNode as the root container.
    this.rootNode = new FrameNode(context);
    // Create ReactiveComponentContent.
    this.contentNode = new ReactiveComponentContent <[Binding<number>, Binding<string>]>(context,
      wrapBuilder<[Binding<number>, Binding<string>]>(buildText),
      {},
      UIUtils.makeBinding<number>(() => params.MsgAge, (val: number) => {
        params.MsgAge = val
        console.info("NodeTest1 get", params.MsgAge);
      }),
      UIUtils.makeBinding<string>(() => params.message, val => {
        console.info("NodeTest2 set before", params.message);
        params.message = val;
        console.info("NodeTest3 set after", params.message);
      }),
    );
    // Add the reactive content to the root node.
    if (this.rootNode !== null) {
      this.rootNode.addComponentContent(this.contentNode);
    }
    return this.rootNode;
  }

  // Method for releasing resources
  dispose() {
    if (this.contentNode !== null) {
      this.contentNode.dispose(); // Release ReactiveComponentContent resources.
    }
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Row() {
      Column() {
        // Display the custom node content.
        NodeContainer(this.myNodeController)
          .width('100%')
          .height(100)
          .backgroundColor('#FFF0F0F0')
        // Trigger resource release.
        Button('ReactiveComponentContent dispose')
          .onClick(() => {
            this.myNodeController.dispose(); // Calling dispose to Release Resources
          })
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

![](figures/ReactiveComponentContent_dispose.gif)

### updateConfiguration<sup>22+</sup>

updateConfiguration(): void

Updates the configuration of the entire node by passing in a [system environment change](../apis-ability-kit/js-apis-app-ability-configuration.md) event. This event can be used to notify the object of the update. Whether the system environment used by the object is updated depends on the current system environment change of the application.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

The following example shows how to use the updateConfiguration API to respond to system environment configuration changes and dynamically update the UI node constructed by ReactiveComponentContent.

```ts
import { NodeController, FrameNode, ReactiveComponentContent, UIContext, FrameCallback } from '@kit.ArkUI';
import { AbilityConstant, Configuration, EnvironmentCallback, ConfigurationConstant } from '@kit.AbilityKit';

@Builder
function buildText() {
  Column() {
    Text('Hello')
      .fontSize(20)
      .fontWeight(FontWeight.Bold)
  }
  .backgroundColor ($r ('sys.color.ohos_id_color_background')) // Use the system color resource, which automatically switches between the dark and light modes.
  .width('100%')
  .alignItems(HorizontalAlign.Center)
  .padding(16)
}

const componentContentMap: Array<ReactiveComponentContent<[]>> = new Array();

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    return this.rootNode;
  }

  createNode(context: UIContext) {
    this.rootNode = new FrameNode(context);
    let component = new ReactiveComponentContent<[]>(context, wrapBuilder(buildText), {});
    componentContentMap.push(component);
    this.rootNode.addComponentContent(component);
  }

  deleteNode() {
    let node = componentContentMap.pop();
    this.rootNode?.dispose();
    node?.dispose();
  }
}

class MyFrameCallback extends FrameCallback {
  onFrame() {
    updateColorMode();
  }
}

// Traverse all ReactiveComponentContent instances and call updateConfiguration to notify the system of environment changes.
function updateColorMode() {
  componentContentMap.forEach((value, index) => {
    // updateConfiguration(): transfers system environment change events and triggers full update of the node.
    // When the system dark/light mode, language, or font size changes, this API is called to notify ReactiveComponentContent of reapplying the latest system configuration.
    value.updateConfiguration();
  })
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  aboutToAppear(): void {
    let environmentCallback: EnvironmentCallback = {
      onMemoryLevel: (level: AbilityConstant.MemoryLevel): void => {
        console.info('onMemoryLevel');
      },
      onConfigurationUpdated: (config: Configuration): void => {
        console.info(`onConfigurationUpdated ${config}`);
        // When the system configuration is updated, updateConfiguration is triggered through frame callback.
        this.getUIContext()?.postFrameCallback(new MyFrameCallback());
      }
    }
    // Register the callback for listening to system environment changes.
    this.getUIContext().getHostContext()?.getApplicationContext().on('environment', environmentCallback);
    // Set the application color mode to follow the system settings.
    this.getUIContext()
      .getHostContext()?.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_NOT_SET);
    this.myNodeController.createNode(this.getUIContext());
  }

  aboutToDisappear(): void {
    // Remove the reference from componentContentMap and release the custom node.
    this.myNodeController.deleteNode();
  }

  build() {
    Column({ space: 16 }) {
      NodeContainer(this.myNodeController);
      Button('Switch to Dark Mode')
        .onClick(() => {
          this.getUIContext()
            .getHostContext()?.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_DARK);
        })
      Button('Switch to Light Mode')
        .onClick(() => {
          this.getUIContext()
            .getHostContext()?.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_LIGHT);
        })
    }
  }
}
```

![](figures/ReactiveComponentContent_updateConfiguration.gif)

### flushState<sup>22+</sup>

flushState(): void

Updates **ReactiveComponentContent**. If the bound parameters used in the **builder** function encapsulated by the [WrappedBuilder](../../ui/state-management/arkts-wrapBuilder.md) object in **ReactiveComponentContent** are class instances decorated by the V1 decorator (such as @Observed), you need to manually call this API to update data after the data of this class changes. If the bound parameters are class instances decorated by the V2 decorator (such as @ObservedV2), the data can be automatically updated without manual calling.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

This example demonstrates the usage of the **flushState** API in **ReactiveComponentContent**. By comparing the data update mechanisms of the V1 and V2 decorators, it illustrates the state update strategies under different reactive solutions.

```ts
import {
  ReactiveComponentContent, NodeContent, Binding, UIUtils, typeNode
} from '@kit.ArkUI';

// Builder function, which is used to build the text component for displaying the age.
@Builder
function buildText(age: Binding<number>) {
  Column() {
    Text(`age: ${age.value}`); // Display the age value.
  }
}

// Class decorated by the V2 decorator, which supports automatic state update.
@ObservedV2
class GeneratedObjectLiteralInterface_1 {
  constructor(age: number) {
    this.age = age;
  }
  @Trace age: number = 0; // Use the @Trace decorator to trace attribute changes.
}

// Use a common class (V1 decorator style). You need to manually trigger the update.
class GeneratedObjectLiteralInterface_2 {
  constructor(age: number) {
    this.age = age;
  }
  age: number = 0; // Common attribute, no automatic tracking.
}

@Entry
@ComponentV2
struct Index {
  private content: NodeContent = new NodeContent();
  // Data object of the V2 decorator, which can be automatically updated
  params: GeneratedObjectLiteralInterface_1 = new GeneratedObjectLiteralInterface_1(25);
  // Data object of the V1 decorator, which needs to be manually updated
  params2: GeneratedObjectLiteralInterface_2 = new GeneratedObjectLiteralInterface_2(25);

  private componentContent: ReactiveComponentContent<[Binding<number>]> | null = null

  build() {
    Row() {
      Scroll() {
        Column({ space: 12 }) {
          // Create ReactiveComponentContent using the V2 decorator.
          Button('Bound parameters are decorated by the V2 decorator').onClick(
            () => {
              let column = typeNode.createNode(this.getUIContext(), "Column");
              column.initialize();
              // Create ReactiveComponentContent and use the data binding of the V2 decorator.
              column.addComponentContent(new ReactiveComponentContent<[Binding<number>]>(this.getUIContext(),
                wrapBuilder<[Binding<number>]>(buildText),
                {},
                UIUtils.makeBinding<number>(() => {
                  return this.params.age; // Bind the data of the V2 decorator.
                })));

              this.content.addFrameNode(column);
            })
          
          // Create ReactiveComponentContent using the V1 decorator.
          Button('Bound parameters are decorated by the V1 decorator').onClick(
            () => {
              let column = typeNode.createNode(this.getUIContext(), "Column");
              column.initialize();
              // Create ReactiveComponentContent and use the data binding of the V1 decorator.
              this.componentContent =
                new ReactiveComponentContent<[Binding<number>]>(this.getUIContext(),
                  wrapBuilder<[Binding<number>]>(buildText),
                  {},
                  UIUtils.makeBinding<number>(() => {
                    return this.params2.age; // Bind the data of the V1 decorator.
                  })
                );
              column.addComponentContent(this.componentContent);
              this.content.addFrameNode(column);
            })
          
          // Update the data of the V2 decorator (automatically updated).
          Button('change age - V2 can be automatically updated').onClick(() => {
            this.params.age += 1; // The V2 decorator automatically detects changes and updates the UI.
          })
          
          // Update the data of the V1 decorator (manual update required).
          Button('change age - V1 must be manually updated').onClick(() => {
            this.params2.age += 1;
            // For the data of the V1 decorator, you need to manually call flushState to trigger UI update.
            this.componentContent?.flushState();
          })
          
          // Display the dynamically created content.
          ContentSlot(this.content)
        }
        .id("column")
        .width('100%')
      }
      .scrollable(ScrollDirection.Vertical)
      .scrollBar(BarState.On)
      .scrollBarColor(Color.Gray)
      .scrollBarWidth(10)
    }
    .height('100%')
  }
}
```

![](figures/ReactiveComponentContent_flushState.gif)

### inheritFreezeOptions<sup>22+</sup>

inheritFreezeOptions(enabled: boolean): void

Checks whether this **ReactiveComponentContent** object inherits the [freeze policy](./arkui-ts/ts-custom-component-parameter.md#componentoptions) from its parent component's custom components. When inheritance is disabled (set to **false**), the **ReactiveComponentContent** object's freeze policy is set to **false**, which means its associated node remains unfrozen even in an inactive state.

> **NOTE**
>
> When **inheritFreezeOptions** is set to **true** for a **ReactiveComponentContent** object, and its parent component is a custom component, **BuilderNode**, **ComponentContent**, **ReactiveBuilderNode**, or **ReactiveComponentContent**, it will inherit the parent component's freeze policy. If the child component is a custom component, its freeze policy is not transferred to the child component.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                                                    |
| ------ | ------ | ---- | ------------------------------------------------------------------------ |
| enabled  | boolean | Yes | Whether the **ReactiveComponentContent** object inherits the freeze policy from its parent component's custom components.<br>The value **true** means to inherit the freeze policy from the parent component's custom components, and **false** means the opposite.|

**Example**

In this example, the inheritance status of ReactiveComponentContent is set to true, the freezing policy of the parent custom component is inherited, the component is frozen when it is inactive, and the component is unfrozen when it is active. The cached data is updated.

```ts
import { ReactiveComponentContent, FrameNode, NodeController, Binding, UIUtils } from '@kit.ArkUI';

@Builder
// Builder component
function buildText(count: Binding<number>) {

  Column() {
    TextBuilder({ message: count.value })
  }
}

class TextNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private contentNode: ReactiveComponentContent<[Binding<number>]> | null = null;
  private count: number = 0;

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    this.contentNode = new ReactiveComponentContent(context, wrapBuilder<[Binding<number>]>(buildText), {},
      UIUtils.makeBinding<number>(() => {
        return this.count
      }));
    this.contentNode.inheritFreezeOptions(true);
    if (this.rootNode !== null) {
      this.rootNode.addComponentContent(this.contentNode);
    }
    return this.rootNode;
  }

  update(): void {
    if (this.contentNode !== null) {
      this.count += 1;
      this.contentNode.flushState();
    }
  }
}

const textNodeController: TextNodeController = new TextNodeController();

@Entry
@Component
struct MyNavigationTestStack {
  @Provide('pageInfo') pageInfo: NavPathStack = new NavPathStack();
  @State message: number = 0;
  @State logNumber: number = 0;

  @Builder
  PageMap(name: string) {
    if (name === 'pageOne') {
      pageOneStack({ message: this.message, logNumber: this.logNumber })
    } else if (name === 'pageTwo') {
      pageTwoStack({ message: this.message, logNumber: this.logNumber })
    }
  }

  build() {
    Column() {
      Button('update ComponentContent')
        .onClick(() => {
          textNodeController.update();
        })
      Navigation(this.pageInfo) {
        Column() {
          Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
            .width('80%')
            .height(40)
            .margin(20)
            .onClick(() => {
              this.pageInfo.pushPath({ name: 'pageOne' }); // Push the navigation destination page specified by name to the navigation stack.
            })
        }
      }.title('NavIndex')
      .navDestination(this.PageMap)
      .mode(NavigationMode.Stack)
    }
  }
}

@Component
struct pageOneStack { // Page 1
  @Consume('pageInfo') pageInfo: NavPathStack;
  @State index: number = 1;
  @Link message: number;
  @Link logNumber: number;

  build() {
    NavDestination() {
      Column() {
        NavigationContentMsgStack({ message: this.message, index: this.index, logNumber: this.logNumber })
        Button('Next Page', { stateEffect: true, type: ButtonType.Capsule }) // Navigate to page 2.
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pushPathByName('pageTwo', null);
          })
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule }) // Return to the home page.
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pop();
          })
      }.width('100%').height('100%')
    }.title('pageOne')
    .onBackPressed(() => {
      this.pageInfo.pop();
      return true;
    })
  }
}

@Component
struct pageTwoStack { // Page 2
  @Consume('pageInfo') pageInfo: NavPathStack;
  @State index: number = 2;
  @Link message: number;
  @Link logNumber: number;

  build() {
    NavDestination() {
      Column() {
        NavigationContentMsgStack({ message: this.message, index: this.index, logNumber: this.logNumber })
        Text('BuilderNode is frozen')
          .fontWeight(FontWeight.Bold)
          .margin({ top: 48, bottom: 48 })
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule }) // Return to page 1.
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pop();
          })
      }.width('100%').height('100%')
    }.title('pageTwo')
    .onBackPressed(() => {
      this.pageInfo.pop();
      return true;
    })
  }
}

@Component({ freezeWhenInactive: true })
  // Set the freeze policy to inactive freeze.
struct NavigationContentMsgStack {
  @Link message: number;
  @Link index: number;
  @Link logNumber: number;

  build() {
    Column() {
      if (this.index === 1) {
        NodeContainer(textNodeController)
      }
    }
  }
}

@Component({ freezeWhenInactive: true })
  // Set the freeze policy to inactive freeze.
struct TextBuilder {
  @Prop @Watch('info') message: number = 0;

  info() {
    console.info(`freeze-test TextBuilder message callback ${this.message}`); // Print logs based on the message content change to determine whether the freeze occurs.
  }

  build() {
    Row() {
      Column() {
        Text(`Update count: ${this.message}`)
          .fontWeight(FontWeight.Bold)
          .margin({ top: 48, bottom: 48 })
      }
    }
  }
}
```

![](figures/reactive_component_content_inheritFreezeOptions.gif)

### isDisposed<sup>22+</sup>

isDisposed(): boolean

Queries whether the current **ReactiveComponentContent** object has been unbound from the backend entity node. All frontend nodes are bound to corresponding backend entity nodes. After **dispose()** is called, subsequent calls may cause crashes or return default values. This API facilitates validation of node validity prior to operations, thereby mitigating risks in scenarios where calls after disposal are required.


**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type   | Description              |
| ------- | ------------------ |
| boolean | Whether the reference to the backend node is released.<br>The value **true** means that the reference to backend node is released, and **false** means the opposite.|

**Example**

This example demonstrates how to use the **isDisposed** API to check whether the **ReactiveComponentContent** object's reference to the backend node is released, providing a complete implementation solution for node status security detection.

```ts
import {
  ReactiveComponentContent,
  Binding,
  MutableBinding,
  UIContext,
  UIUtils,
  NodeController,
  FrameNode
} from '@kit.ArkUI';

@Builder
function buildText(
  MsgAge: MutableBinding<number>,
  message: MutableBinding<string>
) {
  Column() {
    Row() {
      Text(`age: ${MsgAge.value}, name: ${message.value}`)
        .fontSize(15)
    }
  }
  .justifyContent(FlexAlign.Center)
  .alignItems(HorizontalAlign.Center)
  .width('100%')
  .height('100%')
}

interface GeneratedObjectLiteralInterface_1 {
  MsgAge: number;
  message: string;
}

const params: GeneratedObjectLiteralInterface_1 = {
  MsgAge: 10,
  message: 'Mike',
};

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private contentNode: ReactiveComponentContent<[Binding<number>, Binding<string>]> | null = null;

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    this.contentNode = new ReactiveComponentContent <[Binding<number>, Binding<string>]>(context,
      wrapBuilder<[Binding<number>, Binding<string>]>(buildText),
      {},
      UIUtils.makeBinding<number>(() => params.MsgAge, (val: number) => {
        params.MsgAge = val
        console.info("NodeTest1 get", params.MsgAge);
      }),
      UIUtils.makeBinding<string>(() => params.message, val => {
        console.info("NodeTest2 set before", params.message);
        params.message = val;
        console.info("NodeTest3 set after", params.message);
      }),
    );
    if (this.rootNode !== null) {
      this.rootNode.addComponentContent(this.contentNode);
    }
    return this.rootNode;
  }

  dispose() {
    if (this.contentNode !== null) {
      this.contentNode.dispose();
    }
  }

  // Check whether the current node has been released.
  isDisposed(): string {
    if (this.contentNode !== null) {
      if (this.contentNode.isDisposed()) {
        return 'contentNode isDisposed is true';
      } else {
        return 'contentNode isDisposed is false';
      }
    }
    return 'contentNode is null';
  }
}

@Entry
@Component
struct Index {
  @State text: string = ''
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Row() {
      Column({ space: 12 }) {
        NodeContainer(this.myNodeController)
          .width('100%')
          .height(100)
          .backgroundColor('#FFF0F0F0')
        Button('dispose')
          .onClick(() => {
            this.myNodeController.dispose();
            this.text = '';
          })
          .fontSize(15)
          .width(200)
          .height(30)
        Button('isDisposed')
          .onClick(() => {
            this.text = this.myNodeController.isDisposed();
          })
          .width(200)
          .height(30)
          .fontSize(15)
        Text(this.text)
          .fontSize(15)
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

![](figures/ReactiveComponentContent_isDisposed.gif)
