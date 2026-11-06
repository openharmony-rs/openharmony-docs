# Kernel Enhance Kit
<!--Kit: Kernel Enhance Kit-->
<!--Subsystem: Kernel-->
<!--Owner: @gatieme-->
<!--Designer: @tanyihua-->
<!--Tester: @panny060-->
<!--Adviser: @fang-jinxu-->

Kernel Enhance Kit（内核增强套件）提供系统内核级别的增强能力，支持QoS（服务质量）、Purgeable Memory管理和格物服务。其中，Purgeable Memory指内存管理中的可清除内存机制，格物服务是用于端侧AI推理的高性能服务组件。该套件适用于需要对系统资源调度、内存回收和端侧推理性能进行精细化控制的场景，帮助开发者更高效地管理任务优先级和系统资源分配，从而提升应用的运行效率和响应速度。

- C API<!--kernel-c-->
  - 模块<!--kernel-module-->
    - [QoS](capi-qos.md)
  - 头文件<!--kernel-headerfile-->
    - [qos.h](capi-qos-h.md)
  - 结构体<!--kernel-struct-->
    - [OH_QoS_GewuCreateSessionResult](capi-qos-oh-qos-gewucreatesessionresult.md)
    - [OH_QoS_GewuSubmitRequestResult](capi-qos-oh-qos-gewusubmitrequestresult.md)
