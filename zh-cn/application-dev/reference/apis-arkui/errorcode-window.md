# 窗口错误码

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 1300001 重复操作
**错误信息**<br>
Repeated operation.

**错误描述**<br>
当进行某些重复操作时，系统会报此错误码。

**可能原因**<br>
1.窗口已经被创建。<br>
2.窗口已经处于当前状态。

**处理步骤**<br>
在创建窗口前，检查该窗口是否已经被创建或者是否已经处于当前状态。

## 1300002 窗口状态异常
**错误信息**<br>
This window state is abnormal.

**错误描述**<br>
当窗口状态异常，如未创建或已被销毁时，操作该窗口，会报此错误码。

**可能原因**<br>
操作窗口时，该窗口未创建或已被销毁。

**处理步骤**<br>
在对窗口进行操作前，检查该窗口是否存在，确保其已创建且未被销毁，再进行相关操作。

## 1300003 系统服务工作异常
**错误信息**<br>
This window manager service works abnormally.

**错误描述**<br>
当系统服务工作异常时，会报此错误码。

**可能原因**<br>
窗口内部服务没有正常启动。

**处理步骤**<br>
系统服务内部工作异常，请稍候重试，或者重启设备尝试。

## 1300004 无权限操作
**错误信息**<br>
Unauthorized operation.

**错误描述**<br>
当对无操作权限的对象进行操作时，会报此错误码。

**可能原因**<br>
操作了其它进程的窗口对象。

**处理步骤**<br>
请检查是否非法操作了别的进程的对象，删除相关操作。

## 1300005 WindowStage异常
**错误信息**<br>
This window stage is abnormal.

**错误描述**<br>
当WindowStage异常，如已被销毁时，操作该WindowStage，会报此错误码。

**可能原因**<br>
该WindowStage没有被创建或者已经被销毁。

**处理步骤**<br>
在对WindowStage进行操作前，检查该WindowStage是否存在，若已被销毁，请释放该WindowStage下的窗口。

## 1300006 窗口上下文异常
**错误信息**<br>
This window context is abnormal.

**错误描述**<br>
当窗口上下文异常，如已被销毁时，操作该窗口上下文，会报此错误码。

**可能原因**<br>
操作窗口上下文时，该窗口上下文已被销毁。

**处理步骤**<br>
在对窗口上下文进行操作前，检查该窗口上下文是否存在，确保其未被销毁，再进行相关操作。

## 1300007 WindowExtension拉起应用失败

**错误信息**<br>
Failed to start the ability.

**错误描述**<br>
WindowExtension拉起应用失败。

**可能原因**<br>
WindowExtension拉起应用的参数异常。

**处理步骤**<br>
检查WindowExtension参数是否被异常修改，确保其参数合法，再进行相关操作。

## 1300008 显示设备异常

**错误信息**<br>
The display device is abnormal.

**错误描述**<br>
显示设备异常。

**可能原因**<br>
1. 显示设备没有准备好。<br>
2. 显示设备被移除。<br>
3. 显示设备被损坏。

**处理步骤**<br>
确保显示设备正常，再进行相关开发。

## 1300009 父窗口无效

**错误信息**<br>The parent window is invalid.

**错误描述**<br>父窗口无效。

**可能原因**<br>
1. 子窗口没有绑定父窗口。<br>
2. 子窗口绑定的父窗口异常，如父窗口已被销毁等。

**处理步骤**<br>
1. 检查确保子窗口成功绑定父窗口。<br>
2. 检查子窗口绑定的父窗口状态，确保父窗口状态正常。

## 1300010 当前窗口模式不支持该操作

**错误信息**<br>The operation in the current window status is invalid.

**错误描述**<br>当前窗口模式不支持该操作。

**可能原因**<br>
1. 对全屏或分屏窗口进行move操作。<br>
2. 对全屏或分屏窗口进行resize操作。

**处理步骤**<br>
1. 不要对全屏或分屏窗口进行move操作。<br>
2. 不要对全屏或分屏窗口进行resize操作。

## 1300011 销毁画中画窗口失败

**错误信息**<br>
Failed to destroy the PiP window.

**错误描述**<br>
销毁画中画窗口失败。

**可能原因**<br>
画中画窗口空指针。<br>

**处理步骤**<br>
无需处理。

## 1300012 画中画窗口状态异常

**错误信息**<br>
The PiP window state is abnormal.

**错误描述**<br>
画中画窗口状态异常。

