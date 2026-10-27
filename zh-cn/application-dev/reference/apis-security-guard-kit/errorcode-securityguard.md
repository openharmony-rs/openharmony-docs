# 设备风险管理错误码

<!--Kit: Security Guard Kit-->
<!--Subsystem: Security-->
<!--Owner: @sunyibo-->
<!--Designer: @shipengfei-->
<!--Tester: @songjinke-->
<!--Adviser: @zengyawen-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 27000001 内部系统错误

**错误信息**

internal system error.

**错误描述**

调用阻断服务相关接口（[createAuthProvider](js-apis-security-guard-sys.md#securityguardcreateauthprovider)、[destroyAuthProvider](js-apis-security-guard-sys.md#securityguarddestroyauthprovider)、[requestAuthResult](js-apis-security-guard-sys.md#requestauthresult)）时，系统内部发生错误，无法完成对应操作。

**可能原因**

- 系统服务异常或未正常运行。
- 阻断框架内部状态异常，如会话已失效、底层通信失败等。

**处理步骤**

1. 检查系统服务是否正常运行，必要时重启设备后重试。
2. 确认 Provider 实例仍有效：若已调用 [destroyAuthProvider](js-apis-security-guard-sys.md#securityguarddestroyauthprovider) 销毁实例，需重新调用 [createAuthProvider](js-apis-security-guard-sys.md#securityguardcreateauthprovider) 创建后再使用。
3. 若问题持续，请收集日志并联系系统框架维护人员。

## 27000002 同进程阻断服务提供者实例数达上限

**错误信息**

Provider count of the current process has reached the upper limit.

**错误描述**

调用 [createAuthProvider](js-apis-security-guard-sys.md#securityguardcreateauthprovider) 创建阻断服务提供者会话时，当前进程内的 Provider 实例数已达到上限，创建失败。

**可能原因**

同一进程最多允许 1 个 Provider 实例。当前进程已存在未销毁的 Provider 实例时，再次创建将触发此错误。

**处理步骤**

1. 复用当前进程已有的 Provider 实例，避免重复创建。
2. 若确需新建实例，先调用 [destroyAuthProvider](js-apis-security-guard-sys.md#securityguarddestroyauthprovider) 销毁已有实例，再调用 [createAuthProvider](js-apis-security-guard-sys.md#securityguardcreateauthprovider) 创建。

## 27000003 全局阻断服务提供者实例数达上限

**错误信息**

Global provider count has reached the upper limit.

**错误描述**

调用 [createAuthProvider](js-apis-security-guard-sys.md#securityguardcreateauthprovider) 创建阻断服务提供者会话时，全局（跨进程）的 Provider 实例数已达到上限，创建失败。

**可能原因**

系统全局最多允许 16 个 Provider 实例。当全局 Provider 实例数达到该上限时，新进程创建 Provider 将触发此错误。

**处理步骤**

1. 等待其他进程的 Provider 实例被销毁后重试。
2. 协调各调用方合理管理 Provider 生命周期，及时调用 [destroyAuthProvider](js-apis-security-guard-sys.md#securityguarddestroyauthprovider) 释放不再使用的实例。

## 27000004 并发请求数达上限

**错误信息**

concurrent request count has reached the upper limit.

**错误描述**

调用 [AuthProvider.requestAuthResult](js-apis-security-guard-sys.md#requestauthresult) 请求事件阻断结果时，单个 Provider 的并发请求数已达到上限，新请求被拒绝。

**可能原因**

单个 Provider 并发请求上限为 128。当未完成的请求累计达到该上限时，新的请求将触发此错误。

**处理步骤**

1. 等待部分在途请求完成后重试。
2. 调用方对请求做并发控制，避免同时发起过多请求。
3. 必要时按业务优先级排队，控制并发数不超过 128。
