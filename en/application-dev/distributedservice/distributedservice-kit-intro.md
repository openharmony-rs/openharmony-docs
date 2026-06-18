# About This Kit

<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedHardware-->
<!--Owner: @hwzhangchuang-->
<!--Designer: @hwzhangchuang-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=a1815a6960f035b2f960cbb3747e78fb7c1af4a8 translatedAt=2026-06-15T08:08:46.233Z pushedAt=2026-06-17T01:16:54.624Z -->

Distributed Service Kit implements distributed device management, distributed hardware management, distributed keyboard and mouse traversal, and distributed component management.

Distributed services are underpinned by distributed device management, which involves discovering and authenticating nearby devices, querying device information, and listening for device status. That is, distributed services can be performed only between authenticated devices.

You can implement cross-application collaboration by referring to [Cross-Device UIAbility Connection Development](abilityconnectmanager-guidelines.md). After the devices are signed in with the same account and successfully networked, an application can start a [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) of the same application on another device, enabling the exchange of information, byte streams, images, and data streams across devices.

## Working Principles

The application is required to initiate a request for device discovery, authentication, query, and listening.

## Constraints

The application needs user authorization before implementing distributed device management.

<!--RP1-->
<!--RP1End-->