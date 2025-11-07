# OH_IPC_MessageOption
<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @maxiaorong-->
<!--Adviser: @zhang_yixin13-->

## Overview

Defines an IPC message.

**Since**: 12

**Related module**: [OHIPCRemoteObject](capi-ohipcremoteobject.md)

**Header file**: [ipc_cremote_object.h](capi-ipc-cremote-object-h.md)

## Summary

### Member Variables

| Name| Description|
| ---- | ---- |
| OH_IPC_RequestMode mode | Message request mode.|
| uint32_t timeout | Parameter reserved for RPC. It is invalid for IPC.|
| void* reserved | Reserved parameter, which must be NULL.|
