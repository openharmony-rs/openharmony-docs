# About This Kit
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedHardware-->
<!--Owner: @hwzhangchuang-->
<!--Designer: @hwzhangchuang-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=9f53a9e77747af975b5a889ab884bf4bcac288aa translatedAt=2026-06-30T10:23:05.486Z pushedAt=2026-06-30T12:20:31.634Z -->

Distributed Service Kit implements distributed device management, distributed hardware management, distributed keyboard and mouse traversal, and distributed component management.

Distributed services are underpinned by distributed device management, which involves discovering and authenticating nearby devices, querying device information, and listening for device status. That is, distributed services can be performed only between authenticated devices.

You can implement cross-application collaboration by referring to [Cross-Device UIAbility Connection Development](abilityconnectmanager-guidelines.md). After the devices are signed in with the same account and successfully networked, an application can start a [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) of the same application on another device, enabling the exchange of information, byte streams, images, and data streams across devices.

## Working Principles

The application is required to initiate a request for device discovery, authentication, query, and listening.

## Constraints

The application needs user authorization before implementing distributed device management.

<!--RP1-->
<!--RP1End-->