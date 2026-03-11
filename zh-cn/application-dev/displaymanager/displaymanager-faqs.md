# 屏幕开发常见问题
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk; @logn-->
<!--Designer: @hejunfei1991-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

<!--RP1-->
<!--RP1End-->

## 虚拟屏中，Display对象的orientation属性值为4表示什么含义

**问题现象**

获取虚拟屏的Display对象后，orientation属性值为4，未在[Orientation](../reference/apis-arkui/js-apis-display.md#orientation10)枚举范围中。

**产生原因**

虚拟屏本身没有物理屏幕，因此无法感知屏幕方向。在未主动设置屏幕方向的情况下，不能返回Orientation枚举中的任一值，此时orientation属性值返回4用于表示屏幕方向未知。