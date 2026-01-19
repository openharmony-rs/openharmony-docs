# 安全控件通用属性 (系统接口)

<!--Kit: ArkUI-->
<!--Subsystem: Security-->
<!--Owner: @harylee-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

安全控件的基础属性，用于设置安全控件通用的属性。

> **说明：**
>
> 该组件从API Version 10开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见[安全控件通用属性](ts-securitycomponent-attributes.md)。


## key

key(value: string): T

组件的唯一标识，唯一性由使用者保证。与[id](ts-securitycomponent-attributes.md#id15)同时使用时，后赋值的属性会覆盖先赋值的属性，建议仅设置id。

此接口仅用于对应用的测试。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                   | 必填 | 说明                   |
|------------|------|-------|---------|
| value | string |是 |组件的唯一标识，唯一性由使用者保证。<br/>默认值为空字符串。|

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回安全控件的属性。 |