**可能原因**<br>
画中画窗口状态异常。

**处理步骤**<br>
无需处理。

## 1300013 创建画中画窗口失败

**错误信息**<br>
Failed to create the PiP window.

**错误描述**<br>
创建画中画窗口失败。

**可能原因**<br>
1. 启动画中画时传入参数有误。<br>
2. 在非全屏窗口下启动画中画。

**处理步骤**<br>
1. 检查启动画中画参数。<br>
2. 不要在非全屏窗口下启动画中画。

## 1300014 画中画内部错误

**错误信息**<br>
PiP internal error.

**错误描述**<br>
画中画内部错误。

**可能原因**<br>
1.画中画依赖的窗口异常，可能窗口为空。
2.画中画控制器异常。

**处理步骤**<br>
无需处理。

## 1300015 重复操作画中画

**错误信息**<br>
Repeated PiP operation.

**错误描述**<br>
重复操作画中画。

**可能原因**<br>
这个画中画已经被拉起或者已经被关闭。

**处理步骤**<br>
不要重复启动/停止画中画。<br>

## 1300016 参数校验错误

**错误信息**

Parameter validation error.

**错误描述**

参数错误，如值超出允许的范围、字符串/数组的长度不符合要求、参数格式不正确等。

**可能原因**

1.参数的值超出允许的范围。

2.参数的长度超出允许的长度。

3.参数的格式不正确。

**处理步骤**

检查参数是否符合规范。

## 1300017 filter控制器调用错误

**错误信息**

Incorrect filter calling.

**错误描述**

filter控制器无效调用，比如调用时序不对。

**可能原因**

setBackgroundFilter在animateBackgroungFilter之后使用。

**处理步骤**

检查使用时的步骤时序，保证在animateBackgroungFilter之前使用setBackgroundFilter。

## 1300018 API调用超时

**错误信息**

API call timed out.

**错误描述**

接口调用超时。

**可能原因**

同步接口调用等待时间超出了限制范围。

**处理步骤**

需根据具体业务场景而定，常见的几种处理方式：

1.API接口在有限次数内进行重新调用。

2.降级处理，使用缓存或执行其他业务逻辑。

3.中断本次逻辑处理。

## 1300019 闪控球参数校验错误

**错误信息**

Wrong parameters for operating the floating ball.

**错误描述**

参数错误，包括值超出范围、字符串或数组长度不符、参数格式不正确。

**可能原因**

1.参数的值超出允许的范围。

2.参数的长度超出允许的长度。

3.参数的格式不正确。

**处理步骤**

1.参数值应处于允许的范围内。

2.参数的长度超出允许的范围。

3.参数应使用正确的格式。

## 1300020 创建闪控球窗口失败

**错误信息**

Failed to create the floating ball window.

**错误描述**

创建闪控球窗口失败。

**可能原因**

1.启动闪控球时参数有误。

2.在不支持的设备上启动闪控球。

3.应用在后台时启动闪控球。

**处理步骤**

1.启动闪控球前，请检查参数。

2.启动闪控球前，请检查设备环境是否支持。

3.在拉起闪控球前，判断应用是否处于前台。

## 1300021 启动多个闪控球失败

**错误信息**

Failed to start multiple floating ball windows.

**错误描述**

启动多个闪控球失败。

**可能原因**

同一应用创建多个闪控球控制器启动闪控球。

**处理步骤**

同一应用应仅创建一个闪控球控制器以启动闪控球，建议使用单例模式来持有闪控球控制器。

## 1300022 重复操作闪控球

**错误信息**

Repeated floating ball operation.

**错误描述**

重复操作闪控球。

**可能原因**

1.闪控球在启动状态下再次启动。

2.闪控球停止后，再次停止无效。

3.重复注册闪控球回调。

**处理步骤**

1.在启动操作前，检查闪控球是否已启动。

2.在停止操作前，检查闪控球是否已停止。

3.在注册闪控球回调操作前，确保回调未注册。

## 1300023 闪控球内部错误

**错误信息**

Floating ball internal error.

**错误描述**

闪控球内部错误。

**可能原因**

1.闪控球依赖的窗口异常，可能为空。

2.闪控球控制器异常，可能是控制器为空。

**处理步骤**

1.检查闪控球的窗口，确保其非空。

2.检查闪控球控制器的状态，确保其不为空。

## 1300024 闪控球窗口状态异常

**错误信息**

