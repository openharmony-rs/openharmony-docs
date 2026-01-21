# MDM Kit简介
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima-->
<!--Designer: @liuzuming-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

## 业务介绍

MDM Kit（企业设备管理服务）为企业MDM（Mobile Device Management）应用提供设备管理API，用于管理并保护公司设备上的数据和应用程序。[MDM应用](./mdm-kit-term.md#mdm应用设备管理应用)可以通过集中管理、远程配置和监控来保障设备和数据的安全性和稳定性。它广泛应用于企业和政府机构，以确保员工和客户使用的设备和数据受到保护，实现企业高效管理、安全使用设备。

## 场景介绍
- 企业派发设备场景（COPE）：指企业统一购买笔记本电脑、平板电脑、智能手机等设备，并将这些设备分发给企业员工使用，这类设备的所属权属于企业，企业对这类设备进行统一管理。

- 自带设备办公场景（BYOD）：指一些企业允许员工携带自己的平板或智能手机到公司，并将这些设备接入办公环境，用于企业办公或者外来访客携带设备访问工厂、实验室等场景。

## 实现原理

<!--RP1-->
框架层和服务层提供了enterprise_device_management部件，enterprise_device_management部件提供了设备管理应用程序框架和基本设备管理能力。设备管理应用通过[EnterpriseAdminExtensionAbility](./mdm-kit-admin.md)来调用MDM Kit中的接口，实现管理设备的意图。<!--RP1End-->

![intro_arch.png](./figures/intro_arch.png)

## 约束与限制

- SDK版本为5.0.0（API 12）及以上。

- 仅支持Stage模型。

<!--RP3--><!--RP3End-->