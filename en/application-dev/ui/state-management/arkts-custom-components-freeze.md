# Freezing a Custom Component
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

Custom component freezing is designed to optimize the performance of complex UI pages, particularly in scenarios involving multiple page stacks, long lists, or grid layouts. When a state variable is bound to multiple UI components, its changes can easily trigger extensive component refreshes, causing UI freezing and response delays. To enhance refresh performance in such high-load UI scenarios, it is recommended to utilize the freezing capability of custom components.

The freezing capability is a performance optimization mechanism that suspends the refresh capability of inactive components. When frozen, components will not trigger UI re-rendering even if bound state variables change, thereby reducing refresh load in complex UI scenarios.

Before reading this topic, it is recommended to familiarize yourself with [Creating Custom Components](./arkts-create-custom-components.md) to understand the basic syntax.

> **NOTE**
>
> Custom component freezing is supported since API version 11.
>
> Custom component freezing across mixed scenarios is supported since API version 18.
> 
> Since API version 20, the [inheritFreezeOptions](../../reference/apis-arkui/js-apis-arkui-builderNode.md#inheritfreezeoptions20) API of [BuilderNode](../../reference/apis-arkui/js-apis-arkui-builderNode.md) can be set to true to implement the freezing capability of BuilderNode. For details, see [BuilderNode Inherits Component Freezing](../../reference/apis-arkui/js-apis-arkui-builderNode.md#inheritfreezeoptions20).


## Overview

The principles of component freezing are as follows:
1. Set the **freezeWhenInactive** attribute to activate the component freezing mechanism.
2. After enabling this function, the system re-renders only the active custom components. This allows the UI framework to narrow the re-render scope to the (active) custom components visible to users, improving re-render efficiency in complex UI scenarios.
3. When an inactive custom component becomes active, the state management framework performs necessary re-render operations to ensure correct UI display.

In summary, component freezing aims to optimize UI re-render performance on complex UIs. When multiple invisible custom components exist, such as in multiple page stacks, long lists, or grids, you can freeze these components to re-render only visible custom components as needed. The re-render of invisible custom components is delayed until they become visible.

Note that the active or inactive state of a component is not equivalent to its visibility. Component freezing applies only to the following scenarios:

1. [Page routing](../../reference/apis-arkui/js-apis-router.md): The top page in the stack is active, while pages not on top are inactive.
2. [TabContent](../../reference/apis-arkui/arkui-ts/ts-container-tabcontent.md): Only custom components in the currently displayed TabContent are active; others are inactive.
3. [LazyForEach](../../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md): Only custom components in the currently displayed LazyForEach are active; components of cached nodes are inactive.
4. [Navigation](../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md): Custom components in the currently displayed NavDestination are active; components of other non-displayed NavDestinations are inactive. Note: "active/inactive" in this document refers to the frozen active/inactive state of a component, which differs from [onActive](../../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onactive17) and [onInactive](../../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#oninactive17) in the [NavDestination](../../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md) component.
5. Component reuse: Components entering the reuse pool are inactive, while nodes attached from the reuse pool are active.
6. Mixed use: For example, when **LazyForEach** is used under **TabContent**, all nodes in **LazyForEach** of API version 17 or earlier are set to active when switching tabs. Since API version 18, only on-screen nodes of **LazyForEach** are set to active, while other nodes are set to inactive.

## Use Scenarios

### Page Navigation and Routing

> **NOTE**
>
> While this example demonstrates page navigation and routing using **router** APIs, it is recommended to use the **Navigation** component instead, which offers enhanced functionality and greater customization flexibility. For details, see the use cases of [Navigation](#navigation).

When page 1 navigates to page 2 using **router.pushUrl**, it enters the hidden state, where updating its state variables will not trigger UI re-rendering.
For details, see the following.

![freezeInPage](./figures/freezeInPage.png)

Page 1:

```ts
@Entry
@Component({ freezeWhenInactive: true })
struct Page1 {
  @StorageLink('PropA') @Watch('first') storageLink: number = 47;

  first() {
    console.info('first page ' + `${this.storageLink}`);
  }

  build() {
    Column() {
      Text(`From first Page ${this.storageLink}`).fontSize(50)
      Button('first page storageLink + 1').fontSize(30)
        .onClick(() => {
          this.storageLink += 1;
        })
      Button('go to next page').fontSize(30)
        .onClick(() => {
          this.getUIContext().getRouter().pushUrl({ url: 'pages/Page2' });
        })
    }
  }
}
```

Page 2:

```ts
@Entry
@Component({ freezeWhenInactive: true })
struct Page2 {
  @StorageLink('PropA') @Watch('second') storageLink2: number = 1;

  second() {
    console.info('second page: ' + `${this.storageLink2}`);
  }

  build() {
    Column() {

      Text(`second Page ${this.storageLink2}`).fontSize(50)
      Button('back')
        .onClick(() => {
          this.getUIContext().getRouter().back();
        })

      Button('second page storageLink2 + 2').fontSize(30)
        .onClick(() => {
          this.storageLink2 += 2;
        })

    }
  }
}
```

In the preceding example:

1. Click **first page storageLink + 1** on page 1. The **storageLink** state variable changes, and the method **first** registered by [@Watch](./arkts-watch.md) is called.

2. Click **go to next page** on page 1. Page 2 is displayed, page 1 is hidden, and its state changes from active to inactive.

3. Click **this.storageLink2 += 2** on page 2. Only the @Watch decorated **second** method of page 2 is called, because page 1 has been frozen when inactive.

4. Click **back** on page 2. Page 2 is destroyed, and page 1 changes from inactive to active. If the state variable of page 1 is updated at this point, the @Watch decorated **first** method of page 1 is called again.


### TabContent

Freezes the currently invisible TabContent in Tabs. Modifying state variables does not trigger updates of frozen components.

During initial rendering, only the displayed **TabContent** component is created. Remaining **TabContent** components are created only when their corresponding tabs are switched to.

For details, see the following.
![freezeWithTab](./figures/freezewithTabs.png)

```ts
@Entry
@Component
struct TabContentTest {
  @State @Watch('onMessageUpdated') message: number = 0;
  private data: number[] = [0, 1];

  onMessageUpdated() {
    console.info(`TabContent message callback func ${this.message}`);
  }

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

@Component({ freezeWhenInactive: true })
struct FreezeChild {
  @Link @Watch('onMessageUpdated') message: number;
  index: number = 0;

  onMessageUpdated() {
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

1. Click **change message**. The value of **message** changes, and the @Watch decorated **onMessageUpdated** method of the displayed **TabContent** component is called.

2. Click **tab1** to switch to another **TabContent** component. It switches from inactive to active, and the corresponding @Watch decorated **onMessageUpdated** method is called.

3. Click **change message** again. The value of **message** changes, and only the @Watch decorated **onMessageUpdated** method of the displayed **TabContent** component is called.

![TabContent.gif](figures/TabContent.gif)


### LazyForEach

You can freeze custom component instances cached in LazyForEach. Modifying state variables does not trigger updates of cached component instances.

```ts
// Basic implementation of IDataSource used to listen for data changes.
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

  // Called by the framework to unregister the listener from the LazyForEach data source.
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

  // Notify LazyForEach that the child component needs to be deleted from the data item with the specified index.
  notifyDataDelete(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataDelete(index);
    })
  }
}

