# About This Kit
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima; @weizai16-->
<!--Designer: @hp_guo-->
<!--Tester: @lpw_work-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=188ff5fef3d90fc0078e4760b9813c31639f710c translatedAt=2026-10-30T03:21:54.378Z pushedAt=2026-10-30T03:21:54.378Z nl=1 -->

## Introduction

MDM Kit provides device management APIs for enterprise Mobile Device Management (MDM) apps to manage and protect data and applications on company devices. [MDM apps](./mdm-kit-term.md#mdm-app) use centralized management, remote configuration, and monitoring to ensure device and data security and stability. They are widely used in enterprises and government agencies to protect employee and customer devices and data, enabling efficient management and secure device use.

## Scenarios
- Corporate-Owned, Personally Enabled (COPE): Enterprises centrally purchase and deploy devices such as laptops, tablets, and smartphones for employees. These devices are corporate-owned and subject to unified enterprise management.

- Bring Your Own Device (BYOD): Some enterprises allow employees to bring their own tablets or smartphones to the workplace and connect these devices to the office environment. This strategy applies to enterprise workplace scenarios, including those where external visitors access facilities such as factories and laboratories using their own devices.

## Working Principles

<!--RP1-->
The framework layer and system ability (SA) layer use the enterprise_device_management component to provide the device administrator application framework and basic device management capabilities. The device administrator application uses an [EnterpriseAdminExtensionAbility](./mdm-kit-admin.md) to call APIs in MDM Kit to manage devices.<!--RP1End-->

![intro_arch.png](./figures/intro_arch.png)

## Constraints

- The SDK version must be 5.0.0 (API version 12) or later.

- Only the stage model is supported.

<!--RP3--><!--RP3End-->