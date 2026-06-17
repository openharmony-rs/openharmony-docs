# About This Kit

<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=a1815a6960f035b2f960cbb3747e78fb7c1af4a8 translatedAt=2026-06-15T08:12:44.629Z pushedAt=2026-06-16T13:25:28.186Z -->

Multimodal Awareness Kit allows an application to identify user activities (walking, running, driving, etc.) or postures based on the data collected by sensors including gyroscopes and acceleration sensors built in a HarmonyOS device.

## How Multimodal Awareness Kit Works

Multimodal Awareness Kit is offered by the system as a basic service for applications. Depending on the service scenario, an application needs to initiate a subscription request to the system and cancel the subscription when the service scenario ends. In this process, the system reports the device status information to the application on a real-time basis.

## Constraints

Using multimodal awareness capabilities requires the user to grant the necessary permissions. The device must also support the sensors required by the corresponding capability.