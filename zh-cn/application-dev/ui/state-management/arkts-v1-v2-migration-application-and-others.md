# 应用内状态变量和其他场景迁移指导
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

本文档主要介绍应用内状态变量和其他场景迁移场景，包含以下场景。

| V1装饰器名/场景                | V2装饰器名                  |
|------------------------|--------------------------|
| [LocalStorage](./arkts-localstorage.md)                 | [\@ObservedV2](./arkts-new-observedV2-and-trace.md)[\@Trace](./arkts-new-observedV2-and-trace.md)   |
| [AppStorage](./arkts-appstorage.md)                | [AppStorageV2](./arkts-new-appstoragev2.md)  |
| [Environment](./arkts-environment.md)       | 调用Ability接口获取系统环境变量   |
| [PersistentStorage](./arkts-persiststorage.md)     | [PersistenceV2](./arkts-new-persistencev2.md)   |
| 存量迁移场景      | \@ObservedV2、\@Trace、[\@Monitor](./arkts-new-monitor.md) |
| 滑动组件场景      | [makeObserved](./arkts-new-makeObserved.md)|
| [Modifier](../arkts-user-defined-modifier.md)      |[makeObserved](./arkts-new-makeObserved.md)、\@ObservedV2、\@Trace|


## 各装饰器迁移示例

### LocalStorage->\@ObservedV2/\@Trace
**迁移规则**

LocalStorage的目的是实现页面间的状态变量共享。由于V1状态变量和View层耦合，开发者难以自主实现页面间状态变量的共享，因此框架提供了该能力。
状态管理V2将状态变量的观察能力内嵌到数据本身，不再和View层耦合。因此，不再需要类似LocalStorage的能力，可以使用创建\@ObservedV2和\@Trace装饰类的实例，开发者需自行import和export，实现状态变量的页面间共享。

**示例**

**基本场景**

V1:

