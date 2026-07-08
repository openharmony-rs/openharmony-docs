# 页面路由错误码
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @huangxiaolinabc-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->

页面路由错误码用于标识页面跳转、页面替换和Navigation跳转等场景中的常见错误，帮助开发者快速定位路由配置、页面栈和参数传入问题。

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 100002 路由页面跳转时输入的uri错误

**错误信息**

Uri error. The URI of the page to redirect is incorrect or does not exist.

**错误描述**

当跳转页面输入的URI错误或者不存在，系统会产生此错误码。该错误码为string类型。

**可能原因**

输入的路由URI错误或者不存在。

**处理步骤**

请检查输入的路由URI是否正确。

## 100003 路由压入的page过多

**错误信息**

Page stack error. Too many pages are pushed.

**错误描述**

当跳转页面压入页面数超过32，系统会产生此错误码。该错误码为string类型。

**可能原因**

压入的页面数量超过32。

**处理步骤**

请清除多余或无效的页面。

## 100004 命名路由页面跳转时输入的name错误

**错误信息**

Named route error. The named route does not exist.

**错误描述**

当跳转命名路由页面输入的name错误或者不存在，系统会产生此错误码。该错误码为string类型。

**可能原因**

输入的命名路由name错误或者不存在。

**处理步骤**

请检查输入的命名路由name是否正确或者是否存在。

## 100005 Navigation跳转时未注册builder函数

**错误信息**

Builder function not registered.

**错误描述**

Navigation跳转时，未注册创建NavDestination组件的builder函数，系统会产生此错误码。

**可能原因**

- Navigation跳转时，未注册创建NavDestination的builder函数。

- 跳转的目标页面中缺少Navigation组件。

- 未配置路由表。

**处理步骤**

请按以下步骤检查：
1. 检查Navigation是否提供了创建NavDestination的builder函数。
2. 确认路由表已正确配置。
3. 确认跳转的目标页面中包含Navigation组件。

## 100006 Navigation跳转时目标页面不存在NavDestination组件

**错误信息**

NavDestination not found.

**错误描述**

Navigation跳转时，目标页面不存在NavDestination组件，系统会产生此错误码。

**可能原因**

Navigation跳转时，目标页面不存在NavDestination组件。

**处理步骤**

请检查待跳转的目标页面中是否存在NavDestination组件。

## 106200 传入的索引值非法

**错误信息**

index value is invalid.

**错误描述**

调用路由相关接口时传入的索引值非法。

**可能原因**

传入的索引值为非法值，如小于0或超出页面栈有效范围。

**处理步骤**

请检查传入的索引值是否为有效整数，且在当前页面栈的有效范围内。

## 106201 查询路由导航信息失败

**错误信息**

Failed to query route navigation information.

**错误描述**

当前节点未挂载在页面下时，查询路由导航信息失败，系统会产生此错误码。

**可能原因**

可能因为当前节点未挂载在页面下。

**处理步骤**

请检查当前节点是否在页面中。

## 106202 传入的buffer size异常

**错误信息**

buffer size is not large enough.

**错误描述**

传入的buffer size异常。

**可能原因**

给定的buffer size小于容纳目标数据所需的最小缓冲区大小。

**处理步骤**

请检查给定的buffer size是否满足最小缓冲区大小要求。

## 200002 路由页面替换时输入的uri错误

**错误信息**

Uri error. The URI of the page to be used for replacement is incorrect or does not exist.

**错误描述**

当替换页面输入的URI错误或不存在，系统会产生此错误码。该错误码为string类型。

**可能原因**

输入的路由URI错误或不存在。

**处理步骤**

请检查输入的路由URI是否正确。

## 300001 Navigation跳转前静默安装hsp分包失败

**错误信息**

hsp silent install fail.

**错误描述**

Navigation跳转前静默安装跳转页面所在hsp分包失败，系统会产生此错误码。

**可能原因**

下载的目标hsp分包不存在。

**处理步骤**

请检查待跳转的目标页面所在hsp分包是否存在，传入的moduleName是否正确。
