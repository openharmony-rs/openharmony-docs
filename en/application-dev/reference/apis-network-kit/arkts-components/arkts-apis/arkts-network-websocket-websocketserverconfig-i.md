# WebSocketServerConfig

Defines the WebSocketServer configuration.

**Since:** 19

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { webSocket } from '@kit.NetworkKit';
```

## maxConcurrentClientsNumber

```TypeScript
maxConcurrentClientsNumber: number
```

Maximum number of concurrent clients. When the number of concurrent clients reaches the maximum, the server rejects new connections. The default value is **10**.

**Type:** number

**Since:** 19

**System capability:** SystemCapability.Communication.NetStack

## maxConnectionsForOneClient

```TypeScript
maxConnectionsForOneClient: number
```

Maximum number of connections for each client. The default value is **10**.

**Type:** number

**Since:** 19

**System capability:** SystemCapability.Communication.NetStack

## protocol

```TypeScript
protocol?: string
```

Custom protocol.

**Type:** string

**Since:** 19

**System capability:** SystemCapability.Communication.NetStack

## serverCert

```TypeScript
serverCert?: ServerCert
```

Certificate information, which includes the paths of the WebSocketServer certificate file and private key file.

**Type:** [ServerCert](arkts-network-websocket-servercert-i.md)

**Since:** 19

**System capability:** SystemCapability.Communication.NetStack

## serverIP

```TypeScript
serverIP?: string
```

IP address of the WebSocketServer. The default value is **0.0.0.0**.

**Type:** string

**Since:** 19

**System capability:** SystemCapability.Communication.NetStack

## serverPort

```TypeScript
serverPort: number
```

Port of the WebSocketServer.

**Type:** number

**Since:** 19

**System capability:** SystemCapability.Communication.NetStack
