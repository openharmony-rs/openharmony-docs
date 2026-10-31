# Glossary

<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=e82880fc1b3fb82c03ab5c9c350aff1a7e98d202 translatedAt=2026-07-13T10:10:12.203Z pushedAt=2026-07-13T10:17:33.272Z -->

## D

### DeathRecipient

A callback mechanism for subscribing to the lifecycle status of a remote Stub object. After the Proxy registers a callback, the callback is automatically invoked when the process hosting the remote Stub exits or when the SoftBus connection used by RPC is disconnected. This mechanism allows the Proxy to release local proxy objects and related resources.

## I

### Inter Process Communication (IPC)

An intra-device inter-process communication mechanism implemented on top of the Binder driver. IPC follows a client-server model. The client obtains a Proxy for the server, sends requests through the Proxy, and the server-side Stub processes the requests and returns the results. IPC is typically used for background services to provide cross-process API invocation and data transfer within a device.

## R

### Remote Procedure Call (RPC)

A cross-device inter-process communication mechanism implemented on top of SoftBus. RPC uses the same client-server architecture and Proxy-Stub model as IPC. It is typically used for distributed scenarios that require remote API invocation and data transfer across devices. Unlike IPC, which communicates only within a device through the Binder driver, RPC communicates across devices through SoftBus.

## S

### Stub

In the IPC/RPC communication model, the server-side object is called a Stub, and the client-side object is called a Proxy. The Stub receives requests from the Proxy, processes them, and returns the results. The Stub implements the request handling logic, while the Proxy provides the corresponding request invocation methods.