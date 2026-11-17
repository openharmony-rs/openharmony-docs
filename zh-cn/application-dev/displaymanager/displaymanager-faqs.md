---
kits: ["ArkUI / 方舟UI框架"]
description: "汇总屏幕开发中的常见问题，涵盖虚拟屏orientation属性值含义、屏幕方向枚举与实际表现不一致等典型场景，帮助开发者快速定位原因并理解相关概念。"
keywords: [虚拟屏, Display对象, orientation, 屏幕方向]
doctype: faq
status: active
---

# 屏幕开发常见问题
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @wulong158-->
<!--Tester: @LiTongguan2026-->
<!--Adviser: @ge-yafang-->

<!--RP1-->
<!--RP1End-->

## 虚拟屏中，Display对象的orientation属性值为4表示什么含义

**问题现象**

获取虚拟屏的Display对象后，orientation属性值为4，未在[Orientation](../reference/apis-arkui/js-apis-display.md#orientation10)枚举范围中。

**产生原因**

虚拟屏本身没有物理屏幕，因此无法感知屏幕方向。在未主动设置屏幕方向的情况下，不能返回Orientation枚举中的任一值，此时orientation属性值返回4用于表示屏幕方向未知。