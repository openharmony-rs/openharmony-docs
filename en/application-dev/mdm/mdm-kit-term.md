# MDM Kit Terms
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima-->
<!--Designer: @liuzuming-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

## EDM

An Enterprise Device Manager (EDM) serves as the core foundation of the enterprise device management framework.

## BYOD

Bring Your Own Device (BYOD) is an enterprise strategy that allows employees to bring their personal tablets or smartphones to the workplace and connect these devices to the office environment. This strategy applies to enterprise workplace scenarios, including those where external visitors access facilities such as factories and laboratories using their own devices.

## Administrator
### SDA

A Super Device Administrator (SDA) is capable of managing devices and other Device Administrator (DA) applications, including the activation and deactivation of such applications. It is applicable to enterprise device management scenarios.

### DA

A Device Administrator (DA) is responsible for device management tasks, and is applicable to enterprise device management scenarios.

### BDA

A BYOD Device Administrator (BDA) is designed to manage devices in common scenarios, such as disabling photographing and recording.

## MDM Application (Device Administrator Application)
A Mobile Device Management (MDM) application is an enterprise-level application integrated with MDM capabilities. It can centrally manage, monitor, and protect mobile devices (such as smartphones, tablets, and laptops) in an enterprise. It allows IT administrators to remotely configure devices, enforce security policies, deploy applications and safeguard enterprise data.

## EnterpriseAdminExtensionAbility
EnterpriseAdminExtensionAbility is a mandatory component for MDM applications. When developing an MDM application, you need to create an **EnterpriseAdminExtensionAbility** instance and implement MDM service logic in this instance. EnterpriseAdminExtensionAbility implements notifications of system management status changes and defines the callbacks to be invoked when a device administrator application is enabled or disabled or an application is installed or uninstalled. Once this ability is activated, it remains alive and will launch automatically after a system restart or user switch. Note that an MDM application with EnterpriseAdminExtensionAbility activated cannot be uninstalled.

## EMM Provider

An Enterprise Mobility Management (EMM) provider is a company that provides a complete set of EMM software, solutions, and services for other enterprises.
