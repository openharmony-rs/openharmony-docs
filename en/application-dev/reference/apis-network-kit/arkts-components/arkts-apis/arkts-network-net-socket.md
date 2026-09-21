# @ohos.net.socket(Socket Connection)

The **socket** module implements data transfer over TCP, UDP, Web, and TLS socket connections.

> **NOTE:** 
> 
> You are advised to call the APIs of this module in the worker thread or taskpool to perform network-related
> operations. Otherwise, the UI thread may be suspended.

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [constructLocalSocketInstance](arkts-network-socket-constructlocalsocketinstance-f.md) | Creates a **LocalSocket** object. |
| [constructLocalSocketServerInstance](arkts-network-socket-constructlocalsocketserverinstance-f.md) | Creates a **LocalSocketServer** object. |
| [constructMulticastSocketInstance](arkts-network-socket-constructmulticastsocketinstance-f.md) | Creates a **MulticastSocket** object. |
| [constructTCPSocketInstance](arkts-network-socket-constructtcpsocketinstance-f.md) | Creates a **TCPSocket** object. |
| [constructTCPSocketServerInstance](arkts-network-socket-constructtcpsocketserverinstance-f.md) | Creates a **TCPSocketServer** object. |
| [constructTLSSocketInstance](arkts-network-socket-constructtlssocketinstance-f.md#constructtlssocketinstance) | Creates a **TLSSocket** object. |
| [constructTLSSocketInstance](arkts-network-socket-constructtlssocketinstance-f.md#constructtlssocketinstance-1) | Upgrades a **TCPSocket** connection to a **TLSSocket** connection. |
| [constructTLSSocketServerInstance](arkts-network-socket-constructtlssocketserverinstance-f.md) | Creates a **TLSSocketServer** object. |
| [constructUDPSocketInstance](arkts-network-socket-constructudpsocketinstance-f.md) | Creates a **UDPSocket** object. |

### Interfaces

| Name | Description |
| --- | --- |
| [ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md) | Defines base properties of the **LocalSocket** object. |
| [LocalAddress](arkts-network-socket-localaddress-i.md) | Defines the address of a local socket file. When the address is passed for binding, a socket file is created at this address. |
| [LocalConnectOptions](arkts-network-socket-localconnectoptions-i.md) | Defines local socket connection parameters. |
| [LocalSendOptions](arkts-network-socket-localsendoptions-i.md) | Defines the request parameters for the **LocalSocket** object. |
| [LocalSocket](arkts-network-socket-localsocket-i.md) | Defines a **LocalSocket** object. Before calling LocalSocket APIs, you need to call [socket.constructLocalSocketInstance](arkts-network-socket-constructlocalsocketinstance-f.md) to create a **LocalSocket** object. |
| [LocalSocketConnection](arkts-network-socket-localsocketconnection-i.md) | Defines a local socket connection, that is, the session between the local socket client and the server. Before calling LocalSocketConnection APIs, you need to obtain a **LocalSocketConnection** object. |
| [LocalSocketMessageInfo](arkts-network-socket-localsocketmessageinfo-i.md) | Defines the data received by the client over a local socket connection. |
| [LocalSocketServer](arkts-network-socket-localsocketserver-i.md) | Defines a local socket server connection. Before calling LocalSocketServer APIs, you need to call [socket.constructLocalSocketServerInstance](arkts-network-socket-constructlocalsocketserverinstance-f.md) to create a **LocalSocketServer** object. |
| [MulticastSocket](arkts-network-socket-multicastsocket-i.md) | Defines a **MulticastSocket** connection. Before calling MulticastSocket APIs, you need to call [socket.constructMulticastSocketInstance](arkts-network-socket-constructmulticastsocketinstance-f.md) to create a **MulticastSocket** object. |
| [ProxyOptions](arkts-network-socket-proxyoptions-i.md) | Defines the socket proxy information. |
| [SocketMessageInfo](arkts-network-socket-socketmessageinfo-i.md) | Defines the socket connection information. |
| [SocketRemoteInfo](arkts-network-socket-socketremoteinfo-i.md) | Defines information about the socket connection. |
| [SocketStateBase](arkts-network-socket-socketstatebase-i.md) | Defines the status of the socket connection. |
| [TCPConnectOptions](arkts-network-socket-tcpconnectoptions-i.md) | Defines TCP socket connection parameters. |
| [TCPExtraOptions](arkts-network-socket-tcpextraoptions-i.md) | Defines other properties of the **TCPSocket** object. This object is inherited from [ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md). |
| [TCPSendOptions](arkts-network-socket-tcpsendoptions-i.md) | Defines the parameters for sending data over a TCP socket connection. |
| [TCPSocket](arkts-network-socket-tcpsocket-i.md) | Defines a TCP socket connection. Before calling TCPSocket APIs, you need to call [socket.constructTCPSocketInstance](arkts-network-socket-constructtcpsocketinstance-f.md) to create a **TCPSocket** object. |
| [TCPSocketConnection](arkts-network-socket-tcpsocketconnection-i.md) | Defines a **TCPSocketConnection** object, that is, the connection between the TCPSocket client and the server. Before calling TCPSocketConnection APIs, you need to obtain a **TCPSocketConnection** object. |
| [TCPSocketServer](arkts-network-socket-tcpsocketserver-i.md) | Defines a TCP socket server connection. Before calling TCPSocketServer APIs, you need to call [socket.constructTCPSocketServerInstance](arkts-network-socket-constructtcpsocketserverinstance-f.md) to create a **TCPSocketServer** object. |
| [TLSConnectOptions](arkts-network-socket-tlsconnectoptions-i.md) | Defines TLS connection options. |
| [TLSSecureOptions](arkts-network-socket-tlssecureoptions-i.md) | TLS security options. When **cert** (local certificate) and **key** (private key) are not empty, the two-way authentication mode is enabled. If **cert** or **key** is empty, one-way authentication is enabled. |
| [TLSSocket](arkts-network-socket-tlssocket-i.md) | Defines a TLS socket connection. Before calling TLSSocket APIs, you need to call [socket.constructTLSSocketInstance](arkts-network-socket-constructtlssocketinstance-f.md) to create a **TLSSocket** object. |
| [TLSSocketConnection](arkts-network-socket-tlssocketconnection-i.md) | Defines a **TLSSocketConnection** object, that is, the connection between the TLSSocket client and the server. Before calling TLSSocketConnection APIs, you need to obtain a **TLSSocketConnection** object. |
| [TLSSocketServer](arkts-network-socket-tlssocketserver-i.md) | Defines a TLS socket server connection. Before calling TLSSocketServer APIs, you need to call [socket.constructTLSSocketServerInstance](arkts-network-socket-constructtlssocketserverinstance-f.md) to create a **TLSSocketServer** object. |
| [UDPExtraOptions](arkts-network-socket-udpextraoptions-i.md) | Defines other properties of the **UDPSocket** object. This object is inherited from [ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md). |
| [UDPSendOptions](arkts-network-socket-udpsendoptions-i.md) | Defines the parameters for sending data over a UDP socket connection. |
| [UDPSocket](arkts-network-socket-udpsocket-i.md) | Defines a UDP socket connection. Before calling UDPSocket APIs, you need to call [socket.constructUDPSocketInstance](arkts-network-socket-constructudpsocketinstance-f.md) to create a **UDPSocket** object. |

### Enums

| Name | Description |
| --- | --- |
| [Protocol](arkts-network-socket-protocol-e.md) | Enumerates TLS protocol versions. |
| [ProxyTypes](arkts-network-socket-proxytypes-e.md) | Enumerates socket proxy types. |

### Types

| Name | Description |
| --- | --- |
| [X509CertRawData](arkts-network-socket-x509certrawdata-t.md) | Defines the certificate raw data. |

### Properties

| Name | Description |
| --- | --- |
| [NetAddress](arkts-network-socket-p.md) | Define a network address. |
