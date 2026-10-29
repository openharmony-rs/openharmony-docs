# @ohos.FusionConnectivity.PartnerAgentExtensionContext (Context for Device Status Notifications)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=ca9cb26047d0b3f89295b759af81b72a379c30be translatedAt=2026-10-09T13:18:09.790Z pushedAt=2026-10-10T07:12:23.931Z -->

The **PartnerAgentExtensionContext** module provides the context for discovering and managing third-party peripherals. It offers capabilities such as peripheral discovery, pairing and connection, and status notification. This module is applicable to scenarios where your app needs to connect to and manage third-party peripherals and obtain their status information. It helps you manage the connection lifecycle of peripherals in a unified manner.

> **NOTE**
>
> - The APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs of this module can be used only in the Stage model.

## Modules to Import

```ts
import { PartnerAgentExtensionContext } from '@kit.ConnectivityKit';
```

## PartnerAgentExtensionContext

**PartnerAgentExtensionContext** provides the context environment for third-party peripheral discovery and connection management. It is inherited from the **ExtensionContext** class and provides the context related to **PartnerAgentExtensionAbility**. This context provides the runtime environment and capability entry for third-party peripheral discovery and connection management. For details about the discovery policies, connection process, and API usage, see the related API description.

**System capability**: SystemCapability.Communication.FusionConnectivity.Core

**Model restriction**: This API can be used only in the stage model.
