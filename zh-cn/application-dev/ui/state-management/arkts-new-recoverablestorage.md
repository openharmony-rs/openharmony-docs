# RecoverableStorage: 应用终止场景状态变量自动保存与恢复
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

为了增强状态管理框架在应用被系统终止或异常退出场景下的数据恢复能力，开发者可以使用RecoverableStorage自动保存与恢复状态变量。

RecoverableStorage是应用程序中的可选单例对象。此对象的作用是：当应用被系统以资源管控方式终止（如低内存）或因JS_ERROR、APP_FREEZE异常退出时，自动保存所声明的状态变量的当前值；应用被系统重新拉起后，自动恢复这些值，实现UI无感恢复。

与[PersistenceV2](./arkts-new-persistencev2.md)的持久化模型不同，RecoverableStorage采用**快照模型**（非写穿）：仅在系统存盘时机（退后台预备档/异常时点档）一次性提取当前值，而非每次变量变更即写盘。这意味着静止UI零开销，恢复数据为临时数据（用户上滑删除即清除），适合保存页面草稿、滚动位置等轻量UI状态。

在阅读本文档前，建议提前阅读：[\@ComponentV2](./arkts-create-custom-components.md#componentv2)，[\@ObservedV2和\@Trace](./arkts-new-observedV2-and-trace.md)，配合阅读：[RecoverableStorage-API文档](../../reference/apis-arkui/js-apis-stateManagement.md#recoverablestorage26100)。

>**说明：**
>
>RecoverableStorage从API version 26开始支持。

## 概述

RecoverableStorage是应用启动时创建的单例，提供终止/异常退出场景下状态变量的声明、保存与恢复能力。开发者通过`connect`声明变量后，系统在存盘时机自动提取当前值；应用被系统重新拉起后，再次执行`connect`即可读回保存的值。

**快照模型 vs 写穿模型**：

| 维度 | RecoverableStorage（快照） | PersistenceV2（写穿） |
|------|---------------------------|----------------------|
| 写入时机 | 仅系统存盘时机（退后台/异常退出） | 每次变量变更即写盘 |
| 静止UI开销 | 零 | 有持续IO |
| 数据生命周期 | 临时（上滑删除/重启后清除） | 持久（写入磁盘） |
| 适用场景 | 页面草稿、滚动位置等轻量UI状态 | 用户设置、历史记录等持久数据 |

RecoverableStorage支持V1（\@State + 普通类）和V2（\@Local + \@ObservedV2）双状态系统，支持嵌套对象、容器（Array/Map/Set）和\@Computed属性。

## 系统前提

RecoverableStorage依赖系统恢复链路，需要完成以下配置（三处时序各就各位，缺一处对应链路静默失效）：

### 公共配置（两种场景共用同一份EntryAbility）

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(): void {
    // ② 终止链门控（点卡恢复通道）
    this.context.setRestoreEnabled(true);

    // ③ 异常链恢复的关键一步：系统判定"是否走默认恢复"时要读contentStorage，
    // 提前调restoreWindowStage让其就绪，否则异常重启降级为冷启动
    const storage = new LocalStorage();
    this.context.restoreWindowStage(storage);
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/Index', (err) => { /* 常规加载 */ });
  }
}
```

### 两场景唯一差异：调不调enableAppRecovery

**终止场景**：不创建AbilityStage（或创建但不调`enableAppRecovery`）。

**异常退出场景**：

```ts
// MyAbilityStage.ets（module.json5 srcEntry 指向）
import { AbilityStage, appRecovery } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onCreate(): void {
    // ① 必须在AbilityStage.onCreate调用（时序要求）
    appRecovery.enableAppRecovery(
      appRecovery.RestartFlag.ALWAYS_RESTART,
      appRecovery.SaveOccasionFlag.SAVE_WHEN_ERROR | appRecovery.SaveOccasionFlag.SAVE_WITH_FILE
    );
  }
}
```

>**注意：**
>
>`enableAppRecovery`必须在**AbilityStage.onCreate**（app级入口）调用，写在UIAbility.onCreate会晚于挂载时的配置固化，**静默失效**。`setRestoreEnabled(true)`和`restoreWindowStage(storage)`则在UIAbility.onCreate（ability级）调用。

## 使用说明

- connect：声明一个可恢复的状态变量。变量已存在时返回已有引用；否则通过defaultCreator构造默认值并返回。
- keys：获取当前实例（窗口）注册的所有可恢复状态变量的key。
- remove：注销当前实例指定key的可恢复状态变量。注销后该变量不再保存与恢复。
- notifyOnError（connect选项）：响应序列化或反序列化失败的回调。

以上接口详细描述请参考[RecoverableStorage-API文档](../../reference/apis-arkui/js-apis-stateManagement.md#recoverablestorage26100)。

## 使用限制

1. 仅支持**对象类型**（`T extends object`）。连接number、string、boolean等简单类型会抛出[BusinessError(140124)](../../reference/apis-arkui/errorcode-stateManagement.md#140124)。类的**成员属性**可为基本类型。

2. 单实例序列化预算为**150KB**，推荐用户数据总量≤100KB。超限项会被剔除出快照并经notifyOnError上报，不会导致应用崩溃。

3. 须在**自定义组件内**调用，`component`参数传`this`。运行时校验的是component有效性（能否提供getInstanceId），持有有效组件实例时在struct外调用亦可连接成功。

4. 多实例（multiton ability各窗口）各自独立分区，同一key在不同窗口互不干扰。

5. 不支持非built-in类型，如PixelMap、NativePointer、ArrayList等Native类型。

## 支持的类型

### V1形态（@State + 普通类）

嵌套成员在字段初始化器或构造函数中实例化，恢复时数据就地灌入已有实例（原型保留）。

```ts
class Draft {
  text: string = '';
  level: number = 0;
  constructor(text: string = '', level: number = 0) { this.text = text; this.level = level; }
}

