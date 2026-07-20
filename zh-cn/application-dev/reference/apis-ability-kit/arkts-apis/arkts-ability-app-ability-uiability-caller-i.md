# Caller

调用方Caller UIAbility通过[startAbilityByCall](arkts-ability-uiabilitycontext-c.md#startabilitybycall-1)接口拉起目标Callee UIAbility，目标UIAbility启动成功后，返回一个Caller对象给调用方进行通信。

**起始版本：** 9

<!--Device-unnamed-export interface Caller--><!--Device-unnamed-export interface Caller-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## 导入模块

```TypeScript
import { Callee, Caller, OnReleaseCallback, OnRemoteStateChangeCallback, CalleeCallback } from '@kit.AbilityKit';
```

<a id="call"></a>
## call

```TypeScript
call(method: string, data: rpc.Parcelable): Promise<void>
```

Caller UIAbility向Callee UIAbility发送双方约定好的序列化的数据。使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Caller-call(method: string, data: rpc.Parcelable): Promise<void>--><!--Device-Caller-call(method: string, data: rpc.Parcelable): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| method | string | 是 | 由Caller和Callee双方约定好的方法名，Callee方通过该字段区分消息类型。 |
| data | rpc.Parcelable | 是 | 由Caller向Callee发送的消息内容，消息内容是序列化的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16200002](../errorcode-ability.md#16200002-通用组件服务端callee无效) | The callee does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

```TypeScript
import { UIAbility, Caller } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MyMessageAble implements rpc.Parcelable { // 自定义的Parcelable数据结构
  name: string;
  str: string;
  num: number = 1;

  constructor(name: string, str: string) {
    this.name = name;
    this.str = str;
  }

  marshalling(messageSequence: rpc.MessageSequence) {
    messageSequence.writeInt(this.num);
    messageSequence.writeString(this.str);
    console.info(`MyMessageAble marshalling num[${this.num}] str[${this.str}]`);
    return true;
  }

  unmarshalling(messageSequence: rpc.MessageSequence) {
    this.num = messageSequence.readInt();
    this.str = messageSequence.readString();
    console.info(`MyMessageAble unmarshalling num[${this.num}] str[${this.str}]`);
    return true;
  }
}

let method = 'call_Function'; // 约定的通知消息字符串

export default class MainUIAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    this.context.startAbilityByCall({
      bundleName: 'com.example.myservice',
      abilityName: 'MainUIAbility',
      deviceId: ''
    }).then((obj) => {
      let caller: Caller = obj;
      let msg = new MyMessageAble('msg', 'world'); // 参考Parcelable数据定义
      // 向Callee发送消息
      caller.call(method, msg)
        .then(() => {
          console.info('Caller call() called');
        })
        .catch((callErr: BusinessError) => {
          console.error(`Caller.call catch error, error.code: ${callErr.code}, error.message: ${callErr.message}`);
        });
    }).catch((err: BusinessError) => {
      console.error(`Caller GetCaller error, error.code: ${err.code}, error.message: ${err.message}`);
    });
  }
}

```

<a id="callwithresult"></a>
## callWithResult

```TypeScript
callWithResult(method: string, data: rpc.Parcelable): Promise<rpc.MessageSequence>
```

Caller UIAbility向Callee UIAbility发送消息，Callee UIAbility处理完成后返回结果。使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Caller-callWithResult(method: string, data: rpc.Parcelable): Promise<rpc.MessageSequence>--><!--Device-Caller-callWithResult(method: string, data: rpc.Parcelable): Promise<rpc.MessageSequence>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| method | string | 是 | 由Caller和Callee双方约定好的方法名，Callee方通过该字段区分消息类型。 |
| data | rpc.Parcelable | 是 | 由Caller向Callee发送的消息内容，消息内容是序列化的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;rpc.MessageSequence&gt; | Promise对象，返回Callee UIAbility的应答数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16200002](../errorcode-ability.md#16200002-通用组件服务端callee无效) | The callee does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

```TypeScript
import { UIAbility, Caller } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MyMessageable implements rpc.Parcelable {
  name: string
  str: string
  num: number = 1

  constructor(name: string, str: string) {
    this.name = name;
    this.str = str;
  }

  marshalling(messageSequence: rpc.MessageSequence) {
    messageSequence.writeInt(this.num);
    messageSequence.writeString(this.str);
    console.info(`MyMessageAble marshalling num[${this.num}] str[${this.str}]`);
    return true;
  }

  unmarshalling(messageSequence: rpc.MessageSequence) {
    this.num = messageSequence.readInt();
    this.str = messageSequence.readString();
    console.info(`MyMessageAble unmarshalling num[${this.num}] str[${this.str}]`);
    return true;
  }
}

let method = 'call_Function';
let caller: Caller;

export default class MainUIAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    this.context.startAbilityByCall({
      bundleName: 'com.example.myservice',
      abilityName: 'MainUIAbility',
      deviceId: ''
    }).then((obj) => {
      caller = obj;
      let msg = new MyMessageAble('msg', 'world');
      // 向Callee发送消息并获取返回结果
      caller.callWithResult(method, msg)
        .then((data) => {
          console.info('Caller callWithResult() called');
          let retMsg = new MyMessageAble('msg', 'world');
          data.readParcelable(retMsg); // 读取Callee返回的Parcelable数据
        })
        .catch((callErr: BusinessError) => {
          console.error(`Caller.callWithResult catch error, error.code: ${callErr.code}, error.message: ${callErr.message}`);
        });
    }).catch((err: BusinessError) => {
      console.error(`Caller GetCaller error, error.code: ${err.code}, error.message: ${err.message}`);
    });
  }
}

```

<a id="off"></a>
## off('release')

```TypeScript
off(type: 'release', callback: OnReleaseCallback): void
```

取消注册Callee UIAbility断开通知的监听，与[on('release')](Caller.on)是反向操作，当前暂未支持。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Caller-off(type: 'release', callback: OnReleaseCallback): void--><!--Device-Caller-off(type: 'release', callback: OnReleaseCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'release' | 是 | 监听releaseCall事件，固定为'release'。 |
| callback | [OnReleaseCallback](arkts-ability-app-ability-uiability-onreleasecallback-i.md) | 是 | 回调函数，返回off回调结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { UIAbility, Caller, OnReleaseCallback } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MainUIAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    this.context.startAbilityByCall({
      bundleName: 'com.example.myservice',
      abilityName: 'MainUIAbility',
      deviceId: ''
    }).then((obj) => {
      let caller: Caller = obj;
      try {
        // 定义断开连接的回调函数
        let onReleaseCallBack: OnReleaseCallback = (str) => {
          console.info(`Caller OnRelease CallBack is called ${str}`);
        };
        caller.on('release', onReleaseCallBack); // 注册断开连接的监听
        caller.off('release', onReleaseCallBack); // 取消注册断开连接的监听
      } catch (error) {
        console.error(`Caller.on or Caller.off catch error, error.code: ${error.code}, error.message: ${error.message}`);
      }
    }).catch((err: BusinessError) => {
      console.error(`Caller GetCaller error, error.code: ${err.code}, error.message: ${err.message}`);
    });
  }
}

