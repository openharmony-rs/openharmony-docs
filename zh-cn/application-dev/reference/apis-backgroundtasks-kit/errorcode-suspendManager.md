# suspendManager错误码

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->

> **说明**：
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 31800005 参数错误

**错误信息**

Parameter error.

**错误描述**

传入的参数不合法。

**可能原因**

1. 未先注册观察者（observer），直接调用了注销接口。
2. 注册时传入的stateList为空数组或未定义（不存在）。
3. 查询时传入的pidList中包含不存在的进程ID（pid）。

**处理步骤**

1. 在调用[unregisterSuspendStateObserver](js-apis-resourceschedule-suspendManager-sys.md#suspendmanagerunregistersuspendstateobserver)注销监听前，请确保已通过[registerSuspendStateObserver](js-apis-resourceschedule-suspendManager-sys.md#suspendmanagerregistersuspendstateobserver)完成注册。
2. 调用注册接口时，确保stateList参数不为空，且数组元素均为有效的[FreezeState](js-apis-resourceschedule-suspendManager-sys.md#freezestate)枚举值。
3. 调用[getSuspendStateByPidList](js-apis-resourceschedule-suspendManager-sys.md#suspendmanagergetsuspendstatebypidlist)查询状态前，校验pidList中的所有pid均对应当前系统中真实存在的有效进程。

## 31800006 获取冻结管理服务失败

**错误信息**

Failed to get suspend manager service.

**错误描述**

获取冻结管理服务失败。

**可能原因**

系统内部服务异常，后台冻结系统服务不可用。

**处理步骤**

系统服务内部工作异常，请稍候重试，或者重启设备尝试。
