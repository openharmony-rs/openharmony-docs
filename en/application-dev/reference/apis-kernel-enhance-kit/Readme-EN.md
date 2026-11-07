# Kernel Enhance Kit
<!--Kit: Kernel Enhance Kit-->
<!--Subsystem: Kernel-->
<!--Owner: @gatieme-->
<!--Designer: @tanyihua-->
<!--Tester: @panny060-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=84e5c687623c619df721fa927b62d6782396d98d translatedAt=2026-11-04T04:57:21.248Z pushedAt=2026-11-04T08:04:44.724Z nl=1 -->

The Kernel Enhance Kit provides system kernel-level enhancement capabilities, supporting QoS (Quality of Service), Purgeable Memory management, and the Gewu Service. Purgeable Memory refers to the purgeable memory mechanism in memory management, and the Gewu Service is a high-performance service component for on-device AI inference. This kit is suitable for scenarios that require fine-grained control over system resource scheduling, memory reclamation, and on-device inference performance, helping developers manage task priorities and system resource allocation more efficiently, thereby improving application runtime efficiency and responsiveness.

- C API<!--kernel-c-->
  - Modules<!--kernel-module-->
    - [QoS](capi-qos.md)
  - Header Files<!--kernel-headerfile-->
    - [qos.h](capi-qos-h.md)
  - Structs<!--kernel-struct-->
    - [OH_QoS_GewuCreateSessionResult](capi-qos-oh-qos-gewucreatesessionresult.md)
    - [OH_QoS_GewuSubmitRequestResult](capi-qos-oh-qos-gewusubmitrequestresult.md)
