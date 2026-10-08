# Socket Error Codes

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=93c44f09729518908d6cf3484da6e70f75e17aad translatedAt=2026-09-23T01:51:02.445Z pushedAt=2026-09-24T06:00:14.183Z -->

> **NOTE**
>
> The following describes only the error codes specific to this module. For details about the universal error codes, see [Universal Error Codes](../errorcode-universal.md).
> Socket error code mapping: 2301000 + [Kernel Error Code](./errorcode-kernel.md).
> Socket server error code mapping: 2303100 + [Kernel Error Code](./errorcode-kernel.md).
>
> **Error code description for connection disconnection scenarios**
> - Server actively disconnects: When the peer closes normally, both `TCPSocket` and `TLSSocket` trigger the close event without an error code. When the peer disconnects abnormally (connection reset), the `send()` or `message`/`error` event of `TCPSocket` returns 2301104, and `TLSSocket` returns 2303505 (TLS system call error).
> - Client actively disconnects: After the local `close()`, if `TCPSocket` continues to call `send()`, `getState()`, and other APIs, 2301009 is returned; continuing to call `send()` returns 2301032 or 2301108.
> - Disconnection due to cellular network: When the underlying cellular network is disconnected during `TCPSocket.connect()`/`send()`, 2301100, 2301101, or 2301113 is returned; a timeout in a weak network returns 2301110.
> - Disconnection due to internal application reasons: After the local `close()` of `TCPSocket`, misoperations return 2301009, 2301032, or 2301108; calling `TCPSocketServer.send()` and other APIs on a socket for which no connection is established returns 2303207.

## 2301001 Operation Not Allowed

**Error Message**

Operation not permitted.

**Description**

This error code is reported if an operation is not allowed.

**Possible Causes**

The operation is illegal.

**Solution**

Check the operation procedure.

## 2301002 File Not Exist

**Error Message**

No such file or directory.

**Description**

This error code is reported if the requested file does not exist.

**Possible Causes**

The requested file does not exist.

**Solution**

Check the file name or file path.

## 2301003 Process Not Exist

**Error Message**

No such process.

**Description**

This error code is reported if a process does not exist.

**Possible Causes**

This error code is reported if a process does not exist.

**Solution**

Check the process information.

## 2301004 System Call Interrupted

**Error Message**

Interrupted system call.

**Description**

This error code is reported if the system call is interrupted.

**Possible Causes**

The system call is interrupted.

**Solution**

Rectify system call errors.

**Description of TCP/UDP error codes:**
> Mapping format of other TCP/UDP Socket error codes: 2301000 + Linux kernel error code (errno). For details, see Linux kernel error codes.

## 2300002 System Internal Error

**Error Message**

System internal error.

**Description**

This error code is reported if a system internal error occurs.

**Possible Causes**

1. The memory is abnormal.

2. A null pointer is present.

**Solution**

1. Check whether the memory space is sufficient. If not, clear the memory and try again.

2. Check whether the system is normal. If not, try again later or restart the device.

## 2301206 Failed to Connect to the Proxy Server via SOCKS5

**Error Message**

Socks5 failed to connect to the proxy server.

**Description**

This error code is reported if a SOCKS5 client fails to connect to the proxy server.

**Possible Causes**

The proxy server address is incorrect.

**Solution**

Check whether the proxy server address is correct.

## 2301207 Invalid User Name or Password for SOCKS5 Authentication

**Error Message**

Socks5 username or password is invalid.

**Description**

This error code is reported if the user name or password is invalid when the SOCKS5 client uses the password authentication mode.

**Possible Causes**

The user name or password is incorrect.

**Solution**

Check whether the user name and password are correct.

## 2301208 Failed to Connect to the Remote Server via SOCKS5

**Error Message**

Socks5 failed to connect to the remote server.

**Description**

This error code is reported if a SOCKS5 proxy fails to connect to the remote server.

**Possible Causes**

The network of the remote server is faulty.

**Solution**

Check the network status of the remote server.

## 2301209 Authentication Mode Negotiation Failed for SOCKS5

