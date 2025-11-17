# MDM Kit Terms
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima-->
<!--Designer: @liuzuming-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->


## BYOD
Bring Your Own Device (BYOD) allows enterprise employees to use their own mobile devices, such as laptops, tablets, and smartphones, on premises to obtain internal information and operate authorized enterprise applications.

## MDM Application (Device Administrator Application)
A Mobile Device Management (MDM) application is an enterprise-level application integrated with MDM capabilities. It can centrally manage, monitor, and protect mobile devices (such as smartphones, tablets, and laptops) in an enterprise. It allows IT administrators to remotely configure devices, enforce security policies, deploy applications and safeguard enterprise data.

## EnterpriseAdminExtensionAbility
**EnterpriseAdminExtensionAbility** is a mandatory component for MDM applications. When developing MDM applications for enterprises, you need to inherit from **EnterpriseAdminExtensionAbility** and implement MDM service logic in the **EnterpriseAdminExtensionAbility** instance. This component implements notifications of system management status changes and defines the callbacks to be invoked when a device administrator application is enabled or disabled or an application is installed or uninstalled. Once this ability is activated, it remains alive and will launch automatically after a system restart or user switch. Note that an MDM application with **EnterpriseAdminExtensionAbility** activated cannot be uninstalled.