class MyDataSource extends BasicDataSource {
  private dataArray: string[] = [];

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

@Entry
@Component
struct LazyforEachTest {
  private data: MyDataSource = new MyDataSource();
  @State @Watch('onMessageUpdated') message: number = 0;

  onMessageUpdated() {
    console.info(`LazyforEach message callback func ${this.message}`);
  }

  aboutToAppear() {
    for (let i = 0; i <= 20; i++) {
      this.data.pushData(`Hello ${i}`);
    }
  }

  build() {
    Column() {
      Button('change message').onClick(() => {
        this.message++;
      })
      List({ space: 3 }) {
        LazyForEach(this.data, (item: string) => {
          ListItem() {
            FreezeChild({ message: this.message, index: item })
          }
        }, (item: string) => item)
      }.cachedCount(5).height(500)
    }

  }
}

@Component({ freezeWhenInactive: true })
struct FreezeChild {
  @Link @Watch('onMessageUpdated') message: number;
  index: string = '';

  aboutToAppear() {
    console.info(`FreezeChild aboutToAppear index: ${this.index}`);
  }

  onMessageUpdated() {
    console.info(`FreezeChild message callback func ${this.message}, index: ${this.index}`);
  }

  build() {
    Text('message' + `${this.message}, index: ${this.index}`)
      .width('90%')
      .height(160)
      .backgroundColor(0xAFEEEE)
      .textAlign(TextAlign.Center)
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
  }
}
```

In the preceding example:

1. Click **change message**. The value of **message** changes, and the @Watch decorated **onMessageUpdated** method of displayed list items is called, while that of cached list items is not called. (If the component is not frozen, the @Watch decorated **onMessageUpdated** method of both displayed and cached list items is called.)

2. When a list item moves from outside the list content area into the list content area, it switches from inactive to active, and the corresponding @Watch decorated **onMessageUpdated** method is called.

3. Click **change message** again. The value of **message** changes, and only the @Watch decorated **onMessageUpdated** method of displayed list items is called.

![FrezzeLazyforEach.gif](figures/FrezzeLazyforEach.gif)

### Navigation

When a **NavDestination** component becomes invisible, its child custom components are set to inactive, where modifying state variables does not trigger re-rendering. When returning to this page, its child custom components are restored to active state and the @Watch callback is triggered to re-render the page.

In the following example, **NavigationContentMsgStack** is set to inactive state, which does not respond to state variable changes and does not trigger component re-rendering.

```ts
@Entry
@Component
struct MyNavigationTestStack {
  @Provide('pageInfo') pageInfo: NavPathStack = new NavPathStack();
  @State @Watch('info') message: number = 0;
  @State logNumber: number = 0;

