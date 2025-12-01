# Freezing a Custom Component
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

When a custom component decorated by @ComponentV2 is inactive, it can be frozen so that its state variables do not respond to updates. This means that the [@Monitor](./arkts-new-monitor.md) decorated callback will not be triggered, and any nodes associated with these state variables will not be re-rendered. This freezing mechanism offers significant performance benefits in complex UI scenarios. It prevents inactive components from performing unnecessary updates when their state variables change, thereby reducing resource consumption. You can use the **freezeWhenInactive** attribute to specify whether to enable the freezing feature. If no parameter is passed in, this feature is disabled. The freezing feature is supported in the following scenarios and components: [page navigation and routing](../../reference/apis-arkui/js-apis-router.md), [TabContent](../../reference/apis-arkui/arkui-ts/ts-container-tabcontent.md), [Navigation](../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md), and [Repeat](../../reference/apis-arkui/arkui-ts/ts-rendering-control-repeat.md).

To implement this feature, a solid understanding of the basic syntax for @ComponentV2 is required. Therefore, you are advised to read the [\@ComponentV2 documentation](./arkts-new-componentV2.md) before proceeding.

> **NOTE**
>
> Freezing of @ComponentV2 decorated custom components is supported since API version 12.
>
> Custom component freezing across mixed scenarios is supported since API version 18.
>
> Unlike @Component decorated components, @ComponentV2 decorated components do not support freezing cached items in the **LazyForEach** scenario.

## Use Scenarios

### Page Navigation and Routing

> **NOTE**
>
> While this example demonstrates page navigation and routing using **router** APIs, you are advised to use the **Navigation** component instead, which offers enhanced functionality and greater customization flexibility. For details, see the use cases of [Navigation](#navigation).

When page 1 navigates to page 2 using **router.pushUrl**, it enters the hidden state, where updating its state variables will not trigger UI re-rendering.
The figure below shows these pages.

![freezeInPage](./figures/freezeInPage.png)

Page 1 implementation:

```ts
@ObservedV2
export class Book {
  @Trace name: string = '100';

  constructor(page: string) {
    this.name = page;
  }
}

@Entry
@ComponentV2({ freezeWhenInactive: true })
export struct Page1 {
  @Local bookTest: Book = new Book(`A Midsummer Night's Dream`);

  @Monitor('bookTest.name')
  onMessageChange(monitor: IMonitor) {
    console.info(`The book name change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }

  build() {
    Column() {
      Text(`Book name is  ${this.bookTest.name}`).fontSize(25)
      Button('changeBookName').fontSize(25)
        .onClick(() => {
          this.bookTest.name = 'The Old Man and the Sea';
        })
      Button('go to next page').fontSize(25)
        .onClick(() => {
          this.getUIContext().getRouter().pushUrl({ url: 'pages/Page2' });
          setTimeout(() => {
            this.bookTest = new Book(`Jane Austen's Pride and Prejudice`);
          }, 1000)
        })
    }
  }
}
```

Page 2 implementation:

```ts
@Entry
@ComponentV2
struct Page2 {
  build() {
    Column() {
      Text('This is the page2').fontSize(25)
      Button('Back')
        .onClick(() => {
          this.getUIContext().getRouter().back();
        })
    }
  }
}
```

In the preceding example:

1. Click **changeBookName** on page 1. The **name** attribute of the **bookTest** variable changes, and the method **onMessageChange** registered in @Monitor is called.

2. Click **go to next page** on page 1 to go to page 2 and update the state variable **bookTest** after 1s. When **bookTest** is updated, page 2 is displayed, and page 1 is in the inactive state. The state variable **bookTest** decorated with [@Local](./arkts-new-local.md) does not respond to the update, the @Monitor callback is not called, and the associated node is not refreshed.

The trace information is shown below.

![Example Image](./figures/freeze1.png)

3. Click **Back**. Page 2 is destroyed, and the status of page 1 changes from inactive to active. The update of the state variable **bookTest** is observed, the method **onMessageChange** registered in @Monitor is called, and the corresponding text content changes.

![freezeV2Page](./figures/freezeV2page.gif)

### TabContent

The currently invisible TabContent in the Tabs is frozen. Modifying the state variable does not trigger the update of the frozen component.

Note: During the first rendering, Tabs creates only the TabContent that is being displayed. After all TabContents are switched, all TabContents are created.

The figure below shows this mechanism.
![freezeWithTab](./figures/freezewithTabs.png)

```ts
@Entry
@ComponentV2
struct TabContentTest {
  @Local message: number = 0;
  @Local data: number[] = [0, 1];

  build() {
    Row() {
      Column() {
        Button('change message').onClick(() => {
          this.message++;
        })

        Tabs() {
          ForEach(this.data, (item: number) => {
            TabContent() {
              FreezeChild({ message: this.message, index: item })
            }.tabBar(`tab${item}`)
          }, (item: number) => item.toString())
        }
      }
      .width('100%')
    }
    .height('100%')
  }
}

@ComponentV2({ freezeWhenInactive: true })
struct FreezeChild {
  @Param message: number = 0;
  @Param index: number = 0;

  @Monitor('message') onMessageUpdated(mon: IMonitor) {
    console.info(`FreezeChild message callback func ${this.message}, index: ${this.index}`);
  }

  build() {
    Text('message' + `${this.message}, index: ${this.index}`)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
  }
}
```

In the preceding example:

1. Click **change message** to change the value of **message**. The **onMessageUpdated** method registered by @Monitor in the currently displayed TabContent component is triggered.

2. Click **tab1** to switch to another TabContent. The status of the TabContent changes from inactive to active, and the **onMessageUpdated** method registered by @Monitor is triggered.

3. Click **change message** again to change the value of **message**. Only the **onMessageUpdated** method registered by @Monitor in the currently displayed TabContent child component is triggered. Other inactive **TabContent** components do not trigger @Monitor decorated callbacks.

![TabContent.gif](figures/TabContent.gif)


### Navigation

When NavDestination is invisible, its child custom components are set to inactive. Modifying the state variable does not trigger the refresh of the frozen component. When this **NavDestination** component is visible again, its child custom components are restored to the active state and the @Monitor decorated callback is triggered for UI re-rendering.

Note: "Active/Inactive" in this document refers to the frozen active/inactive state of the component, which is different from [onActive](../../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onactive17) and [onInactive](../../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#oninactive17) in the [NavDestination](../../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md) component.

```ts
@Entry
@ComponentV2
struct MyNavigationTestStack {
  @Provider('pageInfo') pageInfo: NavPathStack = new NavPathStack();
  @Local message: number = 0;

  @Monitor('message') info() {
    console.info(`freeze-test MyNavigation message callback ${this.message}`);
  }

  @Builder
  PageMap(name: string) {
    if (name === 'pageOne') {
      PageOneStack({ message: this.message })
    } else if (name === 'pageTwo') {
      PageTwoStack({ message: this.message })
    } else if (name === 'pageThree') {
      PageThreeStack({ message: this.message })
    }
  }

