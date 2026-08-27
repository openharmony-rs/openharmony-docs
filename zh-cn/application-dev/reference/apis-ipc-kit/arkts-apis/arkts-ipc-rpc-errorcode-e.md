# ErrorCode

从API version 9起，IPC支持异常返回功能。错误码对应数值及含义如下，详细说明请参见[ohos.rpc错误码](../errorcode-rpc.md)。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

## CHECK_PARAM_ERROR

```TypeScript
CHECK_PARAM_ERROR = 401
```

检查参数失败。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

## OS_MMAP_ERROR

```TypeScript
OS_MMAP_ERROR = 1900001
```

执行系统调用mmap失败。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

## OS_IOCTL_ERROR

```TypeScript
OS_IOCTL_ERROR = 1900002
```

在共享内存文件描述符上执行系统调用ioctl失败。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

## WRITE_TO_ASHMEM_ERROR

```TypeScript
WRITE_TO_ASHMEM_ERROR = 1900003
```

向共享内存写数据失败。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

## READ_FROM_ASHMEM_ERROR

```TypeScript
READ_FROM_ASHMEM_ERROR = 1900004
```

从共享内存读数据失败。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

## ONLY_PROXY_OBJECT_PERMITTED_ERROR

```TypeScript
ONLY_PROXY_OBJECT_PERMITTED_ERROR = 1900005
```

只有proxy对象允许该操作。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

## ONLY_REMOTE_OBJECT_PERMITTED_ERROR

```TypeScript
ONLY_REMOTE_OBJECT_PERMITTED_ERROR = 1900006
```

只有remote对象允许该操作。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

## COMMUNICATION_ERROR

```TypeScript
COMMUNICATION_ERROR = 1900007
```

和远端对象进行进程间通信失败。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

## PROXY_OR_REMOTE_OBJECT_INVALID_ERROR

```TypeScript
PROXY_OR_REMOTE_OBJECT_INVALID_ERROR = 1900008
```

非法的代理对象或者远端对象。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

## WRITE_DATA_TO_MESSAGE_SEQUENCE_ERROR

```TypeScript
WRITE_DATA_TO_MESSAGE_SEQUENCE_ERROR = 1900009
```

向MessageSequence写数据失败。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

## READ_DATA_FROM_MESSAGE_SEQUENCE_ERROR

```TypeScript
READ_DATA_FROM_MESSAGE_SEQUENCE_ERROR = 1900010
```

读取MessageSequence数据失败。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

## PARCEL_MEMORY_ALLOC_ERROR

```TypeScript
PARCEL_MEMORY_ALLOC_ERROR = 1900011
```

序列化过程中内存分配失败。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

## CALL_JS_METHOD_ERROR

```TypeScript
CALL_JS_METHOD_ERROR = 1900012
```

执行JS回调方法失败。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

## OS_DUP_ERROR

```TypeScript
OS_DUP_ERROR = 1900013
```

执行系统调用dup失败。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core