  info() {
    console.info(`freeze-test MyNavigation message callback ${this.message}`);
  }

  @Builder
  PageMap(name: string) {
    if (name === 'pageOne') {
      PageOneStack({ message: this.message, logNumber: this.logNumber })
    } else if (name === 'pageTwo') {
      PageTwoStack({ message: this.message, logNumber: this.logNumber })
    } else if (name === 'pageThree') {
      PageThreeStack({ message: this.message, logNumber: this.logNumber })
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
  @State index: number = 1;
  @Link message: number;
  @Link logNumber: number;

  build() {
    NavDestination() {
      Column() {
        NavigationContentMsgStack({ message: this.message, index: this.index, logNumber: this.logNumber })
        Text('cur stack size:' + `${this.pageInfo.size()}`)
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
        Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pushPathByName('pageTwo', null);
          })
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule })
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
struct PageTwoStack {
  @Consume('pageInfo') pageInfo: NavPathStack;
  @State index: number = 2;
  @Link message: number;
  @Link logNumber: number;

  build() {
    NavDestination() {
      Column() {
        NavigationContentMsgStack({ message: this.message, index: this.index, logNumber: this.logNumber })
        Text('cur stack size:' + `${this.pageInfo.size()}`)
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
        Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pushPathByName('pageThree', null);
          })
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

@Component
struct PageThreeStack {
  @Consume('pageInfo') pageInfo: NavPathStack;
  @State index: number = 3;
  @Link message: number;
  @Link logNumber: number;

  build() {
    NavDestination() {
      Column() {
        NavigationContentMsgStack({ message: this.message, index: this.index, logNumber: this.logNumber })
        Text('cur stack size:' + `${this.pageInfo.size()}`)
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
        Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pushPathByName('pageOne', null);
          })
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pop();
          })
      }.width('100%').height('100%')
    }.title('pageThree')
    .onBackPressed(() => {
      this.pageInfo.pop();
      return true;
    })
  }
}

@Component({ freezeWhenInactive: true })
struct NavigationContentMsgStack {
  @Link @Watch('info') message: number;
  @Link index: number;
  @Link logNumber: number;

  info() {
    console.info(`freeze-test NavigationContent message callback ${this.message}`);
    console.info(`freeze-test ---- called by content ${this.index}`);
    this.logNumber++;
  }

