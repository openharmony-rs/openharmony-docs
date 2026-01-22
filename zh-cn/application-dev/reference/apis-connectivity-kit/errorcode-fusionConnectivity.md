# 融合短距服务子系统错误码

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 34900001 设备未注册

**错误信息**

The device is not bound.

**错误描述**

该设备未注册。

**可能原因**

应用未调用[bindDevice](js-apis-fusionConnectivity-partnerAgent.md#partneragentbinddevice)注册设备。

**处理步骤**

应用调用[bindDevice](js-apis-fusionConnectivity-partnerAgent.md#partneragentbinddevice)注册设备。

## 34900003 设备未配对

**错误信息**

The device is not paired.

**错误描述**

设备未配对。

**可能原因**

应用注册注册的设备未经过蓝牙配对。

**处理步骤**

执行设备蓝牙配对流程。

## 34900004 设备地址已被注册

**错误信息**

The device address has already been bound with PartnerAgentExtensionAbility.

**错误描述**

该设备地址已经注册过[PartnerAgentExtensionAbility](js-apis-fusionConnectivity-partnerAgentExtensionAbility.md)。

**可能原因**

应用重复注册一个地址。

**处理步骤**

应用调用[unbindDevice](js-apis-fusionConnectivity-partnerAgent.md#partneragentunbinddevice)解注册当前设备，再重新注册[bindDevice](js-apis-fusionConnectivity-partnerAgent.md#partneragentbinddevice)新的Ability。

## 34900005 蓝牙关闭

**错误信息**

Bluetooth disabled.

**错误描述**

蓝牙关闭。

**可能原因**

蓝牙处于关闭状态。

**处理步骤**

打开蓝牙。

## 34900099 操作失败

**错误信息**

Operation failed.

**错误描述**

操作失败。

**可能原因**

因系统原因导致当前操作失败。

**处理步骤**

请重试该操作。