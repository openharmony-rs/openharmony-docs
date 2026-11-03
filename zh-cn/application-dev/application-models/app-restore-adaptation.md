# 应用状态恢复与页面栈恢复适配指南

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->

## 场景介绍

整机内存紧张时，系统会查杀后台应用，大数据统计查杀总量较高。查杀后用户原页面操作中断——用户乘坐地铁刷码进站，在地铁码页面退后台，应用被查杀后，用户下次点击桌面图标可直接打开至出行界面正常刷码出站，无须从首页再逐级进入。小说阅读、新闻阅读、视频播放等场景同理：被杀重拉后恢复到原操作页面，用户操作不中断。

[UIAbility备份恢复](ability-recover-guideline.md)基础文档介绍了通过[setRestoreEnabled()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#setrestoreenabled14)开启备份恢复、通过[onSaveState()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestate)保存临时数据的基本用法。对使用Navigation或router等多页面路由框架的中大型应用，仅保存临时数据还不够——用户被系统回收前停留在第3层甚至更深的页面，重拉后如果只回到首页，用户体验仍然是断裂的。

本文按适配层次组织，开发者可按层次递进接入：

- **第一层：基础能力**——开启备份恢复总开关（唯一必做项）、了解系统保存/恢复链路；页面栈恢复开关（Navigation三件套等）按应用形态选配。
- **第二层：业务数据恢复**——页面状态变量与自定义业务数据的保存恢复。系统只恢复页面栈结构和启动参数，运行时状态需要开发者自行保存恢复。
- **第三层：开发者自定义操作**——恢复启动判定、NavPathStack主动管理、自定义路由自管、不可序列化参数处理。按应用复杂度按需选用。

> **说明：**
>
> 本指南面向的是[UIAbility备份恢复](ability-recover-guideline.md)（default recovery，仅在应用切后台时保存、被系统回收后重拉时恢复），与[应用故障恢复](../dfx/apprecovery-guidelines.md)（fault recovery，通过`appRecovery.enableAppRecovery()`开启，面向异常崩溃场景）是两条独立链路，本文不涉及后者。

## 第一层：基础能力

### 开启备份恢复总开关

在UIAbility的`onCreate`中调用[setRestoreEnabled(true)](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#setrestoreenabled14)，不开启则系统不会保存/恢复任何数据：

``` TypeScript
export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    // 栈恢复总开关
    this.context.setRestoreEnabled(true);
  }
}
```

> **最小适配**：只需要数据恢复、不需要页面栈恢复的应用（如单页工具类，或页面可接受重拉后回到首页），开启总开关并在[onSaveState()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestate)中保存数据（写法见第二层数据通道）即完成适配，无需任何页面栈改造。

### Navigation三件套（按需选配）

需要恢复Navigation页面栈的应用才需要配置三件套；不做三件套时Navigation页面栈不参与恢复，但数据仍可经onSaveState正常保存恢复（即上面的最小适配）。配置时三件缺一不可，任一缺失则整座Navigation页面栈不参与恢复：

1. Navigation设置通用属性[id()](../reference/apis-arkui/arkui-ts/ts-universal-attributes-component-id.md#id)（恢复按id匹配，不设则整座Navigation不恢复）；
2. Navigation设置[recoverable(true)](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#recoverable14)（默认false）；
3. 参与恢复的NavDestination设置[recoverable(true)](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#recoverable14)。

<!-- @[nav_three_piece](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RestoreIndex.ets) -->

``` TypeScript
Navigation(this.pathStack) {
  Column({ space: 12 }) {
    Text('页面栈恢复示例')
      .fontSize(22)
      .fontWeight(FontWeight.Bold)
    if (this.restoreHint !== '') {
      Text(this.restoreHint)
        .fontSize(14)
        .fontColor(Color.Gray)
    }
    Button('打开阅读页（断点续读）')
      .width('80%')
      .onClick(() => {
        this.pathStack.pushPathByName('ReaderPage', { bookId: 'book-1001' } as Record<string, Object>);
        this.reportNavSnapshot();
      })
    Button('进入第三层页面（深栈补推演示）')
      .width('80%')
      .onClick(() => {
        this.pathStack.pushPathByName('ReaderPage', { bookId: 'book-1001' } as Record<string, Object>);
        this.pathStack.pushPathByName('DeepPage', {} as Record<string, Object>);
        this.reportNavSnapshot();
      })
    Button('router 页面恢复示例（方案 C）')
      .width('80%')
      .onClick(() => {
        router.pushUrl({ url: 'restore/RouterPage' });
      })
    Text('操作后退到后台等待系统回收，再次启动验证恢复效果')
      .fontSize(12)
      .fontColor(Color.Gray)
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

页面级（NavDestination）在完成数据通道与空值兜底（见第二层）后开启：

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

**三件套注意事项**：

- 只有**参数可序列化且有空值兜底**的页面才加`recoverable(true)`；广告页、登录页等无需恢复的页面不加即可；
- 若工程入口是广告页/闪屏页，恢复启动时应直接加载内容页绕过广告页，否则广告页会把恢复出的栈顶页顶掉；
- 使用@ohos.router的应用不需要三件套——router页面的`recoverable`属性默认为**true**（API 14起），页面栈由系统惰性全栈恢复，无需任何页面栈改造。唯一要做的页面栈相关工作是排除不需要恢复的页面（广告页等），通过`recoverable: false`显式排除：

<!-- @[router_exclude](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RouterPage.ets) -->

``` TypeScript
Button('跳转广告页（不参与恢复）')
  .width('80%')
  .onClick(() => {
    router.pushUrl({
      url: 'restore/AdvertPage',
      // 广告页等无需恢复的页面显式排除
      recoverable: false
    });
  })
```

### 系统保存/恢复链路

**Ability的恢复重建流程**：

1. 应用进入后台，AMS自动触发备份，调用应用侧`onSaveState`，页面栈序列化为JSON，写入文件；
2. 应用被系统回收（内存不足/性能管控）；
3. 用户重新打开应用，AMS检测到备份文件，Want中标记`APP_RECOVERY`；
4. `onCreate(want, launchParam)`系统读取文件，把保存的键值合并进本次启动Want的parameters字段（一次性，读取后即清除）；
5. `onWindowStageCreate`，页面栈数据由系统注入恢复，用户看到被杀前的页面。

**Navigation的恢复重建流程**：

- 备份时：ArkUI遍历所有`.recoverable(true)`的Navigation → 逐页记录NavDestination的name/param/mode/组件状态 → 序列化为JSON；
- 恢复时：ArkUI解析JSON → 重建NavDestination栈 → 栈顶页面被加载显示（生命周期正常触发） → 非栈顶页面仅记录栈位置（延迟实例化，用户返回时才创建）。

> **关键约束**：Navigation页面栈恢复不保证覆盖全部层级，更深层级建议应用保存路径快照自行补推（见[第三层：NavPathStack主动管理](#navpathstack主动管理)）。

## 第二层：业务数据恢复

系统只恢复页面栈结构和启动参数，应用运行时状态（全局变量、用户数据、自定义业务数据）需要开发者自行保存恢复。有以下两条路径，可互补使用。

### 路径一：持久化存储（不依赖恢复机制）

[Preferences](../reference/apis-arkdata/js-apis-data-preferences.md)/[RDB](../reference/apis-arkdata/js-apis-data-relationalStore.md)/文件等数据存储在磁盘上，**不依赖恢复机制，正常启动和恢复启动都能读**。已持久化的数据不要进备份快照——进程重建后持久化数据仍在，快照里只存定位键。

**页面状态变量恢复**推荐使用PersistentStorage/PersistenceV2，将状态变量持久化到磁盘，恢复启动时自动读取：

V1 — PersistentStorage + @StorageLink：

``` TypeScript
PersistentStorage.persistProp('appTheme', 'light');
@Component
struct MyPage {
  @StorageLink('appTheme') appTheme: string = 'light';
}
```

V2 — PersistenceV2 + @ObservedV2 + AppStorageV2：

``` TypeScript
@ObservedV2
class UserInfo {
  @Trace name: string = '';
  @Trace cartCount: number = 0;
}
PersistenceV2.persistProp('userInfo', new UserInfo());
@ComponentV2
struct MyPage {
  userInfo: UserInfo = AppStorageV2.connect(UserInfo, 'userInfo', new UserInfo())!;
}
```

### 路径二：onSaveState + want.parameters

临时数据（非持久化的页面状态、定位键、路由快照等）通过`onSaveState`写入`wantParam`，恢复启动时从`want.parameters`读回。适合数据量小、随页面栈一起保存恢复的场景。

**数据通道模式**——四个动作：

1. 页面平时把可序列化状态发布到AppStorage（数据通道）；
2. `onSaveState`同步读取AppStorage写入wantParam，返回`ALL_AGREE`；
3. 恢复启动时，`onCreate`把`want.parameters`中的数据经AppStorage中转；
4. 页面挂载后一次性消费，且**消费先于正常初始化、恢复路径直接return**，防止正常初始化把恢复数据覆盖回默认值。

第1步：页面平时发布状态到AppStorage。状态用字面量对象即可，只放可序列化的轻量字段：

<!-- @[reader_state_report](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/ReaderPage.ets) -->

``` TypeScript
/** 数据通道：状态变化时发布到 AppStorage，onSaveState 同步读取；只放可序列化的轻量数据。 */
private reportState(): void {
  AppStorage.setOrCreate('reader.state', {
    'bookId': this.bookId,
    'chapterIndex': this.chapterIndex,
    'progress': this.progress
  } as Record<string, Object>);
  // 草稿单独发布，onSaveState 按长度决定随数据保存还是落盘引用
  AppStorage.setOrCreate('reader.draft', this.draft);
}
```

第2步：`onSaveState`只做同步读取：

<!-- @[restore_on_save_state](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/entryability/RestoreAbility.ets) -->

``` TypeScript
onSaveState(reason: AbilityConstant.StateType,
  wantParam: Record<string, Object>): AbilityConstant.OnSaveResult {
  // 只做同步读取：页面平时已把状态发布到 AppStorage（见 ReaderPage 的 reportState）
  const st = AppStorage.get<Record<string, Object>>(KEY_READER_STATE);
  if (st !== undefined) {
    wantParam[KEY_RESTORE_READER] = st;
  }
  // 超过 2048 字节的草稿走落盘引用，want.parameters 只放文件名
  const draft = AppStorage.get<string>(KEY_READER_DRAFT) ?? '';
  if (draft.length > 2048) {
    wantParam[KEY_RESTORE_DRAFT_FILE] = saveBlob(this.context, 'reader', draft);
  } else if (draft !== '') {
    wantParam[KEY_RESTORE_DRAFT] = draft;
  }
  // 深栈补推用的 Navigation 路径快照
  const navSnapshot = AppStorage.get<string>(KEY_NAV_SNAPSHOT);
  if (navSnapshot !== undefined) {
    wantParam[KEY_RESTORE_NAV_PATH] = navSnapshot;
  }
  // 必须返回 ALL_AGREE，否则数据不落盘
  return AbilityConstant.OnSaveResult.ALL_AGREE;
}
```

第3步：`onCreate`判定恢复启动并中转数据：

<!-- @[restore_on_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/entryability/RestoreAbility.ets) -->

``` TypeScript
onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
  // 开启备份恢复总开关：不开启则系统不会保存/恢复任何数据
  this.context.setRestoreEnabled(true);

  // 判断是否恢复启动（restoreKeys 传入本应用的全部恢复键）
  const restoreKeys: string[] = [KEY_RESTORE_READER, KEY_RESTORE_DRAFT,
    KEY_RESTORE_DRAFT_FILE, KEY_RESTORE_NAV_PATH];
  if (isRestoreLaunch(want, launchParam, restoreKeys)) {
    // 系统在恢复启动时把上次保存的数据放入 want.parameters 带回（仅此一次）；
    // 页面尚未创建，先经 AppStorage 中转，页面挂载后取用
    const reader = want?.parameters?.[KEY_RESTORE_READER] as Record<string, Object> | undefined;
    if (reader !== undefined) {
      AppStorage.setOrCreate(KEY_RESTORE_READER, reader);
    }
    // 短草稿随数据带回；超长草稿按文件名从沙箱读回（读不到降级为空）
    const draftInline = want?.parameters?.[KEY_RESTORE_DRAFT] as string | undefined;
    if (draftInline !== undefined) {
      AppStorage.setOrCreate(KEY_RESTORE_DRAFT, draftInline);
    }
    const draftFile = want?.parameters?.[KEY_RESTORE_DRAFT_FILE] as string | undefined;
    if (draftFile !== undefined) {
      AppStorage.setOrCreate(KEY_RESTORE_DRAFT, loadBlob(this.context, draftFile) ?? '');
    }
    // 深栈补推用的路径快照
    const navPath = want?.parameters?.[KEY_RESTORE_NAV_PATH] as string | undefined;
    if (navPath !== undefined) {
      AppStorage.setOrCreate(KEY_RESTORE_NAV_PATH, navPath);
    }
  } else {
    // 正常冷启：清理历史落盘文件
    cleanupBlob(this.context);
  }
}
```

第4步：页面挂载后一次性消费恢复数据：

<!-- @[page_consume](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/ReaderPage.ets) -->

``` TypeScript
aboutToAppear(): void {
  // 恢复消费：使用 Ability 层中转的恢复数据，取出即删，防止重复消费
  const restored = AppStorage.get<Record<string, Object>>('restore.reader');
  if (restored !== undefined) {
    AppStorage.delete('restore.reader');
    this.restoredFromChannel = true;
    this.bookId = (restored['bookId'] as string) ?? '';
    this.chapterIndex = (restored['chapterIndex'] as number) ?? 1;
    this.progress = (restored['progress'] as number) ?? 0;
    // 落盘草稿优先于随数据带回的短草稿
    const draftFromBlob = AppStorage.get<string>('restore.reader.draft');
    if (draftFromBlob !== undefined) {
      AppStorage.delete('restore.reader.draft');
      this.draft = draftFromBlob;
    } else {
      this.draft = (restored['draft'] as string) ?? '';
    }
    this.source = '恢复启动';
    this.reportState();
    return; // 不走正常冷启初始化
  }
}
```

**数据通道注意事项**：

- onSaveState在保存窗口内被调用，**只做同步读取**，不能在这里才异步采集数据；
- 恢复数据在`want.parameters`中**只出现一次**，取出后即被系统清除，中转消费要"取出即删"防重复；
- 若数据已持久化（preferences/RDB/文件），不要进备份快照——进程重建后持久化数据仍在，快照里只存定位键。

### 超大数据落盘引用

任一场景下存在单项数据接近或超过want.parameters序列化预算（如未提交的长文本草稿），直接放want.parameters会超限或挤占页面栈预算。数据本体写入应用沙箱文件，want.parameters中只放**文件名**（恢复时按文件名读回）：

<!-- @[blob_save](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/common/RestoreUtil.ets) -->

``` TypeScript
/** 超大数据落盘：数据本体写入沙箱文件，返回文件名，want.parameters 只保存文件名。 */
export function saveBlob(context: common.Context, key: string, data: string): string {
  const fileName = BLOB_FILE_PREFIX + key + '.txt';
  const file = context.filesDir + '/' + fileName;
  const f = fs.openSync(file, fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE | fs.OpenMode.TRUNC);
  try {
    fs.writeSync(f.fd, data);
  } finally {
    fs.closeSync(f);
  }
  return fileName;
}
```

<!-- @[blob_load](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/common/RestoreUtil.ets) -->

``` TypeScript
/** 按文件名读回落盘数据；读不到（如设备重启后不还原）返回 null，调用方按空数据降级。 */
export function loadBlob(context: common.Context, fileName: string): string | null {
  try {
    const file = context.filesDir + '/' + fileName;
    if (!fs.accessSync(file)) {
      return null;
    }
    return fs.readTextSync(file);
  } catch (e) {
    return null;
  }
}
```

onSaveState按数据长度分流（短草稿直接放，超长走落盘，见上面onSaveState demo中的草稿分支）；onCreate读回（见onCreate demo，`loadBlob(...) ?? ''`读不到降级为空）。

**注意事项**：

- **引用失效降级**：设备重启不恢复、文件可能不存在，读引用失败时按空数据降级，不能白屏；
- **清理**：非恢复启动时清理过期落盘文件（示例工程按7天清理，与系统备份数据过期时间对齐），防止残留堆积。

## 第三层：开发者自定义操作

按应用复杂度按需选用以下能力。

### 恢复启动判定（三信号合判）

恢复场景下[launchParam.launchReason](../reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#launchparam)取值为`APP_RECOVERY`。但**部分低版本系统中，设备重启后的重拉也可能把launchReason误标为APP_RECOVERY**（API 26起系统不再误标），因此低版本不能单独依赖launchReason判定恢复，需要组合以下信号（按可靠性排序）：

| 信号 | 可靠性 | 说明 |
| --- | --- | --- |
| 系统键`ohos.ability.params.abilityRecoveryRestart`为`true` | 全版本可靠 | 恢复启动时由系统合并进want.parameters，恢复启动一定为true |
| want.parameters中存在本应用保存的恢复键 | 高 | 恢复键只在恢复启动时由系统合并回来，低版本最可靠的信号 |
| launchReason === APP_RECOVERY | API 26及以上可靠，旧版本可能误标 | 26+可单独成立；低版本只能作为辅助信号，与前两个信号联合判定 |

示例工程把三信号合判封装成一个普通函数`isRestoreLaunch`：

<!-- @[restore_launch](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/common/RestoreUtil.ets) -->

``` TypeScript
/**
 * 三信号合判是否恢复启动：系统键为 true（全版本可靠）/ want.parameters 中存在
 * 恢复键（仅恢复启动时由系统带回）/ launchReason 为 APP_RECOVERY（仅 API 26+
 * 可信，低版本可能误标，不能单独采信）。
 * restoreKeys：onSaveState 写入 want.parameters 的全部键名。
 */
export function isRestoreLaunch(want: Want, launchParam: AbilityConstant.LaunchParam,
  restoreKeys: string[]): boolean {
  const sysFlag = want?.parameters?.['ohos.ability.params.abilityRecoveryRestart'];
  const bySysKey: boolean = sysFlag === true || sysFlag === 'true';
  const byRestoreKey: boolean = restoreKeys.some(k => want?.parameters?.[k] !== undefined);
  const byReason: boolean = launchParam?.launchReason === AbilityConstant.LaunchReason.APP_RECOVERY
    && deviceInfo.sdkApiVersion >= 26;
  return bySysKey || byRestoreKey || byReason;
}
```

判定恢复启动后，可控制恢复行为——跳过部分初始化、从want.parameters取临时状态、跳过自动跳页逻辑：

``` TypeScript
onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
  this.context.setRestoreEnabled(true);
  if (isRestoreLaunch(want, launchParam, restoreKeys)) {
    // 恢复启动：可跳过部分初始化、从 want.parameters 取临时状态
    this.restoreFromRecovery(want);
  } else {
    // 正常冷启动：标准初始化
    this.initForColdStart();
  }
}
```

### NavPathStack主动管理

Navigation页面栈恢复不保证覆盖全部层级，更深层级需应用自行补推。

**路径快照 + 补推**——平时每次导航后把当前栈路径快照发布到AppStorage（onSaveState同步读取，见第二层数据通道）；恢复启动后在首页`onPageShow`按快照补齐缺失的更深层级。

补推时机：**首页onPageShow**——此时系统页面栈恢复已完成、页面已渲染。禁止在loadContent回调中补推（系统栈恢复尚未执行，会与系统恢复互相冲突）：

<!-- @[deep_stack_replay_timing](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RestoreIndex.ets) -->

``` TypeScript
onPageShow(): void {
  // 深栈补推时机：此时系统栈恢复已完成、页面已渲染；禁止提前到 loadContent 回调
  // （系统恢复尚未执行，会互相冲突）。恢复启动时首页的自动跳转（如广告页）必须跳过，
  // 否则会把恢复出来的栈顶页挤掉。
  this.replayDeepStack();
}
```

平时发布路径快照：

<!-- @[nav_snapshot_report](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RestoreIndex.ets) -->

``` TypeScript
/** 每次导航后把路径快照发布到 AppStorage，onSaveState 同步读取。 */
private reportNavSnapshot(): void {
  AppStorage.setOrCreate(KEY_NAV_SNAPSHOT, JSON.stringify(this.pathStack.getAllPathName()));
}
```

恢复后逐层补推：

<!-- @[deep_stack_replay](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RestoreIndex.ets) -->

``` TypeScript
/** 按保存的路径快照补齐系统未恢复的深层级。 */
private replayDeepStack(): void {
  const navPath = AppStorage.get<string>(KEY_RESTORE_NAV_PATH);
  if (navPath === undefined) {
    return;
  }
  AppStorage.delete(KEY_RESTORE_NAV_PATH);
  try {
    const names: string[] = JSON.parse(navPath) as string[];
    const current: string[] = this.pathStack.getAllPathName();
    // 从系统已恢复的层数起逐层补齐；补推失败则停在已恢复页，不白屏
    for (let i = current.length; i < names.length; i++) {
      this.pathStack.pushPathByName(names[i], {} as Record<string, Object>);
    }
  } catch (e) {
    // 快照损坏则跳过补推
  }
}
```

**注意事项**：

- 补推的页面param按空对象传入，页面数据靠第二层数据通道恢复（定位键在快照数据里），不要试图把原始param塞进快照；
- 路径快照只是页面名数组，注意对深栈param有依赖的页面要先做[不可序列化参数处理](#不可序列化参数处理)。

### 自定义路由完全自管

应用使用HMRouter（@hadss/hmrouter）等基于uri的三方路由框架，或自研路由。三方路由内部不走系统Navigation栈恢复链路，`recoverable`三件套不可控。

**路由凭证保存重放**——uri天然可序列化。onSaveState只存轻量路由凭证（uri + 可序列化参数），恢复启动后由应用自行按凭证逐层重放路由：

1. **页面登记**：维护"页面名 → 路由凭证"的映射，凭证只含uri与可序列化参数；
2. **保存**：onSaveState把当前路由路径的凭证列表写入wantParam；
3. **重放**：onCreate判定恢复启动后把凭证列表经AppStorage中转，在首页onPageShow（once语义，避免重复触发）按凭证逐层路由跳转。

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
const routes = AppStorage.get<RouteCredential[]>('restore.routes');
if (routes !== undefined) {
  AppStorage.delete('restore.routes'); // 一次性消费
  for (const r of routes) {
    this.router.push(r.uri, r.param); // 按所用路由框架的 API 重放
  }
}
```

**注意事项**：

- 重放期间应用若有"自动跳首页/重定向登录"等导航逻辑必须跳过（用一个布尔变量记录恢复流程未结束即可），重放完成后恢复正常，否则重放的路由会被自动跳转顶掉；
- 本方案demo不随示例工程提供（依赖三方路由包）。HMRouter场景若愿意为其内部Navigation设置id+recoverable，也可选用第一层三件套方案，但HMRouter内部Navigation实例不易注入属性，默认推荐本方案。

### 不可序列化参数处理

Want parameters的值只支持String/Number/Boolean/PlainObject，**函数、Map/Set、Date、类实例不可传输**。进入快照（onSaveState数据与页面param）的参数需要按以下方式处理：

| 原字段类型 | 处理方式 |
| --- | --- |
| string / number / boolean | 直接保留 |
| PlainObject（纯数据对象） | 直接保留 |
| Function / Callback | 删除，页面改为从AppStorage或注册表重新获取 |
| 类实例（MediaItem、PhotoAsset等） | 替换为定位键（如uri、id），页面挂载后按定位键重新查询 |
| Map / Set / Date | 拍平为PlainObject或Array |
| 已持久化的数据（preferences/RDB/文件） | 不进快照（进程重建后仍在），只存定位键 |

回调函数、Proxy对象等复杂对象没有随页面栈恢复的序列化机制，不能进入快照，必须按上表方式替换为定位键、注册表等可重建的数据，页面挂载后重新绑定。

## 通用注意事项

以下内容所有层次通用。

### 空值兜底

页面param为空时若不处理会直接白屏。

系统恢复的页面param经过序列化窄约束后可能为空或残缺，且**框架没有通用的"数据未就绪防白屏"机制**，页面必须在onReady中处理param为空的情况，按三条路径降级：

<!-- @[empty_param_fallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/ReaderPage.ets) -->

``` TypeScript
/** 空值兜底：恢复的 param 可能为空/残缺，不处理会白屏。 */
private handleParam(ctx: NavDestinationContext): void {
  const param = ctx.pathInfo?.param as Record<string, Object> | undefined;
  // param 有效：用定位键重新加载数据
  if (param !== undefined && param['bookId'] !== undefined) {
    this.bookId = param['bookId'] as string;
    if (!this.restoredFromChannel) {
      this.loadFresh();
    }
    return;
  }
  // param 为空：从 AppStorage 恢复通道取
  const restored = AppStorage.get<Record<string, Object>>('restore.reader');
  if (restored !== undefined) {
    AppStorage.delete('restore.reader');
    this.restoredFromChannel = true;
    this.bookId = (restored['bookId'] as string) ?? '';
    this.chapterIndex = (restored['chapterIndex'] as number) ?? 1;
    this.progress = (restored['progress'] as number) ?? 0;
    this.draft = (restored['draft'] as string) ?? '';
    this.source = '恢复启动';
    this.reportState();
    return;
  }
  // 兜底：退回上一页
  ctx.pathStack?.pop();
}
```

### 恢复期间不要自动跳页

应用侧"启动后自动跳首页/自动切Tab/重定向登录/进广告页"等导航逻辑，在恢复启动时会把系统恢复的页面栈顶掉。做法：用普通布尔变量记录"本次启动是恢复启动"（`isRestoreLaunch`的结果即可），上述自动跳转逻辑在恢复启动时跳过；恢复流程结束（页面栈已就位，通常是首页onPageShow之后）再恢复正常导航。

## 约束速查

- **API compatible ≥ 14是硬门槛**：低于14时`setRestoreEnabled()`不可用，无从适配；
- 备份数据存储在[Want](../reference/apis-ability-kit/js-apis-app-ability-want.md#want)的parameters字段中，受序列化大小限制，不适合存放大数据（如长文本草稿、大段编辑内容），此类数据使用[超大数据落盘引用](#超大数据落盘引用)；
- [onSaveState()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestate)必须返回`ALL_AGREE`，否则数据不落盘。若应用实现了[onSaveStateAsync()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestateasync20)（API 20起），系统不再调用同步版onSaveState，两者不要同时使用；
- Want parameters的值只支持String/Number/Boolean/PlainObject，**函数、Map/Set、Date、类实例不可传输**，需要转换为可序列化结构（详见[不可序列化参数处理](#不可序列化参数处理)）；
- Navigation页面栈恢复不保证覆盖全部层级，更深层级建议应用保存路径快照自行补推（详见[NavPathStack主动管理](#navpathstack主动管理)）；
- Navigation参数序列化存在窄约束（嵌套深度、属性个数、字符串长度限制），**违规属性会被静默丢弃且无告警**，恢复后的页面必须做空值兜底（详见[空值兜底](#空值兜底)）；
- 应用正常关闭不触发备份；设备重启后不支持还原备份；备份数据保存7天；
- 备份恢复机制依赖任务保留机制，设置`removeMissionAfterTerminate`为true或设备不支持任务保留（如PC/2in1设备）时机制不生效；
- [UIExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md)不支持备份恢复；
- `setRestoreEnabled()`与router页面`recoverable`属性自API 14起可用；Navigation/NavDestination的`recoverable`属性ArkTS-Dyn自API 14起可用（ArkTS-Sta自API 23起）；
- Navigation与router混用的应用，**以主框架的方案为准**——混用两套恢复链路有互相破坏风险（见[常见问题排查](#常见问题排查)）；
- 逐页评估可行性：页面参数**可序列化 + 有空值兜底**的页面才允许参与页面栈恢复，否则宁可只保数据不保页面——恢复出一个白屏页面比回到首页更糟。

## 常见问题排查

**恢复后页面白屏**

白屏根因通常为以下四类，逐一排查：

1. **页面param为空且无兜底**：param序列化窄约束违规被静默丢弃，页面拿到空param直接渲染空内容——补onReady三条降级路径（见[空值兜底](#空值兜底)）；
2. **页面初始化覆盖恢复数据**：正常初始化无条件执行，把恢复数据覆盖回默认值——恢复消费必须先于正常初始化，且恢复路径直接return（见[第二层：业务数据恢复](#第二层业务数据恢复)数据通道模式第4步）；
3. **补推时机过早**：在loadContent回调中补推，系统栈恢复尚未执行，与系统恢复互相冲突——移到首页onPageShow（见[NavPathStack主动管理](#navpathstack主动管理)）；
4. **自动跳页未跳过**：恢复启动时仍执行"自动跳首页/进广告页"逻辑，把恢复的栈顶页面顶掉——见[恢复期间不要自动跳页](#恢复期间不要自动跳页)。

**双路径冲突**

既开了系统Navigation栈恢复（第一层三件套），又自己做了路由重放（自定义路由自管），两套恢复互相push导致栈重复或错乱——一个应用只用一条页面栈恢复路径。

**恢复判定误判**

低版本系统中设备重启后的重拉被误标`APP_RECOVERY`，应用误走恢复逻辑显示旧数据——使用三信号合判（见[恢复启动判定](#恢复启动判定三信号合判)），低版本不单独依赖launchReason。

**数据没保存上**

onSaveState返回值不是`ALL_AGREE`；或实现了onSaveStateAsync（API 20起）导致同步版不再被调用；或数据含函数/Map/Set/Date等不可序列化字段被静默丢弃。

## 真机验证方法

真机验证步骤（示例工程`UIAbilityRecover`可复现完整流程）：

1. 安装应用，首页进入「页面栈恢复示例」，打开阅读页，模拟翻页/输入草稿；
2. 按Home键退到后台，等待系统因资源管控回收该应用（开发调试可用`hdc shell aa force-stop <bundleName>`模拟被杀，**不要用"最近任务中划掉"——那是主动销毁，不触发恢复**）；
3. **通过桌面图标重新启动应用**（点击launcher图标拉起）；
4. 断言：页面栈恢复到被杀前的页面（非首页）、阅读进度与草稿恢复。

> **注意：**
>
> 恢复验证必须通过桌面图标重拉。使用`aa start`等命令行走的是冷启动路径，测不到恢复行为。
