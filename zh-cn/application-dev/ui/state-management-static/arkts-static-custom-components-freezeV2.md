# V2自定义组件冻结场景

当@ComponentV2装饰的自定义组件处于冻结状态时，状态变量将不响应更新，即@Monitor不会调用，状态变量关联的节点不会刷新。

V2自定义组件冻结支持场景为：页面路由、TabContent、Navigation以及它们的混用。

> **说明：**
>
> - 在ArkTS-Sta上下文中，从API version 23开始，支持状态管理V2自定义组件冻结。
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

import { Entry, ComponentV2, ClickEvent, Column, Text, Button } from '@kit.ArkUI';
import { Monitor, IMonitor, ObservedV2, Trace, Local } from '@kit.ArkUI';

@ObservedV2
export class Book {
  @Trace name: string = '100';

  constructor(page: string) {
    this.name = page;
  }
}

@Entry
@ComponentV2
export struct Page1 {
  @Local bookTest: Book = new Book(`A Midsummer Night's Dream`);

  @Monitor(['bookTest.name']) onMessageUpdated(mon: IMonitor) {
    console.info(`The book name change from ${mon.value<string>()?.before} to ${mon.value<string>()?.now}`);
  }

  build() {
    Column() {
      Text(`Book name is  ${this.bookTest.name}`).fontSize(25)
      Button('changeBookName').fontSize(25)
        .onClick(() => {
          this.bookTest.name = 'The Old Man and the Sea'; // 会立刻触发@Monitor
        })
      Button('go to next page').fontSize(25)
        .onClick(() => {
          this.getUIContext().getRouter().pushUrl({ url: 'pages/Page2' });
          setTimeout(() => {
            this.bookTest = new Book(`Jane Austen's Pride and Prejudice`); // 从Page2返回Page1后触发@Monitor
          }, 1000);
        })
    }
  }
}
```

页面2：

```ts
'use static'

import { Entry, ComponentV2, ClickEvent, Column, Text, Button } from '@kit.ArkUI';
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

在上面的示例中：

1. 点击页面1中的Button “changeBookName”，bookTest变量的name属性改变，@Monitor中注册的方法onMessageUpdated会被调用。
2. 点击页面1中的Button “go to next page”，跳转到页面2，然后延迟1s更新状态变量“bookTest”。在更新“bookTest”的时候，已经跳转到页面2，页面1处于inactive状态，状态变量`@Local bookTest`将不响应更新，其@Monitor不会调用，状态变量关联的节点不会刷新。
3. 点击“Back”，页面2被销毁，页面1的状态由inactive变为active。状态变量“bookTest”的更新被观察到，@Monitor中注册的方法onMessageUpdated被调用，对应的Text显示内容改变。

## TabContent

对Tabs中当前不可见的TabContent进行冻结，不会触发组件的更新。

图示如下：
![freezeWithTab](../state-management/figures/freezewithTabs.png)

```ts
'use static'

import { Entry, ComponentV2, Column, Text, ClickEvent, Row, FontWeight, Button, Tabs, ForEach, TabContent, Repeat } from '@kit.ArkUI';
import { Local, Param, Monitor, IMonitor } from '@kit.ArkUI';

@Entry
@ComponentV2
struct TabContentTest {
  @Local message: number = 0;
  @Local data: number[] = [0, 1, 2, 3, 4];

  build() {
    Row() {
      Column() {
        Button('change message').onClick(() => {
          this.message++;
        })

        Tabs() {
          Repeat<number>(this.data).each(ri => {
            TabContent() {
              FreezeChild({ message: this.message, index: ri.item })
            }.tabBar(`tab${ri.item}`)
          }).key((item: number) => item.toString()).virtualScroll({ disableVirtualScroll: true })
        }
      }
      .width('100%')
    }
    .height('100%')
  }
}

@ComponentV2
struct FreezeChild {
  @Param message: number = 0;
  @Param index: number = 0;
  // 仅处于激活状态的TabContent下的FreezeChild可以立刻触发@Monitor
  @Monitor(['message']) onMessageUpdated(mon: IMonitor) {
    console.info(`FreezeChild message callback func ${this.message}, index: ${this.index}`);
  }

  build() {
    Text('message' + `${this.message}, index: ${this.index}`)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
  }
}

```

