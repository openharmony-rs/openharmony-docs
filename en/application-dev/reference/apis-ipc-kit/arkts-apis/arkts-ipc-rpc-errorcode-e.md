# ErrorCode

The APIs of this module return exceptions since API version 9. The following table lists the error codes.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

## CHECK_PARAM_ERROR

```TypeScript
CHECK_PARAM_ERROR = 401
```

Parameter check failed.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

## OS_MMAP_ERROR

```TypeScript
OS_MMAP_ERROR = 1900001
```

Failed to call mmap.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

## OS_IOCTL_ERROR

```TypeScript
OS_IOCTL_ERROR = 1900002
```

Failed to call **ioctl** with the shared memory file descriptor.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

## WRITE_TO_ASHMEM_ERROR

```TypeScript
WRITE_TO_ASHMEM_ERROR = 1900003
```

Failed to write data to the shared memory.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

## READ_FROM_ASHMEM_ERROR

```TypeScript
READ_FROM_ASHMEM_ERROR = 1900004
```

Failed to read data from the shared memory.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

## ONLY_PROXY_OBJECT_PERMITTED_ERROR

```TypeScript
ONLY_PROXY_OBJECT_PERMITTED_ERROR = 1900005
```

This operation is allowed only on the proxy object.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

## ONLY_REMOTE_OBJECT_PERMITTED_ERROR

```TypeScript
ONLY_REMOTE_OBJECT_PERMITTED_ERROR = 1900006
```

This operation is allowed only on the remote object.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

## COMMUNICATION_ERROR

```TypeScript
COMMUNICATION_ERROR = 1900007
```

Failed to communicate with the remote object over IPC.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

## PROXY_OR_REMOTE_OBJECT_INVALID_ERROR

```TypeScript
PROXY_OR_REMOTE_OBJECT_INVALID_ERROR = 1900008
```

Invalid proxy or remote object.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

## WRITE_DATA_TO_MESSAGE_SEQUENCE_ERROR

```TypeScript
WRITE_DATA_TO_MESSAGE_SEQUENCE_ERROR = 1900009
```

Failed to write data to MessageSequence.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

## READ_DATA_FROM_MESSAGE_SEQUENCE_ERROR

```TypeScript
READ_DATA_FROM_MESSAGE_SEQUENCE_ERROR = 1900010
```

Failed to read data from MessageSequence.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

## PARCEL_MEMORY_ALLOC_ERROR

```TypeScript
PARCEL_MEMORY_ALLOC_ERROR = 1900011
```

Failed to allocate memory during serialization.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

## CALL_JS_METHOD_ERROR

```TypeScript
CALL_JS_METHOD_ERROR = 1900012
```

Failed to invoke the JS callback.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

## OS_DUP_ERROR

```TypeScript
OS_DUP_ERROR = 1900013
```

Failed to call dup.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core
