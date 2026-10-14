# 模块描述(系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

在Stage模型中，WindowStage/Window可以通过[loadContent](arkts-apis-window-Window.md#loadcontent9)接口加载页面并创建UI的实例，并将页面内容渲染到关联的窗口中，所以UI实例和窗口是一一关联的。一些全局的UI接口是和具体UI实例的执行上下文相关的，在当前接口调用时，通过追溯调用链跟踪到UI的上下文，来确定具体的UI实例。若在非UI页面中或者一些异步回调中调用这类接口，可能无法跟踪到当前UI的上下文，导致接口执行失败。

> **说明：**
>
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.arkui.UIContext (UIContext)](arkts-apis-uicontext.md)。

## 导入模块

```ts
import {
  BackgroundLuminanceSamplingConfigs, LuminanceSampler
} from '@kit.ArkUI';
```

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**系统接口**：此接口为系统接口。

### createModalUIExtension

createModalUIExtension(want: Want, options?: ModalUIExtensionOptions, callback?: ModalUIExtensionCallback): number

创建并显示模态UIExtension。使用callback异步回调。返回的sessionId可用于调用[closeModalUIExtension](#closemodaluiextension)关闭该模态UIExtension。

通过该方法创建的模态UIExtension以模态弹层形式展示，其内容在被拉起的[UIExtensionAbility](../apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md)对应进程中运行，宿主应用不参与其内部布局和渲染。

若未指定[transition](arkui-ts/ts-transition-animation-component.md#transitioneffect10对象说明)转场效果，则模态UIExtension无动画展示。若指定了transition，则在模态显示和关闭时分别播放出现和消失转场动画。

被拉起的Ability必须是带UI的Ability扩展，如何实现带UI的Ability扩展请参考[带界面的ExtensionAbility组件](../apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md)。

**起始版本：** 26.2.0

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名    | 类型                                                         | 必填 | 说明                                                       |
| --------- | ------------------------------------------------------------ | ---- | ---------------------------------------------------------- |
| want      | [Want](../apis-ability-kit/js-apis-app-ability-want.md)  | 是   | 要拉起的UIExtensionAbility对应的Want。                     |
| options   | [ModalUIExtensionOptions](#modaluiextensionoptions)        | 否   | 模态UIExtension的创建选项，包括DPI跟随策略、窗口模式跟随策略和转场效果。 |
| callback  | [ModalUIExtensionCallback](#modaluiextensioncallback)     | 否   | 模态UIExtension的生命周期回调集合。                         |

**返回值：**

| 类型   | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| number | 模态UIExtension的sessionId。取值范围：[0, +∞)。值为0表示创建失败，值大于0表示创建成功。该sessionId可用于调用[closeModalUIExtension](#closemodaluiextension)关闭模态UIExtension。 |

**示例：**

```ts
import { Entry, Text, Column, Component, Button, ClickEvent, WindowModeFollowStrategy, DpiFollowStrategy, Curve, TransitionEffect } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import hilog from '@ohos.hilog'
import { UIContext } from '@kit.AbilityKit'

@Entry
@Component
struct ModalUIExtensionExample {
  @State windowModeStrategy: WindowModeFollowStrategy = WindowModeFollowStrategy.FOLLOW_HOST_WINDOW_MODE;
  @State dpiFollowStrategy: DpiFollowStrategy = DpiFollowStrategy.FOLLOW_HOST_DPI;
  @State sessionId: number = 0;
  private uiContext: UIContext = this.getUIContext();
  build() {
    Column(undefined) {
      Button('Create Modal UIExtension')
        .onClick(() => {
          const want: Want = {
            bundleName: 'com.example.modalprovider',
            abilityName: 'ModalUIExtensionAbility',
            parameters: {
              'ability.want.params.uiExtensionType': 'sys/commonUI'
            }
          };
          // 创建并显示模态UIExtension
          this.sessionId = this.uiContext.createModalUIExtension(
            want,
            {
              transition: TransitionEffect.SLIDE.animation({ duration: 5000, curve: Curve.LinearOutSlowIn }),
              dpiFollowStrategy: this.dpiFollowStrategy,
              windowModeFollowStrategy: this.windowModeStrategy
            },
            {
              onRemoteReady: (proxy) => {
                console.info('UIExtension onRemoteReady');
              },
              onReceive: () => {
                console.info('UIExtension onReceive');
              },
              onError: (error) => {
                console.info('UIExtension onError');
              },
              onTerminated: (info) => {
                console.info('UIExtension onTerminated');
              },
              onDrawReady: () => {
                console.info('UIExtension onDrawReady');
              },
            });
        })
    }
  }
}
```

### closeModalUIExtension

closeModalUIExtension(sessionId: number): void

关闭模态UIExtension。

若创建模态UIExtension时指定了[transition](arkui-ts/ts-transition-animation-component.md#transitioneffect10对象说明)转场效果，则在关闭时先播放消失转场动画，动画结束后再关闭。无效的、已关闭的或正在关闭中的sessionId将被静默忽略。

**起始版本：** 26.2.0

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型   | 必填 | 说明                                                                 |
| ---------- | ------ | ---- | -------------------------------------------------------------------- |
| sessionId  | number | 是   | 由[createModalUIExtension](#createmodaluiextension)返回的sessionId。取值范围：[0, +∞)。值为0表示创建失败，值大于0表示创建成功。 |

**示例：**

```ts
import { Entry, Text, Column, Component, Button, ClickEvent, WindowModeFollowStrategy, DpiFollowStrategy, Curve, TransitionEffect } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import hilog from '@ohos.hilog'
import { UIContext } from '@kit.AbilityKit'

@Entry
@Component
struct ModalUIExtensionExample {
  @State windowModeStrategy: WindowModeFollowStrategy = WindowModeFollowStrategy.FOLLOW_HOST_WINDOW_MODE;
  @State dpiFollowStrategy: DpiFollowStrategy = DpiFollowStrategy.FOLLOW_HOST_DPI;
  @State sessionId: number = 0;
  private uiContext: UIContext = this.getUIContext();
  build() {
    Column(undefined) {
      Button('Create Modal UIExtension')
        .onClick(() => {
          const want: Want = {
            bundleName: 'com.example.modalprovider',
            abilityName: 'ModalUIExtensionAbility',
            parameters: {
              'ability.want.params.uiExtensionType': 'sys/commonUI'
            }
          };
          this.sessionId = this.uiContext.createModalUIExtension(
            want,
            {
              transition: TransitionEffect.SLIDE.animation({ duration: 5000, curve: Curve.LinearOutSlowIn }),
              dpiFollowStrategy: this.dpiFollowStrategy,
              windowModeFollowStrategy: this.windowModeStrategy
            },
            {
              onRemoteReady: (proxy) => {
                console.info('UIExtension onRemoteReady');
              },
              onReceive: () => {
                console.info('UIExtension onReceive');
              },
              onError: (error) => {
                console.info('UIExtension onError');
              },
              onTerminated: (info) => {
                console.info('UIExtension onTerminated');
                // 关闭模态UIExtension
                this.uiContext.closeModalUIExtension(this.sessionId);
              },
              onDrawReady: () => {
                console.info('UIExtension onDrawReady');
              },
            });
        })
    }
  }
}
```

## ModalUIExtensionOptions

模态UIExtension的创建选项。

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称                    | 类型                                                           | 只读 | 可选 | 说明                                                   |
| ----------------------- | -------------------------------------------------------------- | ---- | ---- | ------------------------------------------------------ |
| dpiFollowStrategy       | [DpiFollowStrategy](arkui-ts/ts-container-ui-extension-component-sys.md#dpifollowstrategy12) | 否   | 是   | DPI跟随策略。</br>默认值：DpiFollowStrategy.FOLLOW_HOST_DPI |
| windowModeFollowStrategy | [WindowModeFollowStrategy](arkui-ts/ts-container-ui-extension-component-sys.md#windowmodefollowstrategy18) | 否 | 是 | 窗口模式跟随策略。</br>默认值：WindowModeFollowStrategy.FOLLOW_HOST_WINDOW_MODE |
| transition              | [TransitionEffect](arkui-ts/ts-transition-animation-component.md#transitioneffect10对象说明) | 否   | 是   | 模态UIExtension显示和关闭时播放的转场动画效果。</br>默认值：TransitionEffect.IDENTITY（无动画） |

## ModalUIExtensionCallback

模态UIExtension的生命周期回调集合。

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称          | 类型                                                         | 只读 | 可选 | 说明                                                         |
| ------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| onRemoteReady | [Callback](../apis-basic-services-kit/js-apis-base.md#callback)&lt;[UIExtensionProxy](arkui-ts/ts-container-ui-extension-component-sys.md#uiextensionproxy)&gt; | 否 | 是 | UIExtensionAbility连接完成时的回调。回调参数为[UIExtensionProxy](arkui-ts/ts-container-ui-extension-component-sys.md#uiextensionproxy)实例，可通过该实例向被拉起的Ability发送数据。 |
| onReceive     | [ReceiveCallback](arkui-ts/ts-container-ui-extension-component-sys.md#receivecallback18) | 否   | 是   | 收到被拉起的Ability发送的数据时触发的回调。                  |
| onError       | [ErrorCallback](../apis-basic-services-kit/js-apis-base.md#errorcallback)&lt;[BusinessError](../apis-basic-services-kit/js-apis-base.md#businesserror)&gt; | 否   | 是   | 被拉起的Ability扩展在运行过程中发生异常时触发的回调。回调参数类型为[BusinessError](../apis-basic-services-kit/js-apis-base.md#businesserror)，可通过参数中的code、name和message获取错误信息，业务错误码详细介绍请参见[UIExtension错误码](errorcode-uiextension.md)。 |
| onTerminated  | [Callback](../apis-basic-services-kit/js-apis-base.md#callback)&lt;[TerminationInfo](arkui-ts/ts-container-ui-extension-component-sys.md#terminationinfo12)&gt; | 否 | 是 | 被拉起的UIExtensionAbility通过调用[terminateSelfWithResult](../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md#terminateselfwithresult)或者[terminateSelf](../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md#terminateself)正常退出时触发的回调。 |
| onDrawReady   | [VoidCallback](arkui-ts/ts-types.md#voidcallback12) | 否   | 是   | 被拉起的UIExtensionAbility绘制第一帧时触发的回调。           |