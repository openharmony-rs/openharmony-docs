# 页面路由错误码
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @mayaolll-->
<!--Designer: @jiangdayuan-->
<!--Tester: @lxl007-->
<!--Adviser: @HelloCrease-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 100001 内部错误

**错误信息**

Internal error.

**错误描述**

当出现了开发者解决不了的内部异常错误，系统会产生此错误码，并描述具体是哪种内部错误。作为@ohos.router的错误码时，该错误码为string类型。

**可能原因**

未成功获取渲染引擎，解析参数失败等。

**处理步骤**

NA

## 100002 路由页面跳转时输入的uri错误

**错误信息**

Uri error. The URI of the page to redirect is incorrect or does not exist.

**错误描述**

当跳转页面输入的uri错误或者不存在，系统会产生此错误码。该错误码为string类型。

**可能原因**

输入的路由uri错误或者不存在。

**处理步骤**

请检查输入的路由uri是否正确。

## 100003 路由压入的page过多

**错误信息**

Page stack error. Too many pages are pushed.

**错误描述**

当跳转页面压入页面数超过32，系统会产生此错误码。该错误码为string类型。

**可能原因**

压入pages过多。

**处理步骤**

请清除多余或无效的页面。

## 100004 命名路由页面跳转时输入的name错误

**错误信息**

Named route error. The named route does not exist.

**错误描述**

当跳转命名路由页面输入的name错误或者不存在，系统会产生此错误码。该错误码为string类型。

**可能原因**

输入的命名路由name错误或者不存在。

## 100005 Navigation跳转时未注册builder函数

**错误信息**

Builder function not registered.

**错误描述**

Navigation跳转时，Navigation未注册创建NavDestination组件的builder函数，系统会产生此错误码。

**可能原因**

Navigation跳转时，Navigation未注册创建NavDestination的builder函数。

**处理步骤**

请检查Navigation创建NavDestination的builder函数是否存在。

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

传入的索引值非法。

**可能原因**

index为非法值。

**处理步骤**

请检查传入的索引值。

## 106201 查询路由导航信息失败

**错误信息**

Failed to query route navigation information.

**错误描述**

查询路由导航信息失败。

**可能原因**

可能因为当前节点不在Navigation中。

**处理步骤**

请检查当前节点是否在Navigation中。

## 106202 传入的buffer size异常

**错误信息**

buffer size is not large enough.

**错误描述**

传入的buffer size异常。

**可能原因**

给定的buffer size小于可以容纳目标的最小缓冲区大小。

**处理步骤**

请检查给定的buffer size。

## 200002 路由页面替换时输入的uri错误

**错误信息**

Uri error. The URI of the page to be used for replacement is incorrect or does not exist.

**错误描述**

当替换页面输入的uri错误或不存在，系统会产生此错误码。该错误码为string类型。

**可能原因**

输入的路由uri错误或不存在。

**处理步骤**

请检查输入的路由uri是否正确。

## 300001 Navigation跳转前下载hsp分包失败

**错误信息**

hsp silent install fail.

**错误描述**

Navigation跳转前下载跳转页面所在hsp分包失败，系统会产生此错误码。

**可能原因**

下载的目标hsp分包不存在。

**处理步骤**

请检查待跳转的目标页面所在hsp分包是否存在，传入的moduleName是否正确。