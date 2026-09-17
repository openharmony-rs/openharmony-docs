# Parcelable

Writes an object to a **MessageSequence** and reads it from the **MessageSequence** during IPC.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

## Modules to Import

```TypeScript
import { rpc } from '@kit.IPCKit';
```

## marshalling

```TypeScript
marshalling(dataOut: MessageSequence): boolean
```

Marshals this **Parcelable** object into a **MessageSequence** object.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataOut | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | Yes | **MessageSequence** object to which the **Parcelable** object is to be marshaled. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyParcelable implements rpc.Parcelable {
  num: number = 0;
  str: string = '';
  constructor(num: number, str: string) {
    this.num = num;
    this.str = str;
  }
  marshalling(messageSequence: rpc.MessageSequence): boolean {
    messageSequence.writeInt(this.num);
    messageSequence.writeString(this.str);
    return true;
  }
  unmarshalling(messageSequence: rpc.MessageSequence): boolean {
    this.num = messageSequence.readInt();
    this.str = messageSequence.readString();
    hilog.info(0x0000, 'testTag', 'readInt is ' + this.num + ' readString is ' + this.str);
    return true;
  }
}

try {
  let parcelable = new MyParcelable(1, "aaa");
  let data = rpc.MessageSequence.create();
  data.writeParcelable(parcelable);
  let ret = new MyParcelable(0, "");
  data.readParcelable(ret);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## unmarshalling

```TypeScript
unmarshalling(dataIn: MessageSequence): boolean
```

Unmarshals this **Parcelable** object from a **MessageSequence** object.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataIn | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | Yes | **MessageSequence** object from which the **Parcelable** object is to be unmarshaled. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyParcelable implements rpc.Parcelable {
  num: number = 0;
  str: string = '';
  constructor(num: number, str: string) {
    this.num = num;
    this.str = str;
  }
  marshalling(messageSequence: rpc.MessageSequence): boolean {
    messageSequence.writeInt(this.num);
    messageSequence.writeString(this.str);
    return true;
  }
  unmarshalling(messageSequence: rpc.MessageSequence): boolean {
    this.num = messageSequence.readInt();
    this.str = messageSequence.readString();
    hilog.info(0x0000, 'testTag', 'readInt is ' + this.num + ' readString is ' + this.str);
    return true;
  }
}

try {
  let parcelable = new MyParcelable(1, "aaa");
  let data = rpc.MessageSequence.create();
  data.writeParcelable(parcelable);
  let ret = new MyParcelable(0, "");
  data.readParcelable(ret);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```
