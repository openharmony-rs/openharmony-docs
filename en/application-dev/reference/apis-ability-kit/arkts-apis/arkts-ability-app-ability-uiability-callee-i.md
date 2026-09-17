# Callee

Background communication object created by the system for the UIAbility, known as the Callee UIAbility (Callee), which is capable of receiving data sent from the Caller object.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## Modules to Import

```TypeScript
import { UIAbility, Callee, CalleeCallback, Caller, OnReleaseCallback, OnRemoteStateChangeCallback } from '@kit.AbilityKit';
```

## off

```TypeScript
off(method: string): void
```

Unregisters a caller notification callback, which is invoked when the target UIAbility registers a function.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| method | string | Yes | Registered notification message string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16200005](../errorcode-ability.md#16200005-method-not-registered) | The method has not been registered. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { UIAbility, AbilityConstant, Want } from '@kit.AbilityKit';

let method = 'call_Function';

export default class MainUIAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info('Callee onCreate is called');
    try {
      // Unregister the message listener.
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

Registers a caller notification callback, which is invoked when the target UIAbility registers a function.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| method | string | Yes | Method name agreed upon by the Caller UIAbility and Callee UIAbility, used by the Callee UIAbility to identify the type of message. |
| callback | [CalleeCallback](arkts-ability-app-ability-uiability-calleecallback-i.md) | Yes | JS notification synchronization callback of the [rpc.MessageSequence](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-messagesequence-c.md) type. The callback must return at least one empty [rpc.Parcelable](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-parcelable-i.md) object. Otherwise, the function execution fails. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16200004](../errorcode-ability.md#16200004-method-registered) | The method has been registered. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

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

// Define the message processing callback function on the Callee side.
function funcCallBack(pdata: rpc.MessageSequence) {
  let msg = new MyMessageAble('test', '');
  pdata.readParcelable(msg);
  // Return the processing result to the Caller.
  return new MyMessageAble('test1', 'Callee test');
}

export default class MainUIAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info('Callee onCreate is called');
    try {
      // Register a message listener. The callback is triggered when the Caller sends the specified method name.
      this.callee.on(method, funcCallBack);
    } catch (error) {
      console.error(`Callee.on catch error, error.code: ${error.code}, error.message: ${error.message}`);
    }
  }
}
```