**Error Message**

Socks5 failed to negotiate the authentication method.

**Description**

This error code is reported if a SOCKS5 client fails to negotiate the authentication mode with the proxy server.

**Possible Causes**

The proxy server does not support the authentication mode provided by the SOCKS5 client.

**Solution**

Check whether the proxy server supports the authentication mode provided by the SOCKS5 client.

## 2301210 Failed to Send Messages via SOCKS5

**Error Message**

Socks5 failed to send the message.

**Description**

This error code is reported if a SOCKS5 client fails to send messages due to a system call error.

**Possible Causes**

This problem is usually caused by memory overflows and invalid parameters. Check the log for Linux kernel errors.

**Solution**

Create a socket and initiate a connection again.

## 2301211 Failed to Receive Messages via SOCKS5

**Error Message**

Socks5 failed to receive the message.

**Description**

This error code is reported if a SOCKS5 client fails to receive messages due to a system call error.

**Possible Causes**

This problem is usually caused by memory overflows and invalid parameters. Check the log for Linux kernel errors.

**Solution**

Create a socket and initiate a connection again.

## 2301212 Failed to Serialize Messages for SOCKS5

**Error Message**

Socks5 serialization error.

**Description**

This error code is reported if message fails to be serialized for a SOCKS5 client.

**Possible Causes**

The user name or password is too long, or the address and protocol type of the proxy server and the remote server do not match.

**Solution**

Check whether the user name and password exceed the length limit and whether the addresses and protocol types of the proxy server and remote server match.

## 2301213 Failed to Deserialize Messages for SOCKS5

**Error Message**

Socks5 deserialization error.

**Description**

This error code is reported if message fails to be deserialized for a SOCKS5 client.

**Possible Causes**

The length of the response packets sent by the server does not comply with the protocol.

**Solution**

Check the response data packets of the server.

## 2303104 System Call Interrupted

**Error Message**

Interrupted system call.

**Description**

This error code is reported if the system call is interrupted.

**Possible Causes**

Calling the **connect** function may result in a long blocking time. In such a case, the system generates an interrupt signal and returns an **EINTR** error.

**Solution**

Call the **connect** function to try network connection again.

## 2303109 Error File Number

**Error Message**

Bad file number.

**Description**

This error code is reported if an operation is performed on a locally closed socket.

**Possible Causes**

The socket FD may be closed.

**Solution**

Check whether the socket is closed unexpectedly.

## 2301009 Bad File Descriptor

**Error Message**

Bad file descriptor.

**Description**

The file descriptor is invalid or has been closed.

**Possible Causes**

1. The socket has been closed or destroyed.

2. The socket was not created correctly.

3. An operation was performed on a closed socket.

4. The socket fd was closed unexpectedly. The log prompt is `poll to send failed, socket is .*, errno is 9` or `fcntl F_GETFL error, errno is .*`, where `.*` is a wildcard.

**Solution**

1. Check whether the socket is closed unexpectedly.

2. Ensure that the socket has been correctly created and is in a valid state before calling other methods.

3. If the socket has been closed, recreate the socket instance.

## 2301013 Insufficient Permissions

**Error Message**

Insufficient permissions.

**Description**

Insufficient permissions. The operation is denied.

**Possible Causes**

1. The application does not have the necessary network permission configuration (such as **ohos.permission.INTERNET**).

2. System permission restrictions, such as requiring special permissions to access specific ports.

**Solution**

1. Check whether the necessary network permissions (such as **ohos.permission.INTERNET**) are configured in **module.json5**.

2. Check whether the operation meets the permission requirements. You can locate this error using the log keyword "Permission denied".

## 2301032 Sending Data After the Connection Is Disconnected

**Error Message**

Broken pipe.

**Description**

Data is sent to a disconnected connection, and the peer (server or local) has closed the connection.

**Possible Causes**

1. After the server actively closes the connection, the local end still calls send to send data (errno is 32, EPIPE).

2. After the local end actively closes the connection, it still calls send to send data.