  build() {
    Column() {
      Text('msg:' + `${this.message}`)
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
      Text('log number:' + `${this.logNumber}`)
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
    }
  }
}
```

In the preceding example:

1. Click **change message**. The value of **message** changes, and the @Watch decorated **info** method of the displayed **MyNavigationTestStack** component is called.

2. Click **Next Page**. The page switches to **PageOne** and the **PageOneStack** node is created.

3. Click **change message** again. The value of **message** changes, and only the @Watch decorated **info** method of the **NavigationContentMsgStack** child component in **PageOneStack** is called.

4. Click **Next Page**. The page switches to **PageTwo** and the **PageTwoStack** node is created.

5. Click **change message** again. The value of **message** changes, triggering only the @Watch decorated **info** method of the **NavigationContentMsgStack** child component in **PageTwoStack**.

6. Click **Next Page**. The page switches to **PageThree** and the **PageThreeStack** node is created.

7. Click **change message** again. The value of **message** changes, triggering only the @Watch decorated **info** method of the **NavigationContentMsgStack** child component in **PageThreeStack**.

8. Click **Back Page**. **PageTwo** is displayed, and only the @Watch decorated **info** method of the **NavigationContentMsgStack** child component in **PageTwoStack** is called.

9. Click **Back Page** again. **PageOne** is displayed, and only the @Watch decorated **info** method of the **NavigationContentMsgStack** child component in **PageOneStack** is called.

10. Click **Back Page** again. The initial page is displayed, and no method is called.

![navigation-freeze.gif](figures/navigation-freeze.gif)

### Component Reuse

[Component reuse](./arkts-reusable.md) utilizes existing nodes from the cache pool instead of creating new nodes to optimize UI performance and improve application smoothness. Although nodes in the reuse pool are not displayed in the UI component tree, state variable changes still trigger UI re-rendering. To prevent abnormal re-rendering of components in the reuse pool, component freezing can be applied.

**Mixed Use of Component Reuse, if, and Component Freezing**

The following example shows that when the state variable bound to the **if** component changes to **false**, the detach of **ChildComponent** is triggered. Because **ChildComponent** is marked for component reuse, it is not destroyed but enters the reuse pool. If component freezing is enabled simultaneously, the component will not be re-rendered in the reuse pool.

```ts
@Reusable
@Component({ freezeWhenInactive: true })
struct ChildComponent {
  @Link @Watch('descChange') desc: string;
  @State count: number = 0;

  descChange() {
    console.info(`ChildComponent messageChange ${this.desc}`);
  }

  aboutToReuse(params: Record<string, ESObject>): void {
    this.count = params.count as number;
  }

  aboutToRecycle(): void {
    console.info(`ChildComponent has been recycled`);
  }

  build() {
    Column() {
      Text(`ChildComponent desc: ${this.desc}`)
        .fontSize(20)
      Text(`ChildComponent count ${this.count}`)
        .fontSize(20)
    }.border({ width: 2, color: Color.Pink })
  }
}

@Entry
@Component
struct Page {
  @State desc: string = 'Hello World';
  @State flag: boolean = true;
  @State count: number = 0;

  build() {
    Column() {
      Button(`change desc`).onClick(() => {
        this.desc += '!';
      })
      Button(`change flag`).onClick(() => {
        this.count++;
        this.flag = !this.flag;
      })
      if (this.flag) {
        ChildComponent({ desc: this.desc, count: this.count })
      }
    }
    .height('100%')
  }
}
```

In the preceding example:

1. Click **change flag** and change the value of **flag** to **false**.
    - When **ChildComponent** marked with \@Reusable is detached, it is not destroyed. Instead, it enters the reuse pool, triggers the **aboutToRecycle** lifecycle, and sets the component state to inactive.
    - **ChildComponent** also enables component freezing. When **ChildComponent** is inactive, it does not respond to any UI re-rendering caused by state variable changes.
2. Click **change desc** to trigger changes to the member variable **desc** of **Page**.
    - Changes to \@State decorated **desc** will be notified to [\@Link](./arkts-link.md) decorated **desc** of **ChildComponent**.
    - However, **ChildComponent** is inactive and component freezing is enabled. Therefore, changes do not trigger the @Watch('descChange') callback or re-render the ChildComponent UI. If component freezing is not enabled, the current @Watch('descChange') callback is returned immediately, and **ChildComponent** in the reuse pool is re-rendered accordingly.
3. Click **change flag** again and change the value of **flag** to **true**.
    - **ChildComponent** is attached to the component tree from the reuse pool.
    - The **aboutToReuse** lifecycle callback returns and synchronizes the latest **count** value to **ChildComponent**. The value of **desc** is synchronized from [@State](./arkts-state.md) to @Link, so manual assignment in **aboutToReuse** is unnecessary.
    - Set **ChildComponent** to active state and re-render components that were not re-rendered when **ChildComponent** was inactive, such as **Text (ChildComponent desc: ${this.desc})**.

**Mixed Use of LazyForEach, Component Reuse, and Component Freezing**

In scrolling scenarios with long lists containing large amounts of data, **LazyForEach** can be used to create components on demand. Additionally, component reuse can reduce overhead caused by component creation and destruction during scrolling. However, if [reuseId](../../reference/apis-arkui/arkui-ts/ts-universal-attributes-reuse-id.md#reuseid) is set based on reuse type or a large value is set for cacheCount to ensure scrolling performance, the reuse pool or LazyForEach may cache numerous nodes. In such cases, triggering re-renders of all subnodes in **List** results in excessive re-render counts. Component freezing can address this issue.

```ts
import { hiTraceMeter } from '@kit.PerformanceAnalysisKit';
// Basic implementation of IDataSource used to listen for data changes.
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

