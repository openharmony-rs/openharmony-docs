# UIAbility备份恢复适配指导

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhang_hao_zheng-->
<!--Designer: @wendel-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

## 概述

系统内存紧张时会回收后台应用进程。应用被回收后，用户再次打开只能回到首页，此前的页面与操作上下文全部丢失。例如：用户在地铁乘车码页面退至后台，应用被回收；再次点击桌面图标即可回到乘车码页面完成出站。接入备份恢复后，应用可恢复到回收前的页面与数据。

本机制自API版本14起支持，涉及的接口与属性（setRestoreEnabled()、Navigation/NavDestination/router的recoverable）均自API版本14起提供

按下表选择适配方法：先在"路由形态"列找到应用所属的行组，再在"应用特征"列匹配具体行。

| 路由形态 | 应用特征 | 典型场景 | 适配方法 | 详见 |
| --- | --- | --- | --- | --- |
| 不恢复页面栈（单页/多页均可） | 无未持久化的临时数据 | 简单工具类应用 | 无需适配 | - |
| 不恢复页面栈（单页/多页均可） | 有未持久化的临时数据 | 计算器历史记录、备忘录草稿 | 开启总开关 + onSaveState()保存数据 | [数据恢复](#数据恢复) |
| Navigation | 页面栈较浅 | 出行码页、设置二级页 | 三项配置 + 数据保存与恢复 + 参数为空降级 |  [三项配置](#三项配置)、[参数为空降级](#参数为空降级) |
| Navigation | 存在深层页面 | 阅读器逐章深跳、商品多级筛选 | 三项配置 + 数据保存与恢复 + 参数为空降级 + 深层栈补齐 | [深层栈补齐](#深层栈补齐) |
| Navigation | 页面名动态生成/加密或懒加载 | 页面名混淆、按需加载的工程 | 先静态化页面名、保证PageMap可解析，再按Navigation方案适配 | [三项配置](#三项配置) |
| @ohos.router | - | 使用router.pushUrl的工程 | 为无需恢复的页面设置recoverable(false) | [页面栈恢复：Router](#页面栈恢复router) |
| 三方路由框架（HMRouter等） | - | 基于三方框架路由的工程 | 保存路由信息（uri与参数），恢复后逐层重放跳转 | [页面栈恢复：三方路由](#页面栈恢复三方路由) |

> **说明：**
>
>  - 所有方案的第一步均为[开启备份恢复](#开启备份恢复)。
> - 页面参数含函数、类实例等不可序列化字段、单条数据接近200KB上限、需区分恢复启动与正常启动等问题的处理，分别见[处理无法序列化的字段](#处理无法序列化的字段)、[超大数据分流](#超大数据分流)、[判定恢复启动](#判定恢复启动)。


## 约束与限制

### 功能限制
- 应用正常关闭不触发备份；正常启动时不触发恢复。
- 备份恢复机制依赖任务保留机制：设置`removeMissionAfterTerminate`为true或设备不支持任务保留（如PC/2in1设备）时，备份恢复不生效。
- [UIExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md)不支持备份恢复。

### 规格限制
备份数据默认保存7天，过期后自动删除。

## 适配准备

### 开启备份恢复

所有适配方案的第一步，在UIAbility的`onCreate()`中调用[setRestoreEnabled](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#setrestoreenabled14)并传入true，不开启则系统不会保存/恢复任何数据：

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
> 不需要恢复页面栈（可接受恢复启动后回到首页）的应用，完成“开启总开关 + [onSaveState()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestate)保存数据 + 启动时读回”即完成适配，无需页面栈改造。写法见[数据恢复](#数据恢复)。

### 判定恢复启动

恢复场景下[launchParam.launchReason](../reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#launchparam)取值为`APP_RECOVERY`。但API版本26.0.0之前的系统版本中，launchReason不能单独作为恢复启动的判定依据，需要组合检查以下条件（按可靠性排序）：

| 判定条件 | 可靠性 | 说明 |
| --- | --- | --- |
| 系统设置的恢复重启标记`ohos.ability.params.abilityRecoveryRestart`为`true` | 全版本可靠 | 恢复启动时由系统合并进want.parameters，恢复启动一定为true。 |
| want.parameters中带回了本应用保存的数据 | 高 | 这些数据只在恢复启动时由系统合并回来，API版本26.0.0之前最可靠的判断依据。 |
| launchReason === APP_RECOVERY | API版本26.0.0及以上可靠 | API版本26.0.0起可单独成立；之前版本只能作为辅助条件，与前两个条件联合判定。 |

以下示例将上述条件的组合判断封装成一个普通函数`isRestoreLaunch`，调用时将onSaveState()写入want.parameters的全部键名通过`restoreKeys`参数传入：

<!-- @[restore_launch](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/common/RestoreUtil.ets) -->

``` TypeScript
/**
 * 组合判断是否恢复启动：恢复重启标记为 true（全版本可靠）/ want.parameters 中
 * 存在 onSaveState() 保存的数据（仅恢复启动时由系统带回）/ launchReason 为
 * APP_RECOVERY（API版本26.0.0 起可信，之前版本不能单独采信）。
 * restoreKeys：onSaveState() 写入 want.parameters 的全部键名。
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

判定为恢复启动后，本次启动按恢复流程处理：跳过正常冷启动的初始化逻辑，从want.parameters取回上次保存的数据（onCreate()中的完整写法见[数据恢复](#数据恢复)第3步），并按下一节的说明跳过广告页、自动跳首页等自动跳转。

### 跳过恢复期间的自动跳页

应用里“启动后自动跳首页/自动切Tab/重定向登录/进广告页”等导航逻辑，在恢复启动时会覆盖系统恢复的页面栈，须在恢复流程结束前跳过。

用一个布尔变量标记恢复流程是否结束：

1. `onCreate()`判定为恢复启动时，将该变量置为`false`；
2. 自动跳转逻辑执行前先检查该变量，为`false`时本次跳过；
3. 首页`onPageShow()`触发时系统页面栈恢复已完成，等应用的补齐或重新跳转执行完毕后再置为`true`，恢复正常导航。

### 处理无法序列化的字段

Want.parameters的值只支持String/Number/Boolean等基本类型以及由它们组成的对象和数组。函数、回调、Map/Set、Date、Proxy、类实例等复杂对象无法序列化，无法通过`onSaveState()`保存，须先按以下方式处理。`onSaveState()`写入wantParam的数据与页面的param同理，param中这类字段在恢复时会被直接丢弃。

| 原字段类型 | 处理方式 |
| --- | --- |
| string / number / boolean | 直接保留 |
| 由基本类型组成的普通对象 | 直接保留 |
| Function / Callback | 删除；页面改为从AppStorage重新获取，或按名字从应用启动时注册的"名字到函数"映射表取回 |
| 类实例（MediaItem、PhotoAsset等） | 替换为uri、id等可重新查回数据的字段，页面挂载后重新查询 |
| Map / Set / Date | 转换为普通对象或序列化字符串（如JSON.stringify后随字符串传输） |

> **说明：**
>
> 已持久化的数据（preferences/RDB/文件）不通过`onSaveState()`保存——进程重建后持久化数据仍在，快照中只存键名、文件名等能重新查回数据的轻量信息。

## 数据恢复

适用于不需要恢复页面栈（可接受恢复启动后回到首页）、但有未持久化的临时数据（草稿、阅读进度、表单内容等）需要恢复的应用。系统不会恢复应用运行时状态（全局变量、用户数据、自定义业务数据），需要开发者通过[onSaveState()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestate)自行保存恢复。

### 最小适配

临时数据（非持久化的页面状态、页面路径等）通过`onSaveState()`写入`wantParam`，恢复启动时从`want.parameters`读回。

保存的数据须同时满足两个条件：

- 可序列化：只含string、number、boolean及由它们组成的对象、数组。含Function、Callback、Proxy、类实例、Map/Set等无法序列化的字段时，这些字段会被静默丢弃且系统不报错，须先替换为字符串、uri等可序列化形式，见[处理无法序列化的字段](#处理无法序列化的字段)。
- 总量远低于200KB上限：单项数据接近或超过上限时，按[超大数据分流](#超大数据分流)保存到文件。

1. 页面在数据变化时把需要保存的数据写入AppStorage。数据用字面量对象即可，只放可序列化的轻量字段：

   <!-- @[reader_state_report](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/ReaderPage.ets) -->

   ``` TypeScript
   /** 状态变化时把数据发布到 AppStorage，onSaveState 同步读取；只放可序列化的轻量数据。 */
   private reportState(): void {
     AppStorage.setOrCreate('reader.state', {
       'bookId': this.bookId,
       'chapterIndex': this.chapterIndex,
       'progress': this.progress
     } as Record<string, Object>);
     // 草稿单独发布，onSaveState 按长度决定随数据保存还是保存到文件
     AppStorage.setOrCreate('reader.draft', this.draft);
   }
   ```

2. `onSaveState()`同步读取AppStorage写入wantParam，返回`ALL_AGREE`

   <!-- @[restore_on_save_state](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/entryability/RestoreAbility.ets) -->

   ``` TypeScript
   onSaveState(reason: AbilityConstant.StateType,
     wantParam: Record<string, Object>): AbilityConstant.OnSaveResult {
     // 只做同步读取：页面平时已把状态发布到 AppStorage（见 ReaderPage 的 reportState）
     const st = AppStorage.get<Record<string, Object>>(KEY_READER_STATE);
     if (st !== undefined) {
       wantParam[KEY_RESTORE_READER] = st;
     }
     // 草稿超过分流阈值（示例取 2048 字节，可按业务调整）保存到文件，want.parameters 只放文件名
     const draft = AppStorage.get<string>(KEY_READER_DRAFT) ?? '';
     if (draft.length > 2048) {
       wantParam[KEY_RESTORE_DRAFT_FILE] = saveBlob(this.context, 'reader', draft);
     } else if (draft !== '') {
       wantParam[KEY_RESTORE_DRAFT] = draft;
     }
     // 深层栈补齐用的页面路径
     const navSnapshot = AppStorage.get<string>(KEY_NAV_SNAPSHOT);
     if (navSnapshot !== undefined) {
       wantParam[KEY_RESTORE_NAV_PATH] = navSnapshot;
     }
     // 必须返回 ALL_AGREE，否则数据不保存
     return AbilityConstant.OnSaveResult.ALL_AGREE;
   }
   ```

3. 恢复启动时，`onCreate()`把`want.parameters`中的数据写入AppStorage，供页面挂载后读取：

   <!-- @[restore_on_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/entryability/RestoreAbility.ets) -->

   ``` TypeScript
   onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
     // 开启备份恢复总开关：不开启则系统不会保存/恢复任何数据
     this.context.setRestoreEnabled(true);

     // 判断是否恢复启动（restoreKeys 传入 onSaveState() 写入的全部键名）
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
       // 深层栈补齐用的页面路径
       const navPath = want?.parameters?.[KEY_RESTORE_NAV_PATH] as string | undefined;
       if (navPath !== undefined) {
         AppStorage.setOrCreate(KEY_RESTORE_NAV_PATH, navPath);
       }
     } else {
       // 正常冷启动：清理过期的数据文件
       cleanupBlob(this.context);
     }
   }
   ```

4. 页面挂载后先读取恢复数据，**读取先于正常初始化、恢复路径直接return**，防止正常初始化把恢复数据覆盖回默认值：

   <!-- @[page_consume](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/ReaderPage.ets) -->

   ``` TypeScript
   aboutToAppear(): void {
     // 读取恢复数据：从 AppStorage 取出即删，防止重复读取
     const restored = AppStorage.get<Record<string, Object>>('restore.reader');
     if (restored !== undefined) {
       AppStorage.delete('restore.reader');
       this.restoredFromChannel = true;
       this.bookId = (restored['bookId'] as string) ?? '';
       this.chapterIndex = (restored['chapterIndex'] as number) ?? 1;
       this.progress = (restored['progress'] as number) ?? 0;
       // 草稿单独经 AppStorage 中转（短草稿随数据带回、长草稿按文件名读回），不在状态对象里
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

> **说明：**
>
> - `onSaveState()`在系统触发备份的短暂时间窗内被调用，只做同步读取、必须返回`ALL_AGREE`（否则数据不落盘）；不要在这里异步采集或做耗时操作，超时或异常可能导致本次数据不保存。确有异步需求时改用[onSaveStateAsync()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestateasync20)（API版本20起，实现了异步版后系统不再调用同步版）。
> - 恢复数据仅随恢复启动的这一次Want带回，后续启动不再携带；读取后立即从AppStorage删除，防止重复读取。
> - multiton模式下多个UIAbility实例共用进程级[AppStorage](../reference/apis-arkui/arkui-ts/ts-state-management.md#appstorage)，同一键名（如`reader.state`）后写覆盖先写，页面写入、`onSaveState()`保存、`onCreate()`读回统一使用`${instanceKey}:reader.state`带实例标识的键名（`instanceKey`为应用自定义、经want参数传入的实例名，创建与恢复启动时均可获取）。

### 持久化优先

已通过[Preferences](../reference/apis-arkdata/js-apis-data-preferences.md)、[RDB](../reference/apis-arkdata/js-apis-data-rdb.md)或文件持久化的数据，进程被回收后仍然存在，恢复启动后按常规方式从磁盘读回即可，不要重复写入onSaveState()。onSaveState()中只保存能据此查回完整数据的轻量信息（如Preferences键名、表名加主键、文件名），页面挂载后按这些信息重新从磁盘读取。这样既避免超出200KB总大小上限，也避免与磁盘数据形成双份不一致。

### 超大数据分流

want.parameters序列化后的总大小上限为200KB。当单项数据接近该上限时（如未提交的长文本草稿），直接放入want.parameters会挤占总量配额，导致其他数据甚至页面栈数据无法完整保存。

处理方式：数据本体写入应用沙箱文件，want.parameters中只保存文件名；恢复启动时按文件名读回，读不到则按空数据降级。

<!-- @[blob_save](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/common/RestoreUtil.ets) -->

``` TypeScript
/** 超大数据保存到文件：数据本体写入沙箱文件，返回文件名，want.parameters 只保存文件名。 */
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

onSaveState()按数据长度分流：短数据直接写入wantParam，超长数据保存到文件（写法见[最小适配](#最小适配)中onSaveState()示例的草稿分支）。示例中的2048字节仅为分流阈值的示例取值，可按业务调整；系统的实际约束是保存数据序列化后的总大小上限200KB，接近该量级的数据都应保存到文件。

onCreate()读回时使用loadBlob(...) ?? ''，文件读不到时降级为空字符串。

非恢复启动时清理过期的分流文件（示例工程按7天清理，与系统备份数据的过期时间对齐），防止残留堆积。

## 页面栈恢复：Navigation

适用于使用Navigatio实现页面导航的应用。用户被回收前停留在第3层甚至更深的页面时，若只恢复数据、回到首页，之前逐级打开的页面将全部丢失，用户需从头逐级点回。此类应用需同时恢复页面栈。

### 三项配置

Navigation的页面栈恢复需完成以下配置：

1. 为Navigation设置通用属性[id()](../reference/apis-arkui/arkui-ts/ts-universal-attributes-component-id.md#id)：系统按id匹配并恢复对应的导航组件，必须设置。

2. 为Navigation设置[recoverable](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#recoverable14)属性为true：开启该组件的页面栈恢复，必须设置。

3. 为不需要恢复的NavDestination显式设置[recoverable](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#recoverable14)属性为false：该属性默认值为true，Navigation开启后所有子页面默认参与恢复，广告页、登录页等无需恢复的页面必须逐个排除。

各开关的默认值与作用：

| 开关 | 默认值 | 作用 |
|---|---|---|
| [setRestoreEnabled()](#开启备份恢复)（UIAbility级总开关） | false | 不开启则系统不保存、不恢复任何数据。 |
| Navigation的recoverable | false | 不开启则该组件的页面栈不参与恢复。 |
| NavDestination的recoverable | true | Navigation开启后，未显式设置的子页面默认全部参与恢复。 |

> **说明：**
>
> 系统恢复页面时只还原页面结构与启动参数。未做参数为空降级处理的页面，恢复后参数为空，表现为白屏。因此推荐反向排除：不参与恢复的页面逐个显式设置recoverable为false，"不写recoverable"不等于"不恢复"。

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
    Button('进入第三层页面（深层栈补齐演示）')
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
// 三项配置之 1：恢复按 navigationId 匹配，必须设置
.id('restore-nav')
// 三项配置之 2：默认 false，必须显式开启（API版本14+）
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
// 三项配置之页面级：完成数据保存与恢复、参数为空降级处理后才允许开启（API版本14+）
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

> **说明：**
> - 页面名必须静态稳定：系统恢复时按NavDestination的name在PageMap中匹配页面。运行时动态拼接或加密生成的页面名无法匹配，对应页面不能恢复；此类工程需将页面名改为静态常量。确需加密的，改为加密param，页面名保持明文静态。
> - 懒加载页面需保证恢复时映射可解析：PageMap中懒加载（如动态import）的页面，需保证恢复启动时按name能同步取到组件（如预注册name到组件构建器的映射，或在补齐前完成动态加载），否则恢复的页面无法构建。

### 参数为空降级

正常启动时，页面的param由跳转方传入；恢复启动时，页面由系统按页面名重新挂载，param中无法序列化的字段会被静默丢弃、不报错。序列化对嵌套深度、属性个数、字符串长度等也有上限（由系统内部实现决定，可能变化），超出的属性同样被静默丢弃。因此恢复后的param可能为空或残缺。

框架没有通用的防白屏机制，页面必须在onReady()中主动处理param为空的情况，按三条路径降级：

<!-- @[empty_param_fallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/ReaderPage.ets) -->

``` TypeScript
/** 参数为空降级：恢复的 param 可能为空或残缺，不处理会白屏。 */
private handleParam(ctx: NavDestinationContext): void {
  const param = ctx.pathInfo?.param as Record<string, Object> | undefined;
  // param 有效：按参数重新加载数据
  if (param !== undefined && param['bookId'] !== undefined) {
    this.bookId = param['bookId'] as string;
    if (!this.restoredFromChannel) {
      this.loadFresh();
    }
    return;
  }
  // param 为空：从 AppStorage 取恢复数据
  const restored = AppStorage.get<Record<string, Object>>('restore.reader');
  if (restored !== undefined) {
    AppStorage.delete('restore.reader');
    this.restoredFromChannel = true;
    this.bookId = (restored['bookId'] as string) ?? '';
    this.chapterIndex = (restored['chapterIndex'] as number) ?? 1;
    this.progress = (restored['progress'] as number) ?? 0;
    // 草稿单独经 AppStorage 中转，不在状态对象里
    const draft = AppStorage.get<string>('restore.reader.draft');
    if (draft !== undefined) {
      AppStorage.delete('restore.reader.draft');
      this.draft = draft;
    }
    this.source = '恢复启动';
    this.reportState();
    return;
  }
  // 都取不到：退回上一页
  ctx.pathStack?.pop();
}
```

第三条路径有两种选择，由应用按业务决定：调用pop()退出本页，或留在本页加载默认数据。

示例采用pop()：栈内还有上一页时退回上一页；本页是栈内唯一页面时，Navigation显示主页（应用刚启动、未打开任何子页面时的页面）。

### 深层栈补齐

Navigation页面栈恢复不保证覆盖全部层级，更深层级需应用自行补齐：从系统已恢复层级的下一层起，按保存的页面路径逐层执行pushPath，将缺失的页面重新压入导航栈。

具体分两步：

1. 平时记录页面路径：导航栈每次变化后（进入、返回、替换）都更新记录。示例通过NavPathStack的[setInterception](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#setinterception12)统一监听，将当前页面路径（从首页到当前页的页面名序列）写入AppStorage，由onSaveState()同步读取，写法见[数据恢复](#数据恢复)。
2. 恢复后补齐深层级：恢复启动后，在首页onPageShow()中读取保存的页面路径，将系统未恢复的页面逐层pushPath补齐。

补齐时机必须在首页onPageShow()：此时系统页面栈恢复已完成、页面已渲染。不要在loadContent()回调中补齐：回调执行时系统尚未将恢复的页面压回栈中，应用先压入的页面会与系统随后恢复的页面叠加，用户可能看到页面重复或顺序错乱。

<!-- @[deep_stack_replay_timing](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RestoreIndex.ets) -->

``` TypeScript
onPageShow(): void {
  // 深层栈补齐时机：此时系统栈恢复已完成、页面已渲染；不要提前到 loadContent 回调
  // （系统恢复尚未执行，会互相冲突）。恢复启动时首页的自动跳转（如广告页）必须跳过，
  // 否则会覆盖系统恢复出的栈顶页。
  this.replayDeepStack();
}
```

平时发布页面路径：

<!-- @[nav_snapshot_report](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RestoreIndex.ets) -->

``` TypeScript
aboutToAppear(): void {
  // 栈变化统一监听：进入、返回、替换后都更新页面路径，避免只覆盖进入场景
  this.pathStack.setInterception({
    didShow: () => {
      this.reportNavSnapshot();
    }
  });
}

/** 栈变化后把页面路径发布到 AppStorage，onSaveState 同步读取。 */
private reportNavSnapshot(): void {
  AppStorage.setOrCreate(KEY_NAV_SNAPSHOT, JSON.stringify(this.pathStack.getAllPathName()));
}
```

恢复后逐层补齐：

<!-- @[deep_stack_replay](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RestoreIndex.ets) -->

``` TypeScript
/** 按保存的页面路径补齐系统未恢复的深层级。 */
private replayDeepStack(): void {
  const navPath = AppStorage.get<string>(KEY_RESTORE_NAV_PATH);
  if (navPath === undefined) {
    return;
  }
  AppStorage.delete(KEY_RESTORE_NAV_PATH);
  try {
    const names: string[] = JSON.parse(navPath) as string[];
    const current: string[] = this.pathStack.getAllPathName();
    // 从系统已恢复的层数起逐层补齐；补齐失败则停在已恢复页，不白屏
    for (let i = current.length; i < names.length; i++) {
      this.pathStack.pushPathByName(names[i], {} as Record<string, Object>);
    }
  } catch (_) {
    // 页面路径解析失败则跳过补齐，停在已恢复页不白屏；打日志便于排障
    hilog.warn(DOMAIN, TAG, 'replayDeepStack skipped: invalid navPath');
  }
}
```

> **说明：**
>
> - 补齐的页面param按空对象传入，页面数据按[数据恢复](#数据恢复)的方法恢复——页面路径只存页面名，各页数据在页面挂载后自行读取或重新加载，不要试图把原始param一并保存；
> - 页面路径只存页面名、不带参数：跳转时把函数、类实例等放进param的页面，这些字段无法随页面路径保存，要先做[处理无法序列化的字段](#处理无法序列化的字段)。

## 页面栈恢复：Router

使用@ohos.router的应用无需配置三项恢复开关。router页面的recoverable属性默认为true，已打开的页面栈由系统自动恢复，无需应用做页面栈改造。

需要排除不需要恢复的页面（如广告页），跳转时设置recoverable: false即可。

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

应用使用HMRouter（@hadss/hmrouter）等基于uri的三方路由框架或自研路由时，系统的页面栈恢复不作用于三方路由内部，[Navigation的三项配置](#页面栈恢复navigation)不可用，需应用自行恢复页面栈。uri天然可序列化，适配思路是：onSaveState()中保存轻量的路由信息（uri与可序列化参数），恢复启动后按路由信息逐层重新执行跳转。具体分三步：

1. 页面登记：维护"页面名 → 路由信息"的映射，路由信息只含uri与可序列化参数。
2. 保存：onSaveState()将当前路由路径的路由信息列表写入wantParam。
3. 重新跳转：onCreate()判定为恢复启动后，将路由信息列表写入AppStorage；首页onPageShow()中按列表逐层重新执行跳转。onPageShow()须只执行一次（如通过布尔标记保证），避免重复跳转。

``` TypeScript
// 伪代码示意（HMRouter 需按其路由 API 调整跳转调用）
onSaveState(reason: AbilityConstant.StateType,
  wantParam: Record<string, Object>): AbilityConstant.OnSaveResult {
  // 路由信息：uri天然可序列化；param含函数、类实例等字段时，须先转换为可序列化形式
  const routes: RouteInfo[] = getCurrentRoutes(); // [{uri, param}, ...]
  wantParam['restore.routes'] = routes;
  return AbilityConstant.OnSaveResult.ALL_AGREE;
}

// 首页 onPageShow 中：
const routes = AppStorage.get<RouteInfo[]>('restore.routes');
if (routes !== undefined) {
  AppStorage.delete('restore.routes'); // 恢复数据仅随恢复启动的这一次携带，读后即删
  for (const r of routes) {
    this.router.push(r.uri, r.param); // 按所用路由框架的API重新执行跳转
  }
}
```

> **说明：**
>
> - 重新跳转期间，应用的自动跳首页、重定向登录等自动导航逻辑必须跳过，否则重放的页面会被自动跳转覆盖。处理方法：用[判定恢复启动](#判定恢复启动)的结果置一个布尔标记，恢复流程结束前自动导航逻辑一律不执行。
> - 本方案依赖三方路由包，示例工程未包含该依赖，可按上述伪代码接入。
> - HMRouter场景也可为其内部Navigation设置id和recoverable，复用[Navigation的三项配置](#页面栈恢复navigation)方案；但HMRouter内部的Navigation实例不易注入属性，默认推荐本方案。

## 常见问题

**恢复后页面白屏，如何排查？**

优先检查该页面的param是否为空或残缺。恢复启动时页面由系统按页面名重新挂载，param中无法序列化的字段会被静默丢弃、不报错。若页面未在onReady()中处理param为空的情况，会因拿不到数据而白屏。处理方法见[参数为空降级](#参数为空降级)；param含函数、类实例等字段的，先按[处理无法序列化的字段](#处理无法序列化的字段)做转换。

**恢复后栈顶是广告页/闪屏页，原页面被覆盖？**

应用的自动跳页逻辑（自动跳首页、进广告页、重定向登录等）在恢复启动时执行，覆盖了系统恢复的页面。用[判定恢复启动](#判定恢复启动)的结果置一个布尔标记，恢复流程结束前自动跳页逻辑一律跳过。

**Navigation与router混用的应用，恢复后页面重复或返回顺序错乱？**

两套页面栈恢复同时开启会互相破坏。以应用的主框架为准，只保留一套恢复路径。

**多实例（multiton）模式下，多个实例的恢复数据互相覆盖？**

多个UIAbility实例共用同一份AppStorage，用同一键名存数据时，后写入的会覆盖先写入的。键名前加上实例自身的标识，见[数据恢复](#数据恢复)。

**恢复数据读不到或读取失败，如何降级？**

恢复数据缺失时，页面按默认数据正常展示，不因恢复失败阻塞启动。走文件分流的超大数据读不到文件时按空数据降级（见[超大数据分流](#超大数据分流)）；已持久化的数据不依赖恢复，直接从磁盘读回（见[持久化优先](#持久化优先)）。

**页面参数含函数、回调、Proxy等不可序列化对象，如何处理？**

这类对象无法序列化，无法随保存的数据或param带回，恢复时会被直接丢弃且不报错。按[处理无法序列化的字段](#处理无法序列化的字段)替换为uri、id等可重新查回数据的轻量字段。

**单条数据过大，超出want.parameters序列化后总大小上限（200KB），如何处理？**

按[超大数据分流](#超大数据分流)处理：数据本体写入磁盘，保存的数据里只存文件名，恢复时按文件名读回。

**应用内如何区分恢复启动与正常启动？**

按[判定恢复启动](#判定恢复启动)组合判断三个条件：恢复重启标记为true、want.parameters中带回本应用保存的数据、launchReason为APP_RECOVERY。