**Solution**

1. Determine the disconnection timing: if the server closes first, the server actively disconnects; if the local end closes first, the client actively disconnects.

2. Stop sending, re-establish the connection, and then send data.

## 2301100 Network Closed

**Error Message**

Network is down.

**Description**

The network is closed, and the connection is disconnected.

**Possible Causes**

1. The cellular network is disconnected, there is no network signal, or airplane mode is enabled (errno is 100, ENETDOWN).

2. The network service is not started or has stopped.

**Solution**

1. Determine that the disconnection is caused by the cellular network or the network, not by an internal application issue.

2. Check the network connection status, restore the network, and then re-establish the connection.

## 2301101 Network Unreachable

**Error Message**

Network is unreachable.

**Description**

The network is unreachable, and the connection is disconnected.

**Possible Causes**

1. The cellular data network is unavailable or not enabled (errno is 101, ENETUNREACH).

2. The network route is abnormal or the gateway is unreachable.

**Solution**

1. Determine that the disconnection is caused by the cellular/network issue.

2. Check the network connection status, and re-establish the connection after the network is restored.

## 2301104 Connection Reset by Peer

**Error Message**

Connection reset by peer.

**Description**

Connection reset by peer, which usually indicates that the server actively disconnects the connection.

**Possible Causes**

1. The server actively disconnects the connection and sends an RST (errno 104, ECONNRESET).

2. The server process exits abnormally, or the connection is reclaimed by the server due to timeout.

**Solution**

1. Determine that the server actively disconnects the connection.

2. Check the running status of the server and re-establish the connection.

## 2301108 Sending Data After the Connection Is Closed

**Error Message**

Cannot send after transport endpoint shutdown.

**Description**

Sending data after the local connection is closed.

**Possible Causes**

After the local end actively calls close or shutdown, send is still called (errno is 108, ESHUTDOWN).

**Solution**

1. Determine that this is a misoperation after the client actively disconnects.

2. Check the code flow to ensure that no data is sent after the connection is closed.

## 2301110 Connection Timed Out

**Error Message**

Connection timed out.

**Description**

The connection timed out, usually caused by a weak network or cellular network issue.

**Possible Causes**

1. The weak network or poor cellular network signal prevents data from being delivered within the timeout period (errno is 110, ETIMEDOUT).

2. The connection is reclaimed by a network device after a long period without data interaction.

**Solution**

1. Determine that the disconnection is caused by a network issue (cellular/weak network).

2. Check the network quality, and re-establish the connection after the network is restored.

## 2301113 Host Unreachable

**Error Message**

No route to host.

**Description**

The target host is unreachable.

**Possible Causes**

1. The cellular network cannot route to the target host (errno is 113, EHOSTUNREACH).

2. The target server is offline or its IP address has changed.

**Solution**

1. Determine that the disconnection is caused by a network issue (cellular/router).

2. Check the reachability of the target host and the network status.

## 2301115 Connection in progress or connection failed

**Error Message**

Operation now in progress.

**Description**

A compatibility error code returned by the framework when a TCP asynchronous connection is in progress, or when the connection times out or fails.

**Possible Causes**

1. A TCP asynchronous connection is in progress (errno is 115, EINPROGRESS), and the final connection result has not been returned.

2. When **TCPSocket.connect** times out or fails, the framework uniformly returns EINPROGRESS (compatibility handling).

3. This error code may also be returned when **LocalSocket.connect** times out or fails.

**Solution**

1. If the connection is still in progress, wait for the **connect** callback or the **'connect'** event before performing subsequent operations.

2. If the connection has timed out, check the network connection status and the peer service status, and re-establish the connection.

## 2301011 Operation Would Block

**Error Message**

Operation would block.

**Description**

The operation may block.

**Possible Causes**

1. A blocking operation is executed on a non-blocking socket (errno 11, EAGAIN).

2. The socket send buffer is full, or the current resource is temporarily unavailable.

**Solution**

1. Wait until the socket is writable and try again.

2. Check the socket status and resource usage.

## 2301022 Invalid argument

