# Parcelable

在进程间通信（IPC）期间，将类的对象写入MessageSequence并从MessageSequence中恢复它们。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

## 导入模块

```TypeScript
import { rpc } from '@kit.IPCKit';
```

## marshalling

```TypeScript
marshalling(dataOut: MessageSequence): boolean
```

将此可序列对象封送到MessageSequence中。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataOut | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | 是 | 可序列对象将被封送到的MessageSequence对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：封送成功，false：封送失败。 |

**示例**

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

从MessageSequence中解封此可序列对象。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | 是 | 已将可序列对象封送到其中的MessageSequence对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：反序列化成功，false：反序列化失败。 |

**示例**

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
