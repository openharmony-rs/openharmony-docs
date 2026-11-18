# RecoverableStorage: 可恢复的UI状态存储
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

为了增强状态管理框架在应用被资源管控终止或异常退出场景下的数据恢复能力，开发者可以使用[RecoverableStorage](../../reference/apis-arkui/js-apis-stateManagement.md#recoverablestorage)自动保存与恢复状态变量。

RecoverableStorage是应用程序中的可选单例对象。此对象的作用是：当应用被系统以资源管控方式终止（如低内存）或因JS_ERROR、APP_FREEZE异常退出时，自动保存所声明的状态变量的当前值；应用被系统重新拉起后，配合页面栈和路由栈的恢复功能，同时读取此前保存的状态变量值，实现UI无感恢复。

>**说明：**
>
>RecoverableStorage从API版本26.1.0开始支持。
>
>从API版本26.1.0开始，该接口支持在原子化服务中使用。

## 概述

RecoverableStorage是应用启动时创建的单例，提供资源管控终止/异常退出场景下状态变量的声明、保存与恢复能力。开发者通过[connect](../../reference/apis-arkui/js-apis-stateManagement.md#connect-1)声明变量后，系统在存盘时机自动提取当前值；应用被系统恢复重启（系统携带恢复参数自动拉起，区别于手动打开）后，再次执行connect即可读回保存的值。

与[PersistenceV2](./arkts-new-persistencev2.md)的持久化模型不同，RecoverableStorage采用快照模型：仅在系统存盘时机（应用退后台时预备存档/异常发生时存档）一次性提取当前值，而非每次变量变更即写入磁盘。他们的差异如下：

| 维度 | RecoverableStorage（快照） | PersistenceV2（实时持久化） |
|------|---------------------------|----------------------|
| 写入时机 | 仅系统存盘时机（退后台/异常退出） | 每次变量变更即写盘 |
| 无操作时的磁盘写入 | 无 | 变量每次变更都会写入 |
| 数据生命周期 | 临时（上滑删除/重启后清除） | 持久（写入磁盘） |
| 适用场景 | 页面草稿、滚动位置等轻量UI状态 | 用户设置、历史记录等持久数据 |

## 使用前提

在使能应用的恢复能力后，才可正常使用RecoverableStorage的恢复功能，否则RecoverableStorage中的数据将只停留在运行时内存中，无保存恢复能力。

根据场景不同，可以通过以下方式使能应用恢复：

### 使能资源管控终止恢复

在UIAbility的onCreate中调用[setRestoreEnabled](../../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#setrestoreenabled14)(true)开启应用的恢复能力：

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onCreate(): void {
    // 开启应用的恢复能力，未开启时应用被终止后不会恢复
    this.context.setRestoreEnabled(true);
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/Index');
  }
}
```

完成上述配置后，应用退后台时自动存档；被资源管控终止后，从最近任务重新打开即恢复。

### 使能异常退出恢复

在UIAbility的onCreate中调用[restoreWindowStage](../../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#restorewindowstage)初始化页面内容存储，以及在AbilityStage的onCreate中调用[enableAppRecovery](../../reference/apis-ability-kit/js-apis-app-ability-appRecovery.md#apprecoveryenableapprecovery)：

>**注意：**
>
>[enableAppRecovery](../../reference/apis-ability-kit/js-apis-app-ability-appRecovery.md#apprecoveryenableapprecovery)必须在AbilityStage的onCreate（应用级入口）调用，否则异常退出场景不保存、不自动重启。

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onCreate(): void {
    // 初始化页面内容存储，异常退出后的恢复依赖此调用
    this.context.restoreWindowStage(new LocalStorage());
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/Index');
  }
}
```

```ts
// MyAbilityStage.ets（module.json5中srcEntry指向该文件）
import { AbilityStage, appRecovery } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onCreate(): void {
    // 必须在AbilityStage.onCreate调用，写在UIAbility.onCreate会因晚于配置固化而无效
    appRecovery.enableAppRecovery(
      appRecovery.RestartFlag.ALWAYS_RESTART,
      appRecovery.SaveOccasionFlag.SAVE_WHEN_ERROR | appRecovery.SaveOccasionFlag.SAVE_WHEN_BACKGROUND,
      appRecovery.SaveModeFlag.SAVE_WITH_FILE
    );
  }
}
```

## 使用限制

1. 仅支持对象类型（`T extends object`），不支持基本类型。传入number、string、boolean等基本类型会抛出[错误码](../../reference/apis-arkui/errorcode-stateManagement.md)。类的成员属性支持基本类型与联合类型（如`string | null`、`number | undefined`），`null`/`undefined`属性值可正常保存与恢复。

2. 单实例可保存的序列化数据上限为150KB，推荐数据总量不超过100KB。超出上限的数据不会被保存，系统侧将输出错误日志提示开发者。若connect时传入了`notifyOnError`，也会通过`notifyOnError`上报错误信息，不会导致应用崩溃。

3. 须在自定义组件内调用，[component](../../reference/apis-arkui/js-apis-stateManagement.md#recoverableconnectoptionst-s)参数传`this`（组件实例）。运行时校验component有效性，持有有效组件实例时在组件外调用亦可连接成功。

4. [多实例](../../application-models/uiability-launch-type.md)（multiton启动模式的各窗口）各自独立分区，同一key在不同窗口互不干扰。

5. 不支持[PixelMap](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md)、NativePointer、[ArrayList](../../reference/apis-arkts/js-apis-arraylist.md)等非内置类型。

6. 对象之间相互引用（循环引用）时，仅当环上每个嵌套类字段在声明时初始化（如`peer: Node = new Node()`）或使用[\@Type](./arkts-new-observedV2-and-trace.md)标注类型后才能恢复；初始化为`null`且未标注\@Type的字段无法确定类型，该变量恢复时回退为默认值，并在connect时传入`notifyOnError`的情况下通过`notifyOnError`上报。

7. 典型用法为修改所连接对象的属性。对状态变量整体重新赋值（如`this.draft = new Draft()`）会使已保存的引用失效，此后的修改不被跟踪。

## 使用场景

### 保存普通对象与\@Observed装饰的对象

普通类与[\@Observed](./arkts-observed-and-objectlink.md)装饰的类均可作为可恢复状态变量的类型。嵌套成员在声明时创建实例，恢复时数据直接填充到这些已创建的实例中，实例的类信息不丢失（instanceof判断仍成立）。

```ts
import { RecoverableStorage } from '@kit.ArkUI';

// 普通类
class Draft {
  text: string = '';

  constructor(text: string = '') {
    this.text = text;
  }
}

@Entry
@Component
struct MyPage {
  // 连接可恢复状态变量
  @State draft: Draft = RecoverableStorage.connect({
    component: this,   // 传入当前组件实例
    type: Draft,
    defaultCreator: (): Draft => new Draft()
  });

  build() {
    Column() {
      TextInput({ text: this.draft.text })
        .onChange((v: string) => {
          this.draft.text = v;
        })
    }
  }
}
```

\@Observed装饰的类的使用方式相同：

```ts
import { RecoverableStorage } from '@kit.ArkUI';

// @Observed装饰的类
@Observed
class Cart {
  count: number = 0;
}

@Entry
@Component
struct CartPage {
  // 连接@Observed装饰的对象
  @State cart: Cart = RecoverableStorage.connect({
    component: this,   // 传入当前组件实例
    type: Cart,
    defaultCreator: (): Cart => new Cart()
  });

  build() {
    Column() {
      Text(`count: ${this.cart.count}`)
        .onClick(() => {
          this.cart.count += 1;
        })
    }
  }
}
```

### 保存\@ObservedV2装饰的对象

[\@ObservedV2](./arkts-new-observedV2-and-trace.md)装饰的类配合[\@Trace](./arkts-new-observedV2-and-trace.md)与[\@Type](./arkts-new-observedV2-and-trace.md)使用，嵌套对象由\@Type元数据驱动重建。

```ts
import { RecoverableStorage, Type } from '@kit.ArkUI';

@ObservedV2
class Attachment {
  @Trace name: string = '';
}

// @ObservedV2装饰的类，嵌套成员使用@Type标注
@ObservedV2
class Envelope {
  @Trace title: string = '';
  @Type(Attachment)
  attach: Attachment = new Attachment();
}

@Entry
@ComponentV2
struct MyPage {
  // 连接可恢复状态变量
  @Local env: Envelope = RecoverableStorage.connect({
    component: this,   // 传入当前组件实例
    type: Envelope,
    defaultCreator: (): Envelope => new Envelope()
  });

  build() {
    Column() {
      TextInput({ text: this.env.title })
        .onChange((v: string) => {
          this.env.title = v;
        })
    }
  }
}
```

### 保存容器类数据

容器类（Array/Map/Set）须同时传入`defaultSubCreator`，作为容器元素构造器，使元素恢复为类实例。

```ts
import { RecoverableStorage } from '@kit.ArkUI';

// 容器元素类型
class CartItem {
  name: string = '';

  constructor(name: string = '') {
    this.name = name;
  }
}

@Entry
@Component
struct CartPage {
  // 连接容器类可恢复变量，defaultSubCreator使元素恢复为CartItem实例
  @State cart: CartItem[] = RecoverableStorage.connect({
    component: this,   // 传入当前组件实例
    type: Array<CartItem>,
    defaultCreator: (): CartItem[] => [],
    defaultSubCreator: (): CartItem => new CartItem()
  });

  build() {
    Column() {
      ForEach(this.cart, (item: CartItem) => {
        Text(item.name)
      }, (item: CartItem) => item.name)
    }
  }
}
```

### 通过notifyOnError获取错误信息

保存或恢复失败时（如数据超出150KB上限），失败的数据不会被保存，经回调上报原因、受影响的key与附加信息。

```ts
import { RecoverableStorage, RecoverableStorageError } from '@kit.ArkUI';

// 含大字符串属性的类型
class BigDraft {
  data: string = '';
}

@Entry
@Component
struct BigPage {
  // 连接可恢复状态变量并注册错误回调
  @State big: BigDraft = RecoverableStorage.connect({
    component: this,   // 传入当前组件实例
    type: BigDraft,
    key: 'bigDraft',
    defaultCreator: (): BigDraft => new BigDraft(),
    notifyOnError: (e: RecoverableStorageError) => {
      // 保存或恢复失败时上报原因、受影响的key与附加信息
      console.error(`reason: ${e.reason}, keys: ${e.keys.join(',')}, message: ${e.message}`);
    }
  });

  aboutToAppear(): void {
    // 构造超过单实例150KB上限的数据
    this.big.data = 'a'.repeat(200 * 1024);
  }

  build() {
    Column() {
      Text(`data length: ${this.big.data.length}`)
    }
  }
}
```

应用退后台触发保存时，超出上限的数据不会被保存，回调输出如下内容：

```text
reason: serialization, keys: bigDraft, message: serialize budget (153600 bytes) exceeded, 1 key(s) evicted
```