**Error Message**

Invalid argument.

**Description**

Invalid argument.

**Possible Causes**

1. The passed parameter is invalid (errno is 22, EINVAL).

2. The passed IP address, port, or socket option value is incorrect.

**Solution**

1. Check whether the value and format of the passed parameter are correct.

2. Reset the parameter by referring to the API parameter description.

## 2301088 Socket operation on non-socket

**Error Message**

Not a socket.

**Description**

A socket operation was executed on a non-socket file descriptor.

**Possible Causes**

1. The socket was not created correctly or has been destroyed (errno 88, ENOTSOCK).

2. An operation was executed on a closed socket.

**Solution**

1. Check whether the socket is created correctly and not closed.

2. Re-create the socket and then perform the operation.

## 2301098 Network address already in use

**Error Message**

Address already in use.

**Description**

Network address already in use.

**Possible Causes**

1. The bound local address is already occupied by another socket (errno is 98, EADDRINUSE).

2. The port has not been released and is still in the **TIME_WAIT** state.

**Solution**

1. Change the bound address or port.

2. Wait for the port to be released or close the connection that occupies the port.

## 2301099 Cannot Allocate Requested Address

**Error Message**

Cannot assign requested address.

**Description**

Cannot allocate requested address.

**Possible Causes**

1. The bound IP address does not belong to the local host (errno is 99, EADDRNOTAVAIL).

2. The specified local address is invalid or unavailable.

**Solution**

1. Check whether the bound IP address is a local host address.

2. Replace it with an available local address.

## 2301111 Connection Refused

**Error Message**

Connection refused.

**Description**

Connection refused.

**Possible Causes**

1. No process is listening on the target address (errno is 111, ECONNREFUSED).

2. The target server is not started, or the firewall rejects the connection request.

**Solution**

1. Confirm that the target server is started and listening on the corresponding port.

2. Check the network firewall or security policy configuration.

## 2303111 Requested Resource Temporarily Unavailable

**Error Message**

Resource temporarily unavailable. Try again.

**Description**

This error code is reported if the requested system resource is temporarily unavailable.

**Possible Causes**

The system resources are in use.

**Solution**

Try again later.

## 2303188 Socket Operations on Non-Sockets

**Error Message**

Socket operation on non-socket.

**Description**

This error code is reported if a socket descriptor is not specified for the **socket** parameter.

**Possible Causes**

A socket descriptor is not specified for the **socket** parameter.

**Solution**

Check whether the descriptor is correctly obtained.

## 2303191 Incorrect Socket Protocol Type

**Error Message**

Incorrect socket protocol type.

**Description**

This error code is reported if the type of the specified socket protocol is incorrect.

**Possible Causes**

The socket function is called with an unsupported socket protocol type. For example, the protocol type cannot be set to **SOCK_STREAM** socket for the Internet UDP protocol.

**Solution**

Check whether the socket protocol type is correct.

## 2303198 Network Address Already In Use

**Error Message**

Address already in use.

**Description**

This error code is reported if a network address has been used.

**Possible Causes**

The probable cause can be any of the following: The application attempts to bind a socket to an IP address/port that has been used for an existing socket. The socket is not properly closed. The socket is still being closed.

**Solution**

Try another network address.

## 2303199 Failed to Assign the Requested Address

**Error Message**

Cannot assign requested address.

**Description**

This error code is reported if the requested address is invalid in its context.

**Possible Causes**

The remote address or port is invalid for the remote server.

**Solution**

Check whether the address or port is correct.

## 2303200 Network Disabled

**Error Message**

Network is down.

**Description**

This error code is reported if the network is disabled.

**Possible Causes**

The network service is not started or has been stopped.

**Solution**

Check the network connection.

## 2303207 Socket Is Not Connected

**Error Message**

Socket is not connected.

**Description**

An operation that requires a connection is executed on a socket for which no connection has been established.

**Possible Causes**

1. An operation such as sending is executed before the connection is established (errno is 107, ENOTCONN).

2. The connection has been disconnected, but an operation is still executed on the socket.

