# About This Kit

<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=45bd746ae860f1fef969073ffaa0af763a0251fa translatedAt=2026-06-29T06:19:47.332Z pushedAt=2026-06-30T03:18:22.693Z -->

Multimodal Awareness Kit allows an application to identify user activities (walking, running, driving, etc.) or postures based on the data collected by sensors including gyroscopes and acceleration sensors built in a HarmonyOS device.

## How Multimodal Awareness Kit Works

Multimodal Awareness Kit is offered by the system as a basic service for applications. Depending on the service scenario, an application needs to initiate a subscription request to the system and cancel the subscription when the service scenario ends. In this process, the system reports the device status information to the application on a real-time basis.

## Constraints

Using multimodal awareness capabilities requires your application to request the relevant permissions from the user. The device must support the sensors required for the intended capabilities.

<!--RP1-->

### Emulator Support

This Kit supports the emulator.

The emulator and physical devices differ in several general ways. For details, see [Differences Between the Emulator and the Real Device](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-emulator-specification).

<!--RP1End-->