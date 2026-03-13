# WebSocket Error Codes

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 200 Connection Failure

**Error Message**

Websocket connect failed.

**Description**

This error code is reported if the WebSocket connection fails.

**Possible Causes**

1. The server rejects the client connection, the protocol is incorrect, the handshake fails, or the certificate verification fails.

2. No status code is returned when the client or server is disconnected.

**Solution**

Check whether the protocol is valid and whether the certificate verification is successful. If no, reconnect the client and server.

## 2302001 WebSocket URL Error

**Error Message**

Websocket url error.

**Description**

This error code is reported if the WebSocket URL is incorrect.

**Possible Causes**

The WebSocket URL is incorrect.

**Solution**

1. Check whether the WebSocket URL is empty or does not contain the correct protocol (ws:// or wss://).

2. Check whether the WebSocket URL length exceeds 2048 characters.

## 2302002 WebSocket Certificate Does Not Exist

**Error Message**

Websocket certificate file does not exist.

**Description**

The WebSocket certificate does not exist.

**Possible Causes**

The certificate path is incorrect or no certificate is configured.

**Solution**

1. Check whether the CA certificate path is valid.

2. If the **WebSocketRequestOptions.clientCert** is specified, check whether the certificate path and private key path are valid.


## 2302003 WebSocket Connection Already Exists

**Error Message**

Websocket connection already exists.

**Description**

The WebSocket connection already exists.

**Possible Causes**

The WebSocket connection has been established.

**Solution**

The WebSocket connection has been established. You do not need to call the **WebSocket.connect** API again. No further action is required.

## 2302004 Listening Failed on the Specified NIC

**Error Message**

Can't listen to the given NIC.

**Description**

This error code is reported if the WebSocketServer failed to perform listening on the specified NIC.

**Possible Causes**

The IP address in the WebSocketServer server configuration file is invalid.

**Solution**

Check whether the network connection is normal and whether the IP address is valid.

## 2302005 Listening Failed on the Specified Port

**Error Message**

Can't listen to the given Port.

**Description**

This error code is reported if the WebSocketServer failed to perform listening on the specified port.

**Possible Causes**

The port number in the WebSocketServer server configuration file is invalid.

**Solution**

Check whether the port number is valid.

## 2302998 Domain Access Denied

**Error Message**

It is not allowed to access this domain.

**Description**

This error code is reported if access to a certain domain is prohibited.

**Possible Causes**

An incorrect server domain name is configured for the atomic service.

**Solution**

Configure a correct server domain name for the atomic service. For details, see [Configuring Server Domain Names](https://developer.huawei.com/consumer/en/doc/atomic-guides/agc-help-harmonyos-server-domain).

## 2302999 Internal Error

**Error Message**

Internal error.

**Description**

This error code is reported if an internal error occurs.

**Possible Causes**

Null pointer, memory allocation error, or other errors occur.

**Solution**

Reboot the system.
