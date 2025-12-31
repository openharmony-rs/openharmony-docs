# calendarManager错误码
## 201 权限校验失败

**错误信息**

Permission denied.

**错误描述**

权限被拒绝。

**可能原因**

1. 用户在设置中取消权限。

2. 在权限弹框中选择不允许。

**处理步骤**

1. 用户在设置中开启对应权限。

2. 在权限弹框中选择允许。

## 401 参数检查失败

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

## 801 该设备不支持此API

**错误信息**

Capability not supported. Failed to call the API due to limited device capabilities.

**错误描述**

该设备不支持此API，因此无法正常调用。

**可能原因**

可能出现该错误码的场景为：该设备已支持该API所属的Syscap，但是并不支持此API。

**处理步骤**

应避免在该设备上使用此API，或在代码中通过判断来规避异常场景下应用在不同设备上运行所产生的影响。

## 23900001 参数值超出范围

**错误信息**

Parameter value out of range.

**错误描述**

参数值超出范围。

**可能原因**

1. 参数为字串时，长度超范围。

2. 参数值超范围。

**处理步骤**

检查参数字串长度，参数值是否超范围。

## 23900003 未找到指定的账户

**错误信息**

The specified account was not found.

**错误描述**

未找到指定的账户。

**可能原因**

查的账户未创建。

**处理步骤**

创建指定的账户

## 23900004 内部程序错误

**错误信息**

Internal program error. Possible causes:1. dataShare database execution error;2. null pointer error; 3. Data parsing error.

**错误描述**

内部程序错误。

**可能原因**

程序内部错误，开发者无需处理

**处理步骤**

无需处理


<!--RP1--><!--RP1End-->