通过windowStage.[loadContent](../../reference/apis-arkui/arkts-apis-window-Window.md#loadcontent9)和this.getUIContext().[getSharedLocalStorage](../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getsharedlocalstorage12)接口实现页面间的状态变量共享。
<!-- @[Internal_@ObservedV2_@Trace_V1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/Internal@ObservedV2@TraceV1/EntryAbility.ets) -->

``` TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  para: Record<string, number> = { 'count': 47 };
  public storage: LocalStorage = new LocalStorage(this.para);

  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/Page1', this.storage);
  }
}
```
在下面的示例中，使用\@LocalStorageLink，可以将开发者本地的修改同步回LocalStorage中。

<!-- @[Internal_@ObservedV2_@Trace_V1_pag1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/Internal@ObservedV2@TraceV1/pages/Page1.ets) -->

``` TypeScript
// Page1.ets
// 预览器上不支持获取页面共享的LocalStorage实例。
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

<!-- @[Internal_@ObservedV2_@Trace_V1_pag2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/Internal@ObservedV2@TraceV1/pages/Page2.ets) -->

``` TypeScript
// Page2.ets
@Builder
export function Page2Builder() {
  Page2()
}

// Page2组件获得了父亲Page1组件的LocalStorage实例
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
使用Navigation时，需要添加配置系统路由表文件src/main/resources/base/profile/route_map.json，并替换pageSourceFile为Page2页面的路径，并且在module.json5中添加："routerMap": "$profile:route_map"。
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

- 声明\@ObservedV2装饰的MyStorage类，并import到需要使用的页面中。
- 声明被\@Trace的属性作为页面间共享的可观察的数据。

<!-- @[Internal_@ObservedV2_@Trace_V2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/Internal@ObservedV2@TraceV2/storage.ets) -->

``` TypeScript
@ObservedV2
export class MyStorage {
  public static singleton_: MyStorage;

  static instance() {
    if (!MyStorage.singleton_) {
      MyStorage.singleton_ = new MyStorage();
    }
    return MyStorage.singleton_;
  }
  // 页面级UI状态存储的数字
  @Trace public count: number = 47;
}
```

<!-- @[Internal_@ObservedV2_@Trace_V2_pag1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/Internal@ObservedV2@TraceV2/Page1.ets) -->

``` TypeScript
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

<!-- @[Internal_@ObservedV2_@Trace_V2_pag2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/Internal@ObservedV2@TraceV2/Page2.ets) -->

``` TypeScript
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
使用Navigation时，需要添加配置系统路由表文件src/main/resources/base/profile/route_map.json，并替换pageSourceFile为Page2页面的路径，并且在module.json5中添加："routerMap": "$profile:route_map"。
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

如果开发者需要实现类似于\@LocalStorageProp的效果，但希望本地的修改不同步回LocalStorage中，可参考以下示例：
- 在`Page1`中改变`count`值，由于count被\@LocalStorageProp装饰的，因此其更改仅在本地生效，不会同步到LocalStorage。
- 点击`push to Page2`，跳转到`Page2`。由于在`Page1`中改变`count`值不会同步到LocalStorage，因此`Page2`中的Text组件仍显示初始值47。
- 点击`change Storage Count`，调用LocalStorage的setOrCreate，改变`count`对应的值，并通知所有绑定该key的变量。

<!-- @[Internal_@Trace_setOrCreate_V1_pag1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/Internal@TracesetOrCreateV1/Page1.ets) -->

``` TypeScript
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

<!-- @[Internal_@Trace_setOrCreate_V1_pag2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/Internal@TracesetOrCreateV1/Page2.ets) -->

``` TypeScript
// Page2.ets
import { storage } from './Page1'

@Builder
export function Page2Builder() {
  Page2()
}

// Page2组件获得了父亲Page1组件的LocalStorage实例
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
在V2中，可以借助\@Local和\@Monitor实现类似的效果。
- \@Local装饰的`count`变量为组件本地的值，其改变不会同步回`storage`。
- \@Monitor监听`storage.count`的变化，当`storage.count`改变时，在\@Monitor的回调里改变本地\@Local的值。

<!-- @[Internal_@ObservedV2_@Trace_V2_pag1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/Internal@TracesetOrCreateV2/Page1.ets) -->

``` TypeScript
// Page1.ets
import { MyStorage } from './storage';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;

@Entry
@ComponentV2
struct Page1 {
  storage: MyStorage = MyStorage.instance();
  pageStack: NavPathStack = new NavPathStack();
  @Local count: number = this.storage.count;

  @Monitor('storage.count')
  onCountChange(mon: IMonitor) {
    hilog.info(DOMAIN, 'testTag', '%{public}s', `Page1 ${mon.value()?.before} to ${mon.value()?.now}`);
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

<!-- @[Internal_@ObservedV2_@Trace_V2_pag2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/Internal@TracesetOrCreateV2/Page2.ets) -->

``` TypeScript
// Page2.ets
import { MyStorage } from './storage';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;

@Builder
export function Page2Builder() {
  Page2()
}

@ComponentV2
struct Page2 {
  storage: MyStorage = MyStorage.instance();
  pathStack: NavPathStack = new NavPathStack();
  // 已经存储的页面级UI状态数字
  @Local count: number = this.storage.count;

  @Monitor('storage.count')
  onCountChange(mon: IMonitor) {
    hilog.info(DOMAIN, 'testTag', '%{public}s', `Page2 ${mon.value()?.before} to ${mon.value()?.now}`);
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

**自定义组件接收LocalStorage实例场景**

为了配合Navigation的场景，LocalStorage支持作为自定义组件的入参，传递给以当前自定义组件为根节点的所有子自定义组件。
对于该场景，V2可以使用创建多个全局\@ObservedV2和\@Trace装饰类的实例进行替代。

V1:

<!-- @[Internal_Trace_customize_V1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalTraceCustomize/InternalTraceCustomizeV1.ets) -->

``` TypeScript
let localStorageA: LocalStorage = new LocalStorage();
localStorageA.setOrCreate('propA', 'propA');

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
      // 传递不同的LocalStorage实例
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
              this.pageInfo.pushPath({ name: 'pageOne' }); //将name指定的NavDestination页面信息入栈
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
  @LocalStorageLink('propA') propA: string = 'Hello World';

  build() {
    NavDestination() {
      Column() {
        // 显示'propA'
        NavigationContentMsgStack()
        // 显示'propA'
        Text(`${this.propA}`)
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
  @LocalStorageLink('PropB') propB: string = 'Hello World';

  build() {
    NavDestination() {
      Column() {
        // 显示'Hello'，当前LocalStorage实例localStorageB没有propA对应的值，使用本地默认值'Hello'
        NavigationContentMsgStack()
        // 显示'PropB'
        Text(`${this.propB}`)
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
  @LocalStorageLink('PropC') propC: string = 'pageThreeStack';

  build() {
    NavDestination() {
      Column() {
        // 显示'Hello'，当前LocalStorage实例localStorageC没有propA对应的值，使用本地默认值'Hello'
        NavigationContentMsgStack()
        // 显示'PropC'
        Text(`${this.propC}`)
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
  @LocalStorageLink('propA') propA: string = 'Hello';

  build() {
    Column() {
      Text(`${this.propA}`)
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
    }
  }
}
```
V2：

声明\@ObservedV2装饰的class代替LocalStorage。其中LocalStorage的key可以用\@Trace装饰的属性代替。
<!-- @[Internal_Trace_customize_V2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalTraceCustomize/storage.ets) -->

``` TypeScript
@ObservedV2
export class MyStorageA {
  @Trace public propA: string = 'Hello';

  constructor(propA?: string) {
    this.propA = propA ? propA : this.propA;
  }
}

@ObservedV2
export class MyStorageB extends MyStorageA {
  @Trace public propB: string = 'Hello';

  constructor(propB: string) {
    super();
    this.propB = propB;
  }
}

@ObservedV2
export class MyStorageC extends MyStorageA {
  @Trace public propC: string = 'Hello';

  constructor(propC: string) {
    super();
    this.propC = propC;
  }
}
```

在`pageOneStack`、`pageTwoStack`和`pageThreeStack`组件内分别创建`MyStorageA`、`MyStorageB`、`MyStorageC`的实例，并通过\@Param传递给其子组件`NavigationContentMsgStack`，从而实现类似LocalStorage实例在子组件树上共享的能力。

<!-- @[Internal_Trace_Customize_Param](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalTraceCustomize/Index.ets) -->

### AppStorage->AppStorageV2
上一小节中，对于创建全局\@ObserveV2和\@Trace装饰实例的改造不适用于跨Ability的数据共享，可以使用AppStorageV2替代。

V1:

AppStorage与应用进程绑定，支持跨Ability数据共享。
在下面的示例中，使用\@StorageLink，可以使得开发者本地的修改同步回AppStorage中。

<!-- @[Internal_AppStorage_V1_one](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalAppStorageV1one.ets) -->

``` TypeScript
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
          bundleName: 'com.example.myapplication', // 替换成AppScope/app.json5里的bundleName
          abilityName: 'EntryAbility1'
        };
        this.context.startAbility(wantInfo);
      })
    }
  }
}
```

<!-- @[Internal_AppStorage_V1_two](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalAppStorageV1two.ets) -->

``` TypeScript
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
          bundleName: 'com.example.myapplication', // 替换成AppScope/app.json5里的bundleName
          abilityName: 'EntryAbility'
        };
        this.context.startAbility(wantInfo);
      })
    }
  }
}
```
V2:

可以使用AppStorageV2实现跨Ability共享。
如下面示例：

<!-- @[Internal_AppStorage_V2_one](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalAppStorageV2one.ets) -->

<!-- @[Internal_AppStorage_V2_two](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalAppStorageV2two.ets) -->

如果开发者需要实现类似于\@StorageProp的效果，希望本地的修改不同步回AppStorage，而AppStorage的变化能够通知到使用\@StorageProp装饰器的组件，可以参考以下示例对比。

V1：

<!-- @[Internal_StorageProp_V1_one](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalStoragePropV1one.ets) -->

<!-- @[Internal_StorageProp_V1_two](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalStoragePropV1two.ets) -->

V2:

开发者可以使用\@Monitor和\@Local实现类似效果，示例如下。

<!-- @[Internal_StorageProp_V2_one](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalStoragePropV2one.ets) -->

<!-- @[Internal_StorageProp_V2_two](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalStoragePropV2two.ets) -->

### Environment->调用Ability接口直接获取系统环境变量
V1中，开发者可以通过Environment来获取环境变量，但Environment获取的结果无法直接使用，需要配合AppStorage才能得到对应环境变量的值。
在切换V2的过程中，开发者无需再通过Environment来获取环境变量，可以直接通过[UIAbilityContext的config属性](../../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#uiabilitycontext-1)获取系统环境变量。

V1:

以`languageCode`为例。
<!-- @[Internal_Environment_V1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalEnvironmentV1.ets) -->

V2:

封装Env类型来传递多个系统环境变量。

<!-- @[Internal_Environment_V2_one](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/pages/Env.ets) -->
在`onCreate`里获取需要的系统环境变量：
<!-- @[Internal_Environment_V2_two](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalEnvironmentV2/EntryAbility.ets) -->
在页面中获取当前Env的值。
<!-- @[Internal_Environment_V2_three](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalEnvironmentV2/Index.ets) -->

### PersistentStorage->PersistenceV2
V1中PersistentStorage提供了持久化UI数据的能力，而V2则提供了更加方便使用的PersistenceV2接口来替代它。
- PersistentStorage持久化的触发时机依赖AppStorage的观察能力，且与AppStorage耦合，开发者无法自主选择写入或读取持久化数据的时机。
- PersistentStorage使用序列化和反序列化，并没有传入类型，所以在持久化后，会丢失其类型，且对象的属性方法不能持久化。

对于PersistenceV2：
- 与PersistenceV2关联的\@ObservedV2对象，其\@Trace属性的变化，会触发整个关联对象的自动持久化。
- 开发者也可以调用[PersistenceV2.save](../../reference/apis-arkui/js-apis-StateManagement.md#save)和[PersistenceV2.globalConnect](./arkts-new-persistencev2.md#使用globalconnect存储数据)接口来手动触发持久化写入和读取。

V1:

<!-- @[Internal_Persistent_Storage_V1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalPersistentStorageV1.ets) -->

V2:

下面的案例展示了：
- 将`PersistentStorage`的持久化数据迁移到V2的PersistenceV2中。V2对被\@Trace标记的数据可以自动持久化，对于非\@Trace数据，需要手动调用save进行持久化。
- 示例中的move函数和需要显示的组件放在了一个ets中，开发者可以定义自己的move函数，并放入合适的位置进行统一迁移操作。
<!-- @[Internal_Persistent_Storage_V2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalPersistentStorageV2.ets) -->

## V1现有功能向V2的逐步迁移场景

对于已经使用V1开发的大型应用，通常难以一次性从V1迁移到V2，而是需要分批次、分组件地逐步迁移，这就必然会带来V1和V2的混用。

这种场景，通常父组件使用状态管理V1，而迁移的子组件使用状态管理V2。为了模拟这种场景，我们举出以下示例：
- 父组件是\@Component，数据源是\@LocalStorageLink。
- 子组件是\@ComponentV2，使用\@Param接受数据源的数据。

可以通过以下策略进行迁移：
- 声明一个\@ObservedV2装饰的class来封装V1的数据。
- 在\@Component和\@ComponentV2之间，定义一个桥接的\@Component自定义组件。
- 在桥接层：
    - V1->V2的数据同步，可通过\@Watch的监听触发\@ObservedV2装饰的class的属性的赋值。
    - V2->V1的数据同步，可通过在\@ObservedV2装饰的class里声明Monitor，通过LocalStorage的API反向通知给V1状态变量。

具体示例如下：
<!-- @[Internal_Gradual_Migration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalGradualMigration.ets) -->

## 其他迁移场景

### 滑动组件

**List**

开发者可以通过[ChildrenMainSize](../../reference/apis-arkui/arkui-ts/ts-container-list.md#childrenmainsize12)来设置List的子组件在主轴方向的大小信息。

V1：

在状态管理V1中，可以通过[\@State](./arkts-state.md)装饰观察其api调用。

具体示例如下：

<!-- @[Internal_Other_Migrations_List_V1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalOtherMigrationsListV1.ets) -->

V2：

在状态管理V2中，[\@Local](./arkts-new-local.md)只能观察本身的变化，无法观察第一层的变化，而由于ChildrenMainSize定义在框架中，开发者无法使用[\@Trace](./arkts-new-observedV2-and-trace.md)来标注ChildrenMainSize的属性。可以使用[makeObserved](./arkts-new-makeObserved.md)替代。

具体示例如下：

<!-- @[Internal_Other_Migrations_List_V2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalOtherMigrationsListV2.ets) -->

**WaterFlow**

开发者可以通过[WaterFlowSections](../../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#waterflowsections12)来设置WaterFlow瀑布流分组信息。

需要注意的是，数组arr的长度需要与WaterFlowSections的所有SectionOptions的itemsCount总和一致，否则WaterFlow无法处理，导致UI不刷新。

以下两个示例请按照'push option' -> 'splice option' -> 'update option'的顺序进行点击。

V1：

在状态管理V1中，可以通过[\@State](./arkts-state.md)装饰观察其api调用。

具体示例如下：

<!-- @[Internal_Other_Migrations_WaterFlow_V1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalOtherMigrationsWaterFlowV1.ets) -->

V2：

在状态管理V2中，[\@Local](./arkts-new-local.md)只能观察本身的变化，无法观察第一层的变化，由于WaterFlowSections定义在框架中，开发者无法使用[\@Trace](./arkts-new-observedV2-and-trace.md)标注其属性，此时可以使用[makeObserved](./arkts-new-makeObserved.md)替代。

具体示例如下：

<!-- @[Internal_Other_Migrations_WaterFlow_V2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalOtherMigrationsWaterFlowV2.ets) -->

### Modifier

**attributeModifier**

开发者可以通过[attributeModifier](../../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#attributemodifier)动态设置组件的属性方法。

V1：

在状态管理V1中，可以通过[\@State](./arkts-state.md)装饰观察其变化。

具体示例如下：

<!-- @[Internal_attribute_Modifier_V1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalattributeModifierV1.ets) -->

V2：

在状态管理V2中，[\@Local](./arkts-new-local.md)只能观察本身的变化，无法观察第一层的变化，如果要观察attributeModifier的属性变化，可以使用[makeObserved](./arkts-new-makeObserved.md)替代。

具体示例如下：

<!-- @[Internal_attribute_Modifier_V2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalattributeModifierV2.ets) -->

**CommonModifier**

动态设置组件的属性类。以[CommonModifier](../../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#自定义modifier)为例。

V1：

在状态管理V1中，可以通过[\@State](./arkts-state.md)装饰观察其变化。

具体实例如下：

<!-- @[Internal_Common_Modifier_V1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalCommonModifierV1.ets) -->

V2：

在状态管理V2中，[\@Local](./arkts-new-local.md)只能观察本身的变化，无法观察第一层的变化，又因为[CommonModifier](../../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#自定义modifier)在框架内是通过其属性触发刷新，此时可以使用[makeObserved](./arkts-new-makeObserved.md)替代。

具体示例如下：

<!-- @[Internal_Common_Modifier_V2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalCommonModifierV2.ets) -->

**组件Modifier**

动态设置组件的属性类。以Text组件为例。

V1：

在状态管理V1中，可以通过[\@State](./arkts-state.md)装饰观察其变化。

具体示例如下：

<!-- @[Internal_Module_Modifier_V1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalModuleModifierV1.ets) -->

V2：

但在状态管理V2中，[\@Local](./arkts-new-local.md)只能观察本身的变化，无法观察第一层的变化，此时可以使用[makeObserved](./arkts-new-makeObserved.md)替代。

具体示例如下：

<!-- @[Internal_Module_Modifier_V2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalModuleModifierV2.ets) -->
**AttributeUpdater**

[AttributeUpdater](../arkts-user-defined-extension-attributeUpdater.md)可以将属性直接设置给组件，无需标记为状态变量即可直接触发UI更新。

V1：

在状态管理V1中，开发者希望通过修改`MyButtonModifier`的`flag`来改变绑定在Button上的属性。由于状态管理V1的\@State装饰器支持自身及第一层对象属性的观察能力，因此只需用\@State装饰`AttributeUpdater`，即可监听其变化并触发属性更新。

<!-- @[Internal_Attribute_Updater_V1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalAttributeUpdaterV1.ets) -->

V2：

与状态管理V1不同，状态管理V2的\@Local仅观察自身变化，因此`MyButtonModifier`需添加\@ObservedV2装饰器，`flag`需要被\@Trace装饰，并且需要在组件创建过程中读取`flag`以建立其与Button组件的联系。在`AttributeUpdater`场景中，需在`initializeModifier`中读取`flag`（如示例所示），否则无法建立关联。

<!-- @[Internal_Attribute_Updater_V2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/internalmigrate/InternalAttributeUpdaterV2.ets) -->