The floating ball window state is abnormal.

**错误描述**

闪控球窗口状态异常。

**可能原因**

闪控球窗口状态异常，可能未创建或已被销毁。

**处理步骤**

检查闪控球的窗口状态，确保窗口已创建且未被销毁。

## 1300025 闪控球状态不支持该操作

**错误信息**

The floating ball state does not support this operation.

**错误描述**

闪控球状态不支持该操作。

**可能原因**

1.在闪控球未启动时进行更新操作。

2.闪控球未启动时，查询窗口信息。

3.闪控球未启动时，拉起应用窗口。

4.调用闪控球停止接口，流程未完成时启动闪控球。

**处理步骤**

1.进行更新操作前，检查闪控球是否已启动。

2.进行查询闪控球窗口信息操作时，检查闪控球是否已启动。

3.进行拉起应用窗口操作时，检查闪控球是否已启动。

4.等待闪控球回调停止后，再次启动闪控球。

## 1300026 闪控球拉起应用窗口失败

**错误信息**

Failed to restore the main window.

**错误描述**

闪控球拉起应用窗口失败。

**可能原因**

1.传入参数有误。

2.点击后5秒内未拉起应用窗口。

3.拉起非本应用的窗口。

**处理步骤**

1.请检查应用窗口的拉起参数。

2.点击后5秒内拉起应用窗口。

3.仅拉起本应用窗口。

## 1300027 更新闪控球时不能改变模板类型

**错误信息**

When updating the floating ball, the template type cannot be changed.

**错误描述**

更新闪控球时，模板类型与创建时不同。

**可能原因**

更新闪控球与创建闪控球时的模板类型不一致。

**处理步骤**

请确保在更新闪控球时，模板类型与创建闪控球时的模板类型一致。

## 1300028 不支持更新静态模板类型闪控球

**错误信息**

Updating static template-based floating balls is not supported.

**错误描述**

不支持更新静态模板类型闪控球。

**可能原因**

更新静态模板类型的闪控球。

**处理步骤**

请删除已有的静态模板类型闪控球，然后创建新的闪控球。

## 1001 窗口空指针异常<sup>(deprecated)</sup>
**错误信息**<br>
A window null pointer occurs.

**错误描述**<br>
窗口空指针异常，如出现空指针时，操作该窗口，会报此错误码。

**可能原因**<br>
操作窗口时，出现空指针。

**处理步骤**<br>
在对窗口进行操作前，检查该窗口是否存在空指针，确保其不存在空指针，再进行相关操作。

## 1002 无效的窗口类型<sup>(deprecated)</sup>
**错误信息**<br>
This window type is invalid.

**错误描述**<br>
窗口类型无效。

**可能原因**<br>
使用了无效的窗口类型，有效的窗口类型见[WindowType](arkts-apis-window-e.md#windowtype7)。

**处理步骤**<br>
请使用WindowType支持的窗口类型，再进行相关操作。

## 1003 无效的窗口参数<sup>(deprecated)</sup>
**错误信息**<br>
This window parameter is invalid.

**错误描述**<br>
当窗口参数无效时，操作该窗口，会报此错误码。

**可能原因**<br>
操作窗口时，该窗口参数无效。

**处理步骤**<br>
在对窗口进行操作前，检查该窗口参数是否有效，确保其参数有效，再进行相关操作。

## 1004 元能力服务异常<sup>(deprecated)</sup>
**错误信息**<br>
This system ability service works abnormally.

**错误描述**<br>
当元能力服务工作异常时，会报此错误码。

**可能原因**<br>
当销毁窗口时，如初始化proxy失败。

**处理步骤**<br>
元能力服务异常，重启设备尝试。

## 1005 IPC通信失败<sup>(deprecated)</sup>
**错误信息**<br>
This window IPC failed.

**错误描述**<br>
当IPC通信失败时，会报此错误码。

**可能原因**<br>
操作窗口时，该窗口参数IPC传输失败。

**处理步骤**<br>
在对窗口进行操作前，检查该窗口客户端和服务端服务正常，再进行相关操作。

## 1007 WindowExtension拉起应用失败<sup>(deprecated)</sup>
**错误信息**<br>
Failed to start the ability.

**错误描述**<br>
WindowExtension拉起应用失败。

**可能原因**<br>
WindowExtension拉起应用的参数异常。

**处理步骤**<br>
检查WindowExtension参数是否被异常修改，确保其参数合法，再进行相关操作。