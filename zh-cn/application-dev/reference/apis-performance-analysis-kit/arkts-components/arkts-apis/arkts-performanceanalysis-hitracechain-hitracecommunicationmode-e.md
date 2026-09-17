# HiTraceCommunicationMode

跟踪通信类型枚举。用于标识通信发生的层级，例如THREAD用于标记同一应用内线程间通信，PROCESS用于标记同一设备内进程间通信，DEVICE用于标记跨设备的分布式通信。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## DEFAULT

```TypeScript
DEFAULT = 0
```

缺省通信类型。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## THREAD

```TypeScript
THREAD = 1
```

线程间通信。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## PROCESS

```TypeScript
PROCESS = 2
```

进程间通信。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## DEVICE

```TypeScript
DEVICE = 3
```

设备间通信。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace
