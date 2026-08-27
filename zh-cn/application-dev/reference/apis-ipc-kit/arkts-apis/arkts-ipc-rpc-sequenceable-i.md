# Sequenceable

在进程间通信（IPC）期间，将类的对象写入MessageParcel并从MessageParcel中恢复它们。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [Parcelable](arkts-ipc-rpc-parcelable-i.md)

**系统能力：** SystemCapability.Communication.IPC.Core

## 导入模块

```TypeScript
import { rpc } from '@kit.IPCKit';
```

## marshalling

```TypeScript
marshalling(dataOut: MessageParcel): boolean
```

将此可序列对象封送到MessageParcel中。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [marshalling](arkts-ipc-rpc-parcelable-i.md#marshalling)(dataOut: MessageSequence)

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataOut | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | 是 | 可序列对象将被封送到的MessageParcel对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：封送成功，false：封送失败。 |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MySequenceable implements rpc.Sequenceable {
  num: number = 0;
  str: string = '';
  constructor(num: number, str: string) {
    this.num = num;
    this.str = str;
  }
  marshalling(messageParcel: rpc.MessageParcel): boolean {
    messageParcel.writeInt(this.num);
    messageParcel.writeString(this.str);
    return true;
  }
  unmarshalling(messageParcel: rpc.MessageParcel): boolean {
    this.num = messageParcel.readInt();
    this.str = messageParcel.readString();
    return true;
  }
}

try {
  let sequenceable = new MySequenceable(1, "aaa");
  let data = rpc.MessageParcel.create();
  let result = data.writeSequenceable(sequenceable);
  hilog.info(0x0000, 'testTag', 'writeSequenceable is ' + result);
  let ret = new MySequenceable(0, "");
  let result2 = data.readSequenceable(ret);
  hilog.info(0x0000, 'testTag', 'readSequenceable is ' + result2);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## unmarshalling

```TypeScript
unmarshalling(dataIn: MessageParcel): boolean
```

从MessageParcel中解封此可序列对象。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [unmarshalling](arkts-ipc-rpc-parcelable-i.md#unmarshalling)(dataIn: MessageSequence)

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataIn | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | 是 | 已将可序列对象封送到其中的MessageParcel对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：反序列化成功，false：反序列化失败。 |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MySequenceable implements rpc.Sequenceable {
  num: number = 0;
  str: string = '';
  constructor(num: number, str: string) {
    this.num = num;
    this.str = str;
  }
  marshalling(messageParcel: rpc.MessageParcel): boolean {
    messageParcel.writeInt(this.num);
    messageParcel.writeString(this.str);
    return true;
  }
  unmarshalling(messageParcel: rpc.MessageParcel): boolean {
    this.num = messageParcel.readInt();
    this.str = messageParcel.readString();
    return true;
  }
}

try {
  let sequenceable = new MySequenceable(1, "aaa");
  let data = rpc.MessageParcel.create();
  let result = data.writeSequenceable(sequenceable);
  hilog.info(0x0000, 'testTag', 'writeSequenceable is ' + result);
  let ret = new MySequenceable(0, "");
  let result2 = data.readSequenceable(ret);
  hilog.info(0x0000, 'testTag', 'readSequenceable is ' + result2);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```
