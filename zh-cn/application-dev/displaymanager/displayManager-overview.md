---
kits: ["ArkUI / 方舟UI框架"]
description: "屏幕管理提供物理屏、虚拟屏和折叠屏的统一管理，支持查询分辨率、像素密度等属性，监听屏幕旋转、折叠等变化并广播给订阅服务，并提供扩展屏的显示模式查询、坐标系转换及显示大小缩放系数（Density）适配能力，虚拟屏能力仅对系统应用开放。"
keywords: [屏幕属性查询, 屏幕状态监听, 屏幕旋转, 虚拟屏, 物理屏, 扩展屏, 显示模式, 坐标转换, Density]
doctype: guide
status: active
---

# 屏幕管理简介
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @wulong158-->
<!--Tester: @LiTongguan2026-->
<!--Adviser: @ge-yafang-->

屏幕管理主要是针对设备的各种屏幕（包括物理屏、虚拟屏、折叠屏）进行管理，管理其各种属性信息，并当作广播者，将监听到的信息广播给各个需要屏幕信息的订阅服务。

屏幕管理主要包括以下几方面能力：

- 可获取屏幕当前的属性信息，包括屏幕分辨率、物理像素密度、屏幕尺寸等。
- 可监听屏幕发生的各种事件变化，包括屏幕旋转变化、屏幕分辨率变化、屏幕刷新率变化、折叠状态变化等。
- 提供扩展屏的相关能力，包括查询屏幕的显示模式（主屏、扩展屏），获取屏幕在全局坐标系中的位置并进行全局坐标与相对坐标的相互转换，以及适配扩展屏的显示大小缩放系数（Density）。
- 提供虚拟屏的创建和使用，此部分能力仅对系统应用开放。

针对以上能力，具体的开发指导如下：

- **屏幕属性查询与监听**：可见[实现屏幕属性查询及状态监听 (C/C++)](native-display-manager.md)和[实现屏幕属性查询及状态监听 (ArkTS)](screenProperty-guideline.md)。
- **扩展屏显示模式与坐标转换**：可见[实现扩展屏坐标转换](extended-coordinate-transformation-guideline.md)。
- **扩展屏Density适配**：可见[显示大小缩放系数（Density）适配](extended-screen-density.md)。
<!--Del-->
- **虚拟屏**：可见[虚拟屏的创建和使用 (ArkTS) (仅对系统应用开放)](virtualScreen-guideline-sys.md)。
<!--DelEnd-->

## 约束和限制

- 需要在支持SystemCapability.Window.SessionManager能力的系统上使用Display和Screen接口，更详细的系统能力请参考<!--RP1-->[系统能力SystemCapability使用指南](../reference/syscap.md)。<!--RP1End-->
- 在多屏实现中，Screen接口仅支持系统应用使用，且部分接口需要申请ohos.permission.CAPTURE_SCREEN权限。