# 无障碍子系统错误码

<!--Kit: Accessibility Kit-->
<!--Subsystem: BarrierFree-->
<!--Owner: @qiiiiiiian-->
<!--Designer: @z7o-->
<!--Tester: @A_qqq-->
<!--Adviser: @w_Machine_cc-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 9300000 无障碍系统服务工作异常

**错误信息**

System abnormality.

**错误描述**

当无障碍系统服务工作异常时，方法将返回该错误码。

**可能原因**

该错误码表示无障碍系统服务工作异常，可能原因如下：
1. 内部操作失败（Internal operation failed）。
2. 获取必要的服务或客户端对象失败（空指针）（Failed to obtain the required service or client object (null pointer)）。
3. IPC通信失败（IPC communication failed）。
4. 获取无障碍服务代理失败（Failed to obtain the accessibility service proxy）。
5. 等待异步操作结果超时（Timed out while waiting for the result of an asynchronous operation）。
6. 监听器或观察者已注册（The listener or observer has already been registered）。
7. 监听器或观察者未注册（The listener or observer is not registered）。
8. 客户端未连接（The client is not connected）。
9. 目标应用连接无障碍服务失败（The target application failed to connect to the accessibility service）。
10. 从ACE接收的元素信息无效（The element information received from ACE is invalid）。
11. 在ACE中执行操作失败（Failed to perform an action in ACE）。
12. 注入手势事件失败（Failed to inject a gesture event）。

**处理步骤**

1. 等待一段时间后重新调用该方法。
2. 若重试后仍然报此错误码，重启无障碍扩展应用。
3. 若仍报错，重启设备。

<!--Del-->
## 9300001 输入无效的包名称或者Ability名称

**错误信息**

Invalid bundle name or ability name.

**错误描述**

当输入的包名称或者Ability名称无效时，方法将返回该错误码。

**可能原因**

该错误码表示输入无效的包名称或者Ability名称，可能原因如下：
1. 包名称不存在。
2. 包里面没有对应的Ability。

**处理步骤**

1. 检查包名称是否正确。
2. 检查包名称对应的Ability是否正确。

## 9300002 目标Ability已启用

**错误信息**

Target ability already enabled.

**错误描述**

当目标Ability已启用时，方法将返回该错误码。

**可能原因**

该错误码表示目标Ability已启用，无法被再次启用。

**处理步骤**

1. 停止该目标Ability。
2. 重新启用该目标Ability。
<!--DelEnd-->
## 9300003 不具备执行该操作的无障碍权限

**错误信息**

No accessibility permission to perform the operation.

**错误描述**

当应用执行了未授权的辅助操作（即用户在启用无障碍扩展应用时未开启的操作）时，方法将返回该错误码。

**可能原因**

该错误码表示应用不具备该操作的无障碍权限，可能原因是应用执行了用户在启用无障碍扩展应用时没有开启的辅助操作。

**处理步骤**

1. 尝试向用户提示请求执行无障碍辅助操作的必要性，并获取用户授权。授权完成后，应用将具备执行该辅助操作的权限。
2. 重新启用无障碍扩展应用，并开启所需的辅助操作。完成后，该辅助操作将可正常执行而不再报此错误码。

## 9300004 属性不存在

**错误信息**

This property does not exist.

**错误描述**

当输入无障碍节点元素中不存在的属性时，方法将返回该错误码。

**可能原因**

该错误码表示输入了无效的无障碍节点元素的属性，即无障碍节点元素中不存在该属性。

**处理步骤**

1. 检查无障碍节点元素中是否存在该属性。
2. 若不存在，请使用该节点元素中已存在的属性。

## 9300005 不支持该操作

**错误信息**

This action is not supported.

**错误描述**

当应用执行无障碍节点元素不支持的操作时，方法将返回该错误码。

**可能原因**

该错误码表示执行了无障碍节点元素不支持的操作。

**处理步骤**

1. 确认该无障碍节点元素支持的操作列表中是否包含该操作。
2. 若不包含，请使用该节点元素支持的操作。

<!--Del-->

## 9300006 目标应用和无障碍服务建立连接失败

**错误信息**

The connection between the target application and accessibility services failed.

**错误描述**

当目标应用和无障碍服务的连接句柄不存在时，方法将返回该错误码。

**可能原因**

目标应用尚未完成向无障碍服务注册连接。

**处理步骤**

目标应用尚未完成注册连接，尝试延后调用此方法。

## 9300007 触发放大功能失败

**错误信息**

Trigger magnification failed.

**错误描述**

当触发放大功能失败时，方法将返回该错误码。

**可能原因**

1. 未开启放大手势功能。
2. 放大模式未配置。

**处理步骤**

1. 开启放大手势功能。
2. 配置放大模式，完成配置后再次触发放大功能即可成功执行。
<!--DelEnd-->

## 9300008 应用分身索引不合法

**错误信息**

The appIndex is invalid. Possible causes: 1. The appIndex is out of the valid range. 2. The application corresponding to the appIndex does not exist.

**错误描述**

当输入的应用分身索引（即同一应用的多个运行实例的索引）不合法时，方法将返回该错误码。

**可能原因**

该错误码表示应用分身索引不合法，可能原因如下：
1. 应用分身索引不在合法范围，要求是大于等于0的整数。
2. 该索引对应的应用不存在。

**处理步骤**

检查应用分身索引的值是否合法。