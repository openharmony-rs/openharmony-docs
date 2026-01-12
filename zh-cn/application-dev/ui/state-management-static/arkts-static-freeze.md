# V1自定义组件冻结场景

当@Component装饰的自定义组件处于冻结状态时，状态变量将不响应更新，即@Watch不会调用，状态变量关联的节点不会刷新。

V1自定义组件冻结支持场景为：

1. [页面路由](../../reference/apis-arkui/js-apis-router.md)：当前栈顶页面为active状态，非栈顶不可见页面为inactive状态。
2. [TabContent](../../reference/apis-arkui/arkui-ts/ts-container-tabcontent.md)：只有当前显示的TabContent中的自定义组件处于active状态，其余则为inactive。
3. [LazyForEach](../../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md)：仅当前显示的LazyForEach中的自定义组件为active状态，而缓存节点的组件则为inactive状态。
4. [Navigation](../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md)：当前显示的NavDestination中的自定义组件为active状态，而其他未显示的NavDestination组件则为inactive状态。 
5. 组件复用：进入复用池的组件为inactive状态，从复用池上树的节点为active状态。
6. 混用场景：对于以上场景的组合使用，例如TabContent下面使用LazyForEach，切换Tab时，只有LazyForEach的屏上节点会被设置为active状态，其余则为inactive状态。

> **说明：**
>
> - 在ArkTS-Sta上下文中，从API version 23开始，支持状态管理V1自定义组件冻结。
>
> - 在ArkTS-Sta上下文中，自定义组件默认打开组件冻结机制。

## 页面路由