**Solution**

1. Establish the connection first, and then execute the related operation.

2. Check the connection status and re-establish the connection if necessary.

## 2303210 Connection Timeout

**Error Message**

Connection timed out.

**Description**

This error code is reported if the connection to the remote server cannot be set up for a long time.

**Possible Causes**

It is probable that a server breakdown has occurred.

**Solution**

If the issue cannot be resolved locally, verify whether the remote server has encountered a fault.

## 2303501 Null SSL

**Error Message**

SSL is null.

**Description**

The SSL object is null.

**Possible Causes**

1. The [TLSSocket.connect](./js-apis-socket.md#connect9) method was not called.

2. The [TLSSocket.connect](./js-apis-socket.md#connect9) method failed to execute.

3. The SSL connection was not established successfully.

4. The TLSSocket was not bound correctly (the **bind** method was not called). The log prompt is "tlsSocket is null".

**Solution**

1. Ensure that the [TLSSocket.connect](./js-apis-socket.md#connect9) method is called successfully before calling other methods.

2. Check the execution result of the **connect** method to ensure that the connection has been established successfully.

3. If **connect** fails, locate the cause of the failure and try to connect again.

## 2303502 TLS Read Error

**Error Message**

An error occurred when reading data on the TLS socket.

**Description**

An error occurs when reading data from the TLS socket.

**Possible Causes**

The underlying socket is blocked.

**Solution**

Perform data receiving again.

## 2303503 TLS Write Error

**Error Message**

An error occurred when writing data on the TLS socket.

**Description**

An error occurs when writing data to the TLS socket.

**Possible Causes**

When the sender buffer is full, the underlying socket send operation returns the **EWOULDBLOCK** error, which means that the server has not read the message sent from the client.

**Solution**

Check the server status, and rectify the fault.

## 2303504 x509 Failed to Look Up the x509 Certificate

**Error Message**

An error occurred when verifying the X.509 certificate.

**Description**

An error occurred when verifying the x509 certificate.

**Possible Causes**

The local certificate does not match the server certificate.

**Solution**

Check whether the local CA root certificate matches the server certificate.

## 2303505 TLS System Call Error

**Error Message**

An error occurred in the TLS system call.

**Description**

An unrecoverable fatal I/O error occurred in the TLS system call.

**Possible Causes**

1. A network issue caused the communication failure.

2. The underlying socket is abnormal.

3. An error occurred during the TLS handshake.

4. The socket was closed during a TLS operation. The log prompt is `poll to recv failed, socket is .*, errno is .*` or `recv fail, socket:.*, errno:.*`, where `.*` is a wildcard. Common **errno** values for reference: **errno=9** (**EBADF**, invalid file descriptor), **errno=104** (**ECONNRESET**, connection reset), **errno=110** (**ETIMEDOUT**, connection timed out), **errno=111** (**ECONNREFUSED**, connection refused).

**Solution**

1. Refer to the general kernel error code **errno** in the log for detailed information.

2. Check the network connection status.

3. Try to re-establish the TLS connection.

## 2303506 Failed to Close the TLS Connection

**Error Message**

Failed to close the TLS connection.

**Description**

Failed to close the TLS connection.

**Possible Causes**

The TLS/SSL connection to be closed has been disabled.

**Solution**

Initiate a new TLS/SSL connection.

## 2303601 Socket File Descriptor Is Invalid

**Error Message**

Invalid socket FD.

**Description**

The socket file descriptor is invalid.

**Possible Causes**

1. The socket is not created correctly or has been closed.

2. An operation is executed on a destroyed socket.

**Solution**

1. Check whether the socket is valid.

2. Re-create the socket and then execute the operation.

## 2303602 Socket is not connected

**Error Message**

Socket is not connected.

**Description**

The socket is not connected.

**Possible Causes**

1. An operation that requires a connection is executed before the connection is established.

2. The operation continues after the connection is closed.

**Solution**

1. Establish the connection before executing the operation.

2. Check the connection status and initiate the connection again.
