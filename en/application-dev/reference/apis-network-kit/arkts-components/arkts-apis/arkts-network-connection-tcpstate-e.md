# TcpState

Enumerates TCP states.

**Since:** 24

**System capability:** SystemCapability.Communication.NetManager.Core

## TCP_ESTABLISHED

```TypeScript
TCP_ESTABLISHED = 1
```

The connection is established, and data can be sent and received properly.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

## TCP_SYN_SENT

```TypeScript
TCP_SYN_SENT = 2
```

The client sends SYN and waits for ACK+SYN from the server (the first step of the three-way handshake).

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

## TCP_SYN_RECV

```TypeScript
TCP_SYN_RECV = 3
```

The server receives SYN and sends ACK+SYN, and waits for ACK from the client (the second step of the three-way handshake).

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

## TCP_FIN_WAIT1

```TypeScript
TCP_FIN_WAIT1 = 4
```

The active end sends FIN and waits for ACK from the peer end.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

## TCP_FIN_WAIT2

```TypeScript
TCP_FIN_WAIT2 = 5
```

The active end receives ACK of FIN and waits for ACK from the peer end.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

## TCP_TIME_WAIT

```TypeScript
TCP_TIME_WAIT = 6
```

The active end receives FIN from the peer end and replies with ACK. After two times of the maximum segment lifetime, the connection is completely released.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

## TCP_CLOSE

```TypeScript
TCP_CLOSE = 7
```

Initial/closed state, with no connection.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

## TCP_CLOSE_WAIT

```TypeScript
TCP_CLOSE_WAIT = 8
```

The passive end receives FIN and sends ACK, and waits for FIN from the peer end.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

## TCP_LAST_ACK

```TypeScript
TCP_LAST_ACK = 9
```

The passive end sends FIN and waits for ACK from the peer end.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

## TCP_LISTEN

```TypeScript
TCP_LISTEN = 10
```

The server listens and waits for the client to connect.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

## TCP_CLOSING

```TypeScript
TCP_CLOSING = 11
```

Both ends send FIN and wait for ACK from each other.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core