  build() {
    Column() {
      Button('change message')
        .onClick(() => {
          this.message++;
        })
      Navigation(this.pageInfo) {
        Column() {
          Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
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

@ComponentV2
struct PageOneStack {
  @Consumer('pageInfo') pageInfo: NavPathStack = new NavPathStack();
  @Local index: number = 1;
  @Param message: number = 0;

  build() {
    NavDestination() {
      Column() {
        NavigationContentMsgStack({ message: this.message, index: this.index })
        Text('cur stack size:' + `${this.pageInfo.size()}`)
          .fontSize(30)
        Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
          .onClick(() => {
            this.pageInfo.pushPathByName('pageTwo', null);
          })
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule })
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

@ComponentV2
struct PageTwoStack {
  @Consumer('pageInfo') pageInfo: NavPathStack = new NavPathStack();
  @Local index: number = 2;
  @Param message: number = 0;

  build() {
    NavDestination() {
      Column() {
        NavigationContentMsgStack({ message: this.message, index: this.index })
        Text('cur stack size:' + `${this.pageInfo.size()}`)
          .fontSize(30)
        Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
          .onClick(() => {
            this.pageInfo.pushPathByName('pageThree', null);
          })
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule })
          .onClick(() => {
            this.pageInfo.pop();
          })
      }
    }.title('pageTwo')
    .onBackPressed(() => {
      this.pageInfo.pop();
      return true;
    })
  }
}

@ComponentV2
struct PageThreeStack {
  @Consumer('pageInfo') pageInfo: NavPathStack = new NavPathStack();
  @Local index: number = 3;
  @Param message: number = 0;

  build() {
    NavDestination() {
      Column() {
        NavigationContentMsgStack({ message: this.message, index: this.index })
        Text('cur stack size:' + `${this.pageInfo.size()}`)
          .fontSize(30)
        Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
          .height(40)
          .onClick(() => {
            this.pageInfo.pushPathByName('pageOne', null);
          })
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule })
          .height(40)
          .onClick(() => {
            this.pageInfo.pop();
          })
      }
    }.title('pageThree')
    .onBackPressed(() => {
      this.pageInfo.pop();
      return true;
    })
  }
}

@ComponentV2({ freezeWhenInactive: true })
struct NavigationContentMsgStack {
  @Param message: number = 0;
  @Param index: number = 0;

  @Monitor('message') info() {
    console.info(`freeze-test NavigationContent message callback ${this.message}`);
    console.info(`freeze-test ---- called by content ${this.index}`);
  }

  build() {
    Column() {
      Text('msg:' + `${this.message}`)
        .fontSize(30)
    }
  }
}
```

In the preceding example:

1. Click **change message** to change the value of **message**. The **info** method registered by @Monitor in the **MyNavigationTestStack** component that is being displayed is triggered.

2. Click **Next Page** to switch to **PageOne** and create the **PageOneStack** node.

3. Click **change message** again to change the value of **message**. Only the **info** method registered by @Monitor in the **NavigationContentMsgStack** child component of **PageOneStack** is triggered.

4. Click **Next Page** again to switch to **PageTwo** and create the **PageTwoStack** node. The state of the **PageOneStack** node changes from active to inactive.

5. Click **Change Message** again to change the **message** value. Only the **info** method registered by @Monitor in the **NavigationContentMsgStack** child component of **PageTwoStack** is triggered. The @Monitor method is not triggered when the child custom component of the NavDestination that is not on the top of the navigation route stack is in the inactive state.

6. Click **Next Page** to switch to **PageThree** and create the **PageThreeStack** node. The state of the **PageTwoStack** node changes from active to inactive.

7. Click **Change Message** again to change the **message** value. Only the **info** method registered by @Monitor in the **NavigationContentMsgStack** child component of **PageThreeStack** is triggered. The @Monitor method is not triggered when the child custom component of the NavDestination that is not on the top of the navigation route stack is in the inactive state.

8. Click **Back Page** to return to **PageTwo**. In this case, the **PageTwoStack** node status changes from inactive to active, and the **info** method registered by @Monitor in the **NavigationContentMsgStack** child component is triggered.

9. Click **Back Page** again to return to **PageOne**. In this case, the **PageOneStack** node status changes from inactive to active, and the **info** method registered by @Monitor in the **NavigationContentMsgStack** child component is triggered.

10. Click **Back Page** again to return to the initial page. In this case, no triggering occurs.

![navigation-freeze.gif](figures/navigation-freeze.gif)

### Repeat

> **NOTE**
>
> Repeat supports custom component freezing since API version 18.

Freezing custom components in the cache pool of **Repeat** prevents unnecessary component re-renders. You are advised to read [Node Update and Reuse Mechanism](../rendering-control/arkts-new-rendering-control-repeat.md#node-update-and-reuse-mechanism) in advance.

```ts
@Entry
@ComponentV2
struct RepeatVirtualScrollFreeze {
  @Local simpleList: Array<string> = [];
  @Local bgColor: Color = Color.Pink;

  aboutToAppear(): void {
    for (let i = 0; i < 7; i++) {
      this.simpleList.push(`item${i}`);
    }
  }

  build() {
    Column() {
      Row() {
        Button('Reduce length to 5')
          .onClick(() => {
            this.simpleList = this.simpleList.slice(0, 5);
          })
        Button('Change bgColor')
          .onClick(() => {
            this.bgColor = this.bgColor == Color.Pink ? Color.Blue : Color.Pink;
          })
      }

      List() {
        Repeat(this.simpleList)
          .each((obj: RepeatItem<string>) => {
          })
          .key((item: string, index: number) => item)
          .virtualScroll({ totalCount: this.simpleList.length })
          .templateId(() => 'a')
          .template('a', (ri) => {
            ChildComponent({
              message: ri.item,
              bgColor: this.bgColor
            })
          }, { cachedCount: 2 })
      }
      .cachedCount(0)
      .height(500)
    }
    .height('100%')
  }
}

// Enable component freezing.
@ComponentV2({ freezeWhenInactive: true })
struct ChildComponent {
  @Param @Require message: string = '';
  @Param @Require bgColor: Color = Color.Pink;
  @Monitor('bgColor')
  onBgColorChange(monitor: IMonitor) {
    // When the value of bgColor changes, the components in the cache pool are not re-rendered, so no log is printed.
    console.info(`repeat---bgColor change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }

  build() {
    Text(`[a]: ${this.message}`)
      .fontSize(50)
      .backgroundColor(this.bgColor)
  }
}
```

In the preceding example:

After you click **Reduce length to 5**, the two removed components enter the Repeat cache pool. Then, click **Change bgColor** to change the value of **bgColor** to trigger node refresh.

With component freezing enabled (**freezeWhenInactive: true**), only the @Monitor decorated **onBgColorChange** callback in the remaining active nodes is triggered. In the example, the five active nodes are re-rendered, causing five logs to be printed.

![freeze_repeat_L2.gif](figures/freeze_repeat_L2.gif)

```ts
// Disable component freezing.
@ComponentV2({ freezeWhenInactive: false })
struct ChildComponent {
  @Param @Require message: string = '';
  @Param @Require bgColor: Color = Color.Pink;
  @Monitor('bgColor')
  onBgColorChange(monitor: IMonitor) {
    // When the value of bgColor changes, components in the cache pool are also re-rendered, printing logs.
    console.info(`repeat---bgColor change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }

  build() {
    Text(`[a]: ${this.message}`)
      .fontSize(50)
      .backgroundColor(this.bgColor)
  }
}
```

When component freezing is disabled (**freezeWhenInactive: false** - the default setting when **freezeWhenInactive** is not specified), the @Monitor decorated **onBgColorChange** callback is triggered for both the remaining active components and components in the cache pool. This means all seven components are re-rendered, printing seven logs.

![freeze_repeat_L2_unfreeze.gif](figures/freeze_repeat_L2_unfreeze.gif)

### Component Freezing for Child Components Only

You can selectively freeze specific child components by setting **freezeWhenInactive: true** only on those child components.

```ts
// Page1.ets
@ObservedV2
class Book {
  @Trace name: string = 'TS';

  constructor(name: string) {
    this.name = name;
  }
}

@Entry
@ComponentV2
struct Page1 {
  pageInfo: NavPathStack = new NavPathStack();

  build() {
    Column() {
      Navigation(this.pageInfo) {
        Child()

        Button('Go to next page').fontSize(30)
          .onClick(() => {
            this.pageInfo.pushPathByName('Page2', null);
          })
      }
    }
  }
}

@ComponentV2({ freezeWhenInactive: true })
export struct Child {
  @Local bookTest: Book = new Book(`A Midsummer Night's Dream`);

  @Monitor('bookTest.name')
  onMessageChange(monitor: IMonitor) {
    console.info(`The book name change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }

  textUpdate(): number {
    console.info('The text is update');
    return 25;
  }

  build() {
    Column() {
      Text(`The book name is ${this.bookTest.name}`).fontSize(this.textUpdate())

      Button('change BookName')
        .onClick(() => {
          setTimeout(() => {
            this.bookTest = new Book(`Jane Austen's Pride and Prejudice`);
          }, 3000);
        })
    }
  }
}
```

```ts
// Page2.ets
@Builder
function Page2Builder() {
  Page2()
}

@ComponentV2
struct Page2 {
  pathStack: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Column() {
        Text('This is the Page2')

        Button('Back').fontSize(30)
          .onClick(() => {
            this.pathStack.pop();
          })
      }
    }.onReady((context: NavDestinationContext) => {
      this.pathStack = context.pathStack;
    })
  }
}
```

When using **Navigation**, create a **route_map.json** file as shown below in the **src/main/resources/base/profile** directory, replacing the value of **pageSourceFile** with the actual path to **Page2**. Then, add **"routerMap": "$profile: route_map"** to the **module.json5** file.

```json
{
  "routerMap": [
    {
      "name": "Page2",
      "pageSourceFile": "src/main/ets/pages/Page2.ets",
      "buildFunction": "Page2Builder",
      "data": {
        "description" : "This is the Page2"
      }
    }
  ]
}
```

In the preceding example:
- The child component **Child** in **Page1** has **freezeWhenInactive: true** configured.
- Click **change BookName**, and then click **Go to next page** within 3 seconds. When **bookTest** is updated, **Page1** is already in the inactive state after navigation to **Page2**. Due to component freezing enabled for **Child**, the **@Local bookTest** state variable does not respond to updates. This means that the @Monitor decorated callback will not be triggered, and any components associated with the state variable will not be re-rendered.
- Click **Back** to return to the previous page. The callback method decorated by @Monitor is invoked, and the component associated with the state variable is refreshed.

### Component Freezing Across Mixed Scenarios

When components that support freezing are used together, the freezing behavior varies according to the API version. API version 17 or earlier:<br>Thawing a parent component automatically thaws all its child components.<br>API version 18 or later:<br>Thawing a parent component only thaws on-screen child components. For details, see [Mixed Component Usage](./arkts-custom-components-freeze.md#mixed-component-usage).

**Mixed Use of Navigation and TabContent**

```ts
@ComponentV2
struct ChildOfParamComponent {
  @Require @Param child_val: number;