  // Called by the framework to unregister the listener from the LazyForEach data source.
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

  // Notify LazyForEach that the child component needs to be deleted from the data item with the specified index.
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
}

class MyDataSource extends BasicDataSource {
  private dataArray: string[] = [];

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

@Reusable
@Component({freezeWhenInactive: true})
struct ChildComponent {
  @Link @Watch('descChange') desc: string;
  @State item: string = '';
  @State index: number = 0;
  descChange() {
    console.info(`ChildComponent messageChange ${this.desc}`);
  }

  aboutToReuse(params: Record<string, ESObject>): void {
    this.item = params.item;
    this.index = params.index;
  }

  aboutToRecycle(): void {
    console.info(`ChildComponent has been recycled`);
  }
  build() {
    Column() {
      Text(`ChildComponent index: ${this.index} item: ${this.item}`)
        .fontSize(20)
      Text(`desc: ${this.desc}`)
        .fontSize(20)
    }.border({width: 2, color: Color.Pink})
  }
}

@Entry
@Component
struct Page {
  @State desc: string = 'Hello World';
  private data: MyDataSource = new MyDataSource();

  aboutToAppear() {
    for (let i = 0; i < 50; i++) {
      this.data.pushData(`Hello ${i}`);
    }
  }

  build() {
    Column() {
      Button(`change desc`).onClick(() => {
        hiTraceMeter.startTrace('change desc', 1);
        this.desc += '!';
        hiTraceMeter.finishTrace('change desc', 1);
      })
      List({ space: 3 }) {
        LazyForEach(this.data, (item: string, index: number) => {
          ListItem() {
            ChildComponent({index: index, item: item, desc: this.desc}).reuseId(index % 10 < 5 ? '1': '0')
          }
        }, (item: string) => item)
      }.cachedCount(5)
    }
    .height('100%')
  }
}
```

In the preceding example:

1. Swipe the list to position index 14. There are 15 **ChildComponent** instances in the current page's visible area.
2. During swiping:
    - **ChildComponent** instances in the upper part of the list are swiped out of the visible area. In this case, **ChildComponent** enters the LazyForEach cache area and is set to inactive. After components slide out of the **LazyForEach** cache area, they are not destroyed but enter the reuse pool because they are marked for reuse. In this case, components are set to inactive again.
    - Cache nodes of **LazyForEach** at the bottom of the list enter the list. In this case, the system attempts to create nodes to enter the **LazyForEach** cache. If reusable nodes are found, the system retrieves existing nodes from the reuse pool and triggers the **aboutToReuse** lifecycle callback. In this case, nodes enter the **LazyForEach** cache area and their state remains inactive.
3. Click **change desc** to trigger changes to the member variable **desc** of **Page**.
    - Changes to \@State decorated **desc** will be notified to \@Link decorated **desc** of **ChildComponent**.
    - **ChildComponent** instances in the invisible area are inactive, and component freezing is enabled. Therefore, this change triggers the @Watch('descChange') callback of the 15 nodes in the visible area and re-renders these nodes. Nodes cached in **LazyForEach** and the reuse pool are not re-rendered, and the \@Watch callback is not triggered.
    

For details, see the following.
![freeze](./figures/freezeResuable.png)
You can observe changes via \@Trace; only 15 **ChildComponent** nodes are re-rendered.
![freeze](./figures/traceWithFreeze.png)

**Mixed Use of LazyForEach, if, Component Reuse, and Component Freezing**

The following scenario demonstrates mixed use of **LazyForEach**, **if**, component reuse, and component freezing. Under the same parent custom component, reusable nodes may enter the reuse pool in different ways. For example:
- Detaching from the LazyForEach cache area by swiping.
- Notifying subnodes to detach by switching the if condition.

```ts
import { hiTraceMeter } from '@kit.PerformanceAnalysisKit';
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

  // Called by the framework to unregister the listener from the LazyForEach data source.
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

  // Notify LazyForEach that the child component needs to be deleted from the data item with the specified index.
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
}

class MyDataSource extends BasicDataSource {
  private dataArray: string[] = [];

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

@Reusable
@Component({freezeWhenInactive: true})
struct ChildComponent {
  @Link @Watch('descChange') desc: string;
  @State item: string = '';
  @State index: number = 0;
  descChange() {
    console.info(`ChildComponent messageChange ${this.desc}`);
  }