```

<a id="off-1"></a>
## off

```TypeScript
off(type: 'release'): void
```

取消注册Callee UIAbility断开通知的监听，与[Caller.on('release')](Caller.on)是反向操作，当前暂未支持。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Caller-off(type: 'release'): void--><!--Device-Caller-off(type: 'release'): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'release' | 是 | 监听releaseCall事件，固定为'release'。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { UIAbility, Caller, OnReleaseCallback } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let caller: Caller;

export default class MainUIAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    this.context.startAbilityByCall({
      bundleName: 'com.example.myservice',
      abilityName: 'MainUIAbility',
      deviceId: ''
    }).then((obj) => {
      caller = obj;
      try {
        let onReleaseCallBack: OnReleaseCallback = (str) => {
          console.info(`Caller OnRelease CallBack is called ${str}`);
        };
        caller.on('release', onReleaseCallBack);
        caller.off('release'); // 取消注册所有断开连接的监听
      } catch (error) {
        console.error(`Caller.on or Caller.off catch error, error.code: ${error.code}, error.message: ${error.message}`);
      }
    }).catch((err: BusinessError) => {
      console.error(`Caller GetCaller error, error.code: ${err.code}, error.message: ${err.message}`);
    });
  }
}

```

<a id="on"></a>
## on('release')

```TypeScript
on(type: 'release', callback: OnReleaseCallback): void
```

