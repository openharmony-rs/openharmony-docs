# @ohos.net.vpn (VPN Management)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=66333f405b8ba85b102d9221d24e54901f6cfbf8 translatedAt=2026-06-25T01:51:23.943Z pushedAt=2026-06-26T03:00:41.300Z -->

This module is the built-in VPN function provided by the OS. It allows users to set up VPN connections through the network settings of the OS. Generally, this module provides only limited functions and is subject to strict restrictions.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```js
import { vpn } from '@kit.NetworkKit';
```

## LinkAddress

type LinkAddress = connection.LinkAddress

Defines the network link address information.

**System capability**: SystemCapability.Communication.NetManager.Core

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| [connection.LinkAddress](./js-apis-net-connection.md#linkaddress) | Network link address information.|

## RouteInfo

type RouteInfo = connection.RouteInfo

Defines the network route information.

**System capability**: SystemCapability.Communication.NetManager.Core

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| [connection.RouteInfo](./js-apis-net-connection.md#routeinfo) | Network route information.|


## AbilityContext

type AbilityContext = _AbilityContext

**System capability**: SystemCapability.Ability.AbilityRuntime.Core


| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| [_AbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Context of the target **UIAbility**. It is inherited from [Context](../apis-ability-kit/js-apis-inner-application-context.md) and provides the **UIAbility** configuration and methods for operating **UIAbility** and **ServiceExtensionAbility**.|