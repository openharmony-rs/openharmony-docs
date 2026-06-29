# 应用重启

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wendel-->
<!--Designer: @wendel-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

应用重启用于在不同场景下重新初始化应用或恢复应用正常状态。系统提供了应用主动重启、原子化服务主动重启和应用故障恢复被动重启等，开发者可根据实际需求选择合适方案。

## 应用主动重启以重新初始化应用

系统提供了“不保留应用窗口的重启”和“保留应用窗口的重启”两种主动重启应用的方式。以下是两种应用主动重启方式的能力对比，开发者可根据自己的业务需求进行选择。
| 对比维度 | 不保留应用窗口的重启 | 保留应用窗口的重启 |
| --------- | ------------------- | ----------------- |
| 适用场景 | 应用发生内部状态问题需要完全重新初始化；应用完成动态更新需要从初始状态开始。 | 应用发生内部状态问题需要完全重新初始化且不想露出桌面；应用完成动态更新需要从初始状态开始且不想露出桌面。 |
| 用户体验 | 不具有连贯性，用户视野会看到桌面。用户在体验上可能存在割裂感。 | 具有连贯性，用户视野停留在应用。避免用户在体验上出现割裂感。 |
| 调用接口 | ApplicationContext.restartApp<sup>12+</sup> | UIAbilityContext.restartApp<sup>22+</sup> |

### 不保留应用窗口的重启