  @Monitor('child_val') onChange(m: IMonitor) {
    console.info(`Appmonitor ChildOfParamComponent: changed ${m.dirty[0]}: ${m.value()?.before} -> ${m.value()?.now}`);
  }

  build() {
    Column() {
      Text(`Child Param: ${this.child_val}`);
    }
  }
}

@ComponentV2
struct ParamComponent {
  @Require @Param val: number;

  @Monitor('val') onChange(m: IMonitor) {
    console.info(`Appmonitor ParamComponent: changed ${m.dirty[0]}: ${m.value()?.before} -> ${m.value()?.now}`);
  }

  build() {
    Column() {
      Text(`val: ${this.val}`);
      ChildOfParamComponent({child_val: this.val});
    }
  }
}

@ComponentV2
struct DelayComponent {
  @Require @Param delayVal1: number;

  @Monitor('delayVal1') onChange(m: IMonitor) {
    console.info(`Appmonitor DelayComponent: changed ${m.dirty[0]}: ${m.value()?.before} -> ${m.value()?.now}`);
  }

  build() {
    Column() {
      Text(`Delay Param: ${this.delayVal1}`);
    }
  }
}

@ComponentV2 ({freezeWhenInactive: true})
struct TabsComponent {
  private controller: TabsController = new TabsController();
  @Local tabState: number = 47;

  @Monitor('tabState') onChange(m: IMonitor) {
    console.info(`Appmonitor TabsComponent: changed ${m.dirty[0]}: ${m.value()?.before} -> ${m.value()?.now}`);
  }

  build() {
    Column({space: 10}) {
      Button(`Incr state ${this.tabState}`)
        .fontSize(25)
        .onClick(() => {
          console.info('Button increment state value');
          this.tabState = this.tabState + 1;
        })

      Tabs({ barPosition: BarPosition.Start, index: 0, controller: this.controller}) {
        TabContent() {
          ParamComponent({val: this.tabState});
        }.tabBar('Update')
        TabContent() {
          DelayComponent({delayVal1: this.tabState});
        }.tabBar('DelayUpdate')
      }
      .vertical(false)
      .scrollable(true)
      .barMode(BarMode.Fixed)
      .barWidth(400).barHeight(150).animationDuration(400)
      .width('100%')
      .height(200)
      .backgroundColor(0xF5F5F5)
    }
  }
}

@Entry
@Component
struct MyNavigationTestStack {
  @Provide('pageInfo') pageInfo: NavPathStack = new NavPathStack();

  @Builder
  PageMap(name: string) {
    if (name === 'pageOne') {
      PageOneStack()
    } else if (name === 'pageTwo') {
      PageTwoStack()
    }
  }