Caller UIAbility可使用该接口注册与Callee UIAbility连接断开通知的监听。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Caller-on(type: 'release', callback: OnReleaseCallback): void--><!--Device-Caller-on(type: 'release', callback: OnReleaseCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'release' | 是 | 监听releaseCall事件，固定为'release'。 |
| callback | [OnReleaseCallback](arkts-ability-app-ability-uiability-onreleasecallback-i.md) | 是 | 回调函数，返回on回调结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

**示例：**

```TypeScript
import { UIAbility, Caller } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MainUIAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let dstDeviceId: string = 'xxxx';
    this.context.startAbilityByCall({
      bundleName: 'com.example.myservice',
      abilityName: 'MainUIAbility',
      deviceId: dstDeviceId
    }).then((obj) => {
      let caller: Caller = obj;
      try {
        // 注册release事件监听
        caller.on('release', (str) => {
          console.info(`Caller OnRelease CallBack is called ${str}`);
        });
      } catch (error) {
        console.error(`Caller.on catch error, error.code: ${error.code}, error.message: ${error.message}`);
      }
    }).catch((err: BusinessError) => {
      console.error(`Caller GetCaller error, error.code: ${err.code}, error.message: ${err.message}`);
    });
  }
}

```

<a id="onrelease"></a>
## onRelease

```TypeScript
onRelease(callback: OnReleaseCallback): void
```

Caller UIAbility可使用该接口注册与Callee UIAbility连接断开通知的监听。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Caller-onRelease(callback: OnReleaseCallback): void--><!--Device-Caller-onRelease(callback: OnReleaseCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnReleaseCallback](arkts-ability-app-ability-uiability-onreleasecallback-i.md) | 是 | 回调函数，返回onRelease回调结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

**示例：**

```TypeScript
import { UIAbility, Caller } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MainUIAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    this.context.startAbilityByCall({
      bundleName: 'com.example.myservice',
      abilityName: 'MainUIAbility',
      deviceId: ''
    }).then((obj) => {
      let caller: Caller = obj;
      try {
        // 注册与Callee UIAbility连接断开监听
        caller.onRelease((str) => {
          console.info(`Caller OnRelease CallBack is called ${str}`);
        });
      } catch (error) {
        console.error(`Caller.onRelease catch error, error.code: ${error.code}, error.message: ${error.message}`);
      }
    }).catch((err: BusinessError) => {
      console.error(`Caller GetCaller error, error.code: ${err.code}, error.message: ${err.message}`);
    });
  }
}

```

<a id="onremotestatechange"></a>
## onRemoteStateChange

```TypeScript
onRemoteStateChange(callback: OnRemoteStateChangeCallback): void
```

注册协同场景下跨设备组件状态变化监听通知。使用callback异步回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Caller-onRemoteStateChange(callback: OnRemoteStateChangeCallback): void--><!--Device-Caller-onRemoteStateChange(callback: OnRemoteStateChangeCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnRemoteStateChangeCallback](arkts-ability-app-ability-uiability-onremotestatechangecallback-i.md) | 是 | 回调函数，返回onRemoteStateChange回调结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

**示例：**

```TypeScript
import { UIAbility, Caller } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MainAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let dstDeviceId: string = 'xxxxx';
    this.context.startAbilityByCall({
      bundleName: 'com.example.myservice',
      abilityName: 'MainUIAbility',
      deviceId: dstDeviceId
    }).then((obj) => {
      let caller: Caller = obj;
      try {
        // 注册协同场景下跨设备组件状态变化监听
        caller.onRemoteStateChange((str) => {
          console.info('Remote state changed ' + str);
        });
      } catch (error) {
        let code = (error as BusinessError).code;
        let msg = (error as BusinessError).message; 
        console.error(`Caller.onRemoteStateChange catch error, error.code: ${code}, error.message: ${msg}.`);
      }
    }).catch((err: BusinessError) => {
      console.error(`Caller GetCaller error, error.code: ${err.code}, error.message: ${err.message}`);
    });
  }
}

```

<a id="release"></a>
## release

```TypeScript
release(): void
```

Caller主动释放与Callee UIAbility的连接。调用该接口后，Caller不能再使用call或callWithResult向Callee方发送消息。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Caller-release(): void--><!--Device-Caller-release(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16200002](../errorcode-ability.md#16200002-通用组件服务端callee无效) | The callee does not exist. |

**示例：**

```TypeScript
import { UIAbility, Caller } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let caller: Caller;

export default class MainUIAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    this.context.startAbilityByCall({
      bundleName: 'com.example.myservice',
      abilityName: 'MainUIAbility',
      deviceId: ''
    }).then((obj) => {
      caller = obj;
      try {
        // 释放Caller与Callee的连接
        caller.release();
      } catch (releaseErr) {
        console.error(`Caller.release catch error, error.code: ${releaseErr.code}, error.message: ${releaseErr.message}`);
      }
    }).catch((err: BusinessError) => {
      console.error(`Caller GetCaller error, error.code: ${err.code}, error.message: ${err.message}`);
    });
  }
}

```

