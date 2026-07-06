# 同应用进程嵌入式组件 (EmbeddedComponent)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

EmbeddedComponent组件允许当前页面嵌入同一应用内其他EmbeddedUIExtensionAbility供给的UI内容，这些UI运行在独立进程中，提供更高的安全性和稳定性。

EmbeddedComponent组件主要用于实现跨模块、跨进程的嵌入式界面集成，其核心目标是通过模块化设计提升应用的灵活性和用户体验。

开发者在使用时需注意其使用限制和生命周期管理，合理设计应用架构以最大限度地发挥其优势。

## 基本概念

- [EmbeddedComponent](../reference/apis-arkui/arkui-ts/ts-container-embedded-component.md)组件

  EmbeddedComponent组件用于在当前页面嵌入本应用内其他EmbeddedUIExtensionAbility提供的UI。它允许开发者将应用的某些功能或界面嵌入另一个界面中，实现更灵活的用户界面设计，适用于需要进程隔离的模块化开发场景。

- [EmbeddedUIExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-embeddedUIExtensionAbility.md)组件

  提供方应用中定义使用，用于实现跨进程界面嵌入功能，仅能被同应用的UIAbility拉起，并需在多进程权限的场景下使用。

## 使用约束

- 设备要求

  EmbeddedComponent组件仅可在支持[EmbeddedUIExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-embeddedUIExtensionAbility.md)的设备上正常运行。

