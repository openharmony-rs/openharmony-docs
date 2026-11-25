# UIAbility Backup Restore Adaptation Guide

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhang_hao_zheng-->
<!--Designer: @wendel-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=49800d1a4c8d44f51418a6c913e7bf98f425e6ae translatedAt=2026-11-23T07:51:32.341Z pushedAt=2026-11-24T08:51:34.644Z nl=1 -->

## Overview

When system memory is tight, the system reclaims background application processes. After an application is reclaimed, when the user opens it again, it can only return to the home page, and the previous pages and operation context are all lost. For example: a user moves to the background on the metro ride code page, and the application is reclaimed; tapping the desktop icon again returns to the ride code page to complete the exit. After backup restore is enabled, the application can restore to the page and data before reclamation.

This mechanism is supported from API version 14. The involved interfaces and attributes (setRestoreEnabled(), recoverable of Navigation/NavDestination/router) are all provided from API version 14.

Select the adaptation method according to the following table: first find the row group to which the application belongs in the "Routing Form" column, then match the specific row in the "Application Characteristics" column.

| Routing Form | Application Characteristics | Typical Scenario | Adaptation Method | See |
| --- | --- | --- | --- | --- |
| Do not restore page stack (single page/multi-page both OK) | No unpersisted temporary data | Simple utility applications | No adaptation needed | - |
| Do not restore page stack (single page/multi-page both OK) | Has unpersisted temporary data | Calculator history, memo drafts | Enable master switch + onSaveState() to save data | [Data Restoration](#data-restoration) |
| Navigation | Shallow page stack | Travel code page, settings secondary page | Three configurations + data saving and restoration + empty parameter degrade | [Three Configurations](#three-configurations), [Empty Parameter Degradation](#empty-parameter-degradation) |
| Navigation | Has deep pages | Reader chapter-by-chapter deep jump, product multi-level filtering | Three configurations + data saving and restoration + empty parameter degrade + deep stack fill | [Deep Stack Fill](#deep-stack-fill) |
| Navigation | Page name dynamically generated/encrypted or lazy-loaded | Page name obfuscation, on-demand loading projects | First make page names static, ensure PageMap is resolvable, then adapt according to the Navigation solution | [Three Configurations](#three-configurations) |
| @ohos.router | - | Projects using router.pushUrl | Set recoverable(false) for pages that do not need restoration | [Page Stack Restoration: Router](#page-stack-restoration-router) |
| Third-party routing framework (HMRouter, etc.) | - | Projects based on third-party framework routing | Save routing information (uri and parameters), replay navigation layer by layer after restore | [Page Stack Restoration: Third-Party Routing](#page-stack-restoration-third-party-routing) |

> **Description:**
>
> - The first step of all solutions is [Enable Backup Restore](#enable-backup-restore).
> - For handling page parameters containing non-serializable fields such as functions and class instances, a single data item approaching the 200KB upper limit, and the need to distinguish between restore startup and normal startup, see [Handling Non-serializable Fields](#handling-non-serializable-fields), [Oversized Data Offloading](#oversized-data-offloading), and [Determine Restore Startup](#determine-restore-startup) respectively.


## Constraints

### Functional Limitations
- Normal application shutdown does not trigger backup; normal startup does not trigger restore.
- The backup restore mechanism depends on the task retention mechanism: when `removeMissionAfterTerminate` is set to true or the device does not support task retention (such as PC/2in1 devices), backup restore does not take effect.
- The data backup and restore feature is unavailable for a [UIExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md).

### Specifications
Backup data is saved for 7 days by default and automatically deleted after expiration.

## Adaptation Preparation

### Enable Backup Restore

The first step of all adaptation solutions is to call [setRestoreEnabled](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#setrestoreenabled14) in the UIAbility `onCreate()` and pass in true. If not enabled, the system will not save/restore any data:

``` TypeScript
export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    // Backup restore master switch
    this.context.setRestoreEnabled(true);
  }
}
```

> **Description:**
>
> For applications that do not need to restore the page stack (can accept returning to the home page after restore startup), completing "enable master switch + [onSaveState()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestate) to save data + read back at startup" completes the adaptation, with no need for page stack modification. See the syntax in [Data Restoration](#data-restoration).

### Determine Restore Startup

In the restore scenario, [launchParam.launchReason](../reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#launchparam) takes the value `APP_RECOVERY`. However, in system versions before API version 26.0.0, launchReason cannot be used alone as the basis for determining restore startup. The following conditions need to be checked in combination (sorted by reliability):

| Determination Condition | Reliability | Description |
| --- | --- | --- |
| The restore restart flag `ohos.ability.params.abilityRecoveryRestart` set by the system is `true` | Reliable across all versions | At restore startup, it is merged into want.parameters by the system; it is always true at restore startup. |
| want.parameters brings back the data saved by the application | High | This data is merged back by the system only at restore startup; it is the most reliable basis for determination before API version 26.0.0. |
| launchReason === APP_RECOVERY | Reliable from API version 26.0.0 and above | From API version 26.0.0, it can be established alone; in earlier versions, it can only serve as an auxiliary condition, determined jointly with the first two conditions. |

The following example encapsulates the combined determination of the above conditions into a normal function `isRestoreLaunch`. When calling it, pass all key names written by onSaveState() into want.parameters via the `restoreKeys` parameter:

<!-- @[restore_launch](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/common/RestoreUtil.ets) -->

``` TypeScript
/**
 * Combined determination of whether it is restore startup: the restore restart flag is true (reliable across all versions) / want.parameters contains
 * the data saved by onSaveState() (brought back by the system only at restore startup) / launchReason is
 * APP_RECOVERY (trusted from API version 26.0.0; in earlier versions it cannot be trusted alone).
 * restoreKeys: all key names written by onSaveState() into want.parameters.
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

After being determined as restore startup, this startup is handled according to the restore process: skip the initialization logic of normal cold startup, retrieve the previously saved data from want.parameters (see step 3 of [Data Restoration](#data-restoration) for the complete syntax in onCreate()), and skip automatic jumps such as ad pages and automatic jump to the home page according to the next section.

### Skip Automatic Page Jumps During Restore

Navigation logic in the application such as "automatically jump to the home page after startup / automatically switch Tab / redirect login / enter ad page" will overwrite the page stack restored by the system at restore startup, and must be skipped before the restore process ends.

Use a boolean variable to mark whether the restore process has ended:

1. When `onCreate()` determines it is restore startup, set the variable to `false`;
2. Check the variable before the automatic jump logic executes; when it is `false`, skip this time;
3. When the home page `onPageShow()` is triggered, the system page stack restoration is complete. After the application's fill or re-navigation is executed, set it to `true` to restore normal navigation.

### Handling Non-serializable Fields

The values of Want.parameters only support basic types such as String/Number/Boolean and objects and arrays composed of them. Complex objects such as functions, callbacks, Map/Set, Date, Proxy, and class instances are non-serializable and cannot be saved via `onSaveState()`, and must be handled in the following ways first. The data written by `onSaveState()` into wantParam follows the same principle as the page param; such fields in param will be directly discarded during restoration.

| Original Field Type | Handling Method |
| --- | --- |
| string / number / boolean | Keep directly |
| Plain objects composed of basic types | Keep directly |
| Function / Callback | Delete; the page re-fetches from AppStorage, or retrieves by name from the "name-to-function" mapping table registered at application startup |
| Class instances (MediaItem, PhotoAsset, etc.) | Replace with fields such as uri and id that can re-fetch data, and re-query after page mount |
| Map / Set / Date | Convert to plain objects or serialized strings (such as JSON.stringify and then transmit as a string) |

> **Description:**
>
> Persisted data (preferences/RDB/files) is not saved via `onSaveState()` — after process rebuild, persisted data still exists. Only lightweight information such as key names and file names that can re-fetch data is stored in the snapshot.

## Data Restoration

Applicable to applications that do not need to restore the page stack (can accept returning to the home page after restore startup) but have unpersisted temporary data (drafts, reading progress, form content, etc.) that need to be restored. The system will not restore the application runtime state (global variables, user data, custom business data); developers need to save and restore it on their own via [onSaveState()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestate).

### Minimal Adaptation

Temporary data (non-persisted page state, page path, etc.) is written to `wantParam` via `onSaveState()`, and read back from `want.parameters` at restore startup.

The saved data must satisfy two conditions at the same time:

- Serializable: it contains only string, number, boolean, and objects and arrays composed of them. When it contains non-serializable fields such as Function, Callback, Proxy, class instance, Map/Set, these fields are silently discarded and the system does not report an error. They must first be replaced with serializable forms such as string and uri. See [Handling Non-serializable Fields](#handling-non-serializable-fields).
- The total amount is far below the 200KB upper limit: when a single item of data approaches or exceeds the upper limit, save it to file according to [Oversized Data Offloading](#oversized-data-offloading).

1. When data changes, the page writes the data that needs to be saved into AppStorage. A literal object is sufficient for the data, and only lightweight serializable fields are placed in it:

   <!-- @[reader_state_report](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/ReaderPage.ets) -->

   ``` TypeScript
   /** Publish the data to AppStorage when the state changes, and onSaveState reads it synchronously; only place lightweight serializable data. */
   private reportState(): void {
     AppStorage.setOrCreate('reader.state', {
       'bookId': this.bookId,
       'chapterIndex': this.chapterIndex,
       'progress': this.progress
     } as Record<string, Object>);
     // Publish the draft separately. onSaveState decides by length whether to save it with the data or to file
     AppStorage.setOrCreate('reader.draft', this.draft);
   }
   ```

2. `onSaveState()` synchronously reads AppStorage, writes it into wantParam, and returns `ALL_AGREE`

   <!-- @[restore_on_save_state](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/entryability/RestoreAbility.ets) -->

   ``` TypeScript
   onSaveState(reason: AbilityConstant.StateType,
     wantParam: Record<string, Object>): AbilityConstant.OnSaveResult {
     // Only perform synchronous read: the page has already published the state to AppStorage (see reportState in ReaderPage)
     const st = AppStorage.get<Record<string, Object>>(KEY_READER_STATE);
     if (st !== undefined) {
       wantParam[KEY_RESTORE_READER] = st;
     }
     // When the draft exceeds the offloading threshold (the example uses 2048 bytes, which can be adjusted by business), save it to file, and want.parameters only stores the file name
     const draft = AppStorage.get<string>(KEY_READER_DRAFT) ?? '';
     if (draft.length > 2048) {
       wantParam[KEY_RESTORE_DRAFT_FILE] = saveBlob(this.context, 'reader', draft);
     } else if (draft !== '') {
       wantParam[KEY_RESTORE_DRAFT] = draft;
     }
     // Page path used for deep stack completion
     const navSnapshot = AppStorage.get<string>(KEY_NAV_SNAPSHOT);
     if (navSnapshot !== undefined) {
       wantParam[KEY_RESTORE_NAV_PATH] = navSnapshot;
     }
     // Must return ALL_AGREE, otherwise the data is not saved
     return AbilityConstant.OnSaveResult.ALL_AGREE;
   }
   ```

3. At restore startup, `onCreate()` writes the data in `want.parameters` into AppStorage for the page to read after page mount:

   <!-- @[restore_on_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/entryability/RestoreAbility.ets) -->

   ``` TypeScript
   onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
     // Enable the backup restore master switch: if not enabled, the system will not save/restore any data
     this.context.setRestoreEnabled(true);

     // Determine whether it is restore startup (restoreKeys passes in all key names written by onSaveState())
     const restoreKeys: string[] = [KEY_RESTORE_READER, KEY_RESTORE_DRAFT,
       KEY_RESTORE_DRAFT_FILE, KEY_RESTORE_NAV_PATH];
     if (isRestoreLaunch(want, launchParam, restoreKeys)) {
       // At restore startup, the system places the previously saved data into want.parameters and brings it back (only this once);
       // The page has not been created yet, so transfer it through AppStorage first, and use it after page mount
       const reader = want?.parameters?.[KEY_RESTORE_READER] as Record<string, Object> | undefined;
       if (reader !== undefined) {
         AppStorage.setOrCreate(KEY_RESTORE_READER, reader);
       }
       // Short drafts are brought back with the data; oversized drafts are read back from the sandbox by file name (degrade to empty if it cannot be read)
       const draftInline = want?.parameters?.[KEY_RESTORE_DRAFT] as string | undefined;
       if (draftInline !== undefined) {
         AppStorage.setOrCreate(KEY_RESTORE_DRAFT, draftInline);
       }
       const draftFile = want?.parameters?.[KEY_RESTORE_DRAFT_FILE] as string | undefined;
       if (draftFile !== undefined) {
         AppStorage.setOrCreate(KEY_RESTORE_DRAFT, loadBlob(this.context, draftFile) ?? '');
       }
       // Page path used for deep stack completion
       const navPath = want?.parameters?.[KEY_RESTORE_NAV_PATH] as string | undefined;
       if (navPath !== undefined) {
         AppStorage.setOrCreate(KEY_RESTORE_NAV_PATH, navPath);
       }
     } else {
       // Normal cold startup: clean up expired data files
       cleanupBlob(this.context);
     }
   }
   ```

4. After page mount, read the restore data first. **The read precedes normal initialization, and the restore path returns directly**, to prevent normal initialization from overwriting the restore data back to the default value:

   <!-- @[page_consume](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/ReaderPage.ets) -->

   ``` TypeScript
   aboutToAppear(): void {
     // Read restore data: take it from AppStorage and delete it immediately to prevent duplicate reads
     const restored = AppStorage.get<Record<string, Object>>('restore.reader');
     if (restored !== undefined) {
       AppStorage.delete('restore.reader');
       this.restoredFromChannel = true;
       this.bookId = (restored['bookId'] as string) ?? '';
       this.chapterIndex = (restored['chapterIndex'] as number) ?? 1;
       this.progress = (restored['progress'] as number) ?? 0;
       // The draft is transferred separately through AppStorage (short drafts are brought back with the data, long drafts are read back by file name), and is not in the state object
       const draft = AppStorage.get<string>('restore.reader.draft');
       if (draft !== undefined) {
         AppStorage.delete('restore.reader.draft');
         this.draft = draft;
       }
       this.source = 'restore startup';
       this.reportState();
       return; // Do not go through normal cold-start initialization
     }
   }
   ```

> **Description:**
>
> - `onSaveState()` is called within the short time window when the system triggers backup. It only performs synchronous read and must return `ALL_AGREE` (otherwise the data is not written to disk). Do not perform asynchronous collection or time-consuming operations here; a timeout or exception may cause the data not to be saved this time. When asynchronous requirements do exist, use [onSaveStateAsync()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestateasync20) instead (from API version 20; after the asynchronous version is implemented, the system no longer calls the synchronous version).
> - Restore data is brought back only for this restore startup Want, and is not carried in subsequent startups. Delete it from AppStorage immediately after reading to prevent duplicate reads.
> - In multiton mode, multiple UIAbility instances share the process-level [AppStorage](../reference/apis-arkui/arkui-ts/ts-state-management.md#appstorage). For the same key name (such as `reader.state`), a later write overrides an earlier write. For page writing, `onSaveState()` saving, and `onCreate()` reading back, uniformly use the key name `${instanceKey}:reader.state` with an instance identifier (`instanceKey` is an application-defined instance name passed in via the want parameter, and can be obtained both at creation and at restore startup).

### Persistence First

Data that has already been persisted via [Preferences](../reference/apis-arkdata/js-apis-data-preferences.md), [RDB](../reference/apis-arkdata/js-apis-data-rdb.md), or files still exists after the process is reclaimed. After restore startup, read it back from disk in the normal way, and do not write it into onSaveState() again. In onSaveState(), only save lightweight information from which the complete data can be re-fetched (such as the Preferences key name, table name plus primary key, or file name). After page mount, read from disk again based on this information. This avoids exceeding the 200KB total size limit and also avoids forming two inconsistent copies with the disk data.

### Oversized Data Offloading

The total size limit of want.parameters after serialization is 200KB. When a single item of data approaches this upper limit (such as an unsubmitted long-text draft), placing it directly into want.parameters occupies the total quota, causing other data or even page stack data to be unable to be saved completely.

Handling method: write the data body to an application sandbox file, and store only the file name in want.parameters. At restore startup, read it back by file name; if it cannot be read, degrade to empty data.

<!-- @[blob_save](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/common/RestoreUtil.ets) -->

``` TypeScript
/** Save oversized data to file: write the data body to a sandbox file, return the file name, and want.parameters only stores the file name. */
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

onSaveState() offloads by data length: short data is written directly into wantParam, and oversized data is saved to file (see the draft branch in the onSaveState() example in [Minimal Adaptation](#minimal-adaptation)). The 2048 bytes in the example is only an example value for the offloading threshold and can be adjusted by business. The actual system constraint is the 200KB total size limit of the saved data after serialization; data approaching this magnitude should be saved to file.

When onCreate() reads back, use loadBlob(...) ?? ''; when the file cannot be read, degrade to an empty string.

During non-restore startup, clean up expired offloading files (the example project cleans up by 7 days, aligned with the expiration time of system backup data) to prevent residue accumulation.

## Page Stack Restoration: Navigation

Applicable to applications that use Navigation for page navigation. When the user stays on the third or even deeper page before being reclaimed, if only the data is restored and the application returns to the home page, all previously opened pages are lost, and the user must click through level by level from the beginning. Such applications need to restore the page stack at the same time.

### Three Configurations

The page stack restoration of Navigation requires the following configurations:

1. Set the universal attribute [id()](../reference/apis-arkui/arkui-ts/ts-universal-attributes-component-id.md#id) for Navigation: the system matches and restores the corresponding navigation component by id. This must be set.

2. Set the [recoverable](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#recoverable14) attribute of Navigation to true: this enables page stack restoration for the component. This must be set.

3. Explicitly set the [recoverable](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#recoverable14) attribute to false for NavDestination pages that do not need restoration: the default value of this attribute is true. After Navigation is enabled, all subpages participate in restoration by default. Pages that do not need restoration, such as ad pages and login pages, must be excluded one by one.

The default values and functions of each switch:

| Switch | Default Value | Description |
|---|---|---|
| [setRestoreEnabled()](#enable-backup-restore) (UIAbility-level master switch) | false | If not enabled, the system will not save or restore any data. |
| recoverable of Navigation | false | If not enabled, the page stack of this component does not participate in restoration. |
| recoverable of NavDestination | true | After Navigation is enabled, all subpages that are not explicitly set participate in restoration by default. |

> **Description:**
>
> When the system restores a page, it only restores the page structure and startup parameters. A page without empty-parameter degradation handling has an empty parameter after restore, which appears as a white screen. Therefore, reverse exclusion is recommended: explicitly set recoverable to false for each page that does not participate in restoration. "Not writing recoverable" does not mean "not restored".

<!-- @[nav_three_piece](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RestoreIndex.ets) -->

``` TypeScript
Navigation(this.pathStack) {
  Column({ space: 12 }) {
    Text('Page stack restoration example')
      .fontSize(22)
      .fontWeight(FontWeight.Bold)
    if (this.restoreHint !== '') {
      Text(this.restoreHint)
        .fontSize(14)
        .fontColor(Color.Gray)
    }
    Button('Open reading page (resume reading from breakpoint)')
      .width('80%')
      .onClick(() => {
        this.pathStack.pushPathByName('ReaderPage', { bookId: 'book-1001' } as Record<string, Object>);
        this.reportNavSnapshot();
      })
    Button('Enter third-level page (deep stack fill demo)')
      .width('80%')
      .onClick(() => {
        this.pathStack.pushPathByName('ReaderPage', { bookId: 'book-1001' } as Record<string, Object>);
        this.pathStack.pushPathByName('DeepPage', {} as Record<string, Object>);
        this.reportNavSnapshot();
      })
    Button('Router page restoration example')
      .width('80%')
      .onClick(() => {
        router.pushUrl({ url: 'restore/RouterPage' });
      })
    Text('Go to the background and wait for the system to reclaim, then start again to verify the restoration effect')
      .fontSize(12)
      .fontColor(Color.Gray)
  }
  .width('100%')
  .height('100%')
  .justifyContent(FlexAlign.Center)
}
.navDestination(this.PageMap)
// Configuration 1 of three: restoration matches by navigationId, must be set
.id('restore-nav')
// Configuration 2 of three: default false, must be explicitly enabled (API version 14+)
.recoverable(true)
.mode(NavigationMode.Stack)
```

The page level (NavDestination) is enabled after completing data saving and restoration (see [Data Restoration](#data-restoration)) and empty-parameter degradation handling:

``` TypeScript
NavDestination() {
  // Page content
}
.title('Reading page (resume reading from breakpoint)')
.onReady((ctx: NavDestinationContext) => {
  this.handleParam(ctx);
})
// Page-level configuration of three: only allowed to enable after completing data saving and restoration and empty-parameter degradation handling (API version 14+)
.recoverable(true)
```

Pages that do not participate in restoration (such as ad pages) must be explicitly excluded. Otherwise, they will be restored together because the default value is true:

``` TypeScript
NavDestination() {
  // Content of pages that do not need restoration, such as ad pages
}
.title('Ad page')
// The default value is true. If not written, it will be restored - pages that do not participate in restoration must be explicitly excluded
.recoverable(false)
```

> **Description:**
> - The page name must be statically stable: during restoration, the system matches pages in PageMap by the name of NavDestination. A page name dynamically concatenated or encrypted at runtime cannot be matched, and the corresponding page cannot be restored. For such projects, change the page name to a static constant. If encryption is truly required, encrypt the param instead, and keep the page name as static plaintext.
> - Lazy-loaded pages must ensure that the mapping is resolvable during restoration: for lazy-loaded pages in PageMap (such as dynamic import), ensure that the component can be obtained synchronously by name at restore startup (for example, pre-register the mapping from name to component builder, or complete dynamic loading before the fill). Otherwise, the restored page cannot be built.

### Empty Parameter Degradation

At normal startup, the param of a page is passed in by the navigating party. At restore startup, the page is remounted by the system based on the page name. Fields that cannot be serialized in param are silently discarded without reporting an error. Serialization also has upper limits on nesting depth, attribute count, string length, etc. (determined by the internal system implementation and may change). Attributes exceeding the limits are also silently discarded. Therefore, the param after restore may be empty or incomplete.

The framework has no universal anti-white-screen mechanism. The page must actively handle the empty param case in onReady() and degrade along three paths:

<!-- @[empty_param_fallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/ReaderPage.ets) -->

``` TypeScript
/** Empty parameter degradation: the restored param may be empty or incomplete. Without handling, a white screen occurs. */
private handleParam(ctx: NavDestinationContext): void {
  const param = ctx.pathInfo?.param as Record<string, Object> | undefined;
  // param valid: reload data according to the parameter
  if (param !== undefined && param['bookId'] !== undefined) {
    this.bookId = param['bookId'] as string;
    if (!this.restoredFromChannel) {
      this.loadFresh();
    }
    return;
  }
  // param empty: retrieve restore data from AppStorage
  const restored = AppStorage.get<Record<string, Object>>('restore.reader');
  if (restored !== undefined) {
    AppStorage.delete('restore.reader');
    this.restoredFromChannel = true;
    this.bookId = (restored['bookId'] as string) ?? '';
    this.chapterIndex = (restored['chapterIndex'] as number) ?? 1;
    this.progress = (restored['progress'] as number) ?? 0;
    // The draft is transferred separately via AppStorage, not in the state object
    const draft = AppStorage.get<string>('restore.reader.draft');
    if (draft !== undefined) {
      AppStorage.delete('restore.reader.draft');
      this.draft = draft;
    }
    this.source = 'restore startup';
    this.reportState();
    return;
  }
  // Neither is available: return to the previous page
  ctx.pathStack?.pop();
}
```

The third path has two options, decided by the application by business: call pop() to exit the current page, or stay on the current page and load default data.

The example uses pop(): when there is still a previous page in the stack, return to the previous page. When the current page is the only page in the stack, Navigation displays the home page (the page shown when the application has just started and no subpage has been opened).

### Deep Stack Fill

Navigation page stack restoration does not guarantee covering all levels. Deeper levels need to be filled by the application on its own: starting from the level next to the system-restored level, execute pushPath layer by layer according to the saved page path to push the missing pages back into the navigation stack.

Specifically, there are two steps:

1. Record the page path normally: update the record after each change of the navigation stack (enter, return, replace). The example uses [setInterception](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#setinterception12) of NavPathStack for unified listening, writes the current page path (the sequence of page names from the home page to the current page) into AppStorage, and reads it synchronously in onSaveState(). See the syntax in [Data Restoration](#data-restoration).
2. Fill deep levels after restore: after restore startup, read the saved page path in onPageShow() of the home page, and fill the pages not restored by the system layer by layer via pushPath.

The fill timing must be in onPageShow() of the home page: at this point, the system page stack restoration is complete and the page is rendered. Do not fill in the loadContent() callback: when the callback executes, the system has not yet pushed the restored pages back into the stack. The pages pushed by the application first will overlap with the pages restored by the system later, and the user may see duplicate pages or disordered order.

<!-- @[deep_stack_replay_timing](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RestoreIndex.ets) -->

``` TypeScript
onPageShow(): void {
  // Deep stack fill timing: at this point, the system stack restoration is complete and the page is rendered; do not advance it to the loadContent callback
  // (the system restoration has not been executed yet, which will conflict). The automatic jump of the home page at restore startup (such as ad pages) must be skipped,
  // otherwise it will overwrite the top page restored by the system.
  this.replayDeepStack();
}
```

Publish the page path normally:

<!-- @[nav_snapshot_report](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RestoreIndex.ets) -->

``` TypeScript
aboutToAppear(): void {
  // Unified listening for stack changes: update the page path after enter, return, and replace, to avoid covering only the enter scenario
  this.pathStack.setInterception({
    didShow: () => {
      this.reportNavSnapshot();
    }
  });
}

/** After the stack changes, publish the page path to AppStorage, and onSaveState reads it synchronously. */
private reportNavSnapshot(): void {
  AppStorage.setOrCreate(KEY_NAV_SNAPSHOT, JSON.stringify(this.pathStack.getAllPathName()));
}
```

Fill layer by layer after restore:

<!-- @[deep_stack_replay](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RestoreIndex.ets) -->

``` TypeScript
/** Fill the deep levels not restored by the system according to the saved page path. */
private replayDeepStack(): void {
  const navPath = AppStorage.get<string>(KEY_RESTORE_NAV_PATH);
  if (navPath === undefined) {
    return;
  }
  AppStorage.delete(KEY_RESTORE_NAV_PATH);
  try {
    const names: string[] = JSON.parse(navPath) as string[];
    const current: string[] = this.pathStack.getAllPathName();
    // Fill layer by layer from the level restored by the system; if the fill fails, stop at the restored page without a white screen
    for (let i = current.length; i < names.length; i++) {
      this.pathStack.pushPathByName(names[i], {} as Record<string, Object>);
    }
  } catch (_) {
    // If page path parsing fails, skip the fill and stop at the restored page without a white screen; log for troubleshooting
    hilog.warn(DOMAIN, TAG, 'replayDeepStack skipped: invalid navPath');
  }
}
```

> **Description:**
>
> - The param of the filled pages is passed in as an empty object, and the page data is restored according to the method in [Data Restoration](#data-restoration) - the page path stores only page names, and each page reads or reloads its data on its own after page mount. Do not try to save the original param together.
> - The page path stores only page names without parameters: for pages that put functions, class instances, etc. into param during navigation, these fields cannot be saved along with the page path. Handle [Handling Non-serializable Fields](#handling-non-serializable-fields) first.

## Page Stack Restoration: Router

Applications using @ohos.router do not need to configure the three restoration switches. The recoverable attribute of router pages defaults to true, and the opened page stack is automatically restored by the system. No page stack modification is required by the application.

To exclude pages that do not need restoration (such as ad pages), set recoverable: false when navigating.

<!-- @[router_exclude](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/restore/RouterPage.ets) -->

``` TypeScript
Button('Navigate to ad page (does not participate in restoration)')
  .width('80%')
  .onClick(() => {
    router.pushUrl({
      url: 'restore/AdvertPage',
      // Explicitly exclude pages that do not need restoration, such as ad pages
      recoverable: false
    });
  })
```

## Page Stack Restoration: Third-Party Routing

When an application uses a URI-based third-party routing framework such as HMRouter (@hadss/hmrouter) or a self-developed routing framework, the system page stack restoration does not apply to the internal logic of the third-party routing. The [three configurations of Navigation](#page-stack-restoration-navigation) are unavailable, and the application needs to restore the page stack on its own. A URI is naturally serializable. The adaptation approach is as follows: save lightweight routing information (URI and serializable parameters) in onSaveState(), and after restore startup, re-execute navigation layer by layer based on the routing information. The process consists of three steps:

1. Page registration: maintain a mapping of "page name to routing information", where the routing information contains only the URI and serializable parameters.
2. Save: onSaveState() writes the routing information list of the current routing path into wantParam.
3. Re-navigate: after onCreate() determines restore startup, write the routing information list into AppStorage. In the home page onPageShow(), re-execute navigation layer by layer based on the list. onPageShow() must execute only once (for example, ensured by a boolean flag) to avoid duplicate navigation.

``` TypeScript
// Pseudocode example (HMRouter needs to adjust the navigation call according to its routing API)
onSaveState(reason: AbilityConstant.StateType,
  wantParam: Record<string, Object>): AbilityConstant.OnSaveResult {
  // Routing information: URI is naturally serializable; when param contains fields such as functions and class instances, it must first be converted to a serializable form
  const routes: RouteInfo[] = getCurrentRoutes(); // [{uri, param}, ...]
  wantParam['restore.routes'] = routes;
  return AbilityConstant.OnSaveResult.ALL_AGREE;
}

// In the home page onPageShow:
const routes = AppStorage.get<RouteInfo[]>('restore.routes');
if (routes !== undefined) {
  AppStorage.delete('restore.routes'); // Restore data is carried only for this restore startup, and is deleted after being read
  for (const r of routes) {
    this.router.push(r.uri, r.param); // Re-execute navigation according to the API of the routing framework in use
  }
}
```

> **Description:**
>
> - During re-navigation, the application's automatic navigation logic such as automatically jumping to the home page and redirect login must be skipped. Otherwise, the replayed page will be overwritten by the automatic jump. Handling method: use the result of [Determine Restore Startup](#determine-restore-startup) to set a boolean flag, and do not execute any automatic navigation logic before the restore process ends.
> - This solution depends on the third-party routing package. The example project does not include this dependency, and it can be integrated according to the pseudocode above.
> - In the HMRouter scenario, you can also set an id and recoverable for its internal Navigation and reuse the [three configurations of Navigation](#page-stack-restoration-navigation) solution. However, the Navigation instance inside HMRouter is not easy to inject attributes into, so this solution is recommended by default.

## FAQs

**The page shows a white screen after restore. How to troubleshoot?**

First check whether the param of the page is empty or incomplete. At restore startup, the page is remounted by the system based on the page name, and fields that cannot be serialized in param are silently discarded without reporting an error. If the page does not handle the case of an empty param in onReady(), it will show a white screen because it cannot obtain the data. For the handling method, see [Empty Parameter Degradation](#empty-parameter-degradation). If param contains fields such as functions and class instances, first convert them according to [Handling Non-serializable Fields](#handling-non-serializable-fields).

**After restore, the top of the stack is an ad page or splash page, and the original page is overwritten?**

The application's automatic page navigation logic (automatically jumping to the home page, entering the ad page, redirect login, etc.) executes at restore startup and overwrites the page restored by the system. Use the result of [Determine Restore Startup](#determine-restore-startup) to set a boolean flag, and skip all automatic page navigation logic before the restore process ends.

**For an application that uses both Navigation and router, pages are duplicated or the return order is disordered after restore?**

Enabling two sets of page stack restoration at the same time will interfere with each other. Based on the main framework of the application, keep only one restoration path.

**In multiton mode, the restore data of multiple instances overwrites each other?**

Multiple UIAbility instances share the same AppStorage. When data is stored with the same key name, the later written data overwrites the earlier written data. Add the instance's own identifier before the key name. See [Data Restoration](#data-restoration).

**Restore data cannot be read or fails to be read. How to degrade?**

When restore data is missing, the page is displayed normally with default data, and startup is not blocked by a restore failure. For oversized data that uses file offloading, when the file cannot be read, degrade to empty data (see [Oversized Data Offloading](#oversized-data-offloading)). Persisted data does not depend on restoration and is read back directly from the disk (see [Persistence First](#persistence-first)).

**Page parameters contain non-serializable objects such as functions, callbacks, and Proxy. How to handle them?**

Such objects cannot be serialized and cannot be brought back with the saved data or param. They are directly discarded during restoration without reporting an error. Replace them with lightweight fields such as URI and id that can re-fetch data, according to [Handling Non-serializable Fields](#handling-non-serializable-fields).

**A single piece of data is too large and exceeds the total size limit (200KB) after want.parameters serialization. How to handle it?**

Handle it according to [Oversized Data Offloading](#oversized-data-offloading): write the data body to the disk, store only the file name in the saved data, and read it back by file name during restoration.

**How does the application distinguish between restore startup and normal startup?**

Determine the three conditions in combination according to [Determine Restore Startup](#determine-restore-startup): the restore restart flag is true, want.parameters brings back the data saved by this application, and launchReason is APP_RECOVERY.
