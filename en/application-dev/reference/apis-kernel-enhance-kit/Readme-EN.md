# Kernel Enhance Kit
<!--Kit: Kernel Enhance Kit-->
<!--Subsystem: Kernel-->
<!--Owner: @gatieme-->
<!--Designer: @tanyihua-->
<!--Tester: @panny060-->
<!--Adviser: @fang-jinxu-->

Kernel Enhance Kit provides system kernel-level enhancements, supporting Quality of Service (QoS), Purgeable Memory management, and Gewu service. Purgeable Memory refers to the purgeable memory mechanism within memory management, and the Gewu service is a high-performance service component for on-device AI inference. This kit is intended for scenarios that require fine-grained control over system resource scheduling, memory reclamation, and on-device inference performance, helping you manage task priorities and system resource allocation more efficiently, thereby improving application runtime efficiency and responsiveness.

- C API<!--kernel-c-->
  - Modules<!--kernel-module-->
    - [QoS](capi-qos.md)
  - Header Files<!--kernel-headerfile-->
    - [qos.h](capi-qos-h.md)
  - Structs<!--kernel-struct-->
    - [OH_QoS_GewuCreateSessionResult](capi-qos-oh-qos-gewucreatesessionresult.md)
    - [OH_QoS_GewuSubmitRequestResult](capi-qos-oh-qos-gewusubmitrequestresult.md)
