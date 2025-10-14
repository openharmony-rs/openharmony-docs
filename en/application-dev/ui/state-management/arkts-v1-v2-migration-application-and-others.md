# Migration for In-Application State Variables and Related Scenarios
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

This guide provides migration instructions for in-application state variables and their related usage scenarios.

| V1 Decorator Name/Scenario               | V2 Decorator                 |
|------------------------|--------------------------|
| [LocalStorage](./arkts-localstorage.md)                 | [\@ObservedV2](./arkts-new-observedV2-and-trace.md)[\@Trace](./arkts-new-observedV2-and-trace.md)   |
| [AppStorage](./arkts-appstorage.md)                | [AppStorageV2](./arkts-new-appstoragev2.md)  |
| [Environment](./arkts-environment.md)       | Direct ability API calls to obtain system environment variables  |
| [PersistentStorage](./arkts-persiststorage.md)     | [PersistenceV2](./arkts-new-persistencev2.md)   |
| Legacy migration scenarios     | \@ObservedV2, \@Trace, [\@Monitor](./arkts-new-monitor.md)|
| Scrollable component scenarios     | [makeObserved](./arkts-new-makeObserved.md)|
| [Modifier](../arkts-user-defined-modifier.md)      |[makeObserved](./arkts-new-makeObserved.md), \@ObservedV2, \@Trace|


## Migration Examples

### LocalStorage -> \@ObservedV2/\@Trace
**Migration Rules**

In state management V1, LocalStorage is used to share state variables across pages. However, these variables are tightly coupled with the view layer, requiring framework-level support for sharing.
In state management V2, observation capabilities are embedded directly into the data itself, decoupling state from the view layer. As a result, LocalStorage-style functionality is no longer needed. Instead, you can create state instances using the \@ObservedV2 and \@Trace decorators, and then import or export these instances to enable cross-page state sharing.

**Example**

**Common Scenario**

V1:

