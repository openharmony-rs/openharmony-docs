# WebSocket Error Codes

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=ef2b3328db1b7fa83791ef0397254c5c61474766 translatedAt=2026-09-23T01:52:52.206Z pushedAt=2026-09-24T06:00:14.181Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 200 Connection Failure

**Error Message**

Websocket connect failed.

**Description**

WebSocket connection failed.

**Possible Causes**

1. Connection establishment failure: The server may reject the client connection, a protocol issue may cause handshake failure, or the certificate verification may fail.

2. Abnormal link disconnection: No normal status code is returned when the client or server is disconnected.

3. Abnormal header processing during the handshake phase: An error occurs during header addition.

4. Internal system error.

**Solution**

1. Check whether the protocol is valid and whether the certificate verification is successful. If not, reconnect.

2. Check whether the network is abnormal, or switch networks and reconnect.

3. Check whether the added headers are correct.

4. If the problem persists, collect the complete logs and contact technical support for help.

## 2302001 WebSocket URL Error

**Error Message**

Websocket url error.

**Description**

The WebSocket URL is incorrect.

**Possible Causes**

The WebSocket URL is incorrect.

**Solution**

1. Check whether the URL is empty or does not contain the correct protocol (ws:// or wss://).

2. Check whether the URL length exceeds 2048 characters.

## 2302002 WebSocket Certificate Does Not Exist

**Error Message**

Websocket certificate file does not exist.

**Description**

The WebSocket certificate is not found.

**Possible Causes**

The certificate path is incorrect or no certificate is configured.

**Solution**

1. Check whether the CA certificate path is valid.

2. If [WebSocketRequestOptions](./js-apis-webSocket.md#websocketrequestoptions).clientCert is specified, check whether the certificate path and private key path are valid.


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

Can't listen on the given NIC.

**Description**

This error code is reported if the WebSocketServer failed to perform listening on the specified NIC.

**Possible Causes**

The IP address in the WebSocketServer server configuration file is invalid.

**Solution**

Check whether the network connection is normal and whether the IP address is valid.

## 2302005 Listening Failed on the Specified Port

**Error Message**

Can't listen on the given Port.

**Description**

This error code is reported if the WebSocketServer failed to perform listening on the specified port.

**Possible Causes**

The port number in the WebSocketServer configuration file is invalid.

**Solution**

Check whether the port number is valid.

## 2302006 WebSocketServer Connection Does Not Exist

**Error Message**

websocket connection does not exist.

**Description**

The WebSocketServer connection does not exist.

**Possible Causes**

The WebSocketServer connection to be operated (closed or sent a message) has been disconnected or does not exist.

**Solution**

Check whether the connection is still valid, and re-establish the connection before performing the operation if necessary.

## 2302007 Listening Port Already Occupied

**Error Message**

Websocket port already occupied.

**Description**

This error code is reported if the port listened by the WebSocketServer is occupied.

**Possible Causes**

The specified listening port has been occupied by another process.

**Solution**

Replace the port with an idle one.

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