  aboutToReuse(params: Record<string, ESObject>): void {
    this.item = params.item;
    this.index = params.index;
  }

  aboutToRecycle(): void {
    console.info(`ChildComponent has been recycled`);
  }
  build() {
    Column() {
      Text(`ChildComponent index: ${this.index} item: ${this.item}`)
        .fontSize(20)
      Text(`desc: ${this.desc}`)
        .fontSize(20)
    }.border({width: 2, color: Color.Pink})
  }
}

@Entry
@Component
struct Page {
  @State desc: string = 'Hello World';
  @State flag: boolean = true;
  private data: MyDataSource = new MyDataSource();

  aboutToAppear() {
    for (let i = 0; i < 50; i++) {
      this.data.pushData(`Hello ${i}`);
    }
  }

  build() {
    Column() {
      Button(`change desc`).onClick(() => {
        hiTraceMeter.startTrace('change desc', 1);
        this.desc += '!';
        hiTraceMeter.finishTrace('change desc', 1);
      })

      Button(`change flag`).onClick(() => {
        hiTraceMeter.startTrace('change flag', 1);
        this.flag = !this.flag;
        hiTraceMeter.finishTrace('change flag', 1);
      })

      List({ space: 3 }) {
        LazyForEach(this.data, (item: string, index: number) => {
          ListItem() {
            ChildComponent({index: index, item: item, desc: this.desc}).reuseId(index % 10 < 5 ? '1': '0')
          }
        }, (item: string) => item)
      }
      .cachedCount(5)
      .height('60%')

      if (this.flag) {
        ChildComponent({index: -1, item: 'Hello', desc: this.desc}).reuseId( '1')
      }
    }
    .height('100%')
  }
}
```

In the preceding example:

1. Swipe the list to position index 14. There are 10 **ChildComponent** instances on the page, among which nine are subnodes of **LazyForEach** and one is a subnode of **if**.
2. Click **change flag**. The **if** condition changes to **false**, and its subnode **ChildComponent** enters the reuse pool. Nine nodes are displayed on the page.
3. In this case, nodes detached through **LazyForEach** or **if** all enter the reuse pool under the **Page** node.
4. Click **change desc** to update only the nine **ChildComponent** nodes on the page. For details, see figures below.
5. Click **change flag** again. The **if** condition changes to **true**, and **ChildComponent** is attached from the reuse pool to the component tree again. The state of **ChildComponent** changes to active.
6. Click **change desc** again. Nodes attached through **if** and **LazyForEach** from the reuse pool can be re-rendered.

Trace for component freezing enabled

![traceWithFreezeLazyForeachAndIf](./figures/traceWithFreezeLazyForeachAndIf.png)

Trace for component freezing disabled

![traceWithFreezeLazyForeachAndIf](./figures/traceWithLazyForeachAndIf.png)

### Mixed Component Usage

When components that support freezing are used together, freezing behavior varies according to the API version. Set the component freezing flag for the parent component. In API version 17 or earlier, when the parent component is unfrozen, all nodes of its child components are unfrozen. Since API version 18, when the parent component is unfrozen, only on-screen nodes of child components are unfrozen.

**Mixed Use of Navigation and TabContent**

Sample code:

```ts
// index.ets
@Component
struct ChildOfParamComponent {
  @Prop @Watch('onChange') child_val: number;

  onChange() {
    console.info(`Appmonitor ChildOfParamComponent: child_val changed:${this.child_val}`);
  }

  build() {
    Column() {
      Text(`Child Param: ${this.child_val}`);
    }
  }
}

@Component
struct ParamComponent {
  @Prop @Watch('onChange') paramVal: number;

  onChange() {
    console.info(`Appmonitor ParamComponent: paramVal changed:${this.paramVal}`);
  }

  build() {
    Column() {
      Text(`val: ${this.paramVal}`)
      ChildOfParamComponent({ child_val: this.paramVal });
    }
  }
}



@Component
struct DelayComponent {
  @Prop @Watch('onChange') delayVal: number;

  onChange() {
    console.info(`Appmonitor ParamComponent: delayVal changed:${this.delayVal}`);
  }

  build() {
    Column() {
      Text(`Delay Param: ${this.delayVal}`);
    }
  }
}

@Component({ freezeWhenInactive: true })
struct TabsComponent {
  private controller: TabsController = new TabsController();
  @State @Watch('onChange') tabState: number = 47;

