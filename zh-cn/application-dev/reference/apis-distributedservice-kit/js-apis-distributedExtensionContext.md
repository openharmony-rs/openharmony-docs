# @ohos.application.DistributedExtensionContext (协同Extension上下文)
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @hu-zhiqiong-->

DistributedExtensionContext模块是DistributedExtensionAbility（分布式扩展能力）的上下文环境，继承自ExtensionContext（扩展上下文）。它提供协同Extension所需的上下文信息与能力，用于跨设备连接远端ServiceExtensionAbility（服务扩展能力）等协同场景，支持开发者实现分布式协作。

> **说明：**
> 
> 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标标记接口的起始版本。
>
> 本模块接口仅可在Stage模型下使用。

## 使用说明

通过DistributedExtensionAbility子类实例获取DistributedExtensionContext。

```ts
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onCreate() {
    let context = this.context; // 获取DistributedExtensionContext
  }
}
```

## DistributedExtensionContext.connectServiceExtensionAbility

connectServiceExtensionAbility(want: Want, options: ConnectOptions): long

将当前DistributedExtensionAbility连接到远端（其他设备上的）ServiceExtensionAbility（服务扩展能力），建立连接后通过onConnect回调返回的[rpc.IRemoteObject](../apis-ipc-kit/js-apis-rpc.md#iremoteobject)代理与远端ServiceExtensionAbility进行跨设备IPC通信，以使用其对外提供的能力。适用于多设备协同场景，例如在当前设备上调用其他设备的后台服务能力。使用时，开发者首先通过Want中的deviceId指定目标设备、bundleName和abilityName指定目标ServiceExtensionAbility，并构造[ConnectOptions](../apis-ability-kit/js-apis-inner-ability-connectOptions.md)实现onConnect、onDisconnect、onFailed三个回调分别处理连接成功、连接断开和连接失败状态；随后调用connectServiceExtensionAbility发起连接并获取返回的连接ID，连接成功后在onConnect回调中拿到IRemoteObject代理对象，基于该代理与远端ServiceExtensionAbility进行IPC通信；使用完毕后需调用[disconnectServiceExtensionAbility](#distributedextensioncontextdisconnectserviceextensionability)断开连接并释放资源。

ServiceExtensionAbility是一类特殊的[ExtensionAbility](../../application-models/extensionability-overview.md)组件，由系统提供，通常用于提供指定场景的后台服务能力，不支持开发者自定义。ServiceExtensionAbility可以被其他组件连接，并根据调用者的请求信息在后台处理相关事务。连接为长连接，系统不会自动断开，使用完毕后必须由调用方主动调用disconnectServiceExtensionAbility断开连接并释放资源。组件启动规则详见[组件启动规则（Stage模型）](../../application-models/component-startup-rules.md)。

**起始版本：** 26.0.0

**配对调用：**
- 调用后必须调用disconnectServiceExtensionAbility释放连接资源。
- 需要使用此方法返回的连接ID调用disconnectServiceExtensionAbility。
- 未调用disconnectServiceExtensionAbility会导致连接资源泄漏。

**模型约束**：此接口仅可在`Stage`模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名  | 类型                                                         | 必填 | 说明                                                         |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| want    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)      | 是   | 传入需要连接的远端ServiceExtensionAbility（服务扩展能力）的Want（意图）信息，如ability名称、bundle名称、deviceId等。系统将基于这些信息建立到远端设备的连接。 |
| options | [ConnectOptions](../apis-ability-kit/js-apis-inner-ability-connectOptions.md) | 是   | ConnectOptions类型的配置对象，包含服务连接状态回调。连接成功时触发onConnect，连接断开时触发onDisconnect，连接失败时触发onFailed。 |

**返回值：**

| 类型   | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| long | 返回连接ID，后续通过该ID断开连接。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](../apis-ability-kit/errorcode-ability.md)。

| 错误码ID | 错误信息 | 说明 |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. | 参数错误。可能的导致原因：1. 必选参数未指定；2. 参数类型错误；3. 参数校验失败。请检查参数类型和范围，确保必选参数已正确填写。 |
| 16000001 | The specified ability does not exist. | 指定的ability不存在。请检查ability名称、bundle名称等配置是否正确。 |
| 16000002 | Incorrect ability type. | ability类型错误。请检查ability类型是否符合要求。 |
| 16000004 | Cannot start an invisible component. | 无法启动不可见组件。请检查组件是否配置为可见。 |
| 16000005 | The specified process does not have the permission. | 指定进程没有权限。请检查是否已申请相应权限。 |
| 16000006 | Cross-user operations are not allowed. | 不允许跨用户操作。请检查操作是否涉及跨用户调用。 |
| 16000008 | The crowdtesting application expires. | 众测应用已过期。请更新应用版本或重新申请。 |
| 16000011 | The context does not exist. | context不存在。请检查ability是否已被销毁。 |
| 16000012 | The application is controlled. | 应用被管控。请检查应用是否被系统管控。 |
| 16000013 | The application is controlled by EDM. | 应用被EDM管控。请检查EDM策略配置。 |
| 16000050 | Internal error. | 内部错误。请稍后重试。 |
| 16000053 | The ability is not on the top of the UI. | ability不在UI顶层。请检查ability是否为当前前台页面。 |
| 16000055 | Installation-free timed out. | 免安装超时。请检查网络连接或重新尝试。 |

**示例：**