@Entry
@Component
struct MyPage {
  @State draft: Draft = RecoverableStorage.connect({
    component: this,
    type: Draft,
    defaultCreator: (): Draft => new Draft()
  });
}
```

### V2形态（@Local + @ObservedV2 + @Type）

嵌套\@Type成员的类须\@ObservedV2装饰，嵌套重建由\@Type元数据驱动。

```ts
@ObservedV2
class Envelope {
  @Trace title: string = '';
  @Type(Attachment) attach: Attachment = new Attachment();
}

@Entry
@ComponentV2
struct MyPage {
  @Local env: Envelope = RecoverableStorage.connect({
    component: this,
    type: Envelope,
    defaultCreator: (): Envelope => new Envelope()
  });
}
```

### 容器形态（Array/Map/Set顶层connect + defaultSubCreator）

`type`传Array/Map/Set时，`defaultSubCreator`作为容器元素factory，使元素恢复为类实例。

```ts
@Entry
@Component
struct CartPage {
  @State cart: CartItem[] = RecoverableStorage.connect({
    component: this,
    type: Array,
    defaultCreator: (): CartItem[] => [],
    defaultSubCreator: (): CartItem => new CartItem()
  });
}
```

### \@Computed属性

保存与恢复对开发者透明：恢复后读取只读属性得到与保存时一致的值，不报错不回调、无需额外处理。getter-only值由依赖重算，\@Computed随依赖变更按既有计算规则更新。

## 使用场景

### 终止后恢复

应用被系统资源管控终止后，系统自动重新拉起，`connect`读回退后台时保存的值。

```ts
@Entry
@Component
struct DraftPage {
  @State draft: Draft = RecoverableStorage.connect({
    component: this,
    type: Draft,
    defaultCreator: (): Draft => new Draft(''),
    notifyOnError: (e) => console.error(`${e.reason}: ${e.keys.join(',')}`)
  });

  build() {
    Column() {
      TextInput({ text: this.draft.text })
        .onChange((v: string) => { this.draft.text = v; })
    }
  }
}
```

用户在TextInput输入文字 → 按Home退后台（触发存档）→ 应用被终止 → 系统重新拉起 → TextInput文字复原。

### 异常退出后恢复

应用因JS_ERROR或APP_FREEZE退出后，系统自动重启并恢复异常发生时刻的值。前提是AbilityStage已调用`enableAppRecovery`且未注册errorObserver。

### 多实例隔离

每个窗口实例（multiton ability各窗口）有独立分区。一个实例的connect仅返回本实例已注册变量的保存值或默认构造值，绝不返回其他实例的值。

### 通过notifyOnError获取错误信息

序列化/反序列化失败时（如超出150KB预算），超限项被剔除出快照，经回调上报受影响的key及原因。

```ts
@State big: BigDraft = RecoverableStorage.connect({
  component: this,
  type: BigDraft,
  defaultCreator: (): BigDraft => new BigDraft(),
  notifyOnError: (e: RecoverableStorageError) => {
    // e.reason: 'serialization'（超限或字段不可序列化）
    // e.keys: 受影响的key列表
    // e.message: 错误附加信息
    console.error(`over-budget: ${e.reason} keys=${e.keys.join(',')}`);
  }
});
```

## 使用建议

1. **典型用法为修改所连接对象的属性**，而非整体重新赋值。对V1 \@State变量整体重新赋值（`this.draft = new Draft()`）会导致已存引用失效，不被跟踪。

2. **嵌套重建**：V2走\@Type元数据，V1走实例树模板（字段初始化器实例化），均不需要defaultSubCreator。defaultSubCreator仅对容器root（Array/Map/Set）生效。

3. **冷启动语义**：用户手动启动应用（点图标）始终为冷启动，connect返回默认值，不读取恢复数据。仅系统携带恢复重启参数拉起的启动会执行恢复。

4. **上滑删除清除数据**：用户从最近任务上滑删除应用后，系统删除该应用的恢复数据，之后任何打开都不恢复。

5. **多实例建议**：同一key在不同窗口各自独立。如果需要跨实例共享数据，建议使用AppStorageV2或PersistenceV2。
