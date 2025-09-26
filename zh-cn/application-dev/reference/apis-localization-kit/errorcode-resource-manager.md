# 资源管理错误码

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 9001001 无效的资源id

**错误信息**

Invalid resource ID.

**错误描述**

当传入的资源id符合类型校验，但却是一个不存在的资源id时，会报出此错误。

**可能原因**

传入的是一个不存在的id值。

**处理步骤**

1. 排查是否为以下场景：[HAR开启混淆](../../quick-start/har-package.md#编译)、中间码HAR、字节码HAR、跨HAP/HSP包。这四种场景推荐使用[getStringByName()](js-apis-resource-manager.md#getstringbyname9)等方法通过名称获取资源。

2. 检查传入参数的资源id是否已有。  

## 9001002 根据当前资源id，找不到匹配的资源

**错误信息**

No matching resource is found based on the resource ID.

**错误描述**

当传入的资源id符合类型校验，但是根据此资源id匹配不到资源时，会报出此错误。

**可能原因**

1. 传入的是资源id有误。

2. 资源解析有误。

**处理步骤**

检查传入的资源id是否符合预期。

## 9001003 无效的资源名称

**错误信息**

Invalid resource name.

**错误描述**

当传入的资源名称符合类型校验，但却是一个不存在的资源名称时，会报出此错误。

**可能原因**

传入的是一个不存在的资源名称。

**处理步骤**

检查传入的资源名称是否符合预期。

## 9001004 根据当前资源名称，找不到匹配的资源

**错误信息**

No matching resource is found based on the resource name.

**错误描述**

当传入的资源名称符合类型校验，但是根据此资源名称，匹配不到资源。

**可能原因**

1. 传入的是资源名称有误。

2. 资源解析有误。

**处理步骤**

可先检查传入的资源名称是否符合预期。

## 9001005 无效的相对路径

**错误信息**

Invalid relative path.

**错误描述**

根据参数相对路径, 找不到对应的资源。

**可能原因**

传入的相对路径有误。

**处理步骤**

可检查传入的相对路径是否符合预期。

## 9001006 循环引用

**错误信息**

The resource is referenced cyclically.

**错误描述**

解析引用次数过高。

**可能原因**

出现资源循环引用的情况。

**处理步骤**

查看资源$引用的地方，去除循环引用的情况。

## 9001007 根据当前id获取的资源格式化失败

**错误信息**

Failed to format the resource obtained based on the resource ID.

**错误描述**

resId获取的字符串资源格式化失败。

**可能原因**

1. 参数类型不在支持范围内。

2. 参数与占位符个数不等。

3. 参数与占位符类型不匹配。

**处理步骤**

查看args参数类型与占位符的个数、类型是否一致。

## 9001008 根据当前名称获取的资源格式化失败

**错误信息**

Failed to format the resource obtained based on the resource Name.

**错误描述**

resName获取的字符串资源格式化失败。

**可能原因**

1. 参数类型不在支持范围内。

2. 参数与占位符个数不等。

3. 参数与占位符类型不匹配。

**处理步骤**

查看args参数类型与占位符的个数、类型是否一致。

## 9001009 获取系统资源管理器失败

**错误信息**

Failed to access the system resource.

**错误描述**

获取系统资源管理器失败。

**可能原因**

系统资源没有加载到应用进程的沙箱路径。

**处理步骤**

查看应用进程是否包含系统资源沙箱路径。

## 9001010 无效的overlay路径

**错误信息**

Invalid overlay path.

**错误描述**

传入的overlay路径无效。

**可能原因**

路径不存在或者没有在对应应用的安装路径下，访问不到。

**处理步骤**

查看传入overlay路径放的位置。