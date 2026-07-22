# Callee

系统为UIAbility创建的后台通信对象，Callee UIAbility（被调用方）可以通过Callee对象接收Caller对象发送的数据。

**起始版本：** 9

<!--Device-unnamed-export interface Callee--><!--Device-unnamed-export interface Callee-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## 导入模块

```TypeScript
import { Callee, Caller, OnReleaseCallback, OnRemoteStateChangeCallback, CalleeCallback } from '@kit.AbilityKit';
```

## off

```TypeScript
off(method: string): void
```

解除通用组件服务端注册消息通知callback。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Callee-off(method: string): void--><!--Device-Callee-off(method: string): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| method | string | 是 | 已注册的通知事件字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16200005](../errorcode-ability.md#16200005-方法未注册) | The method has not been registered. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

```TypeScript
import { UIAbility, AbilityConstant, Want } from '@kit.AbilityKit';

let method = 'call_Function';

export default class MainUIAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info('Callee onCreate is called');
    try {
      // 取消注册消息监听
      this.callee.off(method);
    } catch (error) {
      console.error(`Callee.off catch error, error.code: ${error.code}, error.message: ${error.message}`);
    }
  }
}

```

## on

```TypeScript
on(method: string, callback: CalleeCallback): void
```

通用组件服务端注册消息通知callback。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Callee-on(method: string, callback: CalleeCallback): void--><!--Device-Callee-on(method: string, callback: CalleeCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| method | string | 是 | 由Caller和Callee双方约定好的方法名，Callee方通过该字段区分消息类型。 |
| callback | [CalleeCallback](arkts-ability-app-ability-uiability-calleecallback-i.md) | 是 | 一个[rpc.MessageSequence](./@ohos.rpc:rpc.MessageSequence)类型入参的js通知同步回调函数, 回调函数至少要返回一个空的[rpc.Parcelable](./@ohos.rpc:rpc.Parcelable)数据对象, 其他视为函数执行错误。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16200004](../errorcode-ability.md#16200004-方法已注册) | The method has been registered. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

```TypeScript
import { UIAbility, AbilityConstant, Want } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';

class MyMessageAble implements rpc.Parcelable {
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

// 定义Callee端的消息处理回调函数
function funcCallBack(pdata: rpc.MessageSequence) {
  let msg = new MyMessageAble('test', '');
  pdata.readParcelable(msg);
  // 返回处理结果给Caller
  return new MyMessageAble('test1', 'Callee test');
}

export default class MainUIAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info('Callee onCreate is called');
    try {
      // 注册消息监听，当Caller发送指定方法名时会触发回调
      this.callee.on(method, funcCallBack);
    } catch (error) {
      console.error(`Callee.on catch error, error.code: ${error.code}, error.message: ${error.message}`);
    }
  }
}

```

