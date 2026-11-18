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

1. observer未注册就调用注销接口。
2. 注册时stateList为空或不存在。
3. 查询时pidList中有不存在的pid。

**处理步骤**

1. 调用[unregisterSuspendStateObserver](js-apis-resourceschedule-suspendManager-sys.md#suspendmanagerunregistersuspendstateobserver)接口前先调用[registerSuspendStateObserver](js-apis-resourceschedule-suspendManager-sys.md#suspendmanagerregistersuspendstateobserver)。
2. 注册时stateList为[FreezeState](js-apis-resourceschedule-suspendManager-sys.md#freezestate)类型。
3. 调用[getSuspendStateByPidList](js-apis-resourceschedule-suspendManager-sys.md#suspendmanagergetsuspendstatebypidlist)时pidList中传入的pid存在。

## 31800006 获取冻结管理服务失败

**错误信息**

Failed to get suspend manager service.

**错误描述**

获取冻结管理服务失败。

**可能原因**

系统内部服务异常，后台冻结系统服务不可用。

**处理步骤**

系统服务内部工作异常，请稍候重试，或者重启设备尝试。
