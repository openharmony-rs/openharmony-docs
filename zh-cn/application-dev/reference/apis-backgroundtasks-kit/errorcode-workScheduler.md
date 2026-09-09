# workScheduler错误码

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 9700001 内存操作失败

**错误信息**

Memory operation failed.

**错误描述**

内存操作失败。

**可能原因**

1. 系统内存泄漏。
2. 系统内存不足。

**处理步骤**

1. 请检查应用代码是否存在内存泄漏问题，如未释放的对象、循环引用等。
2. 检查应用内存使用情况，释放不必要的内存资源。

## 9700002 Parcel读写操作失败

**错误信息**

Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory.

**错误描述**

IPC通信读写Parcel数据失败。

**可能原因**

1. 进程间通信的时候，读取或写入数据对象失败。
2. 读写操作申请内存失败。

**处理步骤**

系统内部工作异常，请稍候重试，或者重启设备尝试。

## 9700003 系统服务失败

**错误信息**

System service operation failed.

**错误描述**

客户端进程请求系统服务时操作失败。

**可能原因**

1. 系统服务还未启动。
2. 系统服务异常。

**处理步骤**

系统服务内部工作异常，请稍候重试，或者重启设备尝试。

## 9700004 参数校验失败

**错误信息**

Input param failed.

**错误描述**

输入参数异常。

**可能原因**

1. 当参数是workInfo时，bundleName和应用的uid不匹配。
2. 取消或查询延迟任务时，延迟任务不存在。
3. 当参数是taskInfo时，abilityName不是launcher ability或taskId校验失败。

**处理步骤**

1. 请检查workInfo中的bundleName是否与应用uid匹配。
2. 如取消或查询延迟任务时出现此错误，请确认该延迟任务已正确创建。
3. 请检查taskInfo中abilityName是否为launcher ability。
4. 如果要完成、查询或取消注册后台刷新任务，请检查taskId是否正确。

## 9700005 StartWork失败

**错误信息**

Calling startWork failed.

**错误描述**

延迟任务申请失败。

**可能原因**

1. 延迟任务已存在。
2. 每个应用uid最多添加10个延迟任务。
3. 重复任务设置的重复时间应至少为20分钟。

**处理步骤**

1. 如提示任务已存在，请避免重复创建相同任务。
2. 请检查当前应用已创建的延迟任务数量是否超过10个。
3. 请检查重复任务的重复时间设置是否满足20分钟的要求。
<!--Del-->
## 9700006 执行频率参数校验失败

**错误信息**

Failed to check the execution frequency parameters.

**错误描述**

执行频率参数检查失败。

**可能原因**

1. uid不存在或格式不正确。
2. workId格式不正确或不存在。
3. interval值不在允许范围内或格式不正确。

**处理步骤**

1. 请检查uid是否与应用uid匹配。
2. 请检查workId是否与应用申请的延迟任务workId匹配。
3. 请检查interval值是否超出范围。
<!--DelEnd-->