  build() {
    Column() {
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
struct PageOneStack {
  @Consume('pageInfo') pageInfo: NavPathStack;

  build() {
    NavDestination() {
      Column() {
        TabsComponent();

        Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pushPathByName('pageTwo', null);
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
struct PageTwoStack {
  @Consume('pageInfo') pageInfo: NavPathStack;

  build() {
    NavDestination() {
      Column() {
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule })
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
```

For API version 17 or earlier:

Navigating to the next page using the **Next page** button and then returning to the previous page will thaw all **TabContent** components.

For API version 18 or later:

Navigating to the next page using the **Next page** button and then returning to the previous page will thaw only the **TabContent** component being displayed.

## Constraints

The **FreezeBuildNode** example below demonstrates the constraint for using a [BuilderNode](../../reference/apis-arkui/js-apis-arkui-builderNode.md) with component freezing. When a BuilderNode is used within a frozen component hierarchy, its imperative mounting mechanism conflicts with the functionality of component freezing, which relies on parent-child relationships. As a result, the child components of the BuilderNode remain active, regardless of their parent's frozen state.

```ts
import { BuilderNode, FrameNode, NodeController, UIContext } from '@kit.ArkUI';

// Define a Params class to pass parameters.
@ObservedV2
class Params {
  // Singleton pattern to ensure that there is only one Params instance.
  static singleton_: Params;

  // Method for obtaining the Params instance.
  static instance() {
    if (!Params.singleton_) {
      Params.singleton_ = new Params(0);
    }
    return Params.singleton_;
  }

  // Decorate the message attribute with the @Trace decorator so that its changes are observable.
  @Trace message: string = 'Hello';
  index: number = 0;

  constructor(index: number) {
    this.index = index;
  }
}

// Define a buildNodeChild component that contains a message attribute and an index attribute.
@ComponentV2
struct buildNodeChild {
  // Use the Params instance as the storage attribute.
  storage: Params = Params.instance();
  @Param index: number = 0;

  // Use the @Monitor decorator to listen for the changes of storage.message.
  @Monitor('storage.message')
  onMessageChange(monitor: IMonitor) {
    console.info(`FreezeBuildNode buildNodeChild message callback func ${this.storage.message}, index:${this.index}`);
  }

  build() {
    Text(`buildNode Child message: ${this.storage.message}`).fontSize(30)
  }
}

// Define a buildText function that receives a Params parameter and constructs a Column component.
@Builder
function buildText(params: Params) {
  Column() {
    buildNodeChild({ index: params.index })
  }
}

class TextNodeController extends NodeController {
  private textNode: BuilderNode<[Params]> | null = null;
  private index: number = 0;
  
  // The constructor receives an index parameter.
  constructor(index: number) {
    super();
    this.index = index;
  }

  // Create and return a FrameNode.
  makeNode(context: UIContext): FrameNode | null {
    this.textNode = new BuilderNode(context);
    this.textNode.build(wrapBuilder<[Params]>(buildText), new Params(this.index));
    return this.textNode.getFrameNode();
  }
}

// Define an Index component that contains a message attribute and a data array.
@Entry
@ComponentV2
struct Index {
  // Use the Params instance as the storage attribute.
  storage: Params = Params.instance();
  private data: number[] = [0, 1];

  build() {
    Row() {
      Column() {
        Button('change').fontSize(30)
          .onClick(() => {
            this.storage.message += 'a';
          })

        Tabs() {
          // Use Repeat to repeatedly render the TabContent component.
          Repeat<number>(this.data)
            .each((obj: RepeatItem<number>) => {
              TabContent() {
                FreezeBuildNode({ index: obj.item })
                  .margin({ top: 20 })
              }.tabBar(`tab${obj.item}`)
            })
            .key((item: number) => item.toString())
        }
      }
    }
    .width('100%')
    .height('100%')
  }
}

// Define a FreezeBuildNode component that contains a message attribute and an index attribute.
@ComponentV2({ freezeWhenInactive: true })
struct FreezeBuildNode {
  // Use the Params instance as the storage attribute.
  storage: Params = Params.instance();
  @Param index: number = 0;

  // Use the @Monitor decorator to listen for the changes of storage.message.
  @Monitor('storage.message')
  onMessageChange(monitor: IMonitor) {
    console.info(`FreezeBuildNode message callback func ${this.storage.message}, index: ${this.index}`);
  }

  build() {
    NodeContainer(new TextNodeController(this.index))
      .width('100%')
      .height('100%')
      .backgroundColor('#FFF0F0F0')
  }
}
```

After the **change** button is clicked, the value of **message** changes, resulting in both expected and unexpected behaviors:

- Expected: The [@Watch](./arkts-watch.md) decorated **onMessageUpdated** callback of the **TabContent** component that is being displayed is triggered.
- Unexpected: For **TabContent** components that are not being displayed, the @Watch decorated **onMessageUpdated** callbacks of child components under the BuilderNode are also triggered, indicating that these components are not frozen.

![builderNode.gif](figures/builderNode.gif)
