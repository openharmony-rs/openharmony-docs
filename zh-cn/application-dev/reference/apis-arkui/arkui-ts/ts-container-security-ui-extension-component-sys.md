# SecurityUIExtensionComponent (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

SecurityUIExtensionComponent用于支持在本页面内嵌入其他应用提供的UI，展示的内容在另一个进程中运行，本应用并不参与其中的布局和渲染。

通常用于有进程隔离诉求的模块化开发场景，SecurityUIExtensionComponent当前仅支持拉起[PhotoPicker](../../apis-media-library-kit/ohos-file-PhotoPickerComponent.md)类型的UIExtensionAbility。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块接口为系统接口。
>
> - 本模块接口仅可在Stage模型下使用。

**起始版本：** 26.0.0

## 子组件

无

## 接口

SecurityUIExtensionComponent(want: Want, options?: SecurityUIExtensionOptions)

创建SecurityUIExtensionComponent组件，用于嵌入显示远程[UIExtensionAbility](../../apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md)提供的UI。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| want | [Want](../../apis-ability-kit/js-apis-app-ability-want.md#want) | 是 | 要加载的Ability信息。通过bundleName和abilityName共同确定被拉起的UIExtensionAbility，同时需要在parameters中配置ability.want.params.uiExtensionType字段指定UIExtensionAbility的类型，当前仅支持'sysPicker/photoPicker'默认值：false |
| options | [SecurityUIExtensionOptions](#securityuiextensionoptions) | 否 | 用于构造SecurityUIExtensionComponent的参数。不填时各字段使用默认值。 |

## SecurityUIExtensionOptions

用于构造SecurityUIExtensionComponent时传递参数。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| isTransferringCaller | boolean | 否 | 是 | 在使用UIExtensionComponent嵌套时，设置当前UIExtensionComponent是否转发上一级的Caller信息。<br/>true：转发上一级的Caller信息；false：不转发上一级的Caller信息。<br/>默认值：false |
| placeholder | [ComponentContent](../js-apis-arkui-ComponentContent.md#componentcontent-1) | 否 | 是 | 设置占位符，在SecurityUIExtensionComponent与UIExtensionAbility建立连接前显示。 |
| dpiFollowStrategy | [SecurityDpiFollowStrategy](#securitydpifollowstrategy) | 否 | 是 | 设置SecurityUIExtensionComponent内容分辨率跟随策略，用于控制嵌入的UIExtensionAbility内容是跟随宿主应用的分辨率还是使用自身的分辨率。<br/>默认值：FOLLOW_UI_EXTENSION_ABILITY_DPI |

## SecurityDpiFollowStrategy

定义SecurityUIExtensionComponent内容分辨率跟随策略的枚举。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| FOLLOW_HOST_DPI | 0 | 表示分辨率跟随宿主。 |
| FOLLOW_UI_EXTENSION_ABILITY_DPI | 1 | 表示分辨率跟随UIExtensionAbility。 |

## 属性

支持[通用属性](ts-component-general-attributes.md)。

## 事件

支持以下事件：

### onRemoteReady

ArkTS-Dyn: onRemoteReady(callback: Callback\<SecurityUIExtensionProxy\>)

ArkTS-Sta: onRemoteReady(callback: Callback\<SecurityUIExtensionProxy\> | undefined)

UIExtensionAbility连接完成时触发的回调，使用callback异步回调。之后可通过返回的[SecurityUIExtensionProxy](#securityuiextensionproxy)向被拉起的Ability发送数据。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | ArkTS-Dyn: [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[SecurityUIExtensionProxy](#securityuiextensionproxy)\><br/>ArkTS-Sta: [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[SecurityUIExtensionProxy](#securityuiextensionproxy)\> \| undefined | 是 | 回调函数，用于向对端Ability发送数据。<br/>ArkTS-Sta模式下,可传入undefined，表示取消回调函数。 |

### onReceive

ArkTS-Dyn: onReceive(callback: Callback\<Record\<string, Object\>\>)

ArkTS-Sta: onReceive(callback: Callback\<Record\<string, RecordData\>\> | undefined)

收到被拉起的Ability发送的数据时触发的回调。使用callback异步回调。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | ArkTS-Dyn: [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<Record\<string, Object\>\><br/>ArkTS-Sta: [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<Record\<string, RecordData\>\> \| undefined | 是 | 回调函数，返回收到的来自对端Ability的数据。<br/>ArkTS-Sta模式下,可传入undefined，表示取消回调函数。 |

### onError

ArkTS-Dyn: onError(callback: ErrorCallback)

ArkTS-Sta: onError(callback: ErrorCallback\<BusinessError\> | undefined)

被拉起的Ability扩展在运行过程中发生异常时触发的回调，不包含与UIExtensionAbility断开连接场景。使用callback异步回调。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | ArkTS-Dyn: [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback)<br/>ArkTS-Sta: [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback)\<[BusinessError](../../apis-basic-services-kit/js-apis-base.md#businesserror)> \| undefined | 是 | 回调函数，入参用于接收异常信息。<br/>ArkTS-Sta模式下,可传入undefined，表示取消回调函数。 |

### onTerminated

ArkTS-Dyn: onTerminated(callback: Callback\<TerminationInfo\>)

ArkTS-Sta: onTerminated(callback: Callback\<TerminationInfo\> | undefined)

被拉起的UIExtensionAbility通过调用[terminateSelfWithResult](../../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult)或[terminateSelf](../../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateself)正常退出时触发此回调。使用callback异步回调。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | ArkTS-Dyn: [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[TerminationInfo](ts-container-embedded-component.md#terminationinfo)\><br/>ArkTS-Sta: [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[TerminationInfo](ts-container-embedded-component.md#terminationinfo)\> \| undefined | 是 | 回调函数，入参用于接收UIExtensionAbility的返回结果。<br/>ArkTS-Sta模式下,可传入undefined，表示取消回调函数。 |

## SecurityUIExtensionProxy

用于在双方建立连接成功后，向组件使用方被拉起的Ability发送数据，以及订阅和取消订阅的注册。

### send

ArkTS-Dyn: send(data: Record\<string, Object\>): void

ArkTS-Sta: send(data: Record\<string, RecordData\>): void

用于在双方建立连接成功后，向组件使用方被拉起的Ability发送数据，提供异步发送能力。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| data | ArkTS-Dyn: Record\<string, Object\><br/>ArkTS-Sta: Record\<string, RecordData\> | 是 | 异步发送给被拉起的扩展Ability的数据。 |

### sendSync

ArkTS-Dyn: sendSync(data: Record\<string, Object\>): Record\<string, Object\>

ArkTS-Sta: sendSync(data: Record\<string, RecordData\>): Record\<string, RecordData\>

用于在双方建立连接成功后，向组件使用方被拉起的Ability发送数据，提供同步发送能力。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| data | ArkTS-Dyn: Record\<string, Object\><br/>ArkTS-Sta: Record\<string, RecordData\> | 是 | 同步发送给被拉起的扩展Ability的数据。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn: Record\<string, Object\><br/>ArkTS-Sta: Record\<string, RecordData\> | 扩展Ability返回的数据。 |

**错误码：**

以下错误码的详细介绍请参见[UIExtension错误码](../errorcode-uiextension.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 100011 | No callback has been registered to respond to this request. |
| 100012 | Transferring data failed. |

### on('asyncReceiverRegister')

on(type: 'asyncReceiverRegister', callback: Callback\<UIExtensionProxy\>): void

订阅被拉起的Ability发生异步注册的回调。使用callback异步回调。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 固定填'asyncReceiverRegister'，代表订阅扩展Ability发生异步注册回调。 |
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[UIExtensionProxy](../../apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#uiextensionproxy)\> | 是 | 回调函数。订阅扩展Ability注册[setReceiveDataCallback](../../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession-sys.md#setreceivedatacallback)后触发的回调。 |

### on('syncReceiverRegister')

on(type: 'syncReceiverRegister', callback: Callback\<UIExtensionProxy\>): void

订阅被拉起的Ability发生同步注册的回调。使用callback异步回调。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 固定填'syncReceiverRegister'，订阅扩展Ability发生同步注册回调。 |
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[UIExtensionProxy](../../apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#uiextensionproxy)\> | 是 | 回调函数。扩展Ability注册[setReceiveDataForResultCallback](../../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession-sys.md#setreceivedataforresultcallback11)后触发的回调。 |

### off('asyncReceiverRegister')

off(type: 'asyncReceiverRegister', callback?: Callback\<UIExtensionProxy\>): void

取消订阅被拉起的Ability发生异步注册的回调。使用callback异步回调。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 固定填'asyncReceiverRegister'，取消订阅扩展Ability发生异步注册回调。 |
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[UIExtensionProxy](../../apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#uiextensionproxy)\> | 否 | 回调函数。为空代表取消订阅所有扩展Ability异步注册后触发回调。非空代表取消订阅异步对应回调。 |

### off('syncReceiverRegister')

off(type: 'syncReceiverRegister', callback?: Callback\<UIExtensionProxy\>): void

取消订阅被拉起的Ability发生同步注册后触发的回调。使用callback异步回调。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 固定填'syncReceiverRegister'，取消订阅扩展Ability发生同步注册回调。 |
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[UIExtensionProxy](../../apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#uiextensionproxy)\> | 否 | 指定取消订阅的回调。为空代表取消订阅所有扩展Ability同步注册后触发回调。 |

## 示例

### 示例1（SecurityUIExtensionComponent基础使用）

本示例展示了SecurityUIExtensionComponent的基本用法，通过配置Want拉起指定Ability的UIExtensionAbility，并在连接异常时通过onError回调获取错误信息。

从API版本26.0.0开始，新增[onError](#onerror)事件。

ArkTS-Dyn示例：

``` TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  @State want: Want = {
    bundleName: 'com.ohos.myapplication',
    abilityName: 'SUIExtensionProvider',
    parameters: {
      'ability.want.params.uiExtensionType': 'sysPicker/photoPicker',
    },
  }

  build() {
    Column() {
      Button('top')
        .width('80%')
        .height(40)
        .margin(3)

      SecurityUIExtensionComponent(this.want)
        .width('90%')
        .height('90%').backgroundColor(Color.Green)
        .onError((error: BusinessError) => {
          this.message = 'Error: ' + JSON.stringify(error);
          hilog.info(0x0000, 'SecurityUIExtensionComponentDemo', this.message);
        })

      Button('bottom')
        .width('80%')
        .height(40)
        .margin(3)
    }
    .height('90%')
    .width('90%')
  }
}
```

ArkTS-Sta示例：

``` TypeScript

import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { State } from '@ohos.arkui.stateManagement'
import { Column, Button, Component, Entry, Color, SecurityUIExtensionComponent } from '@ohos.arkui.component';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  private want: Want = {
    bundleName: 'com.ohos.myapplication',
    abilityName: 'SUIExtensionProvider',
    parameters: {
      'ability.want.params.uiExtensionType': 'sysPicker/photoPicker',
    },
  }

  build() {
    Column() {
      Button('top')
        .width('80%')
        .height(40)
        .margin(3)

      SecurityUIExtensionComponent(this.want)
        .width('90%')
        .height('90%')
        .backgroundColor(Color.Green)
        .onError((error: BusinessError) => {
          this.message = 'Error: ' + JSON.stringify(error);
          hilog.info(0x0000, 'SecurityUIExtensionComponentDemo', this.message);
        })

      Button('bottom')
        .width('80%')
        .height(40)
        .margin(3)
    }
    .height('90%')
    .width('90%')
  }
}
```
