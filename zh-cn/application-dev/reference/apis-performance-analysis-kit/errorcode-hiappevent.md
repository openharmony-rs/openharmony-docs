# 应用事件打点错误码

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @liujiaxing2024-->
<!--SE: @junjie_shi-->
<!--TSE: @gcw_KuLfPSbe-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 11100001 打点功能被关闭

**错误信息**

Function disabled. Possible caused by the param disable in ConfigOption is true.

**错误描述**

- 在调用write接口进行应用事件打点时，由于打点功能未开启，系统将忽略相关事件。
- 在调用setEventParam接口设置事件自定义参数时，由于打点功能未开启，系统将忽略此次调用。

**可能原因**

应用事件打点功能被关闭了。

**处理步骤**

调用配置接口开启打点功能。

   ```ts
   import { hiAppEvent } from '@kit.PerformanceAnalysisKit';

   hiAppEvent.configure({
       disable: false
   });
   ```

## 11101001 非法的事件领域名称
**错误信息**

Invalid event domain. Possible causes: 1. Contain invalid characters; 2. Length is invalid.

**错误描述**

- 在调用write接口进行应用事件打点时，由于传入了非法的事件领域名称，系统将忽略相关事件。
- 在调用setEventParam接口设置事件自定义参数时，由于传入了非法的事件领域名称，系统将忽略此次调用。

**可能原因**

传入的事件领域名称不符合以下规则：

- 事件领域名称只包含数字、字母、下划线字符。
- 事件领域名称以字母开头，不以下划线结尾。
- 事件领域名称非空且长度不超过32个字符。

**处理步骤**

传入合法的事件领域名称。

## 11101002 非法的事件名称

**错误信息**

Invalid event name. Possible causes: 1. Contain invalid characters; 2. Length is invalid.

**错误描述**

- 在调用write接口进行应用事件打点时，由于传入了非法的事件名称，系统将忽略相关事件。
- 在调用setEventParam接口设置事件自定义参数时，由于传入了非法的事件名称，系统将忽略此次调用。

**可能原因**

传入的事件名称不符合以下规则：

- 事件名称只包含$字符、数字字符、字母字符、下划线字符。
- 事件名称首字符必须为字母字符或$字符，中间字符必须为数字字符、字母字符或下划线字符，结尾字符必须为数字字符或字母字符。
- 事件名称非空且长度不超过48个字符。

**处理步骤**

传入合法的事件名称。

## 11101003 非法的事件参数数量

**错误信息**

Invalid number of event parameters. Possible caused by the number of parameters is over 32.

**错误描述**

在调用write接口进行应用事件打点时，由于传入了非法的事件参数数量，额外的事件参数将被丢弃。

**可能原因**

传入的事件参数数量超过32个。

**处理步骤**

传入合法数量的事件参数。

## 11101004 非法的事件参数字符串长度

**错误信息**

Invalid string length of the event parameter.

**错误描述**

- 在调用write接口进行应用事件打点时，由于事件参数值传入了超长的字符串，系统将忽略相关事件参数。
- 在调用setEventParam接口设置事件自定义参数时，由于传入了非法的事件参数值，系统将忽略此次调用。

**可能原因**

- 调用write接口传入的事件参数值中的字符串长度超过8*1024个字符。
- 调用setEventParam接口传入的事件自定义参数值的长度超过1024个字符。

**处理步骤**

传入合法字符串长度的事件参数值。

## 11101005 非法的事件参数名称

**错误信息**

Invalid event parameter name. Possible causes: 1. Contain invalid characters; 2. Length is invalid.

**错误描述**

- 在调用write接口进行应用事件打点时，由于传入了非法的事件参数名称，系统将忽略相关事件参数。
- 在调用setEventParam接口设置事件自定义参数时，由于传入了非法的事件参数名称，系统将忽略此次调用。

**可能原因**

传入的事件参数名称不符合以下规则：

- 事件参数名称只包含$字符、数字字符、字母字符、下划线字符。
- 事件参数名称首字符必须为字母字符或$字符，中间字符必须为数字字符、字母字符或下划线字符，结尾字符必须为数字字符或字母字符。
- 事件参数名称非空且长度不超过32个字符。

**处理步骤**

传入合法的事件参数名称。

## 11101006 非法的事件参数数组长度

**错误信息**

Invalid array length of the event parameter.

**错误描述**

