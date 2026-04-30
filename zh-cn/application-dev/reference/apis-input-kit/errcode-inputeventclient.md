# 输入事件注入错误码

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @@zhang_yixin13-->

> **说明：**
>
> - 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码](../errorcode-universal.md)。

## 4300001 按键状态错误

**错误信息**

The key has been pressed and is not the most recently pressed key, or the number of pressed keys exceeds 5.

**错误描述**

当调用键盘控制器的 pressKey 接口时，如果按键已被按下且不是最近按下的按键，或已按下的按键数超过了5个，会产生此错误码。

**可能原因**

1. 按键已经被按下，且不是最近按下的按键。
2. 已按下的按键数量超过了5个。

**处理步骤**

1. 确保按键在释放状态下才能被按下。
2. 如果按键已被按下，确保它是最近按下的按键。
3. 确保同时按下的按键数量不超过5个。

## 4300001 按键未被按下

**错误信息**

The key has not been pressed.

**错误描述**

当调用键盘控制器的 releaseKey 接口时，如果按键未被按下，会产生此错误码。

**可能原因**

尝试释放一个未被按下的按键。

**处理步骤**

确保只释放已经被按下的按键。

## 4300002 显示器不存在

**错误信息**

The display does not exist.

**错误描述**

当调用鼠标控制器的 moveTo 接口时，如果指定的显示器不存在，会产生此错误码。

**可能原因**

指定的 displayId 对应的显示器不存在。

**处理步骤**

使用有效的显示器 ID，可以通过显示管理接口查询可用的显示器列表。

## 4300001 鼠标按键已被按下

**错误信息**

The mouse button has been pressed.

**错误描述**

当调用鼠标控制器的 pressButton 接口时，如果鼠标按键已被按下，会产生此错误码。

**可能原因**

鼠标按键已经处于按下状态。

**处理步骤**

确保鼠标按键在释放状态下才能被按下。

## 4300001 鼠标按键未被按下

**错误信息**

The mouse button has not been pressed.

**错误描述**

当调用鼠标控制器的 releaseButton 接口时，如果鼠标按键未被按下，会产生此错误码。

**可能原因**

尝试释放一个未被按下的鼠标按键。

**处理步骤**

确保只释放已经被按下的鼠标按键。

## 4300001 轴事件正在进行中

**错误信息**

An axis event is in progress.

**错误描述**

当调用鼠标控制器的 beginAxis 接口时，如果已有轴事件正在进行中，会产生此错误码。

**可能原因**

已经有一个轴事件序列正在进行，尚未结束。

**处理步骤**

确保在开始新的轴事件序列之前，先结束当前正在进行的轴事件序列。

## 4300001 轴事件未在进行中

**错误信息**

No axis event is in progress.

**错误描述**

当调用鼠标控制器的 updateAxis 或 endAxis 接口时，如果没有轴事件正在进行中，会产生此错误码。

**可能原因**

尝试更新或结束一个未开始的轴事件序列。

**处理步骤**

确保在调用 updateAxis 或 endAxis 之前，先调用 beginAxis 开始轴事件序列。