在上面的示例中：

1.点击“change message”更改message的值，当前正在显示的TabContent组件中的@Monitor中注册的方法onMessageUpdated被触发。

2.点击TabBar“tab1”切换到另外的TabContent，TabContent状态由inactive变为active，对应的@Monitor中注册的方法onMessageUpdated被触发。

3.再次点击“change message”更改message的值，仅当前显示的TabContent子组件中的@Monitor中注册的方法onMessageUpdated被触发。其他inactive的TabContent组件不会触发@Monitor。

## Navigation

当NavDestination不可见时，会将其子自定义组件设置成非激活态，不会触发组件的刷新。当返回该页面时，其子自定义组件重新恢复成激活态，触发@Monitor回调进行刷新。

```ts
'use static'

import { Entry, ComponentV2, NavPathStack, NavPathInfo, ClickEvent, NavDestination, Builder, Column, Navigation, Text, NavigationMode, Button, ButtonType } from '@kit.ArkUI';
import { Monitor, IMonitor, Local, Provider, Consumer, Param } from '@kit.ArkUI';

@Entry
@ComponentV2
struct MyNavigationTestStack {
  @Provider('pageInfo') pageInfo: NavPathStack = new NavPathStack();
  @Local message: number = 0;

  @Monitor(['message']) onChange(m: IMonitor) {
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
              let info: NavPathInfo = new NavPathInfo('pageOne', undefined);
              this.pageInfo.pushPath(info); //将name指定的NavDestination页面信息入栈
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
            let info: NavPathInfo = new NavPathInfo('pageTwo', undefined);
            this.pageInfo.pushPath(info); //将name指定的NavDestination页面信息入栈
          })
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule })
          .onClick(() => {
            this.pageInfo.pop();
          })
      }.width('100%').height('100%')
    }.title('pageOne')
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
            let info: NavPathInfo = new NavPathInfo('pageThree', undefined);
            this.pageInfo.pushPath(info); //将name指定的NavDestination页面信息入栈
          })
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule })
          .onClick(() => {
            this.pageInfo.pop();
          })
      }
    }.title('pageTwo')
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
            let info: NavPathInfo = new NavPathInfo('pageOne', undefined);
            this.pageInfo.pushPath(info); //将name指定的NavDestination页面信息入栈
          })
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule })
          .height(40)
          .onClick(() => {
            this.pageInfo.pop();
          })
      }
    }.title('pageThree')
  }
}

@ComponentV2
struct NavigationContentMsgStack {
  @Param message: number = 0;
  @Param index: number = 0;
  // 仅处于激活状态的NavigationContentMsgStack可以立刻触发@Monitor
  @Monitor(['message']) onChange(m: IMonitor) {
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

在上面的示例中：

1.点击“change message”更改message的值，当前正在显示的MyNavigationTestStack组件中的@Monitor中注册的方法onChange被触发。

2.点击“Next Page”切换到PageOne，创建PageOneStack节点。

3.再次点击“change message”更改message的值，仅PageOneStack中的NavigationContentMsgStack子组件中的@Monitor中注册的方法onChange被触发。

4.再次点击“Next Page”切换到PageTwo，创建PageTwoStack节点。PageOneStack节点状态由active变为inactive。

5.再次点击“change message”更改message的值，仅PageTwoStack中的NavigationContentMsgStack子组件中的@Monitor中注册的方法onChange被触发。Navigation路由栈中非栈顶的NavDestination中的子自定义组件，将是inactive状态。@Monitor方法不会触发。

6.再次点击“Next Page”切换到PageThree，创建PageThreeStack节点。PageTwoStack节点状态由active变为inactive。

7.再次点击“change message”更改message的值，仅PageThreeStack中的NavigationContentMsgStack子组件中的@Monitor中注册的方法onChange被触发。Navigation路由栈中非栈顶的NavDestination中的子自定义组件，将是inactive状态。@Monitor方法不会触发。

8.点击“Back Page”回到PageTwo，此时，PageTwoStack节点状态由inactive变为active，其NavigationContentMsgStack子组件中的@Monitor中注册的方法onChange被触发。

9.再次点击“Back Page”回到PageOne，此时，PageOneStack节点状态由inactive变为active，其NavigationContentMsgStack子组件中的@Monitor中注册的方法onChange被触发。

## 混用场景

组件冻结混用场景即当支持组件冻结的场景彼此之间组合使用。当多个冻结条件满足时，只有所有冻结场景都解冻后，组件才会恢复成激活状态。

### Navigation和TabContent的混用

```ts
'use static'