```ts
import { AbilityConstant, Want } from '@kit.AbilityKit';
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleManager } from '@kit.AbilityKit';

const TAG = 'DistributedExtAbility';
const DOMAIN = 0xFF00;

export default class DistributedExtAbility extends DistributedExtensionAbility {


  onCreate(want: Want) {
    hilog.info(DOMAIN, TAG, 'onCreate');
    this.testConnectServiceExtensionAbility();
  }

  onCollaborate(wantParam: Record<string, Object>) {
    hilog.info(DOMAIN, TAG, 'onCollaborate');
    return AbilityConstant.CollaborateResult.ACCEPT;
  }

  onDestroy () {
    hilog.info(DOMAIN, TAG, 'onDestroy');
  }

  connectId: number = -1;
  private testConnectServiceExtensionAbility() {
    hilog.info(DOMAIN, TAG, 'testConnectServiceExtensionAbility');
    let deviceId1: string = '';
    try {
      // 创建设备管理器实例
      let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
      deviceId1 = dmInstance.getLocalDeviceId();
      const message: string = 'local device id: ' + deviceId1;
      hilog.info(DOMAIN, TAG, message);
    } catch (e) {
      let err: BusinessError = e as BusinessError;
      console.error(`Failed to get local device ID. Code: ${err.code}, message: ${err.message}`);
    }
    // 构造连接远端ServiceExtensionAbility所需的Want参数
    const targetWant:Want = {
      deviceId: deviceId1,
      bundleName: 'com.example.test0002',
      abilityName: 'ServiceExtAbility',
    }
    // 构造连接选项，包含连接成功、断开、失败的回调函数
    const options: common.ConnectOptions = {
      onConnect: (name: bundleManager.ElementName, remote: rpc.IRemoteObject): void => {
        const message: string = 'onConnect: ' + name;
        hilog.info(DOMAIN, TAG, message);
      },
      onDisconnect: (name: bundleManager.ElementName): void => {
        const message: string = 'onDisconnect: ' + name;
        hilog.info(DOMAIN, TAG, message);
      },
      onFailed: (code: number): void => {
        const message: string = 'onFailed: code=' + code;
        hilog.info(DOMAIN, TAG, message);
      }
    };
    try {
      // 连接远端ServiceExtensionAbility，并获取连接ID
      const id = this.context.connectServiceExtensionAbility(targetWant, options);
      this.connectId = id;
      const message: string = 'connect called, id=' + id;
      hilog.info(DOMAIN, TAG, message);
    } catch (e) {
      let err: BusinessError = e as BusinessError;
      console.error(`Failed to connect service. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```



## DistributedExtensionContext.disconnectServiceExtensionAbility

disconnectServiceExtensionAbility(connection: long): Promise\<void\>

断开与远端ServiceExtensionAbility（服务扩展能力）的连接，断开连接之后开发者需要将连接成功时onConnect回调中返回的remote对象置空，以避免后续误用已失效的代理对象。使用Promise异步回调。

**起始版本：** 26.0.0

**说明**：与connectServiceExtensionAbility采用同步返回不同，disconnectServiceExtensionAbility采用异步回调方式，需要通过Promise.then/catch或async/await处理异步结果。

**配对调用**：此方法应与connectServiceExtensionAbility配对使用。调用connectServiceExtensionAbility后，必须在使用完毕后调用此方法释放连接资源。需要使用connectServiceExtensionAbility返回的连接ID调用此方法。

**模型约束**：此接口仅可在`Stage`模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名     | 类型   | 必填 | 说明                                                     |
| ---------- | ------ | ---- | -------------------------------------------------------- |
| connection | long | 是   | 连接ID，必须使用connectServiceExtensionAbility返回的连接ID值。使用不存在的连接ID将抛出16000003错误码（The connection id does not exist）。 |

**返回值：**

| 类型            | 说明                               |
| --------------- | ---------------------------------- |
| Promise\<void\> | Promise对象。表示异步断开连接操作，resolve表示断开连接成功，reject表示断开连接失败并返回错误。 |

**错误码：**

以下错误码的详细介绍请参见[元能力子系统错误码](../apis-ability-kit/errorcode-ability.md)。

| 错误码ID | 错误信息 | 说明 |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 16000003 | The connection id does not exist. | 连接ID不存在。请检查连接ID是否正确，或连接是否已被断开。 |
| 16000011 | The ability has been destroyed. The context is no longer valid. | ability已被销毁，context不再有效。请避免在ability销毁后使用context。 |
| 16000050 | Internal error. | 内部错误。请稍后重试。 |

**示例：**

```ts
import { AbilityConstant } from '@kit.AbilityKit';
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';


const TAG = 'DistributedExtAbility';
const DOMAIN = 0xFF00;

export default class DistributedExtAbility extends DistributedExtensionAbility {


  onCreate() {
    hilog.info(DOMAIN, TAG, 'onCreate');
  }

  onCollaborate(wantParam: Record<string, Object>) {
    hilog.info(DOMAIN, TAG, 'onCollaborate');
    return AbilityConstant.CollaborateResult.ACCEPT;
  }

  onDestroy () {
    hilog.info(DOMAIN, TAG, 'onDestroy');
    this.testDisconnectServiceExtensionAbility();
  }

  connectId: number = -1; // 注意：在实际使用时，需先通过connectServiceExtensionAbility接口获取有效的连接ID，并等待onConnect回调确认连接成功后，才能调用disconnectServiceExtensionAbility断开连接

  private async testDisconnectServiceExtensionAbility() {
    hilog.info(DOMAIN, TAG, 'testDisconnectServiceExtensionAbility');
    try {
      // 断开与远端ServiceExtensionAbility的连接
      await this.context.disconnectServiceExtensionAbility(this.connectId);
      hilog.info(DOMAIN, TAG, 'disconnect success');
    } catch (e) {
      let err: BusinessError = e as BusinessError;
      hilog.error(DOMAIN, TAG, `disconnect errCode: ${err.code}, errMessage: ${err.message}`);
    }
  }
}
```