在调用write接口进行应用事件打点时，由于事件参数值传入了超出长度的数组，额外的数组元素将被丢弃。

**可能原因**

传入的事件参数值中的数组长度超过100。

**处理步骤**

传入合法长度数组的事件参数值。

## 11101007 非法的事件自定义参数数量

**错误信息**

The number of parameter keys exceeds the limit.

**错误描述**

在调用setEventParam接口设置事件自定义参数时，由于传入了非法的事件参数数量，系统将忽略此次调用。

**可能原因**

传入的事件自定义参数数量超过64个。

**处理步骤**

传入合法数量的事件自定义参数。

## 11102001 非法的观察者名称

**错误信息**

Invalid watcher name. Possible causes: 1. Contain invalid characters; 2. Length is invalid.

**错误描述**

在调用addWatcher接口进行事件订阅时，由于传入了非法的观察者名称，系统将忽略此次订阅。

**可能原因**

传入的观察者名称不符合以下规则：

- 观察者名称只包含数字、字母、下划线字符。
- 观察者名称以字母开头，不以下划线结尾。
- 观察者名称非空且长度不超过32个字符。

**处理步骤**

传入合法的观察者名称。

## 11102002 非法的过滤事件领域

**错误信息**

Invalid filtering event domain. Possible causes: 1. Contain invalid characters; 2. Length is invalid.

**错误描述**

在调用addWatcher接口进行事件订阅时，由于传入了非法的过滤事件领域，系统将忽略此次订阅。

**可能原因**

传入的过滤事件领域名称不符合以下规则：

- 事件领域名称只包含数字、字母、下划线字符。
- 事件领域名称以字母开头，不以下划线结尾。
- 事件领域名称非空且长度不超过32个字符。

**处理步骤**

传入合法的过滤事件领域名称。

## 11102003 非法的条数值

**错误信息**

Invalid row value. Possible caused by the row value is less than zero.

**错误描述**

在调用addWatcher接口进行事件订阅时，由于回调触发条件传入了非法的事件个数值，系统将忽略此次订阅。

**可能原因**

传入的回调触发条件中的条数值为负数。

**处理步骤**

传入自然数值的条数值。

## 11102004 非法的大小值

**错误信息**

Invalid size value. Possible caused by the size value is less than zero.

**错误描述**

在调用addWatcher接口进行事件订阅时，由于回调触发条件传入了非法的事件大小值，系统将忽略此次订阅。

**可能原因**

传入的回调触发条件中的大小值为负数。

**处理步骤**

传入自然数值的大小值。

## 11102005 非法的超时值

**错误信息**

Invalid timeout value. Possible caused by the timeout value is less than zero.

**错误描述**

在调用addWatcher接口进行事件订阅时，由于回调触发条件传入了非法的超时值，系统将忽略此次订阅。

**可能原因**

传入的回调触发条件中的超时值为负数。

**处理步骤**

传入自然数值的超时值。

## 11103001 非法的最大存储配额值

**错误信息**

Invalid max storage quota value. Possible caused by incorrectly formatted.

**错误描述**

在调用configure接口进行打点配置时，由于传入了非法的最大存储配额值，系统将忽略此次配置。

**可能原因**

传入的最大存储配额值字符串不符合以下规则：

- 配额值字符串只由数字字符和大小单位字符（单位字符支持[b|k|kb|m|mb|g|gb|t|tb]，不区分大小写）构成。
- 配额值字符串必须以数字开头，后面可以选择不传单位字符（默认使用byte作为单位），或者以单位字符结尾。

**处理步骤**

传入合法的最大存储配额值字符串。

## 11104001 非法的事件包大小值

**错误信息**

Invalid size value. Possible caused by the size value is less than or equal to zero.

**错误描述**

在调用setSize接口对每次取出的事件包大小阈值进行设置时，由于传入了非法的事件包大小值，系统将忽略此次设置。

**可能原因**

传入的事件包大小值为负数。

**处理步骤**

传入自然数值的事件包大小。

## 11105001 非法的参数值

**错误信息**

Invalid parameter value. Possible causes: 1. Incorrect parameter length; 2. Incorrect parameter format.

**错误描述**

在调用hiAppEvent接口进行传参时，由于传入了非法的参数值，系统将忽略此次设置。

**可能原因**

- 传入的参数长度不符合规格。
- 传入的参数格式不符合规格。

**处理步骤**

传入符合规格的参数值。