- 应用范围

  EmbeddedComponent组件只能在[UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md)中使用，且被拉起的EmbeddedUIExtensionAbility需与UIAbility属于同一应用；从API版本26.0.0开始，如果EmbeddedComponent所属应用申请了ohos.permission.SUPPORT_CROSS_APP_EMBED_FOR_OA权限（该权限仅企业普通应用可申请），且该应用的[appIdentifier](../quick-start/common-problem-of-application.md#什么是appidentifier)在EmbeddedUIExtensionAbility支持的应用清单（即[extensionAbilities标签](../quick-start/module-configuration-file.md#extensionabilities标签)的appIdentifierAllowList属性）中，则允许EmbeddedComponent跨应用拉起EmbeddedUIExtensionAbility。

- 属性限制

  EmbeddedComponent组件支持[通用属性](../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md)，且宽高默认值和最小值均为10vp；
  
  不支持如下与宽高相关的属性：
  
  "[constraintSize](../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#constraintsize)"、"[aspectRatio](../reference/apis-arkui/arkui-ts/ts-universal-attributes-layout-constraints.md#aspectratio)"、"[layoutWeight](../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#layoutweight)"、"[flexBasis](../reference/apis-arkui/arkui-ts/ts-universal-attributes-flex-layout.md#flexbasis)"、"[flexGrow](../reference/apis-arkui/arkui-ts/ts-universal-attributes-flex-layout.md#flexgrow)"和"[flexShrink](../reference/apis-arkui/arkui-ts/ts-universal-attributes-flex-layout.md#flexshrink)"。

- 事件调用

  与屏幕坐标相关的事件信息会基于EmbeddedComponent的位置宽高进行坐标转换后传递给被拉起的EmbeddedUIExtensionAbility处理。

  EmbeddedComponent组件不支持[点击](../reference/apis-arkui/arkui-ts/ts-universal-events-click.md)等通用事件，仅支持[onTerminated](../reference/apis-arkui/arkui-ts/ts-container-embedded-component.md#onterminated)事件和[onError](../reference/apis-arkui/arkui-ts/ts-container-embedded-component.md#onerror)事件。

## 场景示例

该示例简单展示了EmbeddedComponent组件和EmbeddedUIExtensionAbility的基础使用方式。

**加载项首页**

加载项首页是EmbeddedComponent组件的宿主页面，负责加载和展示嵌入式UI扩展能力的内容。以下是一个完整的加载项首页实现示例：

ArkTS-Dyn示例：
<!-- @[embedded_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility/entry/src/main/ets/pages/EmbeddedComponent/Embedded.ets) -->

``` TypeScript
import { Want } from '@kit.AbilityKit';

@Component
export struct Embedded {
  @State message: string = 'Message: ';
  private want: Want = {
    bundleName: 'com.samples.uiextensionandaccessibility',
    abilityName: 'ExampleEmbeddedAbility',
  };
  @State dpiFollowStrategy: EmbeddedDpiFollowStrategy = EmbeddedDpiFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_DPI;
  @State windowStrategy: EmbeddedWindowModeFollowStrategy = EmbeddedWindowModeFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE;

  build() {
    // ...
      Row() {
        Column() {
          Text(this.message).fontSize(30)
          // 可以在构造时传递options参数以设置相关策略
          EmbeddedComponent(this.want, EmbeddedType.EMBEDDED_UI_EXTENSION, {
            windowModeFollowStrategy: this.windowStrategy,
            dpiFollowStrategy: this.dpiFollowStrategy
          })
            .width('100%')
            .height('90%')
            .onTerminated((info) => {
              // 点击extension页面内的terminateSelfWithResult按钮后触发onTerminated回调，文本框显示如下信息
              this.message = `Termination: code = ${info.code} , want = ${JSON.stringify(info.want)}`;
            })
            .onError((error) => {
              // 失败或异常触发onError回调，文本框显示如下报错内容
              this.message = `Error: code = ${error.code}`;
            })
            .onDrawReady(() => {
              // 从API版本26.0.0开始，新增支持被拉起的EmbeddedUIExtensionAbility绘制第一帧时触发onDrawReady回调
            })
        }
        .width('100%')
      }
      .height('100%')
      // ...
  }
}
```

ArkTS-Sta示例：
<!-- @[embedded_start](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/UIExtensionAndAccessibility/entry/src/main/ets/pages/EmbeddedComponent/Embedded.ets) -->

``` TypeScript
import { State } from '@ohos.arkui.stateManagement'
import { Entry, wrapBuilder, Component, ComponentContent, Column, Color, Row, Text, EmbeddedType, LoadingProgress, EmbeddedComponent, EmbeddedDpiFollowStrategy, EmbeddedWindowModeFollowStrategy, TerminationInfo} from '@ohos.arkui.component';
import { Callback, ErrorCallback, BusinessError, RecordData } from '@ohos.base';

@Builder
function LoadingBuilder() {
  Column(undefined) {
    LoadingProgress()
      .color(Color.Blue)
  }
}
@Entry
@Component
struct Embedded {
  @State message: string = 'Message: ';
  private initPlaceholder : ComponentContent = new ComponentContent(this.getUIContext(), wrapBuilder(LoadingBuilder));
  build() {
    Row() {
      Text(this.message).fontSize(30)
      EmbeddedComponent({
          bundleName: 'com.samples.uiextensionandaccessibility',
          abilityName: 'ExampleEmbeddedAbility',
        }, EmbeddedType.EMBEDDED_UI_EXTENSION,
        {
          placeholder: this.initPlaceholder,
          areaChangePlaceholder: {
            "FOLD_TO_EXPAND" : this.initPlaceholder,
          },
          windowModeFollowStrategy: EmbeddedWindowModeFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE,
          dpiFollowStrategy: EmbeddedDpiFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_DPI
        })
        .width('100%')
        .height('90%')
        .onTerminated((info: TerminationInfo) => {
          this.message = `Termination: code = ${info.code} , want = ${JSON.stringify(info.want)}`;
        } as Callback<TerminationInfo>)
        .onError((error: BusinessError) => {
          this.message = `Error: code = ${error.code}`;
        } as ErrorCallback<BusinessError>)
        .onDrawReady(() => {
          // 从API版本26.0.0开始，新增支持被拉起的EmbeddedUIExtensionAbility绘制第一帧时触发onDrawReady回调，文本框显示如下信息
          this.message = `onDrawReady`;
        })
    }
    .height('100%')
  }
}
```

在ArkTS项目中，EmbeddedUIExtensionAbility的实现代码通常位于项目的ets/extensionAbility目录下。例如，ExampleEmbeddedAbility.ets文件位于./ets/extensionAbility/目录中。

在实现加载项首页时，开发者需要注意以下几点：

- 多进程模型检测

  在应用启动时，建议检测设备是否已开启多进程模型。如果未开启，应提供明确的错误提示或引导用户开启。

- 异常处理

  通过[onError](../reference/apis-arkui/arkui-ts/ts-container-embedded-component.md#onerror)事件处理加载或运行嵌入式能力时可能出现的错误，提升用户体验。

- 生命周期管理

  了解并管理好嵌入式组件的生命周期，确保资源的正确释放和回收。

- 样式配置

  合理配置EmbeddedComponent组件的大小和位置，确保嵌入式界面能够以期望的尺寸和位置显示。

**提供方应用生命周期实现**

提供方应用是指提供嵌入式UI扩展能力的应用。以下是提供方应用生命周期实现的代码示例：

ArkTS-Dyn示例：
<!-- @[exampleEmbeddedAbility_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility/entry/src/main/ets/extensionability/ExampleEmbeddedAbility.ets) -->


``` TypeScript
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[ExampleEmbeddedAbility]'

export default class ExampleEmbeddedAbility extends EmbeddedUIExtensionAbility {
  onCreate() {
    hilog.info(0x0000, TAG, '%{public}s', `onCreate`);
  }

  onForeground() {
    hilog.info(0x0000, TAG, '%{public}s',  `onForeground`);
  }

  onBackground() {
    hilog.info(0x0000, TAG, '%{public}s', `onBackground`);
  }

  onDestroy() {
    hilog.info(0x0000, TAG, '%{public}s', `onDestroy`);
  }

  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    hilog.info(0x0000, TAG , '%{public}s', `onSessionCreate, want: ${JSON.stringify(want)}`);
    let param: Record<string, UIExtensionContentSession> = {
      'session': session
    };
    let storage: LocalStorage = new LocalStorage(param);
    // 加载 Extension.ets 页面内容
    session.loadContent('pages/EmbeddedComponent/Extension', storage);
  }

  onSessionDestroy(session: UIExtensionContentSession) {
    hilog.info(0x0000, TAG , '%{public}s',  `onSessionDestroy`);
  }
}
```

ArkTS-Sta示例：
<!-- @[exampleEmbeddedAbility_start](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/UIExtensionAndAccessibility/entry/src/main/ets/extensionability/ExampleEmbeddedAbility.ets) -->

``` TypeScript
import EmbeddedUIExtensionAbility from '@ohos.app.ability.EmbeddedUIExtensionAbility';
import UIExtensionContentSession from '@ohos.app.ability.UIExtensionContentSession';
import Want from '@ohos.app.ability.Want';
import hilog from '@ohos.hilog';
import { LocalStorage } from '@ohos.arkui.stateManagement';

const TAG: string = '[ExampleEmbeddedAbility]'

export default class ExampleEmbeddedAbility extends EmbeddedUIExtensionAbility {
  onCreate(): void {
    hilog.info(0x0000, TAG, '%{public}s', `onCreate`);
  }

  onForeground(): void {
    hilog.info(0x0000, TAG, '%{public}s', `onForeground`);
  }

  onBackground(): void {
    hilog.info(0x0000, TAG, '%{public}s', `onBackground`);
  }

  async onDestroy(): Promise<void> {
    hilog.info(0x0000, TAG, '%{public}s', `onDestroy`);
  }

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    hilog.info(0x0000, TAG, '%{public}s', `onSessionCreate, want: ${JSON.stringify(want)}`);
    let param: Record<string, UIExtensionContentSession> = {
      'session': session
    };
    let storage: LocalStorage = new LocalStorage(param);
    // 加载Extension.ets页面内容
    session.loadContent('pages/EmbeddedComponent/Extension', storage);
  }

  onSessionDestroy(session: UIExtensionContentSession): void {
    hilog.info(0x0000, TAG, '%{public}s', `onSessionDestroy`);
  }
}
```

关键实现说明：

- 生命周期阶段

  [onCreate](../reference/apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md#oncreate) → [onForeground](../reference/apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md#onforeground)：组件初始化到可见的完整流程；

  [onBackground](../reference/apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md#onbackground) → onForeground：前后台切换时的状态迁移；

  [onDestroy](../reference/apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md#ondestroy)：组件被宿主主动销毁时的资源回收点。

- 会话管理

  [onSessionCreate](../reference/apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md#onsessioncreate)：创建独立存储上下文并加载UI界面；

  [onSessionDestroy](../reference/apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md#onsessiondestroy)：处理会话结束时（如用户主动关闭）的清理操作。

- 上下文传递

  通过[LocalStorage](../ui/state-management/arkts-localstorage.md)实现[UIExtensionContentSession](../reference/apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md)的跨组件传递；

  使用[loadContent](../reference/apis-arkui/arkts-apis-window-Window.md#loadcontent9)方法绑定ArkTS页面与扩展能力上下文。

**入口页面** 

以下提供方应用的入口组件实现，展示了如何使用UIExtensionContentSession会话以及如何通过按钮点击事件退出嵌入式页面并返回结果，该代码文件需要在main_pages.json配置文件中声明使用。

ArkTS-Dyn示例：
<!-- @[extension_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility/entry/src/main/ets/pages/EmbeddedComponent/Extension.ets) -->

``` TypeScript
import { UIExtensionContentSession } from '@kit.AbilityKit';

@Entry()
@Component
struct Extension {
  @State message: string = 'EmbeddedUIExtensionAbility Index';
  private storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  private session: UIExtensionContentSession | undefined = this.storage?.get<UIExtensionContentSession>('session');

  build() {
    Column() {
      Text(this.message)
        .fontSize(20)
        .fontWeight(FontWeight.Bold)
      Button('terminateSelfWithResult').fontSize(20).onClick(() => {
        // 点击按钮后调用terminateSelfWithResult退出
        this.session?.terminateSelfWithResult({
          resultCode: 1,
          want: {
            bundleName: 'com.samples.uiextensionandaccessibility',
            abilityName: 'ExampleEmbeddedAbility',
          }
        });
      })
    }.width('100%').height('100%')
  }
}
```

ArkTS-Sta示例：
<!-- @[extension_start](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/UIExtensionAndAccessibility/entry/src/main/ets/pages/EmbeddedComponent/Extension.ets) -->

``` TypeScript
import UIExtensionContentSession from '@ohos.app.ability.UIExtensionContentSession';
import { Entry, Component, Column, Text, FontWeight, Button, ClickEvent } from '@ohos.arkui.component';
import { LocalStorage, State } from '@ohos.arkui.stateManagement';

@Entry()
@Component
struct Extension {
  @State message: string = 'EmbeddedUIExtensionAbility Index';
  private storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  private session: UIExtensionContentSession | undefined = this.storage?.get<UIExtensionContentSession>('session');

  build(): void {
    Column() {
      Text(this.message)
        .fontSize(20)
        .fontWeight(FontWeight.Bold)
      Button('terminateSelfWithResult').fontSize(20).onClick((event: ClickEvent) => {
        if (this.session != undefined) {
          this.session?.terminateSelfWithResult({
            resultCode: 1,
            want: {
              bundleName: 'com.samples.uiextensionandaccessibility',
              abilityName: 'ExampleEmbeddedAbility',
            }
          });
        }
      })
    }.width('100%').height('100%')
  }
}
```


在实现入口页面时，开发者需要注意以下几点：

1. 会话管理

   正确获取并使用UIExtensionContentSession会话对象，确保与宿主应用的通信正常。

2. 结果返回

   通过terminateSelfWithResult方法向宿主应用返回结果时，需要指定：

   - resultCode：结果代码；

   - want：目标意图，指定结果的接收方。

3. 页面生命周期

   了解并管理好入口页面的生命周期，确保资源的正确释放和回收。

4. 样式配置

   合理配置页面元素的样式，确保界面显示效果符合预期。

**添加配置项**

  为了使嵌入式UI扩展能力正常工作，需要在应用的配置文件中进行相应的设置。

  在module.json5配置文件的"extensionAbilities"标签下增加ExampleEmbeddedAbility配置，以注册ExampleEmbeddedAbility嵌入式UI扩展能力。

<!-- @[exampleEmbeddedAbility_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility/entry/src/main/module.json5) -->

``` JSON5
{
  "name": "ExampleEmbeddedAbility",
  "srcEntry": "./ets/extensionability/ExampleEmbeddedAbility.ets",
  "type": "embeddedUI"
},
```

**预期效果**

1. 在支持EmbeddedUIExtensionAbility的设备上启动应用；

   ![zh-cn_image_0000001502261065](figures/Scenario-Example.jpg)

2. 点击terminateSelfWithResult按钮，提供方内容消失，页面显示onTerminated信息。
