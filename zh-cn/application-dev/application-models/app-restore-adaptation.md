# 应用状态恢复与页面栈恢复适配指南

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->

## 场景介绍

[UIAbility备份恢复](ability-recover-guideline.md)基础文档介绍了通过[setRestoreEnabled()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#setrestoreenabled14)开启备份恢复、通过[onSaveState()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestate)保存临时数据的基本用法。对使用Navigation或router等多页面路由框架的中大型应用，仅保存临时数据还不够——用户被系统回收前停留在第3层甚至更深的页面，重拉后如果只回到首页，用户体验仍然是断裂的。

本文介绍在此基础上完成**整页页面栈与页面数据恢复**的适配方法，包括：

- 依据应用所使用的路由框架选择适配方案（Navigation栈恢复 / 路由凭证保存重放 / 纯router / 超限数据落盘引用）；
- 恢复启动的可靠判定（版本隔离）；
- 页面数据通道、空值兜底、深栈补推等通用改造项；
- 白屏等常见问题的根因与规避方法。

> **说明：**
>
> 本指南面向的是[UIAbility备份恢复](ability-recover-guideline.md)（default recovery，仅在应用切后台时保存、被系统回收后重拉时恢复），与[应用故障恢复](../dfx/apprecovery-guidelines.md)（fault recovery，通过`appRecovery.enableAppRecovery()`开启，面向异常崩溃场景）是两条独立链路，本文不涉及后者。

## 运行机制

### 保存链路

1. 应用切后台时（[onBackground()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onbackground)），系统调用应用侧[onSaveState()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestate)，应用将要恢复的数据写入`wantParam`，并必须返回`ALL_AGREE`；
2. 系统在`wantParam`中追加`pageStack`键，写入序列化的页面栈信息（**应用不要占用`pageStack`键名**）；
3. 数据以文件形式（`<missionId>.state`）落盘到应用沙箱，并在系统侧登记恢复标记（7天过期）。

### 恢复链路

1. 应用因系统资源管控被回收后，用户再次点击桌面图标拉起应用，系统判定本次启动为恢复启动；
2. 系统读取沙箱中的备份文件，把保存的每个键值**合并进本次启动Want的parameters字段**——这就是`onCreate()`中`want.parameters`里恢复数据的来源（一次性，读取后即清除）；
3. 页面栈数据在[onWindowStageCreate()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onwindowstagecreate)加载内容页阶段由系统注入恢复。

### 恢复启动判定与版本差异

恢复场景下[launchParam.launchReason](../reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#launchparam)取值为`APP_RECOVERY`。但**部分低版本系统中，设备重启后的重拉也可能把launchReason误标为APP_RECOVERY**，因此不能单独依赖launchReason判定恢复，需要组合以下信号（按可靠性排序）：

| 信号 | 可靠性 | 说明 |
| --- | --- | --- |
| 系统键`ohos.ability.params.abilityRecoveryRestart`为`true` | 全版本可靠 | 恢复启动时由系统合并进want.parameters，恢复启动一定为true |
| want.parameters中存在本应用保存的恢复键 | 高 | 恢复键只在恢复启动时由系统合并回来，低版本最可靠的信号 |
| launchReason === APP_RECOVERY | 新版本可靠，旧版本可能误标 | 只能作为辅助信号，与恢复键存在性联合判定 |

## 约束限制

- 备份数据存储在[Want](../reference/apis-ability-kit/js-apis-app-ability-want.md#want)的parameters字段中，由于序列化大小限制，支持的最大数据量为200KB。应用自定义数据（不含系统保存的页面栈）建议按100KB以内预算设计，超限数据使用[超限数据落盘引用](#方案d超限数据落盘引用)；
- [onSaveState()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestate)必须返回`ALL_AGREE`，否则数据不落盘。若应用实现了[onSaveStateAsync()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestateasync20)（API 20起），系统不再调用同步版onSaveState，两者不要同时使用；
- Want parameters的值只支持String/Number/Boolean/PlainObject，**函数、Map/Set、Date、类实例不可传输**，需要转换为可序列化结构（详见[页面参数瘦身](#页面参数瘦身)）；
- Navigation页面栈恢复只自动恢复**栈顶前2页**，更深层级需应用自行补推（详见[深栈补推](#深栈补推)）；
- Navigation参数序列化存在窄约束（嵌套深度、属性个数、字符串长度限制），**违规属性会被静默丢弃且无告警**，恢复后的页面必须做空值兜底（详见[空值兜底](#空值兜底)）；
- 应用正常关闭不触发备份；设备重启后不支持还原备份；备份数据保存7天；
- 备份恢复机制依赖任务保留机制，设置`removeMissionAfterTerminate`为true或设备不支持任务保留（如PC/2in1设备）时机制不生效；
- [UIExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md)不支持备份恢复；
- `setRestoreEnabled()`与router页面`recoverable`属性自API 14起可用；Navigation/NavDestination的`recoverable`属性ArkTS-Dyn自API 14起可用（ArkTS-Sta自API 23起）。

## 方案选型

按应用使用的路由框架对号入座：

| 路由框架 | 推荐方案 | 说明 |
| --- | --- | --- |
| Navigation（NavPathStack + NavDestination） | 方案A：Navigation栈恢复 | 系统自动恢复栈顶前2页，改造成本最低 |
| HMRouter（@hadss/hmrouter）等三方路由 | 方案B：路由凭证保存重放 | uri天然可序列化，不受"前2页"限制，不依赖recoverable三件套 |
| @ohos.router | 方案C：纯router | router页面`recoverable`默认为true，仅需开关+数据保存 |
| Navigation与router混用 | 以主框架方案为准 | 混用两套恢复链路有互相破坏风险，需明确恢复目标 |
| 自研/未知路由 | 方案B通用形态 | 保存路由凭证（uri/页面名/参数），onCreate中重放 |

补充规则：

- **API compatible ≥ 14是硬门槛**：低于14时`setRestoreEnabled()`不可用，无从适配；
- 数据量超过预算（如未提交的长文本草稿）时，**方案D可与A/B/C任意叠加**；
- 逐页评估可行性：页面参数**可序列化 + 有空值兜底**的页面才允许参与页面栈恢复（Navigation场景即加`recoverable(true)`），否则宁可只保数据不保页面——恢复出一个白屏页面比回到首页更糟。

## 开发步骤

以下通用基础所有方案必做，方案A/B/C/D按选型叠加。

### 通用基础

#### 开启备份恢复与恢复判定（版本隔离）

在[onCreate()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncreate)中最先开启备份恢复，并完成恢复启动判定。判定逻辑封装为独立类，供Ability与页面共用：

<!-- @[restore_judge](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/common/RestoreJudge.ets) -->

``` TypeScript
import { AbilityConstant, Want } from '@kit.AbilityKit';

const RECOVERY_KEY = 'ohos.ability.params.abilityRecoveryRestart';

/**
 * 恢复启动判定（版本隔离）。
 * 部分低版本系统中，设备重启后的重拉也会把 launchReason 标记为 APP_RECOVERY，
 * 因此不能单独依赖 launchReason 判定恢复，需要结合系统键与恢复数据存在性共同判定。
 */
export class RestoreJudge {
  private static restoring: boolean = false;

  static init(want: Want, launchParam: AbilityConstant.LaunchParam, appRestoreKeys: string[]): void {
    const raw = want?.parameters?.[RECOVERY_KEY] as boolean | string | undefined;
    const flag = raw === true || raw === 'true';
    const byReason = launchParam?.launchReason === AbilityConstant.LaunchReason.APP_RECOVERY;
    const byData = appRestoreKeys.some(k => want?.parameters?.[k] !== undefined);
    RestoreJudge.restoring = flag || (byReason && byData) || byData;
  }

  /** 页面/Ability 任意处调用：当前是否恢复启动（含恢复流程未结束期间）。 */
  static isRestoring(): boolean {
    return RestoreJudge.restoring;
  }

  /** 恢复流程完整结束后调用，放行正常导航逻辑（否则自动跳首页等守卫会永久拦截）。 */
  static finishRestore(): void {
    RestoreJudge.restoring = false;
  }
}
```

判定组合的含义：系统键`abilityRecoveryRestart`为true时一定是恢复启动；恢复键存在（byData）单独成立即可判定恢复启动；launchReason只能与byData联合作为辅助条件。

#### 数据通道（页面平时发布，onSaveState同步读取）

页面恢复所需的数据不能等保存窗口再异步采集——onSaveState只做同步读取。正确做法是页面平时把可序列化状态发布到AppStorage，保存窗口同步读取。

以断点续读页面为例，页面可恢复状态只包含可序列化的定位键与轻量数据：

<!-- @[reader_state](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/ReaderPage.ets) -->

``` TypeScript
/** 页面可恢复状态：只包含可序列化的定位键与轻量数据，不放函数/类实例/Map。 */
export class ReaderState {
  public bookId: string = '';
  public chapterIndex: number = 1;
  public progress: number = 0; // 阅读进度（百分比）
  public draft: string = '';   // 未提交的笔记草稿（超限时走落盘引用）
}
```

页面在关键状态变化时发布到AppStorage：

<!-- @[data_channel_report](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/ReaderPage.ets) -->

``` TypeScript
/** 数据通道：关键状态变化时把可序列化状态发布到 AppStorage，onSaveState 同步读取。 */
private reportState(): void {
  const st = new ReaderState();
  st.bookId = this.bookId;
  st.chapterIndex = this.chapterIndex;
  st.progress = this.progress;
  st.draft = this.draft;
  AppStorage.setOrCreate('reader.state', st);
}
```

<!-- @[restore_on_save_state](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/entryability/RestoreAbility.ets) -->

``` TypeScript
onSaveState(reason: AbilityConstant.StateType,
  wantParam: Record<string, Object>): AbilityConstant.OnSaveResult {
  // 数据通道：只做同步读取，禁止在保存窗口做异步采集
  const st = AppStorage.get<ReaderState>(KEY_READER_STATE);
  if (st !== undefined) {
    if (st.draft.length > 2048) {
      // 超限草稿：本体落盘（方案 D），want.parameters 只放轻量引用
      const ref = RestoreBlob.save(this.context, 'reader', st.draft);
      wantParam[KEY_RESTORE_READER_BLOB] = ref;
      st.draft = '';
    }
    wantParam[KEY_RESTORE_READER] = st;
  }
  // 必须返回 ALL_AGREE，否则数据不落盘
  return AbilityConstant.OnSaveResult.ALL_AGREE;
}
```

#### 恢复数据中转与消费（一次性）

恢复数据在onCreate中即可获取，但页面此时还未挂载。做法是Ability层先把恢复数据经AppStorage中转，页面挂载后一次性消费，避免恢复数据被正常初始化覆盖：

<!-- @[restore_on_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/entryability/RestoreAbility.ets) -->

``` TypeScript
onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
  // 1. 开启备份恢复：必须在应用初始化阶段最先调用
  this.context.setRestoreEnabled(true);

  // 2. 恢复判定（版本隔离）：不能单独依赖 launchReason
  RestoreJudge.init(want, launchParam, [KEY_RESTORE_READER, KEY_RESTORE_NAV_PATH]);

  if (RestoreJudge.isRestoring()) {
    // 3. 恢复数据经 AppStorage 中转给页面（数据先就绪，页面挂载后一次性消费）
    const reader = want?.parameters?.[KEY_RESTORE_READER] as ReaderState | undefined;
    if (reader !== undefined) {
      AppStorage.setOrCreate(KEY_RESTORE_READER, reader);
    }
  } else {
    // 非恢复启动：清理过期的落盘引用文件
    RestoreBlob.cleanup(this.context);
  }
}
```

<!-- @[page_consume](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/ReaderPage.ets) -->

``` TypeScript
aboutToAppear(): void {
  // 恢复消费：优先使用 Ability 层中转的恢复数据，一次性消费防重复
  const restored = AppStorage.get<ReaderState>('restore.reader');
  if (restored !== undefined) {
    AppStorage.delete('restore.reader');
    this.applyRestored(restored);
    return; // 不走正常冷启初始化
  }
}
```

#### 页面参数瘦身

进入快照（onSaveState数据与Navigation页面param）的页面参数只保留可序列化的轻量字段：

| 原字段类型 | 处理方式 |
| --- | --- |
| string / number / boolean | 直接保留 |
| PlainObject（纯数据对象） | 直接保留 |
| Function / Callback | 删除，页面改为从AppStorage或注册表重新获取 |
| 类实例（MediaItem、PhotoAsset等） | 替换为定位键（如uri、id），页面挂载后按定位键重新查询 |
| Map / Set / Date | 拍平为PlainObject或Array |
| 已持久化的数据（preferences/RDB/文件） | 不进快照（进程重建后仍在），只存定位键 |

#### 空值兜底

页面param为空时若不处理会直接白屏。

系统恢复的页面param经过序列化窄约束后可能为空或残缺，且**框架没有通用的"数据未就绪防白屏"机制**，页面必须在onReady中处理param为空的情况，按三条路径降级：

<!-- @[empty_param_fallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/ReaderPage.ets) -->

``` TypeScript
/** 空值兜底：系统恢复的页面 param 经序列化窄约束后可能为空/残缺，必须处理，否则白屏。 */
private handleParam(ctx: NavDestinationContext): void {
  const param = ctx.pathInfo?.param as Record<string, Object> | undefined;
  // 路径 1：param 有效 → 用定位键重新加载数据，不依赖原始 param 中的类实例/回调
  if (param !== undefined && param.bookId !== undefined) {
    this.bookId = param.bookId as string;
    if (!this.restoredFromChannel) {
      this.loadFresh();
    }
    return;
  }
  // 路径 2：系统恢复但 param 为空 → 尝试从 AppStorage 恢复通道取
  const restored = AppStorage.get<ReaderState>('restore.reader');
  if (restored !== undefined) {
    AppStorage.delete('restore.reader');
    this.applyRestored(restored);
    return;
  }
  // 路径 3：兜底 → 退回上一页，避免白屏
  ctx.pathStack?.pop();
}
```

#### 恢复守卫

应用侧"启动后自动跳首页/自动切Tab/重定向登录"等导航逻辑，必须包在`isRestoring()`守卫内，否则会在系统恢复的页面栈之上再push页面，破坏恢复结果。加载内容页时同样注意：

<!-- @[restore_on_window_stage_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/entryability/RestoreAbility.ets) -->

``` TypeScript
onWindowStageCreate(windowStage: window.WindowStage): void {
  // 若工程入口是广告页/闪屏页，恢复启动时应直接加载内容页绕过广告页
  //（根据 RestoreJudge.isRestoring() 选择加载 restore/RestoreIndex 或广告页）。
  windowStage.loadContent('restore/RestoreIndex', (err) => {
    if (err.code) {
      hilog.error(DOMAIN, TAG, 'Failed to load the content. Cause: %{public}s', JSON.stringify(err));
      return;
    }
    hilog.info(DOMAIN, TAG, 'Succeeded in loading the content.');
    // 注意：禁止在此回调中调用 RestoreJudge.finishRestore()——
    // 此时页面尚未挂载、系统 Navigation 栈恢复可能还未执行，守卫会过早失效。
  });
}
```

### 方案A：Navigation栈恢复

系统自动恢复Navigation路由栈（栈顶前2页），应用负责数据通道与兜底。前提三件套缺一不可：

1. Navigation设置通用属性[id()](../reference/apis-arkui/arkui-ts/ts-universal-attributes-component-id.md#id)（恢复按id匹配，不设则整座Navigation不恢复）；
2. Navigation设置[recoverable(true)](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#recoverable14)（默认false）；
3. 参与恢复的NavDestination设置[recoverable(true)](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#recoverable14)。

> **说明：**
>
> 只有**参数可序列化且有空值兜底**的页面才加`recoverable(true)`；广告页、登录页等无需恢复的页面不加即可。

<!-- @[nav_three_piece](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RestoreIndex.ets) -->

``` TypeScript
Navigation(this.pathStack) {
  Column({ space: 12 }) {
    // 首页内容
  }
  .width('100%')
  .height('100%')
  .justifyContent(FlexAlign.Center)
}
.navDestination(this.PageMap)
// 三件套之 1：恢复按 navigationId 匹配，必须设置
.id('restore-nav')
// 三件套之 2：默认 false，必须显式开启（API 14+）
.recoverable(true)
.mode(NavigationMode.Stack)
```

页面级（NavDestination）在完成数据通道与空值兜底后开启：

``` TypeScript
NavDestination() {
  // 页面内容
}
.title('阅读页（断点续读）')
.onReady((ctx: NavDestinationContext) => {
  this.handleParam(ctx);
})
// 三件套之页面级：数据通道与空值兜底完成后才允许开启（API 14+）
.recoverable(true)
```

#### 深栈补推

系统只自动恢复**栈顶前2页**。若业务需要恢复更深的层级，应用需自行保存路径快照并在恢复后逐层补推。每次导航后把当前栈路径发布到AppStorage（onSaveState同步读取）：

<!-- @[nav_snapshot_report](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RestoreIndex.ets) -->

``` TypeScript
/** 深栈补推数据通道：每次导航后把当前栈路径快照发布到 AppStorage，onSaveState 同步读取。 */
private reportNavSnapshot(): void {
  AppStorage.setOrCreate(KEY_NAV_SNAPSHOT, JSON.stringify(this.pathStack.getAllPathName()));
}
```

恢复启动时，在首页onPageShow中按快照从第3层起逐层补推（补推失败则停在已恢复页，不白屏）：

<!-- @[deep_stack_replay](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RestoreIndex.ets) -->

``` TypeScript
/** 深栈补推：系统只自动恢复栈顶前 2 页，更深层级按保存的路径快照逐层补推。 */
private replayDeepStack(): void {
  const navPath = AppStorage.get<string>(KEY_RESTORE_NAV_PATH);
  if (navPath === undefined) {
    return;
  }
  AppStorage.delete(KEY_RESTORE_NAV_PATH);
  try {
    const names: string[] = JSON.parse(navPath) as string[];
    for (let i = 2; i < names.length; i++) {
      // 补推失败则停在已恢复页，不白屏
      this.pathStack.pushPathByName(names[i], {} as Record<string, Object>);
    }
  } catch (e) {
    // 快照损坏则跳过补推
  }
}
```

#### finishRestore时机

`finishRestore()`（放行正常导航守卫）的正确调用位置是**首页onPageShow**——此时Navigation栈已重建、页面已渲染。禁止在loadContent回调中调用（系统栈恢复尚未执行，守卫会过早失效）：

<!-- @[finish_restore_timing](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RestoreIndex.ets) -->

``` TypeScript
onPageShow(): void {
  // finishRestore 的正确时机：首页 onPageShow——此时 Navigation 栈已重建、页面已渲染。
  // 禁止在 loadContent 回调中调用（系统栈恢复尚未执行，守卫会过早失效）。
  if (RestoreJudge.isRestoring()) {
    this.replayDeepStack();
    RestoreJudge.finishRestore();
  }
}
```

### 方案B：自有路由凭证保存重放（HMRouter等三方路由）

不依赖系统Navigation栈恢复：onSaveState只存轻量路由凭证（uri/页面名/可序列化参数），恢复启动后由应用自行重放路由。适用于HMRouter等基于uri的三方路由框架，或自研路由。

要点：

1. **页面登记**：维护"页面名 → 路由凭证"的映射，凭证只含uri与可序列化参数；
2. **保存**：onSaveState把当前路由路径的凭证列表写入wantParam；
3. **重放**：onCreate判定恢复启动后，在首页onPageShow（once语义，避免重复触发）按凭证逐层路由跳转；
4. **守卫**：重放期间`isRestoring()`必须保持true，重放完成后`finishRestore()`。

``` TypeScript
// 伪代码示意（HMRouter 需按其路由 API 调整跳转调用）
onSaveState(reason: AbilityConstant.StateType,
  wantParam: Record<string, Object>): AbilityConstant.OnSaveResult {
  // 路由凭证：uri 天然可序列化，参数须已瘦身
  const routes: RouteCredential[] = RouteRegistry.snapshot(); // [{uri, param}, ...]
  wantParam['restore.routes'] = routes;
  return AbilityConstant.OnSaveResult.ALL_AGREE;
}

// 首页 onPageShow 中：
if (RestoreJudge.isRestoring()) {
  const routes = AppStorage.get<RouteCredential[]>('restore.routes');
  if (routes !== undefined) {
    for (const r of routes) {
      this.router.push(r.uri, r.param); // 按所用路由框架的 API 重放
    }
  }
  RestoreJudge.finishRestore();
}
```

> **说明：**
>
> 本方案demo不随示例工程提供（依赖三方路由包）。HMRouter场景若栈深不超过2页且愿意为其内部Navigation设置id+recoverable，也可选用方案A，但HMRouter内部Navigation实例不易注入属性，默认推荐本方案。

### 方案C：纯@ohos.router

router页面的[recoverable](../reference/apis-arkui/js-apis-router.md#routeroptions)属性默认为**true**（API 14起），纯router应用只需：开启`setRestoreEnabled()` + 保存/恢复业务数据，页面栈由系统惰性全栈恢复（无Navigation"前2页"限制）。

无需恢复的页面（广告页、活动页等）通过`recoverable: false`显式排除：

<!-- @[router_exclude](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RouterPage.ets) -->

``` TypeScript
Button('跳转广告页（不参与恢复）')
  .width('80%')
  .onClick(() => {
    router.pushUrl({
      url: 'restore/AdvertPage',
      // recoverable 默认 true；广告页/登录页等无需恢复的页面显式排除
      recoverable: false
    });
  })
```

若工程入口页是无需恢复的过渡页（广告/闪屏），恢复启动时可直接加载内容页绕过（见[恢复守卫](#恢复守卫)中的loadContent示例）。

### 方案D：超限数据落盘引用

当页面数据接近或超过want.parameters序列化预算（如未提交的长文本草稿、大段编辑内容）时，数据本体写入应用沙箱文件，want.parameters中只放轻量引用对象（文件名/版本/字节数，保持1KB以内），恢复时按引用读回：

<!-- @[blob_ref](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/common/RestoreBlob.ets) -->

``` TypeScript
import { common } from '@kit.AbilityKit';
import { fileIo as fs } from '@kit.CoreFileKit';

const FILE_PREFIX = 'restore_blob_';
const EXPIRE_MS = 7 * 24 * 60 * 60 * 1000; // 与系统备份数据 7 天过期对齐

/** 落盘引用：只包含文件名、版本与字节数，本身必须很小（小于 1KB），实际数据在沙箱文件中。 */
export class BlobRef {
  public file: string = '';
  public ver: number = 1;
  public size: number = 0;
}
```

<!-- @[blob_save](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/common/RestoreBlob.ets) -->

``` TypeScript
/** 保存超限数据：同步写入沙箱文件，返回轻量引用（进 want.parameters）。 */
static save(context: common.Context, key: string, data: string): BlobRef {
  const fileName = FILE_PREFIX + key + '.json';
  const file = context.filesDir + '/' + fileName;
  const f = fs.openSync(file, fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE | fs.OpenMode.TRUNC);
  try {
    fs.writeSync(f.fd, data);
  } finally {
    fs.closeSync(f);
  }
  const ref = new BlobRef();
  ref.file = fileName;
  ref.ver = 1;
  ref.size = data.length;
  return ref;
}
```

<!-- @[blob_load](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/common/RestoreBlob.ets) -->

``` TypeScript
/** 按引用读回数据；引用失效（文件不存在/读取失败）时返回 null，由调用方降级处理。 */
static load(context: common.Context, ref: BlobRef): string | null {
  try {
    const file = context.filesDir + '/' + ref.file;
    if (!fs.accessSync(file)) {
      return null;
    }
    // 直接读文本，避免 UTF-8 字节数与字符串长度不一致导致的截断
    return fs.readTextSync(file);
  } catch (e) {
    return null;
  }
}
```

**引用失效降级**：设备重启不恢复、正常退出不保存，落盘文件可能残留但不会被消费——读引用失败时按空数据降级，不能白屏。**清理**：非恢复启动时清理过期引用文件（7天，与系统备份过期对齐）：

<!-- @[blob_cleanup](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/common/RestoreBlob.ets) -->

``` TypeScript
/** 非恢复启动时清理过期引用文件，防止残留堆积（设备重启/正常退出不触发恢复，引用会残留）。 */
static cleanup(context: common.Context): void {
  try {
    const names = fs.listFileSync(context.filesDir);
    const now = Date.now();
    for (let i = 0; i < names.length; i++) {
      const name = names[i];
      if (name.startsWith(FILE_PREFIX)) {
        const file = context.filesDir + '/' + name;
        const stat = fs.statSync(file);
        if (now - stat.mtime * 1000 > EXPIRE_MS) {
          fs.unlinkSync(file);
        }
      }
    }
  } catch (e) {
    // 清理失败不影响启动
  }
}
```

## 常见问题

**恢复后页面白屏**

白屏根因通常为以下四类，逐一排查：

1. **页面param为空且无兜底**：param序列化窄约束违规被静默丢弃，页面拿到空param直接渲染空内容——补onReady三条降级路径（见[空值兜底](#空值兜底)）；
2. **@StorageLink等双向绑定守卫失效**：页面初始化逻辑无条件执行，把恢复数据覆盖回默认值——恢复消费必须先于正常初始化，且恢复路径直接return；
3. **finishRestore调用过早**：在loadContent回调中调用，系统栈恢复尚未执行，"自动跳首页"等导航逻辑提前放行，在恢复栈上再push——移到首页onPageShow；
4. **自动跳首页未包守卫**：启动逻辑在恢复启动时仍重定向首页，把恢复的栈顶页面顶掉——包`isRestoring()`守卫。

**双路径冲突**

既开了系统Navigation栈恢复（方案A），又自己做了路由重放（方案B式逻辑），两套恢复互相push导致栈重复或错乱——一个应用只用一条页面栈恢复路径。

**恢复判定误判**

低版本系统中设备重启后的重拉被误标`APP_RECOVERY`，应用误走恢复逻辑显示旧数据——使用版本隔离判定（系统键优先+恢复键存在性，见[恢复判定](#恢复启动判定与版本差异)），不单独依赖launchReason。

**数据没保存上**

onSaveState返回值不是`ALL_AGREE`；或实现了onSaveStateAsync（API 20起）导致同步版不再被调用；或数据含函数/Map/Set/Date等不可序列化字段被静默丢弃。

## 验证方法

真机验证步骤（示例工程`UIAbilityRecover`可复现完整流程）：

1. 安装应用，首页进入「页面栈恢复示例」，打开阅读页，模拟翻页/输入草稿；
2. 按Home键退到后台，等待系统因资源管控回收该应用（开发调试可用`hdc shell aa force-stop <bundleName>`模拟被杀，**不要用"最近任务中划掉"——那是主动销毁，不触发恢复**）；
3. **通过桌面图标重新启动应用**（点击launcher图标拉起）；
4. 断言：页面栈恢复到被杀前的页面（非首页）、阅读进度与草稿恢复。

> **注意：**
>
> 恢复验证必须通过桌面图标重拉。使用`aa start`等命令行走的是冷启动路径，测不到恢复行为。
