# 账号管理概述

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @zhaimengchao-->
<!--Adviser: @zengyawen-->

## 简介

系统支持在一台设备上创建多个本地系统账号，以允许多个用户使用同一台设备。多个用户的数据按系统账号进行隔离，以保证不同用户数据的安全性。

## 基本概念

账号是用户身份的标识，不同场景下用户身份存在差异，同一用户往往存在多种账号。按照使用场景，账号模块负责管理以下类别的账号：

- 系统账号：表示用户在端侧设备上的身份标识，该标识在每个端侧设备上唯一。

- 域账号：表示用户在特定域内（比如公司、学校等）的身份标识，该标识在特定域内唯一。

- 分布式账号：表示用户在分布式网络中的身份标识，由特定机构/组织发放、认证和维护，可用于设备之间的认证、组网和服务调用。

- 应用账号：表示应用自定义的用户身份标识，该标识在应用内唯一，由应用管理其生命周期。

## 各类账号间的关系

![account_er](figures/account_er.png)

从上图可以看出，账号管理模块是以系统账号为核心，其他类型账号与系统账号存在关联关系。

- 域账号与系统账号存在一对一关联关系，两者的生命周期一致。
- 分布式账号与系统账号存在一对多关联关系，用户可以在每个系统账号下绑定一个分布式账号；不同系统账号下，分布式账号可以重复。分布式账号的生命周期独立于系统账号。
- 应用账号与系统账号存在多对多关联关系，用户可以在不同系统账号下管理多个应用账号；不同系统账号下，应用账号可以重复。应用账号的生命周期独立于系统账号。
- 域账号、分布式账号和应用账号相互之间无直接关联关系。

删除系统账号后，与之关联的域账号、分布式账号和应用账号也随之删除。

## 相关实例

针对账号管理开发，有以下相关实例可供参考：

- [应用账号管理](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Security/AppAccountManager)
- [分布式账号管理（仅支持系统应用）](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/SystemFeature/DistributedAppDev/DistributedAccount)
