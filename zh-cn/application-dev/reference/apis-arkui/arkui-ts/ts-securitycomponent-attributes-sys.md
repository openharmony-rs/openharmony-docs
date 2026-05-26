# 安全控件通用属性 (系统接口)

<!--Kit: ArkUI-->
<!--Subsystem: Security-->
<!--Owner: @harylee-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

## 模块简介

安全控件的基础属性系统接口，用于设置安全控件通用属性中的系统扩展能力。

该模块主要用于以下场景：

- 在测试或调试场景中，为安全控件设置额外标识。
- 验证安全控件的属性设置和交互行为。

> **说明：**
>
> 该组件从API version 10开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见[安全控件通用属性](ts-securitycomponent-attributes.md)。

## 关键 Class/Interface 介绍

### 核心接口类型

- **SecurityComponentMethod&lt;T&gt;**：安全控件通用属性方法集合，用于承载公开属性之外的系统扩展属性。

### 核心函数类型

- **[key](#key)**：设置组件唯一标识，仅用于测试场景中验证安全控件属性设置和交互行为。

## key

key(value: string): T

组件的唯一标识，唯一性由使用者保证。与[id](ts-securitycomponent-attributes.md#id15)同时使用时，后赋值的属性会覆盖先赋值的属性，建议仅设置id。

此接口仅用于对应用的测试，用于验证安全控件的属性设置和交互行为，在生产环境中应使用公开接口[id](ts-securitycomponent-attributes.md#id15)。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                   | 必填 | 说明                   |
|------------|------|-------|---------|
| value | string |是 | 组件的唯一标识，唯一性由使用者保证。默认值为空字符串。适用于测试场景中按标识精确定位安全控件实例。若同时设置 `id()` 和 `key()`，后设置的属性会覆盖前一个标识；生产环境建议优先使用公开接口 `id()`。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回安全控件的属性。 |
