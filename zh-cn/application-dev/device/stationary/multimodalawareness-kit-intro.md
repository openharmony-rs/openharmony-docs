# Multimodal Awareness Kit简介
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

多模态融合感知是利用设备上的多种传感器数据，如加速度计和陀螺仪等，来识别活动、状态和姿态等信息，例如，判断设备是否处于静止状态。

## 运作机制

多模态融合感知能力作为系统为应用提供的一种基础服务，需要应用在所使用的业务场景，向系统主动发起订阅服务，并在业务场景结束时，主动取消订阅服务，在此过程中系统会将实时的设备状态结果上报给应用。

## 约束与限制

使用多模融合感知，需要用户进行相关权限的申请。设备需要支持对应能力所需的传感器。
