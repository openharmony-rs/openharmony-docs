# Faults

```TypeScript
enum Faults
```

Defines the cause of a task failure.

> **NOTE:** 
> 
> In API version 12 or earlier, only serial connection to the IP addresses associated with the specified domain
> name is supported, and the connection time for a single IP address is not controllable. If the first IP address
> returned by the DNS is blocked, a handshake timeout may occur, leading to a **TIMEOUT** error.

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent

## OTHERS

```TypeScript
OTHERS = 0xFF
```

Other fault.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## DISCONNECTED

```TypeScript
DISCONNECTED = 0x00
```

Network disconnection.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## TIMEOUT

```TypeScript
TIMEOUT = 0x10
```

Timeout.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## PROTOCOL

```TypeScript
PROTOCOL = 0x20
```

Protocol error, for example, an internal server error (500) or a data range that cannot be processed (416).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## PARAM

```TypeScript
PARAM = 0x30
```

Parameter error, for example, incorrect URL format.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Request.FileTransferAgent

## FSIO

```TypeScript
FSIO = 0x40
```

File system I/O error, for example, an error that occurs during the open, search, read, write, or close operation.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## DNS

```TypeScript
DNS = 0x50
```

DNS resolution error.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Request.FileTransferAgent

## TCP

```TypeScript
TCP = 0x60
```

TCP connection error.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Request.FileTransferAgent

## SSL

```TypeScript
SSL = 0x70
```

SSL connection error, for example, a certificate error or certificate verification failure.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Request.FileTransferAgent

## REDIRECT

```TypeScript
REDIRECT = 0x80
```

Redirection error.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Request.FileTransferAgent

## LOW_SPEED

```TypeScript
LOW_SPEED = 0x90
```

Low speed.

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent
