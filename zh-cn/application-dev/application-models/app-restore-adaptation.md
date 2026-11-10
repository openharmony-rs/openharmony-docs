# UIAbility备份恢复适配指导

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhang_hao_zheng-->
<!--Designer: @wendel-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

## 概述

系统内存紧张时会回收后台应用进程。应用被回收后，用户再次打开只能回到首页，此前的页面与操作上下文全部丢失。接入备份恢复后，应用可恢复到回收前的页面与数据。例如：用户在地铁乘车码页面退至后台，应用被回收；再次点击桌面图标即可回到乘车码页面完成出站。小说阅读、新闻阅读、视频播放等场景同理。

[UIAbility备份恢复](ability-recover-guideline.md)基础文档介绍了通过[setRestoreEnabled()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#setrestoreenabled14)开启备份恢复、通过[onSaveState()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestate)保存临时数据的基本用法：应用切后台时系统调用onSaveState()并把页面栈序列化后写入磁盘；应用被回收后恢复启动时，系统把保存的数据合并进本次启动Want的parameters字段带回，页面栈由系统恢复。

页面栈恢复不保证覆盖全部层级（更深层级见[深层栈补齐](#深层栈补齐)）；恢复的页面参数可能为空，需做[参数为空降级](#参数为空降级)处理。

以下所有场景的第一步都是[开启备份恢复](#开启备份恢复)，请根据应用情况在下表中选择适配方法：

| 应用情况 | 典型示例 | 适配方法 | 说明 |
| --- | --- | --- | --- |
| 可接受恢复启动后回到首页，且没有未持久化的临时数据 | 简单工具类应用 | 无需适配 | 应用重启后按常规方式重新加载数据即可（无未保存的临时数据） |
| 单页应用，需要恢复未持久化的临时数据 | 计算器历史记录、备忘录草稿 | 开启总开关 + onSaveState()保存数据 | [数据恢复](#数据恢复) |
| 多页应用，页面可接受恢复启动后回到首页，但业务数据不能丢 | 编辑器（恢复启动后回首页但草稿不丢） | 同上：数据按[数据恢复](#数据恢复)的方法保存恢复，无需页面栈改造 | [数据恢复](#数据恢复) |
| 使用Navigation组件实现页面导航的应用（以NavPathStack管理页面栈），页面栈层级较浅 | 出行码页、设置二级页 | 页面栈恢复三项配置 + 数据保存与恢复 + 参数为空降级 | [页面栈恢复：Navigation](#页面栈恢复navigation) |
| 使用Navigation组件的应用，用户会进入更深层页面（系统默认只恢复较浅层级） | 阅读器逐章深跳、商品多级筛选 | 同上一行，另需保存页面路径，补齐未恢复的深层页面 | [深层栈补齐](#深层栈补齐) |
| 使用Navigation组件的应用，页面名动态生成/加密或页面懒加载 | 页面名混淆、按需加载的工程 | 先把页面名改为静态、保证PageMap（页面名到页面组件构建器的映射）可解析，再做三项配置与参数为空降级（页面栈层级深的应用还需保存页面路径以补齐深层） | [三项配置](#三项配置) |
| @ohos.router应用 | 使用router.pushUrl的工程 | 为无需恢复的页面设置recoverable属性为false，将其排除出恢复范围 | [页面栈恢复：Router](#页面栈恢复router) |
| 三方路由框架（HMRouter等） | 基于三方框架路由的工程 | 保存路由信息（uri与参数），恢复启动后逐层重新执行跳转 | [页面栈恢复：三方路由](#页面栈恢复三方路由) |

无论选择哪种适配方案，以下常见问题按需叠加处理：

| 遇到的情况 | 处理方式 | 详见 |
| --- | --- | --- |
| 页面参数含函数、回调、Proxy等不可序列化对象 | 替换为定位键、注册表等可重建数据 | [函数与类实例等字段的转换](#函数与类实例等字段的转换) |
| 单条数据过大，超出want.parameters序列化后总大小上限（200KB） | 数据本体写入磁盘，保存的数据里只存文件名 | [超大数据分流](#超大数据分流) |
| 需要区分恢复启动与正常启动 | 组合判断三个条件：恢复重启标记为true、want.parameters中带回本应用保存的数据、launchReason为APP_RECOVERY | [判定恢复启动](#判定恢复启动) |


## 约束与限制

**环境与版本**

- 本机制自API版本14起可用（`setRestoreEnabled()`及各`recoverable`属性均为API版本14起），低于该版本无从适配。
- 应用正常关闭不触发备份；备份数据默认保存7天。
- 备份恢复机制依赖任务保留机制：设置`removeMissionAfterTerminate`为true或设备不支持任务保留（如PC/2in1设备）时机制不生效；[UIExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md)不支持备份恢复。

**数据与容量**

- 备份数据存储在[Want](../reference/apis-ability-kit/js-apis-app-ability-want.md#want)的parameters字段中，序列化后总大小上限为200KB。
- [onSaveState()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestate)必须返回`ALL_AGREE`，否则数据不写入磁盘；若应用实现了[onSaveStateAsync()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestateasync20)（API版本20起），系统不再调用同步版onSaveState()，两者不要同时使用。
- Want parameters的值只支持String/Number/Boolean等基本类型以及由它们组成的对象和数组，函数、Map/Set、Date、类实例等无法保存。
- Navigation参数序列化对嵌套深度、属性个数、字符串长度等有上限（上限由系统内部实现决定、可能变化），超出的属性会被静默丢弃且无告警，恢复后的页面必须做[参数为空降级](#参数为空降级)。

**页面栈恢复限制**

- Navigation页面栈恢复不保证覆盖全部层级，更深层级需自行保存页面路径补齐（见[深层栈补齐](#深层栈补齐)）。
- Navigation与router混用的应用，以主框架的方案为准——两套恢复同时开启会互相破坏，典型表现如页面被重复恢复、恢复出的栈顶页被另一套覆盖、返回栈顺序错乱；恢复后出现上述异常时，优先排查是否两套恢复同时开启。
- 逐页评估可行性：页面参数可序列化且已做参数为空降级处理的页面才允许参与页面栈恢复，否则只恢复数据、不恢复页面栈（未做降级处理的页面恢复后参数为空，存在白屏风险）。

## 适配准备

### 开启备份恢复

所有适配方案的第一步，在UIAbility的`onCreate()`中调用[setRestoreEnabled(true)](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#setrestoreenabled14)，不开启则系统不会保存/恢复任何数据：

``` TypeScript
export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    // 备份恢复总开关
    this.context.setRestoreEnabled(true);
  }
}
```

> **说明：**
>
> **最小适配**：有未持久化的临时数据（如草稿）需要恢复、但不需要恢复页面栈（可接受恢复启动后回到首页）的应用，开启总开关并在[onSaveState()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestate)中保存数据（写法见[数据恢复](#数据恢复)）即完成适配，无需任何页面栈改造。

### 判定恢复启动

恢复场景下[launchParam.launchReason](../reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#launchparam)取值为`APP_RECOVERY`。但API版本26.0.0之前的系统版本中，launchReason不能单独作为恢复启动的判定依据，需要组合检查以下条件（按可靠性排序）：

| 判定条件 | 可靠性 | 说明 |
| --- | --- | --- |
| 系统设置的恢复重启标记`ohos.ability.params.abilityRecoveryRestart`为`true` | 全版本可靠 | 恢复启动时由系统合并进want.parameters，恢复启动一定为true |
| want.parameters中带回了本应用保存的数据 | 高 | 这些数据只在恢复启动时由系统合并回来，API版本26.0.0之前最可靠的判断依据 |
| launchReason === APP_RECOVERY | API版本26.0.0及以上可靠 | API版本26.0.0起可单独成立；之前版本只能作为辅助条件，与前两个条件联合判定 |

示例工程把上述条件的组合判断封装成一个普通函数`isRestoreLaunch`，调用时把onSaveState()写入want.parameters的全部键名通过`restoreKeys`参数传入：

<!-- @[restore_launch](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/common/RestoreUtil.ets) -->

``` TypeScript
/**
 * 三信号合判是否恢复启动：系统键为 true（全版本可靠）/ want.parameters 中存在
 * 恢复键（仅恢复启动时由系统带回）/ launchReason 为 APP_RECOVERY（API版本26.0.0 起
 * 可信；之前版本从系统设置强行停止后的再次启动也会被误标，不能单独采信）。
 * restoreKeys：onSaveState 写入 want.parameters 的全部键名。
 */
export function isRestoreLaunch(want: Want, launchParam: AbilityConstant.LaunchParam,
  restoreKeys: string[]): boolean {
  const sysFlag = want?.parameters?.['ohos.ability.params.abilityRecoveryRestart'];
  const bySysKey: boolean = sysFlag === true || sysFlag === 'true';
  const byRestoreKey: boolean = restoreKeys.some(k => want?.parameters?.[k] !== undefined);
  const byReason: boolean = launchParam?.launchReason === AbilityConstant.LaunchReason.APP_RECOVERY &&
    deviceInfo.sdkApiVersion >= 26;
  return bySysKey || byRestoreKey || byReason;
}
```

判定恢复启动后，即可针对恢复启动单独处理：不执行正常冷启动时的部分初始化，改为从want.parameters取回上次保存的数据，并跳过广告页、自动跳首页等自动跳转：

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

## 数据恢复

适用：不需要恢复页面栈（可接受恢复启动后回到首页）、但有未持久化的临时数据（草稿、阅读进度、表单内容等）需要恢复的应用。系统不会恢复应用运行时状态（全局变量、用户数据、自定义业务数据），需要开发者通过[onSaveState()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestate)自行保存恢复。

### 最小适配

临时数据（非持久化的页面状态、页面路径等）通过`onSaveState()`写入`wantParam`，恢复启动时从`want.parameters`读回。

适用条件有两条：

- **数据可序列化**：只含string、number、boolean、数组等可序列化类型的字段。含Function、Callback、Proxy、类实例、Map/Set等无法序列化的字段时，这些字段不会被保存且系统不报错，须先按[函数与类实例等字段的转换](#函数与类实例等字段的转换)替换为字符串、uri等可序列化形式；
- **数据总量远低于总大小上限200KB**：任一单项数据接近或超过上限时，按[超大数据分流](#超大数据分流)保存到文件。

保存与恢复分四步流程：

1. 页面在数据变化时把需要保存的数据写入AppStorage；
2. `onSaveState()`同步读取AppStorage写入wantParam，返回`ALL_AGREE`；
3. 恢复启动时，`onCreate()`把`want.parameters`中的数据写入AppStorage，供页面挂载后读取；
4. 页面挂载后先读取恢复数据，**读取先于正常初始化、恢复路径直接return**，防止正常初始化把恢复数据覆盖回默认值。

第1步：页面在数据变化时把需要保存的数据写入AppStorage。数据用字面量对象即可，只放可序列化的轻量字段：

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

第2步：`onSaveState()`只做同步读取：

<!-- @[restore_on_save_state](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/entryability/RestoreAbility.ets) -->

``` TypeScript
onSaveState(reason: AbilityConstant.StateType,
  wantParam: Record<string, Object>): AbilityConstant.OnSaveResult {
  // 只做同步读取：页面平时已把状态发布到 AppStorage（见 ReaderPage 的 reportState）
  const st = AppStorage.get<Record<string, Object>>(KEY_READER_STATE);
  if (st !== undefined) {
    wantParam[KEY_RESTORE_READER] = st;
  }
  // 草稿超过分流阈值（示例取 2048 字节，可按业务调整）走落盘引用，want.parameters 只放文件名
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

第3步：`onCreate()`判定恢复启动（判定规则见[判定恢复启动](#判定恢复启动)），把恢复数据写入AppStorage：

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

第4步：页面挂载后读取恢复数据：

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
    // 草稿统一经独立恢复键中转（短草稿随数据带回、长草稿按文件名读回），不在状态对象里
    const draft = AppStorage.get<string>('restore.reader.draft');
    if (draft !== undefined) {
      AppStorage.delete('restore.reader.draft');
      this.draft = draft;
    }
    this.source = '恢复启动';
    this.reportState();
    return; // 不走正常冷启初始化
  }
}
```

> **说明：**上例只展示了恢复分支——`if`内处理完恢复数据即`return`，不再执行正常初始化。正常冷启动时`restored`为undefined，`if`不成立，方法继续向下执行按业务加载默认数据（本示例的默认数据在onReady的handleParam中处理）。即恢复启动与正常冷启动走同一方法的不同分支，并不是该方法只处理恢复。

**使用要点**：

- onSaveState()在系统触发备份的短暂时间窗内被调用，**只做同步读取**，不能在这里才异步采集数据，也不要做耗时操作——超时或异常可能导致本次数据不保存；
- 恢复数据仅随恢复启动的这一次Want带回，后续启动不再携带；应用读取后应即从AppStorage删除，防止重复读取；
- 若数据已持久化（preferences/RDB/文件），不要通过`onSaveState()`保存——进程重建后持久化数据仍在，保存的数据里只存定位键。

> **注意：multiton多实例需按实例隔离AppStorage数据**
>
> [AppStorage](../reference/apis-arkui/arkui-ts/ts-state-management.md#appstorage)由整个应用进程共用，multiton模式启动的多个UIAbility实例运行在同一进程，即共用同一份AppStorage：多个实例都用同一个名字（如`reader.state`）存数据时，后写入的会覆盖先写入的，保存的数据错乱。
>
> 隔离做法：在数据名字前加上实例自己的标识，三处保持一致——页面写入、`onSaveState()`保存、`onCreate()`读回都用`` `${instanceKey}:reader.state` ``这个名字。标识直接使用启动该实例时在want参数中传入的实例名`instanceKey`（由应用自己定义并传入，创建实例与恢复启动时都能从want中拿到）。
>
> 清理时机与单实例相同：实例读取完自己的恢复数据后，立即从AppStorage删除，避免下次误读旧数据。

### 持久化优先

已通过[Preferences](../reference/apis-arkdata/js-apis-data-preferences.md)、[RDB](../reference/apis-arkdata/js-apis-data-rdb.md)或文件保存的数据在进程被回收后仍然存在，恢复启动后按常规方式从磁盘读回即可，**不要把已持久化的数据再写入备份快照**——快照里只存**定位键**（如preferences键名、表名+主键、文件名），页面挂载后按定位键重新读取。这样既避免快照超限，也避免快照与磁盘双份数据不一致。

### 超大数据分流

任一适配方案下存在单项数据接近或超过want.parameters序列化后总大小上限200KB（如未提交的长文本草稿），直接放want.parameters会超限，或使页面栈数据无法完整保存。做法：数据本体写入应用沙箱文件，want.parameters中只放**文件名**（恢复时按文件名读回，读不到按空数据降级）：

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

onSaveState()按数据长度分流（短数据直接放，超长保存到文件，见[最小适配](#最小适配)onSaveState()示例中的草稿分支。示例中的2048字节仅为分流阈值的示例取值，可按业务调整——系统约束是快照序列化后总大小上限200KB，接近该量级的数据都应保存到文件）；onCreate()读回时`loadBlob(...) ?? ''`读不到降级为空。非恢复启动时清理过期文件（示例工程按7天清理，与系统备份数据过期时间对齐），防止残留堆积。

## 页面栈恢复：Navigation

适用：使用Navigation的中大型应用——用户被回收前停留在第3层甚至更深的页面时，若只恢复数据、回到首页，用户之前逐级打开的页面全部丢失，需从头逐级点回原页面；此类应用需要同时恢复页面栈。

### 三项配置

Navigation的页面栈恢复需要以下三项配置，其中第1、2项必须同时设置：

1. Navigation设置通用属性[id()](../reference/apis-arkui/arkui-ts/ts-universal-attributes-component-id.md#id)（恢复按id匹配）。
2. Navigation设置[recoverable(true)](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#recoverable14)。
3. NavDestination设置[recoverable](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#recoverable14)属性，不需要恢复的页面显式设置`.recoverable(false)`。

三个开关的默认值如下：

| 开关 | 默认值 | 效果 |
|---|---|---|
| [setRestoreEnabled()](#开启备份恢复)（UIAbility级总开关） | false | 不开启则系统不保存/恢复任何数据。 |
| Navigation的recoverable（API版本14+） | false | 不开启则整个Navigation组件的页面栈不参与恢复。 |
| NavDestination的recoverable（API版本14+） | **true** | Navigation开启后，未显式设置的子页面默认全部参与恢复。 |

> **说明：**
>
> NavDestination的recoverable默认值为true。这意味着Navigation一旦开启recoverable(true)，其下所有NavDestination（含广告页、登录页、活动页等）默认全部参与恢复。系统恢复时只还原页面组件结构与启动参数，未做参数为空降级处理的页面恢复后参数为空，表现为白屏。因此**选择性恢复的推荐做法是反向排除**：不参与恢复的页面必须逐个显式设置`.recoverable(false)`，"不写recoverable"不等于"不恢复"。

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
    Button('router页面恢复示例')
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
// 三件套之 2：默认 false，必须显式开启（API版本14+）
.recoverable(true)
.mode(NavigationMode.Stack)
```

页面级（NavDestination）在完成数据保存与恢复（见[数据恢复](#数据恢复)）与参数为空降级处理后开启：

``` TypeScript
NavDestination() {
  // 页面内容
}
.title('阅读页（断点续读）')
.onReady((ctx: NavDestinationContext) => {
  this.handleParam(ctx);
})
// 三件套之页面级：数据通道与空值兜底完成后才允许开启（API版本14+）
.recoverable(true)
```

不参与恢复的页面（如广告页）必须显式排除，否则因默认值为true会被一并恢复：

``` TypeScript
NavDestination() {
  // 广告页等无需恢复的页面内容
}
.title('广告页')
// 默认值是 true，不写就会被恢复——不参与恢复必须显式排除
.recoverable(false)
```

**三项配置使用要点**：

- 只有**参数可序列化且已做参数为空降级处理**的页面才可参与恢复；广告页、登录页等无需恢复的页面因NavDestination默认值为true，**必须显式设置`.recoverable(false)`排除**——不设置不等于不恢复；
- **页面名必须静态稳定**：系统恢复按NavDestination的name在PageMap中匹配页面，运行时动态拼接或加密生成的页面名，恢复时匹配不上，该页面无法恢复。此类工程需把页面名改为静态常量；确需加密的改为加密param，页面名保持明文静态；
- **懒加载页面需保证恢复时映射可解析**：PageMap中懒加载（动态import等）的页面，需保证恢复启动时按name能同步取到组件（如预注册name到组件构建器的映射，或在补齐前完成动态加载），否则恢复的页面无法构建；
- 若工程入口是广告页/闪屏页，恢复启动时须跳过自动跳页逻辑，否则广告页会覆盖恢复出的栈顶页——处理方法见[恢复期间不要自动跳页](#恢复期间不要自动跳页)。

### 参数为空降级

正常启动时，页面的param由跳转方传入；恢复启动时，页面由系统按页面名重新挂载，param中无法序列化的字段会被直接丢弃且不报错，因此param可能为空或残缺。**框架没有通用的防白屏机制**，页面必须在onReady()中处理param为空的情况，按三条路径降级：

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
    // 草稿经独立恢复键中转，不在状态对象里
    const draft = AppStorage.get<string>('restore.reader.draft');
    if (draft !== undefined) {
      AppStorage.delete('restore.reader.draft');
      this.draft = draft;
    }
    this.source = '恢复启动';
    this.reportState();
    return;
  }
  // 兜底：退回上一页
  ctx.pathStack?.pop();
}
```

第三条路径不一定要用`pop()`退出本页，留在本页加载默认数据也可以，由应用按业务决定。示例采用`pop()`：栈内还有上一页时退回上一页；本页是栈内唯一页面时，Navigation显示主页——即应用刚启动、未打开任何子页面时的那个页面。

### 深层栈补齐

Navigation页面栈恢复不保证覆盖全部层级，更深层级需应用自行补齐：从系统已恢复层级的下一层起，按保存的路径逐层重新执行页面跳转（pushPath），把缺失的页面压回导航栈。

**按保存的页面路径补齐**——在导航栈每次变化后（进入、返回、替换，示例通过NavPathStack的[setInterception](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#setinterception12)统一监听）把当前页面路径（从首页到当前页逐级记录的页面名序列）写入AppStorage（onSaveState()同步读取，方法见[数据恢复](#数据恢复)）；恢复启动后在首页`onPageShow()`按保存的路径补齐缺失的更深层级。

补齐时机：**首页onPageShow()**——此时系统页面栈恢复已完成、页面已渲染。不要在loadContent()回调中补齐：回调执行时系统还没把恢复的页面压回栈里，应用先压入的页面会和系统随后恢复的页面叠在一起，用户可能看到页面重复或顺序错乱：

<!-- @[deep_stack_replay_timing](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RestoreIndex.ets) -->

``` TypeScript
onPageShow(): void {
  // 深栈补推时机：此时系统栈恢复已完成、页面已渲染；禁止提前到 loadContent 回调
  // （系统恢复尚未执行，会互相冲突）。恢复启动时首页的自动跳转（如广告页）必须跳过，
  // 否则会覆盖系统恢复出的栈顶页。
  this.replayDeepStack();
}
```

平时发布页面路径：

<!-- @[nav_snapshot_report](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RestoreIndex.ets) -->

``` TypeScript
aboutToAppear(): void {
  // 栈变化统一监听：进入、返回、替换后都更新快照，避免只覆盖进入场景
  this.pathStack.setInterception({
    didShow: () => {
      this.reportNavSnapshot();
    }
  });
}

/** 栈变化后把路径快照发布到 AppStorage，onSaveState 同步读取。 */
private reportNavSnapshot(): void {
  AppStorage.setOrCreate(KEY_NAV_SNAPSHOT, JSON.stringify(this.pathStack.getAllPathName()));
}
```

恢复后逐层补齐：

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
  } catch (_) {
    // 快照损坏则跳过补推，停在已恢复页不白屏；打日志便于排障
    hilog.warn(DOMAIN, TAG, 'replayDeepStack skipped: broken snapshot');
  }
}
```

**使用要点**：

- 补齐的页面param按空对象传入，页面数据按[数据恢复](#数据恢复)的方法恢复——页面路径只存页面名，各页数据在页面挂载后自行读取或重新加载，不要试图把原始param一并保存；
- 页面路径只存页面名、不带参数：跳转时把函数、类实例等放进param的页面，这些字段无法随页面路径保存，要先做[函数与类实例等字段的转换](#函数与类实例等字段的转换)。

## 页面栈恢复：Router

使用@ohos.router的应用不需要[页面栈恢复：Navigation](#页面栈恢复navigation)中的三项配置：router页面的`recoverable`属性默认为**true**（API版本14起），已打开的页面栈由系统自动恢复，无需应用做页面栈改造。唯一要做的页面栈相关工作是排除不需要恢复的页面（广告页等），通过`recoverable: false`显式排除：

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

## 页面栈恢复：三方路由

应用使用HMRouter（@hadss/hmrouter）等基于uri的三方路由框架，或自研路由时，系统的页面栈恢复不作用于三方路由内部，[页面栈恢复：Navigation](#页面栈恢复navigation)的三项配置不可用。此类应用需要自己恢复页面栈，做法是**保存路由信息（uri与参数），恢复启动后逐层重新执行跳转**。uri天然可序列化，onSaveState()只需保存轻量路由信息（uri与可序列化参数），恢复启动后由应用按路由信息逐层重新执行跳转，具体分三步：

1. **页面登记**：维护"页面名 → 路由信息"的映射，路由信息只含uri与可序列化参数；
2. **保存**：onSaveState()把当前路由路径的路由信息列表写入wantParam；
3. **重新跳转**：onCreate()判定恢复启动后把路由信息列表写入AppStorage，在首页onPageShow()（once语义，避免重复触发）按路由信息逐层重新执行路由跳转。

``` TypeScript
// 伪代码示意（HMRouter 需按其路由 API 调整跳转调用）
onSaveState(reason: AbilityConstant.StateType,
  wantParam: Record<string, Object>): AbilityConstant.OnSaveResult {
  // 路由信息：uri天然可序列化；param含函数、类实例等字段时，须先转换为可序列化形式
  const routes: RouteCredential[] = RouteRegistry.snapshot(); // [{uri, param}, ...]
  wantParam['restore.routes'] = routes;
  return AbilityConstant.OnSaveResult.ALL_AGREE;
}

// 首页 onPageShow 中：
const routes = AppStorage.get<RouteCredential[]>('restore.routes');
if (routes !== undefined) {
  AppStorage.delete('restore.routes'); // 恢复数据仅随恢复启动的这一次携带，读后即删
  for (const r of routes) {
    this.router.push(r.uri, r.param); // 按所用路由框架的API重新执行跳转
  }
}
```

**使用要点**：

- 重新跳转期间，应用的"自动跳首页/重定向登录"等自动导航逻辑必须跳过，否则重新执行的跳转会被自动跳转覆盖——处理方法见[恢复期间不要自动跳页](#恢复期间不要自动跳页)；
- 本方案demo不随示例工程提供（依赖三方路由包）。HMRouter场景若愿意为其内部Navigation设置id+recoverable，也可选用[页面栈恢复：Navigation](#页面栈恢复navigation)三项配置方案，但HMRouter内部Navigation实例不易注入属性，默认推荐本方案。

## 通用适配要点

以下内容各场景通用。

### 函数与类实例等字段的转换

Want parameters的值只支持String/Number/Boolean等基本类型以及由它们组成的对象和数组。**函数、Map/Set、Date、类实例无法序列化，无法通过`onSaveState()`保存，须先按以下方式转换**（`onSaveState()`写入wantParam的数据与页面的param同理——param中这类字段在恢复时会被直接丢弃）：

| 原字段类型 | 处理方式 |
| --- | --- |
| string / number / boolean | 直接保留 |
| 由基本类型组成的普通对象 | 直接保留 |
| Function / Callback | 删除，页面改为从AppStorage或注册表重新获取 |
| 类实例（MediaItem、PhotoAsset等） | 替换为定位键（如uri、id），页面挂载后按定位键重新查询 |
| Map / Set / Date | 转换为普通对象或序列化字符串（如JSON.stringify后随字符串传输） |
| 已持久化的数据（preferences/RDB/文件） | 不通过`onSaveState()`保存（进程重建后仍在），只存定位键 |

回调函数、Proxy对象等复杂对象同样无法通过`onSaveState()`保存，须按上表方式替换。表中两个概念说明：

- **定位键**：能重新查回完整数据的轻量字段，如uri、id、preferences键名、文件名——页面挂载后按定位键重新查询或读取原数据；
- **注册表**：应用在内存中维护的"名字 → 函数/对象"的映射表（应用每次启动时注册）——页面挂载后按名字从表中取回函数或对象，再重新绑定。

### 恢复期间不要自动跳页

应用里"启动后自动跳首页/自动切Tab/重定向登录/进广告页"等导航逻辑，在恢复启动时会覆盖系统恢复的页面栈。做法：用一个普通布尔变量记录恢复流程是否结束——`onCreate()`判定为恢复启动时把变量置为`false`；首页`onPageShow()`触发时（此时系统页面栈恢复已完成），等应用的补齐或重新跳转执行完毕再把变量置为`true`。上述自动跳转逻辑执行前先检查该变量：为`false`时本次跳过，为`true`后恢复正常导航。

## 常见问题

**恢复后页面白屏，如何排查？**

优先检查该页面的param是否为空或残缺：恢复启动时页面由系统按页面名重新挂载，param中无法序列化的字段会被直接丢弃且不报错。若页面在`onReady()`中未处理param为空的情况，会因拿不到数据而白屏。请按[参数为空降级](#参数为空降级)补齐降级处理；param含函数、类实例等字段的，先按[函数与类实例等字段的转换](#函数与类实例等字段的转换)转换。

**恢复后栈顶是广告页/闪屏页，原页面被覆盖？**

应用的自动跳页逻辑（自动跳首页、进广告页、重定向登录等）在恢复启动时执行，会盖住系统恢复出的页面。按[恢复期间不要自动跳页](#恢复期间不要自动跳页)处理：恢复流程结束前跳过这些自动跳转。

**Navigation与router混用的应用，恢复后页面重复或返回顺序错乱？**

两套页面栈恢复同时开启会互相破坏，典型表现即页面被重复恢复、恢复出的栈顶页被另一套覆盖、返回栈顺序错乱。以应用的主框架为准，只保留一套恢复路径。

**multiton模式下多个实例的恢复数据互相覆盖？**

多个UIAbility实例共用同一份AppStorage，用同一个名字存数据时，后写入的会覆盖先写入的。隔离方法见[数据恢复](#数据恢复)章"multiton多实例需按实例隔离AppStorage数据"的说明：数据名字前加上实例自己的标识。

**恢复数据读不到或读取失败，如何降级？**

整体原则：恢复数据缺失时，页面应能按默认数据正常展示，不要因恢复失败而阻塞启动。走文件分流的超大数据读不到文件时按空数据降级（见[超大数据分流](#超大数据分流)）；已持久化的数据不依赖恢复，直接从磁盘读回（见[持久化优先](#持久化优先)）。

## 相关实例

示例工程[UIAbilityRecover](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Ability/UIAbilityRecover)（applications_app_samples仓的`code/DocsSample/Ability/UIAbilityRecover`目录）覆盖本文各适配场景：数据保存与恢复、Navigation页面栈恢复（含参数为空降级与深层栈补齐）、Router页面排除、超大数据分流。将仓库导入DevEco Studio后运行该工程，按各示例页面内的提示操作即可对照验证本文的适配效果。
