# Socket Error Codes

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=66333f405b8ba85b102d9221d24e54901f6cfbf8 translatedAt=2026-06-25T01:50:06.309Z pushedAt=2026-06-26T03:00:41.284Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).
> Socket error code mapping: 2301000 + [Kernel Error Codes](./errorcode-kernel.md).
> Socket error code mapping: 2303100 + [Kernel Error Codes](./errorcode-kernel.md).

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

Not a socket.

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

Address not available.

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

The SSL/TLS connection object is null. Invalid parameter.

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

This error code is reported if an error occurs while reading data on the TLS socket.

**Possible Causes**

The underlying socket is blocked.

**Solution**

Perform data receiving again.

## 2303503 TLS Write Error

**Error Message**

An error occurred when writing data on the TLS socket.

**Description**

This error code is reported if an error occurs while writing data on the TLS socket.

**Possible Causes**

When the send buffer is full, the underlying socket sends an **EWOUDLBLOCK** error, which means that the server does not read the data sent from the client.

**Solution**

Check the server status, and rectify the fault.

## 2303504 x509 Failed to Look Up the x509 Certificate

**Error Message**

An error occurred when verifying the x509 certificate.

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

## 2303506 Failed to Close TLS Connections

**Error Message**

Failed to close the TLS connection.

**Description**

This error code is reported if the TLS/SSL connection to be closed has been disabled.

**Possible Causes**

The TLS/SSL connection to be closed has been disabled.

**Solution**

Initiate a new TLS/SSL connection.