  onChange() {
    console.info(`Appmonitor TabsComponent: tabState changed:${this.tabState}`);
  }

  build() {
    Column({ space: 10 }) {
      Button(`Incr state ${this.tabState}`)
        .fontSize(25)
        .onClick(() => {
          console.info('Button increment state value');
          this.tabState = this.tabState + 1;
        })

      Tabs({ barPosition: BarPosition.Start, index: 0, controller: this.controller }) {
        TabContent() {
          ParamComponent({ paramVal: this.tabState });
        }.tabBar('Update')

        TabContent() {
          DelayComponent({ delayVal: this.tabState });
        }.tabBar('DelayUpdate')
      }
      .vertical(false)
      .scrollable(true)
      .barMode(BarMode.Fixed)
      .barWidth(400)
      .barHeight(150)
      .animationDuration(400)
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

Final effect

![freeze](figures/freeze_tabcontent.gif)

Click **Next Page** to enter the **pageOne** page. There are two tabs on the page and the **Update** tab is displayed by default. Enable component freezing. If the **Tabcontent** tab is not selected, the state variable is not refreshed.

Click **Incr state** and search for **Appmonitor** in the log. Three records are displayed.

![freeze](figures/freeze_tabcontent_update.png)

Switch to the **DelayUpdate** tab and click **Incr state**. Search for **Appmonitor** in the log. Two records are displayed. The state variable in the **DelayUpdate** tab does not refresh the state variable related to the **Update** tab.

![freeze](figures/freeze_tabcontent_delayupdate.png)

For API version 17 or earlier:

Click **Next page** to enter the next page and then return. The tab defaults to **DelayUpdate**. Click **Incr state** and search for **Appmonitor** in the log. Four records are displayed. When the page route returns, all tabs of **Tabcontent** are unfrozen.

![freeze](figures/freeze_tabcontent_back_api15.png)

For API version 18 or later:

Click **Next page** to enter the next page and then return. The tab defaults to **DelayUpdate**. Click **Incr state** and search for **Appmonitor** in the log. Two records are displayed. When the page route returns, only nodes with corresponding tabs are unfrozen.

![freeze](figures/freeze_tabcontent_back_api16.png)

**Page and LazyForEach**

When **Navigation** and **TabContent** are used together, child nodes of **TabContent** are unlocked because child components are recursively unfrozen from the parent component when the previous page is displayed. Additionally, the page lifecycle **OnPageShow** exhibits similar behavior. **OnPageShow** sets the root node of the current page to active state. As a subnode of the page, **TabContent** is also set to active state. When the screen turns off or on, page lifecycles **OnPageHide** and **OnPageShow** are triggered respectively. Therefore, when **LazyForEach** is used on the page, manual screen-off and screen-on can also achieve the page routing effect. Sample code:

```ts
import { hiTraceMeter } from '@kit.PerformanceAnalysisKit';
// Basic implementation of IDataSource used to listen for data changes.
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

  // Called by the framework to unregister the listener from the LazyForEach data source.
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

  // Notify LazyForEach that the child component needs to be deleted from the data item with the specified index.
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
}

class MyDataSource extends BasicDataSource {
  private dataArray: string[] = [];

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

@Reusable
@Component({freezeWhenInactive: true})
struct ChildComponent {
  @State desc: string = '';
  @Link @Watch('sumChange') sum: number;

  sumChange() {
    console.info(`sum: Change ${this.sum}`);
  }

  aboutToReuse(params: Record<string, Object>): void {
    this.desc = params.desc as string;
    this.sum = params.sum as number;
  }

  aboutToRecycle(): void {
    console.info(`ChildComponent has been recycled`);
  }
  build() {
    Column() {
      Divider()
        .color('#ff11acb8')
      Text(`Child component: ${this.desc}`)
        .fontSize(30)
        .fontWeight(30)
      Text(`${this.sum}`)
        .fontSize(30)
        .fontWeight(30)
    }
  }
}

@Entry
@Component ({freezeWhenInactive: true})
struct Page {
  private data: MyDataSource = new MyDataSource();
  @State sum: number = 0;
  @State desc: string = '';

  aboutToAppear() {
    for (let index = 0; index < 20; index++) {
      this.data.pushData(index.toString());
    }
  }

  build() {
    Column() {
      Button(`add sum`).onClick(() => {
        this.sum++;
      })
        .fontSize(30)
        .margin(20)
      List() {
        LazyForEach(this.data, (item: string) => {
          ListItem() {
            ChildComponent({desc: item, sum: this.sum});
          }
          .width('100%')
          .height(100)
        }, (item: string) => item)
      }.cachedCount(5)
    }
    .height('100%')
    .width('100%')
  }
}
```

As described in the mixed use scenario, **LazyForEach** nodes include on-screen nodes and **cachedCount** nodes.

![freeze](figures/freeze_lazyforeach.png)

Swipe down **LazyForEach** to add nodes to **cachedCount**. Click the **add sum** button and search for the log "sum: Change." Eight records are displayed.

![freeze](figures/freeze_lazyforeach_add.png)

For API version 17 or earlier:

When the screen turns on after being turned off, OnPageShow is triggered. Click add sum. The number of printed logs equals the sum of on-screen nodes and cachedCount nodes.

![freeze](figures/freeze_lazyforeach_api15.png)

Since API version 18:

When the screen turns on after being turned off, OnPageShow is triggered. Click add sum. Only the number of on-screen nodes is printed, and nodes in cachedCount remain frozen.

![freeze](figures/freeze_lazyforeach_api16.png)

## Constraints

### BuilderNode Cannot Inherit Parent Component Freezing

In versions earlier than API version 20, BuilderNode cannot inherit parent component freezing. The **FreezeBuildNode** example below demonstrates the constraint for using a [BuilderNode](../../reference/apis-arkui/js-apis-arkui-builderNode.md) with component freezing. When a BuilderNode is used within a frozen component hierarchy, its imperative mounting mechanism conflicts with component freezing functionality, which relies on parent-child relationships. As a result, child components of the BuilderNode remain active, regardless of their parent's frozen state.

In API version 20 and later, you can set inheritFreezeOptions of BuilderNode to true to enable BuilderNode to inherit freezing capability. For details, see [BuilderNode Inherits Component Freezing](../../reference/apis-arkui/js-apis-arkui-builderNode.md#inheritfreezeoptions20).

```ts
import { BuilderNode, FrameNode, NodeController, UIContext } from '@kit.ArkUI';

// Define a Params class to pass parameters.
class Params {
  index: number = 0;

  constructor(index: number) {
    this.index = index;
  }
}

// Define a BuildNodeChild component that contains a message attribute and an index attribute.
@Component
struct BuildNodeChild {
  @StorageProp('buildNodeTest') @Watch('onMessageUpdated') message: string = 'hello world';
  @State index: number = 0;

  // Call this method when message is updated.
  onMessageUpdated() {
    console.info(`FreezeBuildNode builderNodeChild message callback func ${this.message},index: ${this.index}`);
  }

  build() {
    Text(`buildNode Child message: ${this.message}`).fontSize(30)
  }
}

// Define a buildText function that receives a Params parameter and constructs a Column component.
@Builder
function buildText(params: Params) {
  Column() {
    BuildNodeChild({ index: params.index })
  }
}

// Define a TextNodeController class that inherits from NodeController.
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

// Define an index component that contains a message attribute and a data array.
@Entry
@Component
struct Index {
  @StorageLink('buildNodeTest') message: string = 'hello';
  private data: number[] = [0, 1];

  build() {
    Row() {
      Column() {
        Button('change').fontSize(30)
          .onClick(() => {
            this.message += 'a';
          })

        Tabs() {
          ForEach(this.data, (item: number) => {
            TabContent() {
              FreezeBuildNode({ index: item })
            }.tabBar(`tab${item}`)
          }, (item: number) => item.toString())
        }
      }
    }
    .width('100%')
    .height('100%')
  }
}

// Define a FreezeBuildNode component that contains a message attribute and an index attribute.
@Component({ freezeWhenInactive: true })
struct FreezeBuildNode {
  @StorageProp('buildNodeTest') @Watch('onMessageUpdated') message: string = '1111';
  @State index: number = 0;

  // Call this method when message is updated.
  onMessageUpdated() {
    console.info(`FreezeBuildNode message callback func ${this.message}, index: ${this.index}`);
  }

  build() {
    NodeContainer(new TextNodeController(this.index))
      .width('100%')
      .height('100%')
      .backgroundColor('#FFF0F0F0')
  }
}
```

In the preceding example:

Click **change** to change the value of message. The @Watch registered method in the displayed TabContent component is triggered. Unexpectedly: For **TabContent** components that are not displayed, the @Watch decorated **onMessageUpdated** callbacks of child components under the BuilderNode are also triggered, indicating these components are not frozen.

![builderNode.gif](figures/builderNode.gif)
