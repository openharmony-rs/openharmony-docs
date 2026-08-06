# @ohos.rpc

本模块提供进程间通信能力，包括设备内的进程间通信（IPC）和设备间的进程间通信（RPC），前者基于Binder驱动，后者基于软总线驱动。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare namespace rpc--><!--Device-unnamed-declare namespace rpc-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Ashmem](arkts-ipc-rpc-ashmem-c.md) | 提供与匿名共享内存对象相关的方法，包括创建、关闭、映射和取消映射Ashmem、从Ashmem读取数据和写入数据、获取Ashmem大小、设置Ashmem保护。 共享内存只适用与本设备内跨进程通信。 - 大数据传输：传输大量数据(如图片、文件)时使用共享内存提升效率。 - 跨进程数据共享：多个进程需要共享访问同一块内存数据。 - 传输效率问题：大数据通过共享内存传输避免序列化开销，提升传输效率。 - 内存复用问题：多进程可共享访问同一内存，避免数据拷贝。 - 提升传输性能：共享内存机制大幅提升大数据传输效率。 - 减少内存占用：避免数据多次拷贝，节省内存资源。 |
| [CallingInfo](arkts-ipc-rpc-callinginfo-c.md) | IPC上下文信息，包括PID和UID、本端和对端设备ID、检查接口调用是否在同一设备上。 |
| [IPCSkeleton](arkts-ipc-rpc-ipcskeleton-c.md) | 用于获取IPC上下文信息，包括获取UID和PID、获取本端和对端设备ID、检查接口调用是否在同一设备上。 |
| [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md) | 该接口可用于查询或获取接口描述符、添加或删除死亡通知、转储对象状态到特定文件、发送消息。 |
| [MessageOption](arkts-ipc-rpc-messageoption-c.md) | 公共消息选项，使用指定的标志类型，构造指定的MessageOption对象。 |
| [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | 在RPC过程中，发送方可以使用MessageParcel提供的写方法，将待发送的数据以特定格式写入该对象。接收方可以使用MessageParcel提供的读方法从该对象中读取特定格式的数据。数据格式包括：基础类型及数组、IPC对象、 接口描述符和自定义序列化对象。 |
| [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | 在RPC或IPC过程中，发送方可以使用MessageSequence提供的写方法，将待发送的数据以特定格式写入该对象。接收方可以使用MessageSequence提供的读方法从该对象中读取特定格式的数据。数据格式包括：基础类型及数 组、IPC对象、接口描述符和自定义序列化对象。读取顺序必须与写入顺序一致，否则会导致数据解析错误。 |
| [RemoteObject](arkts-ipc-rpc-remoteobject-c.md) | 实现远程对象。服务提供者必须继承此类。 |
| [RemoteProxy](arkts-ipc-rpc-remoteproxy-c.md) | 实现IRemoteObject代理对象。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DeathRecipient](arkts-ipc-rpc-deathrecipient-i.md) | 用于订阅远端对象的死亡通知。当被订阅该通知的远端对象死亡时，本端可收到消息，调用[onRemoteDied]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_接口。远端对象死亡可以为远端对象所在进程 死亡，远端对象所在设备关机或重启，当远端对象与本端对象属于不同设备时，也可为远端对象离开组网时。 |
| [IRemoteBroker](arkts-ipc-rpc-iremotebroker-i.md) | 远端对象的代理持有者。用于获取代理对象。 |
| [Parcelable](arkts-ipc-rpc-parcelable-i.md) | 在进程间通信（IPC）期间，将类的对象写入MessageSequence并从MessageSequence中恢复它们。 |
| [RequestResult](arkts-ipc-rpc-requestresult-i.md) | 发送请求的响应结果。 |
| [SendRequestResult](arkts-ipc-rpc-sendrequestresult-i.md) | 发送请求的响应结果。 |
| [Sequenceable](arkts-ipc-rpc-sequenceable-i.md) | 在进程间通信（IPC）期间，将类的对象写入MessageParcel并从MessageParcel中恢复它们。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ErrorCode](arkts-ipc-rpc-errorcode-e.md) | 从API version 9起，IPC支持异常返回功能。错误码对应数值及含义如下，详细说明请参见\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| [TypeCode](arkts-ipc-rpc-typecode-e.md) | 从API version 12起，IPC新增[writeArrayBuffer]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_和 [readArrayBuffer]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_方法传递ArrayBuffer数据，传递数据时通过具体类型值来分辨业务是以哪一种TypedArray去进行数据 的读写。类型码对应数值及含义如下。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnRemoteDiedFunc](arkts-ipc-rpc-onremotediedfunc-t.md) | Called to perform subsequent operations when a death notification of the remote object is received. |

