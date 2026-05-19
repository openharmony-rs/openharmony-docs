# 应用退出

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @ccllee1-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @HelloCrease-->

## 概述

开发应用时，应用退出指操作系统彻底销毁应用的进程，回收所有内存与线程。组件退出仅销毁特定组件实例（如UIAbility），但其宿主进程依然在后台存活。

只有当进程中所有的应用组件都销毁，进程进入销毁流程。当应用中的所有进程都销毁，则应用退出。

## 应用退出机制

由于应用可能包含多个进程，每个进程中又能运行多个UIAbility组件，因此当某个进程中的最后一个UIAbility组件退出后，该进程随之退出，而当应用的最后一个进程退出时，整个应用即完成退出过程。其中UIAbility的退出机制根据触发诱因和系统处理方式的不同，主要分为正常退出与异常退出两大类。

- **正常退出**：由用户主动交互或开发者编码触发。包含开发者显式调用退出接口（如terminateSelf()）、用户点击返回键、在多任务管理界面清理卡片，以及通过Dock栏右键关闭等。在此类场景下，系统会严格遵循生命周期规范，依次触发标准的销毁回调，允许应用执行数据保存和资源释放。

- **异常退出**：由于不可控因素或系统干预导致的非预期中断。包含应用内部发生未捕获的严重崩溃（Crash）、内存泄漏，或由于违反系统管控策略被强行终止。异常退出时，系统会直接强制终止应用进程，此时往往无法保证生命周期回调的完整执行。

不同退出场景下，UIAbility的生命周期执行情况如下表所示：

| 退出类型    | 具体触发场景       | 是否触发onDestroy  |
| ------------| ---------------- | ----------------------- |
| 应用正常退出  | 开发者显式调用terminateSelf()终止当前应用进程，常见场景包括：应用检测到致命错误，主动终止进程以避免数据损坏；2.完成应用内一键清理缓存等核心任务后，主动结束生命周期。 |   是   |
| 用户通过返回键退出 | 用户侧滑返回或按返回键退出。 |  是   |
| 用户主动清理UIAbility | 用户在多任务管理界面中上滑清理单个卡片，或点击"清除全部"按钮。 |  是 |
| 应用异常  | 应用进程崩溃或被系统强制终止。常见场景包括：应用内部发生jscrash或出现指针异常等。 |   否 |
| 系统清理   | 系统因资源回收等原因自动清理UIAbility。常见场景包括：系统内存极度紧张，回收后台进程以释放资源；基于电量优化、权限变更等策略终止进程。 |  否 |


## 应用正常退出

应用正常退出时，其包含的UIAbility组件也会正常退出。UIAbility正常退出是指组件在符合业务预期的情况下的退出过程。在此场景下，系统会触发onDestroy()生命周期回调，允许应用释放持有的系统资源。

**场景示例**：用户点击应用内自定义的“退出”按钮；或者由UIAbility承载的广告页面倒计时结束，需要自动关闭。

**开发实现**：开发者可以在业务逻辑执行完毕后，通过调用[terminateSelf()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateself-1)接口主动退出当前UIAbility。


**开发步骤**：

1. 在UIAbility中获取UIAbilityContext实例。
2. 调用terminateSelf()接口退出UIAbility。

<!-- @[appStop_terminateSelf](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/GuideForAppExit/terminateSelf/src/main/ets/terminateselfability/TerminateSelfAbility.ets) --> 

``` TypeScript
import { AbilityConstant, ConfigurationConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';

const DOMAIN = 0x0000;

export default class EntryAbility extends UIAbility {
  // ...

  onForeground(): void {
    // Ability has brought to foreground
    hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onForeground');

    // 获取UIAbilityContext
    let context = this.context;

    setTimeout(() => {
      context.terminateSelf().then(() => {
        console.info('Succeeded in terminating self.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to terminate self. Code is ${err.code}, message is ${err.message}`);
      });
    }, 2000);
  }

  // ...
}
```


## 用户通过返回键退出
**场景示例**：在手机类设备上，用户按下返回键时，系统回调UIAbility的[onBackPressed()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onbackpressed10)回调，该回调默认返回false，系统将UIAbility置于后台而不是销毁。

**开发实现**：开发者可以通过重写[onBackPressed()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onbackpressed10)方法返回true来改变返回键的默认行为，例如在onBackPressed()中调用terminateSelf()，实现按下返回键时直接退出UIAbility。

**开发步骤**：

默认情况下，按下返回键会将UIAbility置于后台。如果需要按下返回键时直接退出UIAbility，可以重写onBackPressed()方法退出应用。

在UIAbility中重写onBackPressed()方法。

<!-- @[appStop_backPressed](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/GuideForAppExit/onBackPressed/src/main/ets/onbackpressedability/OnBackPressedAbility.ets) --> 

``` TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';

const DOMAIN = 0x0000;

export default class OnBackPressedAbility extends UIAbility {
  // ...

  onBackPressed() {
    // 调用terminateSelf退出UIAbility
    this.context.terminateSelf().then(() => {
      console.info('Succeeded in terminating self.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to terminate self. Code is ${err.code}, message is ${err.message}`);
    });

    // 返回true表示消费该事件，不再进行默认处理
    return true;
  }
}
```

## 用户主动清理UIAbility

用户可以通过各种方式主动退出UIAbility：

- **单任务清理**：上滑清理单个任务卡片，对应的UIAbility实例会退出并执行onDestroy生命周期回调。
- **一键清理**：点击"一键清理"按钮，批量清除所有任务卡片，所有UIAbility实例都会退出并执行onDestroy生命周期回调。
- **Dock栏退出**：在PC/2in1或Tablet设备上，用户通过Dock栏退出，UIAbility的onDestroy不保证回调。

## 应用异常

当应用出现异常情况时，例如JavaScript崩溃、空指针异常等，应用直接崩溃退出。这种情况下不会执行onDestroy生命周期回调。

## 系统清理

系统在某些场景下会强制清理应用进程，不会执行onDestroy生命周期回调：

比如：系统温度过高、整机可用内存不足、应用升级等。