import {  Entry, ComponentV2, Margin, NavPathStack, NavPathInfo, NavDestination, Builder, Column, Navigation, Text, NavigationMode, Button, ButtonType, Tabs, TabContent, TabsController, BarPosition, BarMode, Color } from '@kit.ArkUI';
import { Monitor, IMonitor, Local, Provider, Consumer, Param, Require } from '@kit.ArkUI';

@ComponentV2
struct ChildOfParamComponent {
  @Require @Param child_val: number;
  // 处于激活状态的ChildOfParamComponent才可以立刻触发@Monitor
  @Monitor(['child_val']) onMessageUpdated(m: IMonitor) {
    console.info(`Appmonitor ChildOfParamComponent: changed ${m.dirty[0]}: ${m.value<number>()?.before} -> ${m.value<number>()?.now}`);
  }

  build() {
    Column() {
      Text(`Child Param： ${this.child_val}`)
    }
  }
}

@ComponentV2
struct ParamComponent {
  @Require @Param val: number;
  // 处于激活状态的ParamComponent才可以立刻触发@Monitor
  @Monitor(['val']) onMessageUpdated(m: IMonitor) {
    console.info(`Appmonitor ParamComponent: changed ${m.dirty[0]}: ${m.value<number>()?.before} -> ${m.value<number>()?.now}`);
  }

  build() {
    Column() {
      Text(`val： ${this.val}`)
      ChildOfParamComponent({child_val: this.val})
    }
  }
}

@ComponentV2
struct DelayComponent {
  @Require @Param delayVal1: number;
  // 处于激活状态的DelayComponent才可以立刻触发@Monitor
  @Monitor(['delayVal1']) onMessageUpdated(m: IMonitor) {
    console.info(`Appmonitor DelayComponent: changed ${m.dirty[0]}: ${m.value<number>()?.before} -> ${m.value<number>()?.now}`);
  }

  build() {
    Column() {
      Text(`Delay Param： ${this.delayVal1}`);
    }
  }
}

@ComponentV2
struct TabsComponent {
  private controller: TabsController = new TabsController();
  @Local tabState: number = 47;

  @Monitor(['tabState']) onMessageUpdated(m: IMonitor) {
    console.info(`Appmonitor TabsComponent: changed ${m.dirty[0]}: ${m.value<number>()?.before} -> ${m.value<number>()?.now}`);
  }

  build() {
    Column() {
      Button(`Incr state ${this.tabState}`)
        .fontSize(25)
        .onClick(() => {
          console.info('Button increment state value');
          this.tabState = this.tabState + 1;
        })

      Tabs({ barPosition: BarPosition.Start, index: 0, controller: this.controller}) {
        TabContent() {
          ParamComponent({val: this.tabState})
        }.tabBar('Update')
        TabContent() {
          DelayComponent({delayVal1: this.tabState})
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
@ComponentV2
struct MyNavigationTestStack {
  @Provider('pageInfo') pageInfo: NavPathStack = new NavPathStack();

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
              let info: NavPathInfo = new NavPathInfo('pageOne', undefined);
              this.pageInfo.pushPath(info);
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

  build() {
    NavDestination() {
      Column() {
        TabsComponent();

        Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            let info: NavPathInfo = new NavPathInfo('pageTwo', undefined);
            this.pageInfo.pushPath(info);
          })
      }.width('100%').height('100%')
    }.title('pageOne')
  }
}

@ComponentV2
struct PageTwoStack {
  @Consumer('pageInfo') pageInfo: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Column() {
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pop(); // 返回上一个页面后仅解冻可见的TabContent
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