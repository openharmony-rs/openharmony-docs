# SecurityUIExtensionComponent (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

SecurityUIExtensionComponent用于支持在本页面内嵌入其他应用提供的UI，展示的内容在另一个进程中运行，本应用并不参与其中的布局和渲染。

> **说明：**
>
> - 本模块为系统接口。
> - 本模块仅可在Stage模型下使用。

**起始版本：** 26.0.0

## 子组件

无

## 接口

SecurityUIExtensionComponent(want: Want, options?: SecurityUIExtensionOptions)

创建SecurityUIExtensionComponent组件，用于嵌入显示远程UIExtensionAbility提供的UI。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| want | [Want](../../apis-ability-kit/js-apis-app-ability-want.md) | 是 | 要加载的Ability信息。 |
| options | [SecurityUIExtensionOptions](#securityuiextensionoptions) | 否 | 用于构造SecurityUIExtensionComponent的参数。不填时各字段使用默认值。 |

## SecurityUIExtensionOptions

用于构造SecurityUIExtensionComponent时传递参数。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| isTransferringCaller | boolean | 否 | 是 | 在使用UIExtensionComponent嵌套时，设置当前UIExtensionComponent是否转发上一级的Caller信息。</br> 默认值：false |
| placeholder | [ComponentContent](../js-apis-arkui-ComponentContent.md) | 否 | 是 | 设置占位符，在SecurityUIExtensionComponent与UIExtensionAbility建立连接前显示。 |
| dpiFollowStrategy | [SecurityDpiFollowStrategy](#securitydpifollowstrategy) | 否 | 是 | 设置SecurityUIExtensionComponent内容分辨率跟随策略，用于控制嵌入的UIExtensionAbility内容是跟随宿主应用的分辨率还是使用自身的分辨率。默认值：FOLLOW_UI_EXTENSION_ABILITY_DPI。 |

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

onRemoteReady(callback: Callback\<SecurityUIExtensionProxy\>)

UIExtensionAbility连接完成时触发的回调，使用callback异步回调。之后可通过返回的[SecurityUIExtensionProxy](#securityuiextensionproxy)向被拉起的Ability发送数据。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | Callback\<[SecurityUIExtensionProxy](#securityuiextensionproxy)\> | 是 | 回调函数，用于向对端Ability发送数据。 |

### onReceive

onReceive(callback: Callback\<Record\<string, Object\>\>)

收到被拉起的Ability发送的数据时触发的回调。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<Record\<string, Object\>\> | 是 | 回调函数，返回收到的来自对端Ability的数据。 |

### onError

onError(callback: [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback))

被拉起的Ability扩展在运行过程中发生异常时触发的回调，不包含与UIExtensionAbility断开连接场景。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback) | 是 | 回调函数，入参用于接收异常信息。 |

### onTerminated

onTerminated(callback: Callback\<TerminationInfo>)

被拉起的UIExtensionAbility通过调用[terminateSelfWithResult](../../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult)或[terminateSelf](../../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateself)正常退出时触发此回调。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[TerminationInfo](#terminationinfo)\> | 是 | 回调函数，入参用于接收UIExtensionAbility的返回结果。 |

## TerminationInfo

用于表示被拉起的UIExtensionAbility正常退出时的返回结果。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| code | number | 否 | 否 | 被拉起UIExtensionAbility退出时返回的结果码，0表示正常退出，非0表示异常退出。具体结果码含义由被拉起的UIExtensionAbility定义。 |
| want | [Want](../../apis-ability-kit/js-apis-app-ability-want.md) | 否 | 是 | 被拉起UIExtensionAbility退出时返回的数据。 |

## SecurityUIExtensionProxy

用于在双方建立连接成功后，向组件使用方被拉起的Ability发送数据，以及订阅和取消订阅的注册。

### send

send(data: Record\<string, Object\>): void

用于在双方建立连接成功后，向组件使用方被拉起的Ability发送数据，提供异步发送能力。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| data | Record\<string, Object\> | 是 | 异步发送给被拉起的扩展Ability的数据。 |

### sendSync

sendSync(data: Record\<string, Object\>): Record\<string, Object\>

用于在双方建立连接成功后，向组件使用方被拉起的Ability发送数据，提供同步发送能力。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| data | Record\<string, Object\> | 是 | 同步发送给被拉起的扩展Ability的数据。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Record\<string, Object\> | 扩展Ability返回的数据。 |

**错误码：**

以上错误码的详细介绍请参见[UIExtension错误码](../errorcode-uiextension.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 100011 | No callback has been registered to respond to this request. |
| 100012 | Transferring data failed. |

### on('asyncReceiverRegister')

on(type: 'asyncReceiverRegister', callback: Callback\<SecurityUIExtensionProxy\>): void

订阅被拉起的Ability发生异步注册的回调。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 固定填'asyncReceiverRegister'，代表订阅扩展Ability发生异步注册回调。 |
| callback | Callback\<[SecurityUIExtensionProxy](#securityuiextensionproxy)\> | 是 | 回调函数。订阅扩展Ability注册setReceiveDataCallback后触发的回调。 |

### on('syncReceiverRegister')

on(type: 'syncReceiverRegister', callback: Callback\<SecurityUIExtensionProxy\>): void

订阅被拉起的Ability发生同步注册的回调。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 固定填'syncReceiverRegister'，订阅扩展Ability发生同步注册回调。 |
| callback | Callback\<[SecurityUIExtensionProxy](#securityuiextensionproxy)\> | 是 | 回调函数。扩展Ability注册setReceiveDataForResultCallback后触发的回调。 |

### off('asyncReceiverRegister')

off(type: 'asyncReceiverRegister', callback?: Callback\<SecurityUIExtensionProxy\>): void

取消订阅被拉起的Ability发生异步注册的回调。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 固定填'asyncReceiverRegister'，取消订阅扩展Ability发生异步注册回调。 |
| callback | Callback\<[SecurityUIExtensionProxy](#securityuiextensionproxy)\> | 否 | 回调函数。为空代表取消订阅所有扩展Ability异步注册后触发回调。非空代表取消订阅异步对应回调。 |

### off('syncReceiverRegister')

off(type: 'syncReceiverRegister', callback?: Callback\<SecurityUIExtensionProxy\>): void

取消订阅被拉起的Ability发生同步注册后触发的回调。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 固定填'syncReceiverRegister'，取消订阅扩展Ability发生同步注册回调。 |
| callback | Callback\<[SecurityUIExtensionProxy](#securityuiextensionproxy)\> | 否 | 指定取消订阅的回调。为空代表取消订阅所有扩展Ability同步注册后触发回调。 |

## 示例

### 示例（SecurityUIExtensionComponent基础使用）

本示例展示`SecurityUIExtensionComponent`组件的基础使用方式，包括使用方加载远程UIExtensionAbility、双向数据通信和生命周期管理。示例应用的`bundleName`为"com.example.securityuidemo"，被拉起的`UIExtensionAbility`为"SecurityUIExtProvider"。

- 使用方入口界面`ets/pages/Index.ets`内容如下：

```ts
import { Want, ComponentContent } from '@kit.ArkUI';

class Params {
}

@Builder
function LoadingBuilder(params: Params) {
  Column() {
    LoadingProgress()
      .color(Color.Blue)
  }
}

@Entry
@Component
struct Index {
  @State message: string = '等待接收数据';
  @State visible: Visibility = Visibility.Hidden;
  @State wid: number = 300;
  @State hei: number = 300;
  private proxy: SecurityUIExtensionProxy | null = null;
  private initPlaceholder = new ComponentContent(this.getUIContext(), wrapBuilder(LoadingBuilder), new Params);

  aboutToDisappear(): void {
    this.proxy?.off('syncReceiverRegister');
    this.proxy?.off('asyncReceiverRegister');
  }

  build() {
    Column() {
      Text(this.message).fontSize(20).margin({ bottom: 10 })

      SecurityUIExtensionComponent(
        {
          bundleName: 'com.example.securityuidemo',
          abilityName: 'SecurityUIExtProvider',
          parameters: {
            'ability.want.params.uiExtensionType': 'sys/commonUI'
          }
        } as Want,
        {
          placeholder: this.initPlaceholder,
          dpiFollowStrategy: SecurityDpiFollowStrategy.FOLLOW_HOST_DPI
        }
      )
        .width(this.wid)
        .height(this.hei)
        .border({ width: 2, color: Color.Blue })
        .onRemoteReady((proxy: SecurityUIExtensionProxy) => {
          console.info('onRemoteReady');
          this.proxy = proxy;
          this.proxy.on('asyncReceiverRegister', (proxy1: SecurityUIExtensionProxy) => {
            console.info('asyncReceiverRegister callback');
          });
          this.proxy.on('syncReceiverRegister', (proxy2: SecurityUIExtensionProxy) => {
            console.info('syncReceiverRegister callback');
          });
        })
        .onReceive((data: Record<string, Object>) => {
          this.message = JSON.stringify(data);
          console.info('onReceive: ' + JSON.stringify(data));
        })
        .onError((error: BusinessError) => {
          console.error('onError: code = ' + error.code);
        })
        .onTerminated((info: TerminationInfo) => {
          console.info('onTerminated: code = ' + info.code + ', want = ' + JSON.stringify(info.want));
        })

      Button('向UIExtensionAbility发送数据').margin({ top: 10 }).onClick(() => {
        if (this.proxy) {
          this.proxy.send({ data: 'Hello from SecurityUIExtensionComponent' });
          try {
            let result = this.proxy.sendSync({ data: 'Sync Hello' });
            console.info('sendSync result: ' + JSON.stringify(result));
          } catch (err) {
            console.error('sendSync failed: ' + JSON.stringify(err));
          }
        }
      })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

- 提供方扩展Ability文件`ets/uiextensionability/SecurityUIExtProvider.ets`内容如下：

```ts
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';

const TAG: string = '[SecurityUIExtProvider]';

export default class SecurityUIExtProvider extends UIExtensionAbility {
  onCreate() {
    console.info(TAG, `onCreate`);
  }

  onForeground() {
    console.info(TAG, `onForeground`);
  }

  onBackground() {
    console.info(TAG, `onBackground`);
  }

  onDestroy() {
    console.info(TAG, `onDestroy`);
  }

  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    console.info(TAG, `onSessionCreate, want: ${JSON.stringify(want)}`);
    let param: Record<string, UIExtensionContentSession> = {
      'session': session
    };
    let storage: LocalStorage = new LocalStorage(param);
    session.loadContent('pages/extension', storage);
  }

  onSessionDestroy(session: UIExtensionContentSession) {
    console.info(TAG, `onSessionDestroy`);
  }
}
```

- 提供方扩展Ability入口页面文件`ets/pages/extension.ets`内容如下：

```ts
import { UIExtensionContentSession } from '@kit.AbilityKit';

let storage = new LocalStorage();

@Entry(storage)
@Component
struct Extension {
  private session: UIExtensionContentSession | undefined = storage.get<UIExtensionContentSession>('session');
  @State message: string = '';

  onPageShow() {
    if (this.session) {
      this.session.setReceiveDataCallback((data: Record<string, Object>) => {
        this.message = JSON.stringify(data);
        console.info('receiveData: ' + JSON.stringify(data));
      });

      this.session.setReceiveDataForResultCallback((data: Record<string, Object>): Record<string, Object> => {
        this.message = JSON.stringify(data);
        console.info('receiveDataForResult: ' + JSON.stringify(data));
        return { result: 'Handled' };
      });
    }
  }

  build() {
    Column() {
      Text('SecurityUIExtensionAbility页面').fontSize(20).fontWeight(FontWeight.Bold)
      Text(this.message).fontSize(16).margin({ top: 10 })
      Button('向使用方发送数据').margin({ top: 10 }).onClick(() => {
        if (this.session) {
          this.session.sendData({ data: 'Hello from UIExtensionAbility' });
        }
      })
      Button('退出').margin({ top: 10 }).onClick(() => {
        if (this.session) {
          this.session.terminateSelf();
        }
        storage.clear();
      })
      Button('退出并返回结果').margin({ top: 10 }).onClick(() => {
        if (this.session) {
          this.session.terminateSelfWithResult({
            resultCode: 0,
            want: {
              bundleName: 'com.example.securityuidemo',
              parameters: { result: 123456 }
            }
          });
        }
        storage.clear();
      })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

- 在`module.json5`配置文件的"extensionAbilities"标签下增加`SecurityUIExtProvider`配置：

```json
{
  "name": "SecurityUIExtProvider",
  "srcEntry": "./ets/uiextensionability/SecurityUIExtProvider.ets",
  "type": "sys/commonUI",
  "exported": true
}
```
