---
kits: ["ArkUI / 方舟UI框架"]
description: "扩展屏开发概述，介绍扩展屏场景下屏幕显示模式、坐标转换、显示大小缩放系数（Density）的基本概念，帮助应用适配多屏业务。"
keywords: [扩展屏, 多屏, Display, 显示模式, 坐标转换, Density]
doctype: guide
status: active
---

# 扩展屏开发概述
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @wulong158-->
<!--Tester: @LiTongguan2026-->
<!--Adviser: @ge-yafang-->

## 场景介绍

设备外接扩展屏后，鼠标和窗口可以在[主屏](display-terminology.md#主屏)与[扩展屏](display-terminology.md#扩展屏)之间移动，应用可以同时利用多块屏幕显示内容。多屏环境对应用的显示模式识别、跨屏坐标转换、显示大小缩放系数（Density）适配提出了新的要求。

扩展屏开发主要涉及以下几方面内容：

- **显示模式**：多屏模式下，屏幕可能处于主屏、扩展屏等不同的显示模式。应用可以查询各屏幕当前的显示模式，并监听其变化，以决定在哪些屏幕上创建窗口、显示内容。
- **坐标转换**：多屏模式下，鼠标和窗口可以在主屏与扩展屏之间移动。应用需要把坐标在全局坐标系与相对坐标系之间相互转换，以正确处理鼠标事件和窗口布局。
- **显示大小缩放系数适配**：主屏与扩展屏可分别设置独立的Density，窗口跨屏后其Density会跟随所在屏幕变化，应用需适配该变化以避免界面元素过大或过小。

针对以上内容的详细开发步骤，可见以下指导：

- [获取屏幕显示模式](extended-coordinate-transformation-guideline.md#获取屏幕显示模式)
- [实现扩展屏坐标转换](extended-coordinate-transformation-guideline.md#扩展屏中坐标系的使用)
- [显示大小缩放系数（Density）适配](extended-screen-density.md)

## 约束与限制

扩展屏相关能力及指导，主要适用于PC/2in1设备外接显示器的场景