Use the windowStage.[loadContent](../../reference/apis-arkui/arkts-apis-window-Window.md#loadcontent9) and this.getUIContext().[getSharedLocalStorage](../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getsharedlocalstorage12) APIs to share state variables between pages.
```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  para: Record<string, number> = { 'count': 47 };
  storage: LocalStorage = new LocalStorage(this.para);

  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/Page1', this.storage);
  }
}
```
In this example, \@LocalStorageLink is used to synchronize local changes to LocalStorage.

```ts
// Page1.ets
// The Previewer does not support accessing LocalStorage instances shared across pages.
@Entry({ useSharedStorage: true })
@Component
struct Page1 {
  @LocalStorageLink('count') count: number = 0;
  pageStack: NavPathStack = new NavPathStack();

  build() {
    Navigation(this.pageStack) {
      Column() {
        Text(`${this.count}`)
          .fontSize(50)
          .onClick(() => {
            this.count++;
          })
        Button('push to Page2')
          .onClick(() => {
            this.pageStack.pushPathByName('Page2', null);
          })
      }
    }
  }
}
```

```ts
// Page2.ets
@Builder
export function Page2Builder() {
  Page2()
}

// The Page2 component obtains the LocalStorage instance of the parent component Page1.
@Component
struct Page2 {
  @LocalStorageLink('count') count: number = 0;
  pathStack: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Column() {
        Text(`${this.count}`)
          .fontSize(50)
          .onClick(() => {
            this.count++;
          })
        Button('change')
          .fontSize(50)
          .onClick(() => {
            const storage = this.getUIContext().getSharedLocalStorage();
            if (storage) {
              storage.set('count', 20);
            }
          })
      }
    }
    .onReady((context: NavDestinationContext) => {
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
        "description": "LocalStorage example"
      }
    }
  ]
}
```
V2:

- Declare the \@ObservedV2 decorated **MyStorage** class and import it to the page to use.
- Declare the \@Trace decorated properties as observable data shared between pages.

```ts
// storage.ets
@ObservedV2
export class MyStorage {
  static singleton_: MyStorage;

  static instance() {
    if (!MyStorage.singleton_) {
      MyStorage.singleton_ = new MyStorage();
    }
    return MyStorage.singleton_;
  }

  @Trace count: number = 47;
}
```

```ts
// Page1.ets
import { MyStorage } from './storage';

@Entry
@ComponentV2
struct Page1 {
  storage: MyStorage = MyStorage.instance();
  pageStack: NavPathStack = new NavPathStack();

  build() {
    Navigation(this.pageStack) {
      Column() {
        Text(`${this.storage.count}`)
          .fontSize(50)
          .onClick(() => {
            this.storage.count++;
          })
        Button('push to Page2')
          .onClick(() => {
            this.pageStack.pushPathByName('Page2', null);
          })
      }
    }
  }
}
```

```ts
// Page2.ets
import { MyStorage } from './storage';

@Builder
export function Page2Builder() {
  Page2()
}

@ComponentV2
struct Page2 {
  storage: MyStorage = MyStorage.instance();
  pathStack: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Column() {
        Text(`${this.storage.count}`)
          .fontSize(50)
          .onClick(() => {
            this.storage.count++;
          })
      }
    }
    .onReady((context: NavDestinationContext) => {
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
        "description" : "LocalStorage example"
      }
    }
  ]
}
```

The following example demonstrates @LocalStorageProp behavior, where local modifications do not synchronize back to LocalStorage:
- In **Page1**, changes to the **count** variable decorated with \@LocalStorageProp remain local to the component and do not synchronize back to LocalStorage.
- Clicking **push to Page2** navigates to **Page2**, where the **Text** component displays the original value **47** from LocalStorage.
- Clicking **change Storage Count** updates the value of **count** via **setOrCreate** of LocalStorage and triggers notifications to all bound variables.

```ts
// Page1.ets
export let storage: LocalStorage = new LocalStorage();

storage.setOrCreate('count', 47);

@Entry(storage)
@Component
struct Page1 {
  @LocalStorageProp('count') count: number = 0;
  pageStack: NavPathStack = new NavPathStack();

  build() {
    Navigation(this.pageStack) {
      Column() {
        Text(`${this.count}`)
          .fontSize(50)
          .onClick(() => {
            this.count++;
          })
        Button('change Storage Count')
          .onClick(() => {
            storage.setOrCreate('count', storage.get<number>('count') as number + 100);
          })
        Button('push to Page2')
          .onClick(() => {
            this.pageStack.pushPathByName('Page2', null);
          })
      }
    }
  }
}
```

```ts
// Page2.ets
import { storage } from './Page1'

@Builder
export function Page2Builder() {
  Page2()
}

// The Page2 component obtains the LocalStorage instance of the parent component Page1.
@Component
struct Page2 {
  @LocalStorageProp('count') count: number = 0;
  pathStack: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Column() {
        Text(`${this.count}`)
          .fontSize(50)
          .onClick(() => {
            this.count++;
          })
        Button('change Storage Count')
          .onClick(() => {
            storage.setOrCreate('count', storage.get<number>('count') as number + 100);
          })
      }
    }
    .onReady((context: NavDestinationContext) => {
      this.pathStack = context.pathStack;
    })
  }
}
```
In V2, you can use \@Local and \@Monitor to achieve the similar behavior.
- The **count** variable decorated with \@Local is local to the component. Changes to it will not synchronize back to **storage**.
- \@Monitor listens for changes of **storage.count**. When **storage.count** changes, the \@Local value is updated in the callback of \@Monitor.

```ts
// Page1.ets
import { MyStorage } from './storage';

@Entry
@ComponentV2
struct Page1 {
  storage: MyStorage = MyStorage.instance();
  pageStack: NavPathStack = new NavPathStack();
  @Local count: number = this.storage.count;

  @Monitor('storage.count')
  onCountChange(mon: IMonitor) {
    console.info(`Page1 ${mon.value()?.before} to ${mon.value()?.now}`);
    this.count = this.storage.count;
  }

  build() {
    Navigation(this.pageStack) {
      Column() {
        Text(`${this.count}`)
          .fontSize(50)
          .onClick(() => {
            this.count++;
          })
        Button('change Storage Count')
          .onClick(() => {
            this.storage.count += 100;
          })
        Button('push to Page2')
          .onClick(() => {
            this.pageStack.pushPathByName('Page2', null);
          })
      }
    }
  }
}
```

```ts
// Page2.ets
import { MyStorage } from './storage';

@Builder
export function Page2Builder() {
  Page2()
}

@ComponentV2
struct Page2 {
  storage: MyStorage = MyStorage.instance();
  pathStack: NavPathStack = new NavPathStack();
  @Local count: number = this.storage.count;

  @Monitor('storage.count')
  onCountChange(mon: IMonitor) {
    console.info(`Page2 ${mon.value()?.before} to ${mon.value()?.now}`);
    this.count = this.storage.count;
  }

  build() {
    NavDestination() {
      Column() {
        Text(`${this.count}`)
          .fontSize(50)
          .onClick(() => {
            this.count++;
          })
        Button('change Storage Count')
          .onClick(() => {
            this.storage.count += 100;
          })
      }
    }
    .onReady((context: NavDestinationContext) => {
      this.pathStack = context.pathStack;
    })
  }
}
```

**Scenario Where a Custom Component Receives a LocalStorage Instance**

To support scenarios where **Navigation** is used, LocalStorage instances can be passed as parameters to custom components and shared with all child components using the current custom component as the root.
In V2, this scenario can be implemented by creating multiple global instances of \@ObservedV2 and \@Trace decorated classes.

V1:

```ts
let localStorageA: LocalStorage = new LocalStorage();
localStorageA.setOrCreate('PropA', 'PropA');

let localStorageB: LocalStorage = new LocalStorage();
localStorageB.setOrCreate('PropB', 'PropB');

let localStorageC: LocalStorage = new LocalStorage();
localStorageC.setOrCreate('PropC', 'PropC');

@Entry
@Component
struct MyNavigationTestStack {
  @Provide('pageInfo') pageInfo: NavPathStack = new NavPathStack();

  @Builder
  PageMap(name: string) {
    if (name === 'pageOne') {
      // Pass multiple LocalStorage instances.
      PageOneStack({}, localStorageA)
    } else if (name === 'pageTwo') {
      PageTwoStack({}, localStorageB)
    } else if (name === 'pageThree') {
      PageThreeStack({}, localStorageC)
    }
  }

  build() {
    Column({ space: 5 }) {
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
      .borderWidth(1)
    }
  }
}

@Component
struct PageOneStack {
  @Consume('pageInfo') pageInfo: NavPathStack;
  @LocalStorageLink('PropA') PropA: string = 'Hello World';

  build() {
    NavDestination() {
      Column() {
        // Display 'PropA'.
        NavigationContentMsgStack()
        // Display 'PropA'.
        Text(`${this.PropA}`)
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
  @LocalStorageLink('PropB') PropB: string = 'Hello World';

  build() {
    NavDestination() {
      Column() {
        // Display 'Hello'. The current LocalStorage instance localStorageB has no value corresponding to PropA. Therefore, the local default value 'Hello' is used.
        NavigationContentMsgStack()
        // Display "PropB".
        Text(`${this.PropB}`)
        Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pushPathByName('pageThree', null);
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
  @LocalStorageLink('PropC') PropC: string = 'pageThreeStack';

  build() {
    NavDestination() {
      Column() {
        // Display 'Hello'. The current LocalStorage instance localStorageC has no value corresponding to PropA. Therefore, the local default value 'Hello' is used.
        NavigationContentMsgStack()
        // Display "PropC".
        Text(`${this.PropC}`)
        Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pushPathByName('pageOne', null);
          })

      }.width('100%').height('100%')
    }.title('pageThree')
    .onBackPressed(() => {
      this.pageInfo.pop();
      return true;
    })
  }
}

@Component
struct NavigationContentMsgStack {
  @LocalStorageLink('PropA') PropA: string = 'Hello';

  build() {
    Column() {
      Text(`${this.PropA}`)
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
    }
  }
}
```
V2:

Declare the \@ObservedV2 decorated class to replace LocalStorage functionality. LocalStorage keys can be replaced with \@Trace decorated properties.
```ts
// storage.ets
@ObservedV2
export class MyStorageA {
  @Trace propA: string = 'Hello';

  constructor(propA?: string) {
    this.propA = propA ? propA : this.propA;
  }
}

@ObservedV2
export class MyStorageB extends MyStorageA {
  @Trace propB: string = 'Hello';

  constructor(propB: string) {
    super();
    this.propB = propB;
  }
}

@ObservedV2
export class MyStorageC extends MyStorageA {
  @Trace propC: string = 'Hello';

  constructor(propC: string) {
    super();
    this.propC = propC;
  }
}
```

In the **pageOneStack**, **pageTwoStack**, and **pageThreeStack** components, create instances of **MyStorageA**, **MyStorageB**, and **MyStorageC**, respectively. Pass these instances to the child component **NavigationContentMsgStack** using \@Param. This way, the same cross-component state sharing capability as LocalStorage is achieved.

```ts
// Index.ets
import { MyStorageA, MyStorageB, MyStorageC } from './storage';

@Entry
@ComponentV2
struct MyNavigationTestStack {
  pageInfo: NavPathStack = new NavPathStack();

  @Builder
  PageMap(name: string) {
    if (name === 'pageOne') {
      pageOneStack()
    } else if (name === 'pageTwo') {
      pageTwoStack()
    } else if (name === 'pageThree') {
      pageThreeStack()
    }
  }

  build() {
    Column({ space: 5 }) {
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
      .borderWidth(1)
    }
  }
}

@ComponentV2
struct pageOneStack {
  pageInfo: NavPathStack = new NavPathStack();
  @Local storageA: MyStorageA = new MyStorageA('PropA');

  build() {
    NavDestination() {
      Column() {
        // Display 'PropA'.
        NavigationContentMsgStack({ storage: this.storageA })
        // Display 'PropA'.
        Text(`${this.storageA.propA}`)
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
    .onReady((context: NavDestinationContext) => {
      this.pageInfo = context.pathStack;
    })
  }
}

@ComponentV2
struct pageTwoStack {
  pageInfo: NavPathStack = new NavPathStack();
  @Local storageB: MyStorageB = new MyStorageB('PropB');

  build() {
    NavDestination() {
      Column() {
        // Display "Hello".
        NavigationContentMsgStack({ storage: this.storageB })
        // Display "PropB".
        Text(`${this.storageB.propB}`)
        Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pushPathByName('pageThree', null);
          })

      }.width('100%').height('100%')
    }.title('pageTwo')
    .onBackPressed(() => {
      this.pageInfo.pop();
      return true;
    })
    .onReady((context: NavDestinationContext) => {
      this.pageInfo = context.pathStack;
    })
  }
}

@ComponentV2
struct pageThreeStack {
  pageInfo: NavPathStack = new NavPathStack();
  @Local storageC: MyStorageC = new MyStorageC('PropC');

  build() {
    NavDestination() {
      Column() {
        // Display "Hello".
        NavigationContentMsgStack({ storage: this.storageC })
        // Display "PropC".
        Text(`${this.storageC.propC}`)
        Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pushPathByName('pageOne', null);
          })

      }.width('100%').height('100%')
    }.title('pageThree')
    .onBackPressed(() => {
      this.pageInfo.pop();
      return true;
    })
    .onReady((context: NavDestinationContext) => {
      this.pageInfo = context.pathStack;
    })
  }
}

@ComponentV2
struct NavigationContentMsgStack {
  @Require @Param storage: MyStorageA;

  build() {
    Column() {
      Text(`${this.storage.propA}`)
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
    }
  }
}
```

### AppStorage -> AppStorageV2
The approach of creating global \@ObservedV2 and \@Trace decorated instances described in the previous section is not suitable for cross-ability data sharing. For this scenario, you can use AppStorageV2.

V1:

AppStorage is bound to the application process and enables data sharing across abilities.
Using \@StorageLink allows local modifications to synchronize back to AppStorage.

```ts
// EntryAbility Index.ets
import { common, Want } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @StorageLink('count') count: number = 0;
  private context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  build() {
    Column() {
      Text(`EntryAbility count: ${this.count}`)
        .fontSize(50)
        .onClick(() => {
          this.count++;
        })
      Button('Jump to EntryAbility1').onClick(() => {
        let wantInfo: Want = {
          bundleName: 'com.example.myapplication', // Replace it with the bundle name in AppScope/app.json5.
          abilityName: 'EntryAbility1'
        };
        this.context.startAbility(wantInfo);
      })
    }
  }
}
```

```ts
// EntryAbility1 Index1.ets
import { common, Want } from '@kit.AbilityKit';

@Entry
@Component
struct Index1 {
  @StorageLink('count') count: number = 0;
  private context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  build() {
    Column() {
      Text(`EntryAbility1 count: ${this.count}`)
        .fontSize(50)
        .onClick(() => {
          this.count++;
        })
      Button('Jump to EntryAbility').onClick(() => {
        let wantInfo: Want = {
          bundleName: 'com.example.myapplication', // Replace it with the bundle name in AppScope/app.json5.
          abilityName: 'EntryAbility'
        };
        this.context.startAbility(wantInfo);
      })
    }
  }
}
```
V2:

AppStorageV2 can be used to achieve cross-ability data sharing.
Example:

```ts
import { common, Want } from '@kit.AbilityKit';
import { AppStorageV2 } from '@kit.ArkUI';

@ObservedV2
export class MyStorage {
  @Trace count: number = 0
}

@Entry
@ComponentV2
struct Index {
  @Local storage: MyStorage = AppStorageV2.connect(MyStorage, 'storage', () => new MyStorage())!;
  private context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  build() {
    Column() {
      Text(`EntryAbility1 count: ${this.storage.count}`)
        .fontSize(50)
        .onClick(() => {
          this.storage.count++;
        })
      Button('Jump to EntryAbility1').onClick(() => {
        let wantInfo: Want = {
          bundleName: 'com.example.myapplication', // Replace it with the bundle name in AppScope/app.json5.
          abilityName: 'EntryAbility1'
        };
        this.context.startAbility(wantInfo);
      })
    }
  }
}

```

```ts
import { common, Want } from '@kit.AbilityKit';
import { AppStorageV2 } from '@kit.ArkUI';

@ObservedV2
export class MyStorage {
  @Trace count: number = 0
}

@Entry
@ComponentV2
struct Index1 {
  @Local storage: MyStorage = AppStorageV2.connect(MyStorage, 'storage', () => new MyStorage())!;
  private context = this.getUIContext().getHostContext() as common.UIAbilityContext;

    build() {
      Column() {
        Text(`EntryAbility1 count: ${this.storage.count}`)
          .fontSize(50)
          .onClick(() => {
            this.storage.count++;
          })
        Button('Jump to EntryAbility').onClick(() => {
          let wantInfo: Want = {
            bundleName: 'com.example.myapplication', // Replace it with the bundle name in AppScope/app.json5.
            abilityName: 'EntryAbility'
          };
          this.context.startAbility(wantInfo);
        })
      }
    }
}
```

For scenarios that require @StorageProp-like behavior, where local variables can be modified without synchronizing back to AppStorage, while the component still receives updates from AppStorage:

V1:

```ts
// EntryAbility Index.ets
import { common, Want } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @StorageProp('count') count: number = 0;
  private context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  build() {
    Column() {
      Text(`EntryAbility count: ${this.count}`)
        .fontSize(25)
        .onClick(() => {
          this.count++;
        })
      Button('change Storage Count')
        .onClick(() => {
          AppStorage.setOrCreate('count', AppStorage.get<number>('count') as number + 100);
        })
      Button('Jump to EntryAbility1').onClick(() => {
        let wantInfo: Want = {
          bundleName: 'com.example.myapplication', // Replace it with the bundle name in AppScope/app.json5.
          abilityName: 'EntryAbility1'
        };
        this.context.startAbility(wantInfo);
      })
    }
  }
}
```

```ts
// EntryAbility1 Index1.ets
import { common, Want } from '@kit.AbilityKit';

@Entry
@Component
struct Index1 {
  @StorageProp('count') count: number = 0;
  private context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  build() {
    Column() {
      Text(`EntryAbility1 count: ${this.count}`)
        .fontSize(50)
        .onClick(() => {
          this.count++;
        })
      Button('change Storage Count')
        .onClick(() => {
          AppStorage.setOrCreate('count', AppStorage.get<number>('count') as number + 100);
        })
      Button('Jump to EntryAbility').onClick(() => {
        let wantInfo: Want = {
          bundleName: 'com.example.myapplication', // Replace it with the bundle name in AppScope/app.json5.
          abilityName: 'EntryAbility'
        };
        this.context.startAbility(wantInfo);
      })
    }
  }
}
```

V2:

Use \@Monitor and \@Local to achieve the similar behavior:

```ts
import { common, Want } from '@kit.AbilityKit';
import { AppStorageV2 } from '@kit.ArkUI';

@ObservedV2
export class MyStorage {
  @Trace count: number = 0;
}

@Entry
@ComponentV2
struct Index {
  @Local storage: MyStorage = AppStorageV2.connect(MyStorage, 'storage', () => new MyStorage())!;
  @Local count: number = this.storage.count;
  private context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  @Monitor('storage.count')
  onCountChange(mon: IMonitor) {
    console.info(`Index1 ${mon.value()?.before} to ${mon.value()?.now}`);
    this.count = this.storage.count;
  }

  build() {
    Column() {
      Text(`EntryAbility1 count: ${this.count}`)
        .fontSize(25)
        .onClick(() => {
          this.count++;
        })
      Button('change Storage Count')
        .onClick(() => {
          this.storage.count += 100;
        })
      Button('Jump to EntryAbility1').onClick(() => {
        let wantInfo: Want = {
          bundleName: 'com.example.myapplication', // Replace it with the bundle name in AppScope/app.json5.
          abilityName: 'EntryAbility1'
        };
        this.context.startAbility(wantInfo);
      })
    }
  }
}
```

```ts
import { common, Want } from '@kit.AbilityKit';
import { AppStorageV2 } from '@kit.ArkUI';

@ObservedV2
export class MyStorage {
  @Trace count: number = 0;
}

@Entry
@ComponentV2
struct Index1 {
  @Local storage: MyStorage = AppStorageV2.connect(MyStorage, 'storage', () => new MyStorage())!;
  @Local count: number = this.storage.count;
  private context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  @Monitor('storage.count')
  onCountChange(mon: IMonitor) {
    console.info(`Index1 ${mon.value()?.before} to ${mon.value()?.now}`);
    this.count = this.storage.count;
  }

  build() {
    Column() {
      Text(`EntryAbility1 count: ${this.count}`)
        .fontSize(25)
        .onClick(() => {
          this.count++;
        })
      Button('change Storage Count')
        .onClick(() => {
          this.storage.count += 100;
        })
      Button('Jump to EntryAbility').onClick(() => {
        let wantInfo: Want = {
          bundleName: 'com.example.myapplication', // Replace it with the bundle name in AppScope/app.json5.
          abilityName: 'EntryAbility'
        };
        this.context.startAbility(wantInfo);
      })
    }
  }
}
```

### Environment -> Direct API Calls to Obtain System Environment Variables
In V1, you can obtain environment variables through **Environment**. However, the result obtained by **Environment** cannot be directly used. It must be combined with AppStorage to obtain the corresponding environment variable values.
After migration to V2, you can directly obtain the system environment variables through the [config](../../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#uiabilitycontext-1) property of **UIAbilityContext**, eliminating the need for the **Environment** API.

V1:

The following uses **languageCode** as an example.
```ts
// Store languageCode to AppStorage.
Environment.envProp('languageCode', 'en');

@Entry
@Component
struct Index {
  @StorageProp('languageCode') languageCode: string = 'en';

  build() {
    Row() {
      Column() {
        // Obtain the current device language code.
        Text(this.languageCode)
      }
    }
  }
}
```

V2:

Encapsulate an **Env** class to manage multiple system environment variables.

```ts
// Env.ets
import { ConfigurationConstant } from '@kit.AbilityKit';

export class Env {
  language: string | undefined;
  colorMode: ConfigurationConstant.ColorMode | undefined;
  fontSizeScale: number | undefined;
  fontWeightScale: number | undefined;
}

export let env: Env = new Env();
```
Obtain the required system environment variables from **onCreate**.
```ts
// EntryAbility.ets
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { env } from '../pages/Env';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    env.language = this.context.config.language;
    env.colorMode = this.context.config.colorMode;
    env.fontSizeScale = this.context.config.fontSizeScale;
    env.fontWeightScale = this.context.config.fontWeightScale;
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/Index');
  }
}

```
Obtain the current value of **Env** on the page.
```ts
// Index.ets
import { env } from '../pages/Env';

@Entry
@ComponentV2
struct Index {
  build() {
    Row() {
      Column() {
        // Output the environment variables of the current device.
        Text(`languageCode: ${env.language}`).fontSize(20)
        Text(`colorMode: ${env.colorMode}`).fontSize(20)
        Text(`fontSizeScale: ${env.fontSizeScale}`).fontSize(20)
        Text(`fontWeightScale: ${env.fontWeightScale}`).fontSize(20)
      }
    }
  }
}
```

### PersistentStorage -> PersistenceV2
In V1, **PersistentStorage** provides UI data persistence. In V2, this functionality is replaced by the more convenient **PersistenceV2** API.
- In V1, persistence triggering relies on AppStorage's observation capability and is coupled with AppStorage. As a result, you cannot control when to read or write persistent data.
- **PersistentStorage** uses serialization and deserialization without explicit type information, resulting in type loss after persistence, and object methods cannot be persisted.

**PersistenceV2** advantages:
- When an \@ObservedV2 object is associated with **PersistenceV2**, changes to its \@Trace properties automatically trigger persistence of the entire object.
- You can manually trigger persistence operations by calling the [PersistenceV2.save](../../reference/apis-arkui/js-apis-StateManagement.md#save) and [PersistenceV2.globalConnect](./arkts-new-persistencev2.md#using-globalconnect-to-store-data) APIs.

V1:

```ts
class data {
  name: string = 'ZhangSan';
  id: number = 0;
}

PersistentStorage.persistProp('numProp', 47);
PersistentStorage.persistProp('dataProp', new data());

@Entry
@Component
struct Index {
  @StorageLink('numProp') numProp: number = 48;
  @StorageLink('dataProp') dataProp: data = new data();

  build() {
    Column() {
      // The current result is saved when the application exits. After the restart, the last saved result is displayed.
      Text(`numProp: ${this.numProp}`)
        .onClick(() => {
          this.numProp += 1;
        })
        .fontSize(30)

      // The current result is saved when the application exits. After the restart, the last saved result is displayed.
      Text(`dataProp.name: ${this.dataProp.name}`)
        .onClick(() => {
          this.dataProp.name += 'a';
        })
        .fontSize(30)
      // The current result is saved when the application exits. After the restart, the last saved result is displayed.
      Text(`dataProp.id: ${this.dataProp.id}`)
        .onClick(() => {
          this.dataProp.id += 1;
        })
        .fontSize(30)

    }
    .width('100%')
  }
}
```

V2:

This example demonstrates:
- Migrating persisted data from PersistentStorage (V1) to PersistenceV2 (V2). In V2, properties decorated with \@Trace are automatically persisted, while non-\@Trace decorated properties require manual **save** calls for persistence.
- The **move** function and the components to display are placed in the same .ets file in this example. You can define your own **move** functions and place them in appropriate locations for unified migration operations.
```ts
// Migrate to globalConnect.
import { PersistenceV2, Type } from '@kit.ArkUI';

// Register a callback for serialization failure.
PersistenceV2.notifyOnError((key: string, reason: string, msg: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});

class Data {
  name: string = 'ZhangSan';
  id: number = 0;
}

@ObservedV2
class V2Data {
  @Trace name: string = '';
  @Trace Id: number = 1;
}

@ObservedV2
export class Sample {
  // For complex objects, use the @Type decorator to ensure successful serialization.
  @Type(V2Data)
  @Trace num: number = 1;
  @Trace V2: V2Data = new V2Data();
}

// Auxiliary data used to determine whether data migration is complete.
@ObservedV2
class StorageState {
  @Trace isCompleteMoving: boolean = false;
}

function move() {
  let movingState = PersistenceV2.globalConnect({type: StorageState, defaultCreator: () => new StorageState()})!;
  if (!movingState.isCompleteMoving) {
    PersistentStorage.persistProp('numProp', 47);
    PersistentStorage.persistProp('dataProp', new Data());
    let num = AppStorage.get<number>('numProp')!;
    let V1Data = AppStorage.get<Data>('dataProp')!;
    PersistentStorage.deleteProp('numProp');
    PersistentStorage.deleteProp('dataProp');

    // Create the corresponding V2 data.
    let migrate = PersistenceV2.globalConnect({type: Sample, key: 'connect2', defaultCreator: () => new Sample()})!;  // You can use the default constructor.
    // Assign values. Properties decorated with @Trace are automatically saved. For non-@Trace objects, you can call save() to save the data, for example, PersistenceV2.save('connect2').
    migrate.num = num;
    migrate.V2.name = V1Data.name;
    migrate.V2.Id = V1Data.id;

    // Set the migration flag to true.
    movingState.isCompleteMoving = true;
  }
}

move();

@Entry
@ComponentV2
struct Page1 {
  @Local refresh: number = 0;
  // Store data with key: connect2.
  @Local p: Sample = PersistenceV2.globalConnect({type: Sample, key:'connect2', defaultCreator:() => new Sample()})!;

  build() {
    Column({space: 5}) {
      // The current result is saved when the application exits. After the restart, the last saved result is displayed.
      Text(`numProp: ${this.p.num}`)
        .onClick(() => {
          this.p.num += 1;
        })
        .fontSize(30)

      // The current result is saved when the application exits. After the restart, the last saved result is displayed.
      Text(`dataProp.name: ${this.p.V2.name}`)
        .onClick(() => {
          this.p.V2.name += 'a';
        })
        .fontSize(30)
      // The current result is saved when the application exits. After the restart, the last saved result is displayed.
      Text(`dataProp.id: ${this.p.V2.Id}`)
        .onClick(() => {
          this.p.V2.Id += 1;
        })
        .fontSize(30)
    }
    .width('100%')
  }
}
```

## Gradual Migration from V1 to V2

For large applications already using V1, a complete one-time migration to V2 is often impractical. Instead, migration typically occurs incrementally by components and modules, resulting in the coexistence of both V1 and V2 components.

A typical scenario is as follows:
- The parent component is written using V1 state management (\@Component with \@LocalStorageLink as the data source).
- The child component is written using V2 state management (\@ComponentV2 with \@Param to receive data).

In this case, migration can be achieved using the following strategy:
- Declare a class decorated with \@ObservedV2 to encapsulate V1 data.
- Create a bridge component (\@Component) between the V1 parent (\@Component) and the V2 child (\@ComponentV2).
- At the bridge layer:
    - To synchronize data from V1 to V2, use the \@Watch listener to update properties in the class decorated with \@ObservedV2.
    - To synchronize data from V2 to V1, declare **Monitor** in the class decorated with \@ObservedV2 and use LocalStorage APIs for propagating changes back to V1 state variables.

The following is an example:
```ts
let storage: LocalStorage = new LocalStorage();

@ObservedV2
class V1StorageData {
  @Trace title: string = 'V1OldComponent'

  @Monitor('title')
  onStrChange(monitor: IMonitor) {
    monitor.dirty.forEach((path: string) => {
      console.info(`${path} changed from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`)
      if (path === 'title') {
        storage.setOrCreate('title', this.title);
      }
    })
  }
}

let v1Data: V1StorageData = new V1StorageData();

@Entry(storage)
@Component
struct V1OldComponent {
  @LocalStorageLink('title') title: string = 'V1OldComponent';

  build() {
    Column() {
      Text(`V1OldComponent: ${this.title}`)
        .fontSize(20)
        .onClick(() => {
          this.title = 'new value from V1OldComponent';
        })
      // Define a bridge \@Component for synchronizing variables between V1 and V2.
      Bridge()
    }
  }
}


@Component
struct Bridge {
  @LocalStorageLink('title') @Watch('titleWatch') title: string = 'Bridge';

  titleWatch() {
    v1Data.title = this.title;
  }

  build() {
    NewV2Component()
  }
}

@ComponentV2
struct NewV2Component {
  build() {
    Column() {
      Text(`NewV2Component: ${v1Data.title}`)
        .fontSize(20)
        .onClick(() => {
          v1Data.title = 'NewV2Component';
        })
    }
  }
}
```

## Other Migration Scenarios

### Scrollable Components

**List**

You can use [ChildrenMainSize](../../reference/apis-arkui/arkui-ts/ts-container-list.md#childrenmainsize12) to set the size of child components along the main axis of a **List** component.

V1:

In V1, you can use [\@State](./arkts-state.md) to observe API calls.

The following is an example:

```ts
@Entry
@Component
struct ListExample {
  private arr: Array<number> = new Array(10).fill(0);
  private scroller: ListScroller = new ListScroller();
  @State listSpace: number = 10;
  @State listChildrenSize: ChildrenMainSize = new ChildrenMainSize(100);

  build() {
    Column() {
      Button('change Default').onClick(() => {
        this.listChildrenSize.childDefaultSize += 10;
      })

      Button('splice 5').onClick(() => {
        this.listChildrenSize.splice(0, 5, [100, 100, 100, 100, 100]);
      })

      Button('update 5').onClick(() => {
        this.listChildrenSize.update(0, 200);
      })

      List({ space: this.listSpace, scroller: this.scroller }) {
        ForEach(this.arr, (item: number) => {
          ListItem() {
            Text(`item-` + item)
          }.backgroundColor(Color.Pink)
        })
      }
      .childrenMainSize(this.listChildrenSize) // 10
    }
  }
}
```

V2:

In V2, [\@Local](./arkts-new-local.md) can only observe changes to the variable itself, but not its top-level internal changes. In addition, because **ChildrenMainSize** is defined by the framework, you cannot decorate its properties with [\@Trace](./arkts-new-observedV2-and-trace.md). You can use the [makeObserved](./arkts-new-makeObserved.md) instead.

The following is an example:

```ts
import { UIUtils } from '@kit.ArkUI';

@Entry
@ComponentV2
struct ListExample {
  private arr: Array<number> = new Array(10).fill(0);
  private scroller: ListScroller = new ListScroller();
  listSpace: number = 10;
  // Use makeObserved to enable observation of ChildrenMainSize changes.
  listChildrenSize: ChildrenMainSize = UIUtils.makeObserved(new ChildrenMainSize(100));

  build() {
    Column() {
      Button('change Default').onClick(() => {
        this.listChildrenSize.childDefaultSize += 10;
      })

      Button('splice 5').onClick(() => {
        this.listChildrenSize.splice(0, 5, [100, 100, 100, 100, 100]);
      })

      Button('update 5').onClick(() => {
        this.listChildrenSize.update(0, 200);
      })

      List({ space: this.listSpace, scroller: this.scroller }) {
        ForEach(this.arr, (item: number) => {
          ListItem() {
            Text(`item-` + item)
          }.backgroundColor(Color.Pink)
        })
      }
      .childrenMainSize(this.listChildrenSize) // 10
    }
  }
}
```

**WaterFlow**

You can use [WaterFlowSections](../../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#waterflowsections12) to configure sections in a **WaterFlow** component.

Note that the length of array **arr** must match the total sum of **itemsCount** values across all **SectionOptions** in **WaterFlowSections**. Mismatch will prevent proper **WaterFlow** processing and cause UI re-render issues.

The following two examples show buttons **push option**, **splice option**, and **update option** are clicked in sequence.

V1:

In V1, you can use [\@State](./arkts-state.md) to observe API calls.

The following is an example:

```ts
@Entry
@Component
struct WaterFlowSample {
  @State colors: Color[] = [Color.Red, Color.Orange, Color.Yellow, Color.Green, Color.Blue, Color.Pink];
  @State sections: WaterFlowSections = new WaterFlowSections();
  scroller: Scroller = new Scroller();
  @State private arr: Array<number> = new Array(9).fill(0);
  oneColumnSection: SectionOptions = {
    itemsCount: 4,
    crossCount: 1,
    columnsGap: '5vp',
    rowsGap: 10,
  };
  twoColumnSection: SectionOptions = {
    itemsCount: 2,
    crossCount: 2,
  };
  lastSection: SectionOptions = {
    itemsCount: 3,
    crossCount: 3,
  };

  aboutToAppear(): void {
    let sectionOptions: SectionOptions[] = [this.oneColumnSection, this.twoColumnSection, this.lastSection];
    this.sections.splice(0, 0, sectionOptions);
  }

  build() {
    Column() {
      Text(`${this.arr.length}`)

      Button('push option').onClick(() => {
        let section: SectionOptions = {
          itemsCount: 1,
          crossCount: 1,
        };
        this.sections.push(section);
        this.arr.push(100);
      })

      Button('splice option').onClick(() => {
        let section: SectionOptions = {
          itemsCount: 8,
          crossCount: 2,
        };
        this.sections.splice(0, this.arr.length, [section]);
        this.arr = new Array(8).fill(10);
      })

      Button('update option').onClick(() => {
        let section: SectionOptions = {
          itemsCount: 8,
          crossCount: 2,
        };
        this.sections.update(1, section);
        this.arr = new Array(16).fill(1);
      })

      WaterFlow({ scroller: this.scroller, sections: this.sections }) {
        ForEach(this.arr, (item: number) => {
          FlowItem() {
            Text(`${item}`)
              .border({ width: 1 })
              .backgroundColor(this.colors[item % 6])
              .height(30)
              .width(50)
          }
        })
      }
    }
  }
}
```

V2:

In V2, [\@Local](./arkts-new-local.md) can only observe changes to the variable itself, but not its top-level internal changes. In addition, because **WaterFlowSections** is defined by the framework, you cannot decorate its properties with [\@Trace](./arkts-new-observedV2-and-trace.md). You can use [makeObserved](./arkts-new-makeObserved.md) instead.

The following is an example:

```ts
import { UIUtils } from '@kit.ArkUI';

@Entry
@ComponentV2
struct WaterFlowSample {
  colors: Color[] = [Color.Red, Color.Orange, Color.Yellow, Color.Green, Color.Blue, Color.Pink];
  // Use makeObserved to enable observation of WaterFlowSections changes.
  sections: WaterFlowSections = UIUtils.makeObserved(new WaterFlowSections());
  scroller: Scroller = new Scroller();
  @Local private arr: Array<number> = new Array(9).fill(0);
  oneColumnSection: SectionOptions = {
    itemsCount: 4,
    crossCount: 1,
    columnsGap: '5vp',
    rowsGap: 10,
  };
  twoColumnSection: SectionOptions = {
    itemsCount: 2,
    crossCount: 2,
  };
  lastSection: SectionOptions = {
    itemsCount: 3,
    crossCount: 3,
  };

  aboutToAppear(): void {
    let sectionOptions: SectionOptions[] = [this.oneColumnSection, this.twoColumnSection, this.lastSection];
    this.sections.splice(0, 0, sectionOptions);
  }

  build() {
    Column() {
      Text(`${this.arr.length}`)

      Button('push option').onClick(() => {
        let section: SectionOptions = {
          itemsCount: 1,
          crossCount: 1,
        };
        this.sections.push(section);
        this.arr.push(100);
      })

      Button('splice option').onClick(() => {
        let section: SectionOptions = {
          itemsCount: 8,
          crossCount: 2,
        };
        this.sections.splice(0, this.arr.length, [section]);
        this.arr = new Array(8).fill(10);
      })

      Button('update option').onClick(() => {
        let section: SectionOptions = {
          itemsCount: 8,
          crossCount: 2,
        };
        this.sections.update(1, section);
        this.arr = new Array(16).fill(1);
      })

      WaterFlow({ scroller: this.scroller, sections: this.sections }) {
        ForEach(this.arr, (item: number) => {
          FlowItem() {
            Text(`${item}`)
              .border({ width: 1 })
              .backgroundColor(this.colors[item % 6])
              .height(30)
              .width(50)
          }
        })
      }
    }
  }
}
```

### Modifiers

**attributeModifier**

You can use [attributeModifier](../../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#attributemodifier) to dynamically set component attributes.

V1:

In V1, you can use [\@State](./arkts-state.md) to observe changes.

The following is an example:

```ts
class MyButtonModifier implements AttributeModifier<ButtonAttribute> {
  isDark: boolean = false;

  applyNormalAttribute(instance: ButtonAttribute): void {
    if (this.isDark) {
      instance.backgroundColor(Color.Black);
    } else {
      instance.backgroundColor(Color.Red);
    }
  }
}

@Entry
@Component
struct AttributeDemo {
  @State modifier: MyButtonModifier = new MyButtonModifier();

  build() {
    Row() {
      Column() {
        Button('Button')
          .attributeModifier(this.modifier)
          .onClick(() => {
            this.modifier.isDark = !this.modifier.isDark;
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

V2:

In V2, [\@Local](./arkts-new-local.md) can only observe changes to the variable itself, but not its top-level internal changes. To observe the attribute changes of **attributeModifier**, use [makeObserved](./arkts-new-makeObserved.md) instead.

The following is an example:

```ts
import { UIUtils } from '@kit.ArkUI';

class MyButtonModifier implements AttributeModifier<ButtonAttribute> {
  isDark: boolean = false;

  applyNormalAttribute(instance: ButtonAttribute): void {
    if (this.isDark) {
      instance.backgroundColor(Color.Black);
    } else {
      instance.backgroundColor(Color.Red);
    }
  }
}

@Entry
@ComponentV2
struct AttributeDemo {
  // Use makeObserved to enable property (this.modifier) observation for attributeModifier.
  modifier: MyButtonModifier = UIUtils.makeObserved(new MyButtonModifier());

  build() {
    Row() {
      Column() {
        Button('Button')
          .attributeModifier(this.modifier)
          .onClick(() => {
            this.modifier.isDark = !this.modifier.isDark;
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

**CommonModifier**

The component modifier is used to dynamically set component attributes. The following uses [CommonModifier](../../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#custom-modifier) as an example.

V1:

In V1, you can use [\@State](./arkts-state.md) to observe changes.

The following is an example.

```ts
import { CommonModifier } from '@ohos.arkui.modifier';

class MyModifier extends CommonModifier {
  applyNormalAttribute(instance: CommonAttribute): void {
    super.applyNormalAttribute?.(instance);
  }

  public setGroup1(): void {
    this.borderStyle(BorderStyle.Dotted);
    this.borderWidth(8);
  }

  public setGroup2(): void {
    this.borderStyle(BorderStyle.Dashed);
    this.borderWidth(8);
  }
}

@Component
struct MyImage1 {
  @Link modifier: CommonModifier;

  build() {
    // 'app.media.app_icon' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
    Image($r('app.media.app_icon'))
      .attributeModifier(this.modifier as MyModifier)
  }
}

@Entry
@Component
struct Index {
  @State myModifier: CommonModifier = new MyModifier().width(100).height(100).margin(10);
  index: number = 0;

  build() {
    Column() {
      Button($r('app.string.EntryAbility_label'))
        .margin(10)
        .onClick(() => {
          console.info('Modifier', 'onClick');
          this.index++;
          if (this.index % 2 === 1) {
            (this.myModifier as MyModifier).setGroup1();
            console.info('Modifier', 'setGroup1');
          } else {
            (this.myModifier as MyModifier).setGroup2();
            console.info('Modifier', 'setGroup2');
          }
        })

      MyImage1({ modifier: this.myModifier })
    }
    .width('100%')
  }
}
```

V2:

In V2, [\@Local](./arkts-new-local.md) can only observe changes to the variable itself, but not its top-level internal changes. Since [CommonModifier](../../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#custom-modifier) triggers UI re-renders through its property changes, [makeObserved](./arkts-new-makeObserved.md) must be used to enable proper observation.

The following is an example:

```ts
import { UIUtils } from '@kit.ArkUI';
import { CommonModifier } from '@ohos.arkui.modifier';

class MyModifier extends CommonModifier {
  applyNormalAttribute(instance: CommonAttribute): void {
    super.applyNormalAttribute?.(instance);
  }

  public setGroup1(): void {
    this.borderStyle(BorderStyle.Dotted);
    this.borderWidth(8);
  }

  public setGroup2(): void {
    this.borderStyle(BorderStyle.Dashed);
    this.borderWidth(8);
  }
}

@ComponentV2
struct MyImage1 {
  @Param @Require modifier: CommonModifier;

  build() {
    // 'app.media.app_icon' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
    Image($r('app.media.app_icon'))
      .attributeModifier(this.modifier as MyModifier)
  }
}

@Entry
@ComponentV2
struct Index {
  // Use makeObserved to enable observation of CommonModifier changes.
  @Local myModifier: CommonModifier = UIUtils.makeObserved(new MyModifier().width(100).height(100).margin(10));
  index: number = 0;

  build() {
    Column() {
      Button($r('app.string.EntryAbility_label'))
        .margin(10)
        .onClick(() => {
          console.info('Modifier', 'onClick');
          this.index++;
          if (this.index % 2 === 1) {
            (this.myModifier as MyModifier).setGroup1();
            console.info('Modifier', 'setGroup1');
          } else {
            (this.myModifier as MyModifier).setGroup2();
            console.info('Modifier', 'setGroup2');
          }
        })

      MyImage1({ modifier: this.myModifier })
    }
    .width('100%')
  }
}
```

**Component Modifier**

The component modifier is used to dynamically set component attributes. The following uses the **Text** component as an example.

V1:

In V1, you can use [\@State](./arkts-state.md) to observe changes.

The following is an example:

```ts
import { TextModifier } from '@ohos.arkui.modifier';

class MyModifier extends TextModifier {
  applyNormalAttribute(instance: TextModifier): void {
    super.applyNormalAttribute?.(instance);
  }

  public setGroup1(): void {
    this.fontSize(50);
    this.fontColor(Color.Pink);
  }

  public setGroup2(): void {
    this.fontSize(50);
    this.fontColor(Color.Gray);
  }
}

@Component
struct MyImage1 {
  @Link modifier: TextModifier;
  index: number = 0;

  build() {
    Column() {
      Text('Test')
        .attributeModifier(this.modifier as MyModifier)

      Button($r('app.string.EntryAbility_label'))
        .margin(10)
        .onClick(() => {
          console.info('Modifier', 'onClick');
          this.index++;
          if (this.index % 2 === 1) {
            (this.modifier as MyModifier).setGroup1();
            console.info('Modifier', 'setGroup1');
          } else {
            (this.modifier as MyModifier).setGroup2();
            console.info('Modifier', 'setGroup2');
          }
        })
    }
  }
}

@Entry
@Component
struct Index {
  @State myModifier: TextModifier = new MyModifier().width(100).height(100).margin(10);
  index: number = 0;

  build() {
    Column() {
      MyImage1({ modifier: this.myModifier })

      Button('replace whole')
        .margin(10)
        .onClick(() => {
          this.myModifier = new MyModifier().backgroundColor(Color.Orange);
        })
    }
    .width('100%')
  }
}
```

V2:

In V2, [\@Local](./arkts-new-local.md) can only observe its own changes, but cannot observe the top-level changes. You can use [makeObserved](./arkts-new-makeObserved.md) instead.

The following is an example:

```ts
import { UIUtils } from '@kit.ArkUI';
import { TextModifier } from '@ohos.arkui.modifier';

class MyModifier extends TextModifier {
  applyNormalAttribute(instance: TextModifier): void {
    super.applyNormalAttribute?.(instance);
  }

  public setGroup1(): void {
    this.fontSize(50);
    this.fontColor(Color.Pink);
  }

  public setGroup2(): void {
    this.fontSize(50);
    this.fontColor(Color.Gray);
  }
}

@ComponentV2
struct MyImage1 {
  @Param @Require modifier: TextModifier;
  index: number = 0;

  build() {
    Column() {
      Text('Test')
        .attributeModifier(this.modifier as MyModifier)

      Button($r('app.string.EntryAbility_label'))
        .margin(10)
        .onClick(() => {
          console.info('Modifier', 'onClick');
          this.index++;
          if (this.index % 2 === 1) {
            (this.modifier as MyModifier).setGroup1();
            console.info('Modifier', 'setGroup1');
          } else {
            (this.modifier as MyModifier).setGroup2();
            console.info('Modifier', 'setGroup2');
          }
        })
    }
  }
}

@Entry
@ComponentV2
struct Index {
  // Use makeObserved to enable observation of TextModifier changes.
  @Local myModifier: TextModifier = UIUtils.makeObserved(new MyModifier().width(100).height(100).margin(10));
  index: number = 0;

  build() {
    Column() {
      MyImage1({ modifier: this.myModifier })

      Button('replace whole')
        .margin(10)
        .onClick(() => {
          this.myModifier = UIUtils.makeObserved(new MyModifier().backgroundColor(Color.Orange));
        })
    }
    .width('100%')
  }
}
```
**AttributeUpdater**

[AttributeUpdater](../arkts-user-defined-extension-attributeUpdater.md) allows attributes to be directly applied to components, enabling UI updates without marking them as state variables.

V1:

In V1, you can change the **flag** property in **MyButtonModifier** to update the attributes bound to the **Button**. Because \@State supports observation of both the object itself and its top-level properties, simply decorating **AttributeUpdater** with \@State is enough to listen for changes and trigger updates.

```ts
// xxx.ets
import { AttributeUpdater } from '@kit.ArkUI';

class MyButtonModifier extends AttributeUpdater<ButtonAttribute> {
  flag: boolean = false;

  initializeModifier(instance: ButtonAttribute): void {
    instance.backgroundColor('#ff2787d9')
      .width('50%')
      .height(30)
  }

  applyNormalAttribute(instance: ButtonAttribute): void {
    if (this.flag) {
      instance.borderWidth(2);
    } else {
      instance.borderWidth(10);
    }
  }
}

@Entry
@Component
struct Index {
  @State modifier: MyButtonModifier = new MyButtonModifier();

  build() {
    Row() {
      Column() {
        Button('Button')
          .attributeModifier(this.modifier)
        Button('Update')
          .onClick(() => {
            this.modifier.flag = !this.modifier.flag;
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

V2:

Unlike in V1, \@Local in V2 only observes changes to the object itself. Therefore, **MyButtonModifier** must be decorated with \@ObservedV2, and the **flag** property must be decorated with \@Trace. In addition, **flag** must be accessed during component creation to establish its dependency with the **Button** component. In this scenario, it should be accessed in **initializeModifier** (as shown below); otherwise, the dependency will not be established.

```ts
// xxx.ets
import { AttributeUpdater } from '@kit.ArkUI';

@ObservedV2
class MyButtonModifier extends AttributeUpdater<ButtonAttribute> {
  @Trace flag: boolean = false;

  initializeModifier(instance: ButtonAttribute): void {
    // initializeModifier is called during component initialization. Accessing flag here ensures it is bound with the Button component.
    this.flag;
    instance.backgroundColor('#ff2787d9')
      .width('50%')
      .height(30)
  }

  applyNormalAttribute(instance: ButtonAttribute): void {
    if (this.flag) {
      instance.borderWidth(2);
    } else {
      instance.borderWidth(10);
    }
  }
}

@Entry
@ComponentV2
struct Index {
  // In V2, decorators only observe this layer, that is, changes when modifier is reassigned.
  @Local modifier: MyButtonModifier = new MyButtonModifier();

  build() {
    Row() {
      Column() {
        Button('Button')
          .attributeModifier(this.modifier)
        Button('Update')
          .onClick(() => {
            this.modifier.flag = !this.modifier.flag;
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