从API version 12开始，ApplicationContext提供了[restartApp](../reference/apis-ability-kit/js-apis-inner-application-applicationContext.md#applicationcontextrestartapp12)接口，用于主动重启应用并拉起指定的UIAbility。重启过程中不保留当前应用窗口，相当于完全重新启动应用。重启过程中不会触发应用中Ability的onDestroy生命周期回调。

存在以下约束限制：
- 仅支持主线程调用该接口。
- 待重启的应用需要处于获得焦点状态。
- 不支持3秒内重复调用重启接口。

示例代码：
<!-- @[restartapp_withoutWindow](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/restartapp/entry/src/main/ets/pages/Index.ets) --> 

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { common, Want } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @State message: string = 'restartApp';
  private context = this.getUIContext().getHostContext()?.getApplicationContext() as common.ApplicationContext;

  build() {
    RelativeContainer() {
      Button(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          let want: Want = {
            bundleName: 'com.example.restartapp',
            abilityName: 'EntryAbility'
          };
          if (this.context) {
            try {
              this.context.restartApp(want);
            } catch (err) {
              hilog.error(0x0000, 'testTag', `restart failed: ${err.code}, ${err.message}`);
            }
          } else {
            hilog.error(0x0000, 'testTag', "%{public}s", 'AppContext is null');
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

### 保留应用窗口的重启

从API version 22开始，UIAbilityContext提供了[restartApp](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#restartapp22)接口，用于重启当前UIAbility所在的进程，并拉起应用内的指定UIAbility。与ApplicationContext的restartApp不同，该接口可选择保留当前窗口或跳转到新窗口。重启过程中不触发进程中Ability的onDestroy生命周期回调。

存在以下约束限制：
- 仅支持主线程调用该接口。
- 待重启的应用需要处于获得焦点状态。
- 不支持3秒内重复调用重启接口。

示例代码：

1. 指定当前UIAbility，重启后刷新当前窗口至初始状态。
   <!-- @[restartapp_withOldWindow](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/restartapp/entry/src/main/ets/pages/Index2.ets) --> 
   
   ``` TypeScript
   import { hilog } from '@kit.PerformanceAnalysisKit';
   import { common, Want } from '@kit.AbilityKit';
   
   @Entry
   @Component
   struct Index {
     @State message: string = 'restartApp with window';
   
     build() {
       RelativeContainer() {
         Button(this.message)
           .id('HelloWorld')
           .fontSize($r('app.float.page_text_font_size'))
           .fontWeight(FontWeight.Bold)
           .alignRules({
             center: { anchor: '__container__', align: VerticalAlign.Center },
             middle: { anchor: '__container__', align: HorizontalAlign.Center }
           })
           .onClick(async () => {
             // 指定当前UIAbility，刷新当前窗口
             let want: Want = {
               bundleName: 'com.example.restartapp',
               abilityName: 'EntryAbility'
             };
             let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
             try {
               await context.restartApp(want);
               hilog.info(0x0000, 'testTag', 'restart success');
             } catch (err) {
               hilog.error(0x0000, 'testTag', `restart failed: ${err.code}, ${err.message}`);
             }
           })
       }
       .height('100%')
       .width('100%')
     }
   }
   ```

2. 指定应用内其他UIAbility，重启后跳转并打开新的Ability窗口。
   <!-- @[restartapp_withNewWindow](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/restartapp/entry/src/main/ets/pages/Index3.ets) --> 
   
   ``` TypeScript
   import { hilog } from '@kit.PerformanceAnalysisKit';
   import { common, Want } from '@kit.AbilityKit';
   
   @Entry
   @Component
   struct Index {
     @State message: string = 'restartApp to new page';
   
     build() {
       RelativeContainer() {
         Button(this.message)
           .id('HelloWorld')
           .fontSize($r('app.float.page_text_font_size'))
           .fontWeight(FontWeight.Bold)
           .alignRules({
             center: { anchor: '__container__', align: VerticalAlign.Center },
             middle: { anchor: '__container__', align: HorizontalAlign.Center }
           })
           .onClick(async () => {
             // 指定应用内其他UIAbility，跳转到新窗口
             let want: Want = {
               bundleName: 'com.example.restartapp',
               abilityName: 'SecondAbility'
             };
             let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
             try {
               await context.restartApp(want);
               hilog.info(0x0000, 'testTag', 'restart success');
             } catch (err) {
               hilog.error(0x0000, 'testTag', `restart failed: ${err.code}, ${err.message}`);
             }
           })
       }
       .height('100%')
       .width('100%')
     }
   }
   ```

## 原子化服务主动重启

从API version 20开始，系统为原子化服务（Atomic Service）提供了专用的重启接口[restartSelfAtomicService](../reference/apis-ability-kit/js-apis-app-ability-abilityManager.md#abilitymanagerrestartselfatomicservice20)，用于触发原子化服务更新并重启当前原子化服务。重启过程中不会保留当前原子化服务窗口，也不会触发旧Ability的onDestroy生命周期回调。

存在以下约束限制：
- 仅支持以独立窗口方式拉起原子化服务。
- 不支持3秒内重复调用重启接口。

原子化服务是应用的一种特殊形式，也可采用[应用主动重启以重新初始化应用](#应用主动重启以重新初始化应用)的方式进行重启。

以下是三种方式主动重启原子化服务的能力对比，开发者可以根据自己的业务需求进行选择。

| 对比维度 | 原子化服务主动重启 | 不保留原子化服务窗口的重启 | 保留原子化服务窗口的重启 |
| --------- | ----------------  | ------------------- | ----------------- |
| 适用场景 | 原子化服务主动触发更新并重新初始化；原子化服务发生内部状态问题需要完全重新初始化。 | 原子化服务发生内部状态问题需要完全重新初始化；原子化服务完成动态更新需要从初始状态开始。 | 原子化服务发生内部状态问题需要完全重新初始化且不想露出桌面；原子化服务完成动态更新需要从初始状态开始且不想露出桌面。 |
| 用户体验 | 不具有连贯性，用户视野会看到桌面。用户在体验上可能存在割裂感。 | 不具有连贯性，用户视野会看到桌面。用户在体验上可能存在割裂感。 | 具有连贯性，用户视野停留在应用。避免用户在体验上出现割裂感。 |
| 免安装更新 | 支持                          | 不支持                           | 不支持                      |
| 调用接口 | AbilityManager.restartSelfAtomicService<sup>20+</sup> | ApplicationContext.restartApp<sup>12+</sup> | UIAbilityContext.restartApp<sup>22+</sup> |

示例代码：

``` TypeScript
import { AbilityConstant, EmbeddableUIAbility, Want, abilityManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

const DOMAIN = 0x0000;

export default class DemoAbility extends EmbeddableUIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(DOMAIN, 'DemoAbility', 'DemoAbility onCreate');
    try {
      // 触发当前原子化服务重启
      abilityManager.restartSelfAtomicService(this.context);
      hilog.info(DOMAIN, 'DemoAbility', 'restartSelfAtomicService success');
    } catch (e) {
      hilog.error(DOMAIN, 'DemoAbility', `restartSelfAtomicService error: ${JSON.stringify(e as BusinessError)}`);
    }
  }
}
```

## 应用故障恢复被动重启

应用故障恢复重启接口由appRecovery模块提供，详见[应用恢复开发指导](../dfx/apprecovery-guidelines.md)。
