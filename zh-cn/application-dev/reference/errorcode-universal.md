# 通用错误码

<!--Kit: Common-->
<!--Subsystem: Common-->
<!--Owner: @zengyawen-->
<!--Designer: @lingminghw-->
<!--Tester: @RayShih-->
<!--Adviser: @zengyawen-->

## 201 API权限校验失败

**错误信息**

Permission verification failed. The application does not have the permission required to call the API.

**错误描述**

权限校验失败，应用无权限使用该API，需要申请权限。

**可能原因**

1. 应用配置文件未声明对应权限。具体请[参考](../security/AccessToken/declare-permissions.md)。

2. 敏感权限未完成动态申请，用户未授予权限。具体请[参考](../security/AccessToken/request-user-authorization.md)。

3. 应用身份不满足接口的权限调用约束。

**处理步骤**

1. 在配置文件中补充接口依赖的权限。具体请[参考](../security/AccessToken/declare-permissions.md)。

2. 针对敏感权限增加动态申请逻辑。具体请[参考](../security/AccessToken/request-user-authorization.md)。

3. 确保调用方应用身份符合接口权限要求。

## 202 非系统应用调用系统 API

**错误信息**

Permission verification failed. A non-system application calls a system API.

**错误描述**

权限校验失败，非系统应用使用了系统API。

**可能原因**

非系统应用，使用了系统API，请校验是否使用了系统API。

**处理步骤**

请检查是否调用了系统API，并且去掉。

## 203 企业管理策略禁止使用此系统功能

**错误信息**

This function is prohibited by enterprise management policies.

**错误描述**

企业管理策略禁止使用此系统功能。

**可能原因**

试图操作已被设备管理应用禁用的系统功能。

**处理步骤**

请使用[getDisallowedPolicy](./apis-mdm-kit/js-apis-enterprise-restrictions.md#restrictionsgetdisallowedpolicydeprecated)接口检查该系统功能是否被禁用，并使用[setDisallowedPolicy](./apis-mdm-kit/js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicydeprecated)接口解除禁用状态。

<!--Del-->
## 204 用户访问控制策略拦截，访问被拒绝

**错误信息**

Access denied due to user access control policy. Possible causes:
1. The operation is prohibited by OS-account constraints.
2. The required privilege for the operation has expired or has not been granted.

**错误描述**

由于用户访问控制策略拦截，访问被拒绝。

**可能原因**

1. 系统账号约束禁止此操作。
2. 执行此操作所需的特权已过期或未被授予。

**处理步骤**

1. 确认目标操作涉及的用户约束和用户特权。
2. 若目标操作受约束管控，则通过[isOsAccountConstraintEnabled](./apis-basic-services-kit/js-apis-osAccount.md#isosaccountconstraintenabled11)接口判断目标操作涉及的约束是否使能，若已使能，则停止操作。
3. 若目标操作受特权管控，则通过[acquireAuthorization](./apis-basic-services-kit/js-apis-osAccount-sys.md#acquireauthorization24)接口申请目标特权，若申请成功则继续执行目标操作，否则停止操作。
<!--DelEnd-->

## 401 函数参数数量或参数类型不匹配

**错误信息**

Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.

**错误描述**

1. 必填参数为空。

2. 参数类型不正确。

3. 参数校验失败。无论是同步还是异步接口，此类异常大部分都通过同步的方式抛出。

**可能原因**

1. 必选参数没有传入。

2. 参数类型错误 (Type Error)。

3. 参数数量错误 (Argument Count Error)。

4. 空参数错误 (Null Argument Error)。

5. 参数格式错误 (Format Error)。

6. 参数值范围错误 (Value Range Error)。

**处理步骤**

请检查必选参数是否传入，或者传入的参数类型是否错误。对于参数校验失败，阅读参数规格约束，按照可能原因进行排查。

## 501 资源被其他线程占用，访问被拒绝 

**错误信息**

Access denied because the resource is occupied by another thread.

**错误描述**

资源已被其他线程占用锁定，本次访问请求被拒绝。

**可能原因**

当前资源正在被其他线程使用，无法完成操作。

**处理步骤**

确保同一组件/资源只在一个线程中使用。

## 801 API功能在部分设备不支持

**错误信息**

Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported.

**错误描述**

功能不支持。

**可能原因**

可能出现该错误码的场景为：硬件不支持或依赖的业务特性不支持。

**处理步骤**

1. 应避免在该设备上使用此API。

2. 若该API有前置的isxxxsupported接口，先调用isxxxsupported判断是否支持该API功能，再调用此API。

## 803 服务在当前国家或地区不可用

**错误信息**

The service is unavailable in the current country or region.

**错误描述**

服务在当前国家或地区不可用。

**可能原因**

服务在当前国家未开放。

**处理步骤**

应用应捕获错误，对服务提供的功能进行隔离，避免影响用户体验。可以进一步查询开发者资料获取Kit支持的国家和地区信息。

<!--RP1--><!--RP1End-->