> **说明：**
>
> 本示例使用了router进行页面跳转，建议开发者使用组件导航(Navigation)代替页面路由(router)来实现页面切换。Navigation提供了更多的功能和更灵活的自定义能力。请参考[使用Navigation的组件冻结用例](#navigation)。

当页面1调用router.pushUrl接口跳转到页面2时，页面1为隐藏不可见状态，此时如果更新页面1中的状态变量，不会触发页面1刷新。
图示如下：

![freezeInPage](../state-management/figures/freezeInPage.png)

页面1：

```ts
'use static'

import { Entry, Component, Column, Text, Button } from '@kit.ArkUI';
import { Watch, StorageLink } from '@kit.ArkUI';

@Entry
@Component
struct Page1 {
  @StorageLink('PropA') @Watch('first') storageLink: number = 47;

  first(propertyName: string) {
    console.info('first page ' + `${this.storageLink}`);
  }

  getValue(): number{
    console.info('first page getValue');
    return this.storageLink;
  }

  build() {
    Column() {
      Text(`From first Page ${this.getValue()}`).fontSize(50)
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

页面2：

```ts
'use static'

import { Entry, Component, Column, Text, Button } from '@kit.ArkUI';
import { Watch, StorageLink } from '@kit.ArkUI';

@Entry
@Component
struct Page2 {
  @StorageLink('PropA') @Watch('second') storageLink2: number = 1;

  second(propertyName: string) {
    console.info('second page: ' + `${this.storageLink2}`);
  }

  getValue(): number{
    console.info('second page getValue');
    return this.storageLink2;
  }

  build() {
    Column() {

      Text(`second Page ${this.getValue()}`).fontSize(50)
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

在上面的示例中：

1.在页面1中点击`first page storageLink + 1`，storageLink状态变量改变，[@Watch](../state-management/arkts-watch.md)注册的方法first会被调用。

2.在页面1中点击`go to next page`，跳转到页面2，页面1隐藏，状态由active变为inactive。

3.在页面2中点击`this.storageLink2 += 2`，只会回调页面2中@Watch注册的方法second，因为页面1的状态变量此时已被冻结。

4.在页面2中点击`back`，页面2被销毁，页面1的状态由inactive变为active，重新刷新在inactive时被冻结的状态变量，页面1中@Watch注册的方法first被再次调用。


## TabContent

对Tabs中当前不可见的TabContent进行冻结，修改状态变量不会触发冻结组件的更新。

需要注意的是：在首次渲染的时候，Tabs只会创建当前正在显示的TabContent，当切换全部的TabContent后，TabContent才会被全部创建。

图示如下：
![freezeWithTab](../state-management/figures/freezewithTabs.png)

```ts
'use static'

import { Entry, Component, ForEach, Column, Text, Button, Row, Tabs, TabContent, TabsController, FontWeight } from '@kit.ArkUI';
import { State, Link, Watch } from '@kit.ArkUI';

@Entry
@Component
struct TabContentTest {
  @State @Watch('onMessageUpdated') message: number = 0;
  private data: number[] = [0.0, 1.0, 2.0, 3.0, 4.0];

  onMessageUpdated(propertyName: string) {
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
@Component
struct FreezeChild {
  @Link @Watch('onMessageUpdated') message: number;
  index: number = 0;

  getValue(): number {
    console.info(`FreezeChild getValue, ${this.index}`)
    return this.message;
  }

  onMessageUpdated(propertyName: string) {
    console.info(`FreezeChild message callback func ${this.message}, index: ${this.index}`);
  }

  build() {
    Text('message' + `${this.getValue()}, index: ${this.index}`)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
  }
}
```

在上面的示例中：

1.点击`change message`更改message的值，当前正在显示的TabContent组件中的@Watch注册的方法onMessageUpdated被触发。

2.点击`tab1`切换到另外的TabContent，该TabContent的状态由inactive变为active，对应的@Watch注册的方法onMessageUpdated被触发。 

3.再次点击`change message`更改message的值，仅当前显示的TabContent子组件中的@Watch注册的方法onMessageUpdated被触发。

## LazyForEach

对LazyForEach中缓存的自定义组件进行冻结，修改状态变量不会触发缓存组件的更新。

```ts
'use static'

import { Entry, Component, ForEach, TextAlign, Column, List, ListItem, Text, Button, FontWeight, Row, Color, LazyForEach, IDataSource, DataChangeListener } from '@kit.ArkUI';
import { State, Link, Watch } from '@kit.ArkUI';

class BasicDataSource<string> implements IDataSource<string> {
  private listeners: Array<DataChangeListener> = Array<DataChangeListener>();
  private originDataArray: Array<string> = new Array<string>();

  public totalCount(): int {
    return this.originDataArray.length;
  }

  public getData(index: int): string {
    return this.originDataArray[index as int];
  }

  notifyDataAdd(index: int): void {
    this.listeners.forEach(listener => {
      listener.onDataAdd(index);
    });
  }

  notifyDataChange(index: int): void {
    this.listeners.forEach(listener => {
      listener.onDataChange(index);
    });
  }

  onDataReloaded(): void {
    this.listeners.forEach((listener: DataChangeListener) => {
      listener.onDataReloaded();
    });
  }

  registerDataChangeListener(listener: DataChangeListener) {
    if (this.listeners.indexOf(listener) < 0) {
      this.listeners.push(listener);
    }
  }

  unregisterDataChangeListener(listener: DataChangeListener) {
    const pos = this.listeners.indexOf(listener)
    if (pos >= 0) {
      this.listeners.splice(pos, 1);
    }
  }
}

class TestDataSource extends BasicDataSource<string> {
  private dataArray: string[] = [];

  public totalCount(): int {
    return this.dataArray.length;
  }

  public getData(index: int): string {
    return this.dataArray[index as int];
  }

  public pushData(data: string): void {
    this.dataArray.push(data);
  }

  public changeData(index: int, data: string): void {
    this.dataArray[index as int] = data;
    this.notifyDataChange(index);
  }
}

@Entry
@Component
struct LazyForEachSample {
  @State data: TestDataSource = new TestDataSource();
  @State @Watch('onMessageUpdated') message: number = 0;

  onMessageUpdated(propertyName: string) {
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

      List() {
        LazyForEach<string>(this.data, (item: string, index: int): void => {
          ListItem() {
            FreezeChild({ message: this.message, index: item })
          }
        }, (item: string, index: int): string => item)
      }
      .height('100%').width('90%')
      .borderWidth(2).clip(true)
    }
  }
}
@Component
struct FreezeChild {
  @Link @Watch('onMessageUpdated') message: number;
  index: string = '';

  aboutToAppear() {
    console.info(`FreezeChild aboutToAppear index: ${this.index}`);
  }

  getValue(): number {
    console.info(`FreezeChild getValue index:${this.index} message:${this.message}`)
    return this.message;
  }

  onMessageUpdated(propertyName: string) {
    console.info(`FreezeChild message callback func ${this.message}, index: ${this.index}`);
  }

  build() {
    Text('message' + `${this.getValue()}, index: ${this.index}`)
      .width('90%')
      .height(160)
      .backgroundColor(0xAFEEEE)
      .textAlign(TextAlign.Center)
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
  }
}
```

在上面的示例中：

1.点击`change message`更改message的值，当前正在显示的ListItem中的子组件@Watch注册的方法onMessageUpdated被触发。缓存节点中@Watch注册的方法不会被触发。

2.List区域外的ListItem滑动到List区域内，状态由inactive变为active，对应的@Watch注册的方法onMessageUpdated被触发。

3.再次点击`change message`更改message的值，仅有当前显示的ListItem中的子组件@Watch注册的方法onMessageUpdated被触发。

## Navigation

当NavDestination不可见时，会将其子自定义组件设置成非激活态，修改状态变量不会触发冻结组件的刷新。当返回该页面时，其子自定义组件重新恢复成激活态，触发@Watch回调进行刷新。

在下面例子中，NavigationContentMsgStack会被设置成非激活态，将不再响应状态变量的变化，也不会触发组件刷新。

```ts
'use static'

import { Entry, Component, Margin, NavPathStack, NavPathInfo, ClickEvent, NavDestination, Builder, Column, Navigation, Text, NavigationMode, Button, FontWeight, ButtonType } from '@kit.ArkUI';
import { State, Link, Watch, StorageLink } from '@kit.ArkUI';

@Entry
@Component
struct MyNavigationTestStack {
  @StorageLink('pageInfo') pageInfo: NavPathStack = new NavPathStack();
  @State @Watch('info') message: number = 0;
  @State logNumber: number = 0;

  info(propertyName: string) {
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
        .onClick((e: ClickEvent) => {
          this.message++;
        })
      Navigation(this.pageInfo) {
        Column() {
          Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
            .width('80%')
            .height(40)
            .margin(20)
            .onClick((e: ClickEvent) => {
              let info: NavPathInfo = new NavPathInfo("pageOne", undefined)
              this.pageInfo.pushPath(info); //将name指定的NavDestination页面信息入栈
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
  @StorageLink('pageInfo') pageInfo: NavPathStack = new NavPathStack();
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
          .onClick((e: ClickEvent) => {
            let info: NavPathInfo = new NavPathInfo("pageTwo", undefined)
            this.pageInfo.pushPath(info); //将name指定的NavDestination页面信息入栈
          })
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick((e: ClickEvent) => {
            this.pageInfo.pop();
          })
      }.width('100%').height('100%')
    }.title('pageOne')
  }
}

@Component
struct PageTwoStack {
  @StorageLink('pageInfo') pageInfo: NavPathStack = new NavPathStack();
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
          .onClick((e: ClickEvent) => {
            let info: NavPathInfo = new NavPathInfo("pageThree", undefined)
            this.pageInfo.pushPath(info); //将name指定的NavDestination页面信息入栈
          })
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick((e: ClickEvent) => {
            this.pageInfo.pop();
          })
      }.width('100%').height('100%')
    }.title('pageTwo')
  }
}

@Component
struct PageThreeStack {
  @StorageLink('pageInfo') pageInfo: NavPathStack = new NavPathStack();
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
          .onClick((e: ClickEvent) => {
            let info: NavPathInfo = new NavPathInfo("pageOne", undefined)
            this.pageInfo.pushPath(info); //将name指定的NavDestination页面信息入栈
          })
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick((e: ClickEvent) => {
            this.pageInfo.pop();
          })
      }.width('100%').height('100%')
    }.title('pageThree')
  }
}

@Component
struct NavigationContentMsgStack {
  @Link @Watch('info') message: number;
  @Link index: number;
  @Link logNumber: number;

  info(propertyName: string) {
    console.info(`freeze-test NavigationContent message callback ${this.message}`);
    console.info(`freeze-test ---- called by content ${this.index}`);
    this.logNumber++;
  }

  getValue(): number {
    console.info(`freeze-test getValue ${this.index}`);
    return this.message;
  }

  build() {
    Column() {
      Button('msg:' + `${this.getValue()}`)
        .fontSize(30)
        .fontWeight(FontWeight.Bold)

      Button('log number:' + `${this.logNumber}`)
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
    }
  }
}
```

在上面的示例中：

1.点击`change message`更改message的值，当前正在显示的MyNavigationTestStack组件中的@Watch注册的方法info被触发。

2.点击`Next Page`切换到PageOne，创建PageOneStack节点。

3.再次点击`change message`更改message的值，仅PageOneStack中的NavigationContentMsgStack子组件中@Watch注册的方法info被触发。

4.再次点击`Next Page`切换到PageTwo，创建PageTwoStack节点。

5.再次点击`change message`更改message的值，仅PageTwoStack中的NavigationContentMsgStack子组件中@Watch注册的方法info被触发。

6.再次点击`Next Page`切换到PageThree，创建PageThreeStack节点。

7.再次点击`change message`更改message的值，仅PageThreeStack中的NavigationContentMsgStack子组件中@Watch注册的方法info被触发。

8.点击`Back Page`回到PageTwo，此时，仅PageTwoStack中的NavigationContentMsgStack子组件中@Watch注册的方法info被触发。

9.再次点击`Back Page`回到PageOne，此时，仅PageOneStack中的NavigationContentMsgStack子组件中@Watch注册的方法info被触发。

10.再次点击`Back Page`回到初始页，此时，无任何触发。

## 组件复用

[组件复用](../state-management/arkts-reusable.md)通过重利用缓存池中已存在的节点，而非创建新节点，来优化UI性能并提升应用流畅度。复用池中的节点尽管未在UI组件树上展示，但是状态变量的更改仍会触发UI刷新。为了解决复用池中组件异常刷新问题，可以使用组件冻结避免复用池中的组件刷新。

**LazyForEach、组件复用和组件冻结混用场景**

在数据很多的长列表滑动场景下，开发者会使用LazyForEach来按需创建组件，同时配合组件复用降低在滑动过程中因创建和销毁组件带来的开销。但是开发者如果根据其复用类型不同，设置了[reuseId](../../reference/apis-arkui/arkui-ts/ts-universal-attributes-reuse-id.md#reuseid)，或者为了保证滑动性能设置了较大的cacheCount，这就可能使复用池或者LazyForEach缓存较多的节点。在这种情况下，如果开发者触发List下所有子节点的刷新，就会带来节点刷新数量过多的问题，这个时候，可以考虑搭配组件冻结使用。

```ts
'use static'

import { Entry, Component, ClickEvent, ForEach, Column, List, ListItem, Text, Button, Row, Color, Reusable, LazyForEach, IDataSource, DataChangeListener } from '@kit.ArkUI';
import { State, Link, Watch } from '@kit.ArkUI';

@Reusable
@Component
struct ChildComponent {
  @Link @Watch('descChange') desc: string;
  @State item: string = '';
  @State index: number = 0;
  descChange(propertyName: string) {
    console.info(`ChildComponent messageChange ${this.desc} this.index: ${this.index}`);
  }
  
  getValue(): string {
    console.info(`Child getvalue,id: ${this.index}`);
    return this.desc;
  }

  aboutToRecycle(): void {
    console.info(`ChildComponent has been recycled`);
  }
  build() {
    Column() {
      Text(`ChildComponent index: ${this.index} item: ${this.item}`)
        .fontSize(20)
      Text(`desc: ${this.getValue()}`)
        .fontSize(20)
    }.border({width: 2, color: Color.Pink})
  }
}

@Entry
@Component
struct Page {
  @State desc: string = 'Hello World';
  private data: TestDataSource = new TestDataSource();

  aboutToAppear() {
    for (let i = 0; i < 50; i++) {
      this.data.pushData(`Hello ${i}`);
    }
  }

  build() {
    Column() {
      Button(`change desc`).onClick(() => {
        this.desc += '!';
      })
      List({ space: 3 }) {
        LazyForEach(this.data, (item: string, index: int) => {
          ListItem() {
            ChildComponent({index: index, item: item, desc: this.desc})
          }
        }, (item: string) => item)
      }.cachedCount(5)
    }
    .height('100%')
  }
}

class BasicDataSource<string> implements IDataSource<string> {
  private listeners: Array<DataChangeListener> = Array<DataChangeListener>();
  private originDataArray: Array<string> = new Array<string>();

  public totalCount(): int {
    return this.originDataArray.length;
  }

  public getData(index: int): string {
    return this.originDataArray[index as int];
  }

  notifyDataAdd(index: int): void {
    this.listeners.forEach(listener => {
      listener.onDataAdd(index);
    });
  }

  notifyDataChange(index: int): void {
    this.listeners.forEach(listener => {
      listener.onDataChange(index);
    });
  }

  onDataReloaded(): void {
    this.listeners.forEach((listener: DataChangeListener) => {
      listener.onDataReloaded();
    });
  }

  registerDataChangeListener(listener: DataChangeListener) {
    if (this.listeners.indexOf(listener) < 0) {
      this.listeners.push(listener);
    }
  }

  unregisterDataChangeListener(listener: DataChangeListener) {
    const pos = this.listeners.indexOf(listener)
    if (pos >= 0) {
      this.listeners.splice(pos, 1);
    }
  }
}

class TestDataSource extends BasicDataSource<string> {
  private dataArray: string[] = [];

  public totalCount(): int {
    return this.dataArray.length;
  }

  public getData(index: int): string {
    return this.dataArray[index as int];
  }

  public pushData(data: string): void {
    this.dataArray.push(data);
  }

  public changeData(index: int, data: string): void {
    this.dataArray[index as int] = data;
    this.notifyDataChange(index);
  }
}
```

在上面的示例中：

1. 滑动到index为14的位置，当前屏幕上可见区域内有15个`ChildComponent`。
2. 在滑动过程中：
    - 列表上端的`ChildComponent`滑出可视区域外，此时先进入LazyForEach的缓存区域内，被设置inactive。在滑出LazyForEach缓存区域外后，因为标记了组件复用，所以并不会被析构，而是会进入复用池，此时再次被设置inactive。
    - 列表下端LazyForEach的缓存节点会进入List范围内，此时会试图请求创建新的节点进入LazyForEach的缓存，发现有可复用的节点时，从复用池中拿出已有节点，触发aboutToReuse生命周期回调，此时因为节点进入的是LazyForEach的缓存区域，所以其状态依旧是inactive。
3. 点击`change desc`，触发`Page`的成员变量`desc`的变化：
    - `desc`是\@State装饰的，其变化会通知给其子组件`ChildComponent`\@Link装饰的`desc`。
    - 非可视区域内的`ChildComponent`是inactive状态，且开启了组件冻结，所以这次变化只触发可视区域内的15个节点的`@Watch('descChange')`回调，并只刷新对应可视区域内的15个节点。LazyForEach和复用池中的节点并不会刷新，也不会触发\@Watch回调。
    

图示如下：
![freeze](../state-management/figures/freezeResuable.png)

## 组件混用

当支持组件冻结的场景彼此之间组合使用时，组件冻结机制也会随之叠加冻结和解冻。只有当叠加的所有场景都处于active状态时，状态变量的改变才会触发UI刷新。

**Navigation和TabContent的混用**

```ts
'use static'

import { Entry, Component, Margin, NavPathStack, NavPathInfo, ClickEvent, NavDestination, Builder, Column, Navigation, Text, NavigationMode, Button, ButtonType, Row, Tabs, TabContent, TabsController, BarPosition, BarMode, Color } from '@kit.ArkUI';
import { State, Link, Watch, StorageLink, PropRef } from '@kit.ArkUI';

@Component
struct ChildOfParamComponent {
  @PropRef @Watch('onChange') child_val: number;

  onChange(propertyName: string) {
    console.info(`Appmonitor ChildOfParamComponent: child_val changed:${this.child_val}`);
  }

  getValue(): number {
    console.info(`getValue child_val ${this.child_val}`)
    return this.child_val;
  }

  build() {
    Column() {
      Text(`Child Param： ${this.getValue()}`);
    }
  }
}

@Component
struct ParamComponent {
  @PropRef @Watch('onChange') paramVal: number;

  onChange(propertyName: string) {
    console.info(`Appmonitor ParamComponent: paramVal changed:${this.paramVal}`);
  }

  getValue(): number {
    console.info(`getValue paramVal ${this.paramVal}`)
    return this.paramVal;
  }

  build() {
    Column() {
      Text(`val： ${this.getValue()}`)
      ChildOfParamComponent({ child_val: this.paramVal });
    }
  }
}



@Component
struct DelayComponent {
  @PropRef @Watch('onChange') delayVal: number;

  onChange(propertyName: string) {
    console.info(`Appmonitor ParamComponent: delayVal changed:${this.delayVal}`);
  }
  getValue(): number {
    console.info(`getValue delayVal ${this.delayVal}`)
    return this.delayVal;
  }

  build() {
    Column() {
      Text(`Delay Param： ${this.getValue()}`);
    }
  }
}

@Component
struct TabsComponent {
  private controller: TabsController = new TabsController();
  @State @Watch('onChange') tabState: number = 47;

  onChange(propertyName: string) {
    console.info(`Appmonitor TabsComponent: tabState changed:${this.tabState}`);
  }

  getValue(): number {
    console.info(`getValue tabState ${this.tabState}`);
    return this.tabState;
  }

  build() {
    Column() {
      Button(`Incr state ${this.getValue()}`)
        .fontSize(25)
        .onClick((e: ClickEvent) => {
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
  @StorageLink('pageInfo') pageInfo: NavPathStack = new NavPathStack();

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
            .onClick((e: ClickEvent) => {
              let info: NavPathInfo = new NavPathInfo("pageOne", undefined)
              this.pageInfo.pushPath(info);
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
  @StorageLink('pageInfo') pageInfo: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Column() {
        TabsComponent();

        Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick((e: ClickEvent) => {
            let info: NavPathInfo = new NavPathInfo("pageTwo", undefined)
            this.pageInfo.pushPath(info);
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
  @StorageLink('pageInfo') pageInfo: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Column() {
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick((e: ClickEvent) => {
            this.pageInfo.pop();
          })
      }.width('100%').height('100%')
    }.title('pageTwo')
  }
}
```

在上述示例代码中：

1.点击`Next Page`，进入pageOne页面，页面中存在两个tab标签，点击这两个标签将其全部创建。回到Update标签，DelayUpdate标签未被选中，状态变量不会刷新。点击`Incr state`，日志中查询Appmonitor，Param和Child刷新。

2.切换到DelayUpdate标签，点击`Incr state`，日志中查询Appmonitor，存在2个打印。DelayUpdate中状态变量不会刷新与Update标签中相关的状态变量。

3.点击`Next page`进入下一个页面并返回，标签默认在DelayUpdate，再次点击`Incr state`，日志中查询Appmonitor，存在2个打印，页面路由返回时，只会解冻对应标签的节点。
