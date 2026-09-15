# 白平衡相关问题
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 问题现象

白平衡无法使用、手动设置白平衡值不生效、白平衡模式与白平衡手动设置色温值之间的切换问题。

## 可能原因

问题在于白平衡相关接口调用的时序问题，白平衡模式错误导致设置色温值失败。具体原因可能有如下情况：

1. 白平衡模式和手动设置白平衡色温值的时序问题。

2. 手动设置白平衡值失败问题。

**问题分析步骤**

步骤一：白平衡模式和手动设置白平衡值都可以直接单独设置。如果先设置了白平衡模式，则需要将模式首先调整为[WhiteBalanceMode.MANUAL](../../reference/apis-camera-kit/arkts-apis-camera-e.md#whitebalancemode20)，然后才可以手动设置白平衡值；但是如果先手动设置白平衡值，则可以直接设置白平衡模式。

步骤二：手动设置白平衡色温值失败，可以通过查看SetManualWhiteBalance相关log来判断问题，包括session是否已经commit。如果之前设置过白平衡模式，则需要判断是否将白平衡模式调整为[WhiteBalanceMode.MANUAL](../../reference/apis-camera-kit/arkts-apis-camera-e.md#whitebalancemode20)，再进行设置色温值。

相关log搜索关键词：whiteBalance

## 解决措施

正确使用setWhiteBalance的方法：

1. 时序问题：保证在commitConfig之后调用。

2. 色温值范围问题：先调用getWhiteBalanceRange方法获取当前机型支持的色温值范围，然后根据范围取值。如果获取失败，可能该机型或者版本不支持该方法。

3. 如果在设置色温值之前，设置过白平衡模式，需要先将白平衡模式调整为WhiteBalanceMode.MANUAL，再设置色温值。

白平衡示例代码可参考[白平衡设置(ArkTS)](camera-whitebalance.md)。