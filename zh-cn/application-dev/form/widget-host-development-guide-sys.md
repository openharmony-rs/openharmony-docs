# ArkTS卡片使用方开发指导（仅对系统应用开放）
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->

## 卡片概述

卡片是一种界面展示形式，可以将应用的重要信息或操作前置到卡片，以达到服务直达，减少体验层级的目的。

卡片常用于嵌入到其他应用（当前只支持系统应用）中作为其界面的一部分显示，并支持拉起页面，发送消息等基础的交互功能。卡片使用方负责显示卡片。

- 卡片的基本概念：

  - 卡片提供方：提供卡片显示内容原子化服务，控制卡片的显示内容、控件布局以及控件点击事件。
  
  - 卡片使用方：显示卡片内容的宿主应用，控制卡片在宿主中展示的位置。
  
  - 卡片管理服务：用于管理系统中所添加卡片的常驻代理服务，包括卡片对象的管理与使用，以及卡片周期性刷新等。
  
   ![formHostModule](./figures/widget-host-development-guide-1.png)

## 场景介绍

卡片使用方开发，即基于Stage模型的卡片使用方开发，主要指导如下：

- 卡片组件FormComponent的使用。
- 通过formHost模块提供的卡片使用方相关接口操作卡片的删除、更新等行为。

## 卡片组件

提供卡片组件，实现卡片的显示功能。详情见[FormComponent](../reference/apis-arkui/arkui-ts/ts-basic-components-formcomponent-sys.md)。

> **说明：**
>
> - 该组件从API Version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 该组件为卡片组件的使用方。
>
> - 该组件使用需要具有系统签名。
>
> - 本模块为系统接口。

通过卡片组件成功添加卡片时，会调用到卡片提供方FormExtensionAbility中的[onAddForm](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonaddform)方法。

### 临时卡片和常态卡片

在卡片组件中的temporary字段可以配置卡片是临时卡片还是常态卡片。true为临时卡片，false为常态卡片。

- 常态卡片：卡片使用方会持久化的卡片。如添加到桌面的卡片。

- 临时卡片：卡片使用方不会持久化的卡片。
  
由于临时卡片的数据具有非持久化的特殊性，某些场景例如卡片服务框架死亡重启，此时临时卡片数据在卡片管理服务中已经删除，且对应的卡片ID不会通知到提供方，所以卡片提供方需要自己负责清理长时间未删除的临时卡片数据。同时对应的卡片使用方可能会将之前请求的临时卡片转换为常态卡片。如果转换成功，卡片提供方也需要对对应的临时卡片ID进行处理，把卡片提供方记录的临时卡片数据转换为常态卡片数据，防止提供方在清理长时间未删除的临时卡片时，把已经转换为常态卡片的临时卡片信息删除，导致卡片信息丢失。  

## formHost接口

formHost提供一系列的卡片使用方接口，来操作卡片的更新、删除等行为，具体的API介绍详见[@ohos.app.form.formHost (formHost)(系统接口)](../reference/apis-form-kit/js-apis-app-form-formHost-sys.md)。

## 卡片使用方示例
<!-- @[form_host_index](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormHost/entry/src/main/ets/pages/Index.ets) -->

![screenshot](./figures/widget-host-development-guide-2.jpeg)

## 相关实例

针对卡片使用方开发，有以下实例可供参考：

- [卡片使用方（Stage）（API12）](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Form/FormHost)
